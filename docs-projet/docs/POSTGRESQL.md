# 📚 COURS : FONCTIONS POSTGRESQL

> Créer et utiliser des fonctions SQL dans Supabase

---

## 🎯 OBJECTIFS

1. Créer des fonctions PostgreSQL
2. Documenter les fonctions
3. Utiliser les fonctions dans l'app
4. Optimisation et indexation

---

## 📖 POURQUOI DES FONCTIONS ?

### Avantages

- ✅ **Performance** : Traitement côté serveur
- ✅ **Réutilisabilité** : Une fonction, plusieurs usages
- ✅ **Sécurité** : Logique côté serveur
- ✅ **Maintenabilité** : Centralisée

### Cas d'Usage

- Récupérer des données complexes
- Calculs/agrégations
- Filtres avancés
- Stats/dashboard

---

## 🔨 CRÉER UNE FONCTION

### Syntaxe de Base

```sql
CREATE OR REPLACE FUNCTION nom_fonction(parametres)
RETURNS type_retour AS $$
BEGIN
  -- Logique
  RETURN resultat;
END;
$$ LANGUAGE plpgsql;
```

### Exemple 1 : get_user_data

**Objectif** : Récupérer toutes les données d'un utilisateur

```sql
CREATE OR REPLACE FUNCTION get_user_data(user_id UUID)
RETURNS TABLE (
  id UUID,
  email TEXT,
  full_name TEXT,
  events_count INTEGER,
  tickets_count INTEGER
) AS $$
BEGIN
  RETURN QUERY
  SELECT 
    u.id,
    u.email,
    u.full_name,
    COUNT(DISTINCT e.id)::INTEGER as events_count,
    COUNT(DISTINCT t.id)::INTEGER as tickets_count
  FROM auth.users u
  LEFT JOIN events e ON e.organizer_id = u.id
  LEFT JOIN tickets t ON t.user_id = u.id
  WHERE u.id = user_id
  GROUP BY u.id, u.email, u.full_name;
END;
$$ LANGUAGE plpgsql;

-- Documentation
COMMENT ON FUNCTION get_user_data IS 
'Récupère les données complètes d''un utilisateur avec ses stats';
```

### Exemple 2 : list_items_filtered

**Objectif** : Liste avec filtres

```sql
CREATE OR REPLACE FUNCTION list_events_filtered(
  p_status TEXT DEFAULT NULL,
  p_min_date TIMESTAMP DEFAULT NULL,
  p_max_capacity INTEGER DEFAULT NULL
)
RETURNS TABLE (
  id UUID,
  title TEXT,
  date TIMESTAMP WITH TIME ZONE,
  capacity INTEGER,
  status TEXT
) AS $$
BEGIN
  RETURN QUERY
  SELECT 
    e.id,
    e.title,
    e.date,
    e.capacity,
    e.status
  FROM events e
  WHERE 
    (p_status IS NULL OR e.status = p_status)
    AND (p_min_date IS NULL OR e.date >= p_min_date)
    AND (p_max_capacity IS NULL OR e.capacity <= p_max_capacity)
  ORDER BY e.date DESC;
END;
$$ LANGUAGE plpgsql;

COMMENT ON FUNCTION list_events_filtered IS 
'Liste les événements avec filtres optionnels sur status, date, capacité';
```

### Exemple 3 : aggregate_stats

**Objectif** : Stats globales en JSON

```sql
CREATE OR REPLACE FUNCTION get_dashboard_stats()
RETURNS JSON AS $$
DECLARE
  result JSON;
BEGIN
  SELECT json_build_object(
    'total_users', (
      SELECT COUNT(*) FROM auth.users
    ),
    'total_events', (
      SELECT COUNT(*) FROM events
    ),
    'total_tickets', (
      SELECT COUNT(*) FROM tickets
    ),
    'revenue_total', (
      SELECT COALESCE(SUM(price), 0) 
      FROM tickets 
      WHERE status = 'paid'
    ),
    'avg_event_capacity', (
      SELECT ROUND(AVG(capacity), 0) 
      FROM events
    ),
    'upcoming_events', (
      SELECT COUNT(*) 
      FROM events 
      WHERE date > NOW()
    )
  ) INTO result;
  
  RETURN result;
END;
$$ LANGUAGE plpgsql;

COMMENT ON FUNCTION get_dashboard_stats IS 
'Retourne les statistiques globales du dashboard en JSON';
```

---

## 📝 DOCUMENTATION

### Dans PostgreSQL

```sql
-- Commenter la fonction
COMMENT ON FUNCTION get_user_data IS 'Description complète';

-- Voir les commentaires
SELECT 
  p.proname as function_name,
  pg_catalog.obj_description(p.oid, 'pg_proc') as description
FROM pg_catalog.pg_proc p
WHERE p.proname LIKE '%user%';
```

### Dans Notion

**Template documentation fonction** :
```markdown
## get_user_data(user_id)

### Description
Récupère les données complètes d'un utilisateur avec ses statistiques.

### Paramètres
- `user_id` (UUID) : ID de l'utilisateur

### Retour
Table avec :
- id (UUID)
- email (TEXT)
- full_name (TEXT)
- events_count (INTEGER)
- tickets_count (INTEGER)

### Usage
\`\`\`typescript
const { data } = await supabase
  .rpc('get_user_data', { user_id: userId });
\`\`\`

### Exemple retour
\`\`\`json
{
  "id": "...",
  "email": "user@example.com",
  "full_name": "John Doe",
  "events_count": 5,
  "tickets_count": 12
}
\`\`\`
```

---

## 🔗 UTILISER DANS L'APP

### TypeScript Types

```typescript
// src/types/database.ts
export interface UserData {
  id: string;
  email: string;
  full_name: string;
  events_count: number;
  tickets_count: number;
}

export interface DashboardStats {
  total_users: number;
  total_events: number;
  total_tickets: number;
  revenue_total: number;
  avg_event_capacity: number;
  upcoming_events: number;
}
```

### Appel Simple

```typescript
const { data, error } = await supabase
  .rpc('get_user_data', { user_id: userId });

if (error) {
  console.error('Error:', error);
  return;
}

console.log(data); // UserData
```

### Avec Custom Hook

```typescript
// src/hooks/useUserData.ts
import { useQuery } from '@tanstack/react-query';
import { supabase } from '@/config/supabase';
import type { UserData } from '@/types/database';

export function useUserData(userId: string) {
  return useQuery({
    queryKey: ['user-data', userId],
    queryFn: async () => {
      const { data, error } = await supabase
        .rpc('get_user_data', { user_id: userId });
      
      if (error) throw error;
      return data[0] as UserData;
    },
    enabled: !!userId,
  });
}
```

### Dans un Component

```typescript
import { useUserData } from '@/hooks/useUserData';

export function UserProfile({ userId }: { userId: string }) {
  const { data, isLoading, error } = useUserData(userId);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  if (!data) return null;

  return (
    <div>
      <h2>{data.full_name}</h2>
      <p>{data.email}</p>
      <p>Events organized: {data.events_count}</p>
      <p>Tickets purchased: {data.tickets_count}</p>
    </div>
  );
}
```

---

## ⚡ OPTIMISATION

### Index

**Créer des index** pour les colonnes souvent filtrées :

```sql
-- Index sur date pour filtres rapides
CREATE INDEX idx_events_date ON events(date);

-- Index sur foreign keys
CREATE INDEX idx_events_organizer ON events(organizer_id);

-- Index composite
CREATE INDEX idx_events_status_date ON events(status, date);
```

### EXPLAIN ANALYZE

**Analyser les performances** :

```sql
EXPLAIN ANALYZE
SELECT * FROM get_user_data('user-id-here');
```

---

## 🧪 EXERCICE

### Exercice 1 : Créer 2-3 Fonctions

**Fonction 1 : get_user_events**
- Paramètre : user_id
- Retour : Liste des événements de l'utilisateur

**Fonction 2 : get_event_stats**
- Paramètre : event_id
- Retour : Stats de l'événement (tickets vendus, revenus, etc.)

**Fonction 3 (bonus) : search_events**
- Paramètres : query (text), filters
- Retour : Événements correspondants

### Exercice 2 : Documenter

1. Commenter chaque fonction en SQL
2. Créer la doc dans Notion
3. Ajouter les types TypeScript

### Exercice 3 : Utiliser

1. Appeler les fonctions depuis React
2. Créer des custom hooks
3. Afficher les données dans l'UI

---

## ✅ VALIDATION

- [ ] 2-3 fonctions PostgreSQL créées
- [ ] Fonctions commentées (SQL)
- [ ] Documentation dans Notion
- [ ] Types TypeScript définis
- [ ] Fonctions utilisées dans l'app
- [ ] Au moins 1 custom hook

---

## 📚 RESSOURCES

- [PostgreSQL Functions](https://www.postgresql.org/docs/current/sql-createfunction.html)
- [Supabase Edge Functions](https://supabase.com/docs/guides/database/functions)
- [PL/pgSQL Guide](https://www.postgresql.org/docs/current/plpgsql.html)

---

**Durée** : 2-3h  
**Niveau** : Intermédiaire/Avancé  
**Version** : 1.0

