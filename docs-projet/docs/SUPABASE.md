# 📚 Supabase - Backend-as-a-Service

> PostgreSQL + Auth + API temps réel + Storage

---

## 🎯 Vue d'ensemble

**Supabase** est une alternative open-source à Firebase, basée sur PostgreSQL. Il fournit une base de données, une authentification, du storage, et des API auto-générées.

**Site officiel** : https://supabase.com  
**Documentation** : https://supabase.com/docs  
**Dashboard** : https://supabase.com/dashboard

### Composants Principaux

- **Database** : PostgreSQL 15+ avec interface SQL
- **Auth** : Authentification complète (email, OAuth, magic links)
- **Storage** : Stockage de fichiers
- **Edge Functions** : Fonctions serverless
- **Realtime** : Subscriptions temps réel
- **API** : REST API auto-générée

---

## 🚀 Setup Initial

### 1. Créer le Projet

1. Aller sur https://supabase.com/dashboard
2. "New project"
3. Nom, password, région
4. Attendre ~2 min (provisioning)

### 2. Récupérer les Clés

Dashboard → Settings → API

- **URL** : `https://xxx.supabase.co`
- **anon/public key** : Pour le frontend (sécurisée par RLS)
- **service_role key** : Pour les opérations admin (backend/MCP uniquement)

⚠️ **Important** : Ne JAMAIS exposer la `service_role` key côté client !

### 3. Installation SDK

```bash
npm install @supabase/supabase-js
```

### 4. Configuration

**`.env`** :
```env
VITE_SUPABASE_URL=https://xxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJ...
```

**`src/config/supabase.ts`** :
```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseKey);
```

---

## 🔐 Authentification

### Setup Auth Context

**`src/contexts/AuthContext.tsx`** :
```typescript
import { createContext, useContext, useEffect, useState } from 'react';
import { supabase } from '@/config/supabase';
import type { User } from '@supabase/supabase-js';

interface AuthContextType {
  user: User | null;
  loading: boolean;
  signUp: (email: string, password: string) => Promise<void>;
  signIn: (email: string, password: string) => Promise<void>;
  signOut: () => Promise<void>;
}

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export function AuthProvider({ children }: { children: React.ReactNode }) {
  const [user, setUser] = useState<User | null>(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // Check active session
    supabase.auth.getSession().then(({ data: { session } }) => {
      setUser(session?.user ?? null);
      setLoading(false);
    });

    // Listen for auth changes
    const { data: { subscription } } = supabase.auth.onAuthStateChange(
      (_event, session) => {
        setUser(session?.user ?? null);
      }
    );

    return () => subscription.unsubscribe();
  }, []);

  const signUp = async (email: string, password: string) => {
    const { error } = await supabase.auth.signUp({ email, password });
    if (error) throw error;
  };

  const signIn = async (email: string, password: string) => {
    const { error } = await supabase.auth.signInWithPassword({ email, password });
    if (error) throw error;
  };

  const signOut = async () => {
    const { error } = await supabase.auth.signOut();
    if (error) throw error;
  };

  return (
    <AuthContext.Provider value={{ user, loading, signUp, signIn, signOut }}>
      {children}
    </AuthContext.Provider>
  );
}

export const useAuth = () => {
  const context = useContext(AuthContext);
  if (!context) throw new Error('useAuth must be used within AuthProvider');
  return context;
};
```

### Protected Route

```typescript
import { Navigate } from 'react-router-dom';
import { useAuth } from '@/contexts/AuthContext';

export function ProtectedRoute({ children }: { children: React.ReactNode }) {
  const { user, loading } = useAuth();

  if (loading) return <div>Loading...</div>;
  if (!user) return <Navigate to="/login" replace />;

  return <>{children}</>;
}
```

### OAuth (BONUS)

**Configuration** :
1. Dashboard → Authentication → Providers
2. Activer Google/Facebook
3. Configurer OAuth credentials (Client ID/Secret)
4. Configurer les Redirect URLs

**Code** :
```typescript
const signInWithGoogle = async () => {
  const { error } = await supabase.auth.signInWithOAuth({
    provider: 'google',
    options: {
      redirectTo: `${window.location.origin}/auth/callback`
    }
  });
  if (error) throw error;
};
```

**Documentation** :
- Google OAuth : https://supabase.com/docs/guides/auth/social-login/auth-google
- Facebook OAuth : https://supabase.com/docs/guides/auth/social-login/auth-facebook

---

## 🗄️ Base de Données

### Créer une Table

**SQL Editor** :
```sql
CREATE TABLE events (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  title TEXT NOT NULL,
  description TEXT,
  date TIMESTAMP WITH TIME ZONE NOT NULL,
  capacity INTEGER,
  organizer_id UUID REFERENCES auth.users(id),
  created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

### CRUD Operations

**Lecture** :
```typescript
const { data, error } = await supabase
  .from('events')
  .select('*')
  .order('date', { ascending: true });
```

**Lecture avec Filtres** :
```typescript
const { data, error } = await supabase
  .from('events')
  .select('*')
  .eq('organizer_id', userId)
  .gte('date', new Date().toISOString());
```

**Insertion** :
```typescript
// ⚠️ ATTENTION : Pour le projet, insérer dans Airtable, pas Supabase !
const { data, error } = await supabase
  .from('events')
  .insert({
    title: 'Workshop AI',
    date: '2024-12-01',
    capacity: 40
  });
```

**Update** :
```typescript
const { error } = await supabase
  .from('events')
  .update({ capacity: 50 })
  .eq('id', eventId);
```

**Delete** :
```typescript
const { error } = await supabase
  .from('events')
  .delete()
  .eq('id', eventId);
```

---

## ⚡ Fonctions PostgreSQL

### Créer une Fonction

**SQL Editor** :
```sql
CREATE OR REPLACE FUNCTION get_user_events(user_id UUID)
RETURNS TABLE (
  id UUID,
  title TEXT,
  date TIMESTAMP WITH TIME ZONE,
  tickets_count INTEGER
) AS $$
BEGIN
  RETURN QUERY
  SELECT 
    e.id,
    e.title,
    e.date,
    COUNT(t.id)::INTEGER as tickets_count
  FROM events e
  LEFT JOIN tickets t ON t.event_id = e.id
  WHERE e.organizer_id = user_id
  GROUP BY e.id, e.title, e.date
  ORDER BY e.date DESC;
END;
$$ LANGUAGE plpgsql;

-- Documentation
COMMENT ON FUNCTION get_user_events IS 'Récupère tous les événements d''un utilisateur avec le nombre de tickets';
```

### Appeler la Fonction

```typescript
const { data, error } = await supabase
  .rpc('get_user_events', { user_id: userId });
```

### Exemple : Fonction de Stats

```sql
CREATE OR REPLACE FUNCTION get_dashboard_stats()
RETURNS JSON AS $$
DECLARE
  result JSON;
BEGIN
  SELECT json_build_object(
    'total_users', (SELECT COUNT(*) FROM auth.users),
    'total_events', (SELECT COUNT(*) FROM events),
    'total_tickets', (SELECT COUNT(*) FROM tickets),
    'revenue', (SELECT SUM(price) FROM tickets WHERE status = 'paid')
  ) INTO result;
  
  RETURN result;
END;
$$ LANGUAGE plpgsql;

COMMENT ON FUNCTION get_dashboard_stats IS 'Retourne les statistiques globales du dashboard';
```

**Utilisation** :
```typescript
const { data, error } = await supabase.rpc('get_dashboard_stats');
// data = { total_users: 150, total_events: 25, ... }
```

---

## 🔒 Row Level Security (RLS)

### Activer RLS

```sql
ALTER TABLE events ENABLE ROW LEVEL SECURITY;
```

### Policies

**Lecture publique** :
```sql
CREATE POLICY "Events are viewable by everyone"
ON events FOR SELECT
USING (true);
```

**Modification par owner** :
```sql
CREATE POLICY "Users can update own events"
ON events FOR UPDATE
USING (auth.uid() = organizer_id);
```

**Insertion authentifiée** :
```sql
CREATE POLICY "Authenticated users can create events"
ON events FOR INSERT
WITH CHECK (auth.role() = 'authenticated');
```

**Suppression par owner** :
```sql
CREATE POLICY "Users can delete own events"
ON events FOR DELETE
USING (auth.uid() = organizer_id);
```

### Tester les Policies

```sql
-- Tester en tant qu'utilisateur spécifique
SET request.jwt.claim.sub = 'user-uuid-here';
SELECT * FROM events;
```

**Documentation** : https://supabase.com/docs/guides/database/postgres/row-level-security

---

## 🔄 Synchronisation avec Airtable

### Architecture (Important pour le Projet)

```
Airtable (Écriture) ─sync→ Supabase (Lecture)
       ↑                           ↓
     Admin                   Application
```

**Règle d'or** : L'application lit UNIQUEMENT depuis Supabase, écrit dans Airtable.

### Setup Sync

1. **Airtable** : Installer extension "Supabase Sync"
2. **Configuration** : Entrer URL + Service Role Key Supabase
3. **Mapping** : Mapper tables Airtable → Supabase
4. **Test** : Insert dans Airtable → Vérifier Supabase

**Documentation Sync** :
- Guide Supabase : https://supabase.com/docs/guides/integrations/airtable

---

## 📚 Ressources

### Documentation Officielle
- **Quick Start** : https://supabase.com/docs/guides/getting-started
- **Auth Guide** : https://supabase.com/docs/guides/auth
- **Database** : https://supabase.com/docs/guides/database
- **Functions** : https://supabase.com/docs/guides/database/functions
- **RLS** : https://supabase.com/docs/guides/database/postgres/row-level-security

### Frameworks Quickstarts
- **React** : https://supabase.com/docs/guides/getting-started/quickstarts/reactjs
- **Vite** : https://supabase.com/docs/guides/getting-started/quickstarts/react
- **React Native / Expo** : https://supabase.com/docs/guides/getting-started/quickstarts/react-native

### Community
- **Discord** : https://discord.supabase.com
- **GitHub** : https://github.com/supabase/supabase
- **Blog** : https://supabase.com/blog

---

## 💡 Best Practices

### Sécurité
- ✅ Toujours activer RLS sur les tables
- ✅ Tester les policies RLS avant déploiement
- ⚠️ Ne JAMAIS exposer la `service_role` key côté client
- ✅ Utiliser des policies granulaires
- ✅ Documenter les policies

### Performance
- ✅ Utiliser les fonctions PostgreSQL pour logique complexe
- ✅ Créer des index sur les colonnes fréquemment filtrées
- ✅ Utiliser `.select()` pour limiter les colonnes
- ✅ Paginer les résultats avec `.range()`

### Architecture Projet
- ✅ Lire depuis Supabase (rapide)
- ✅ Écrire dans Airtable (interface admin)
- ❌ Ne PAS insérer directement dans Supabase (contourne Airtable)
- ✅ Documenter toutes les fonctions PostgreSQL

---

## ❓ FAQ

**Pourquoi lire de Supabase et écrire dans Airtable ?**
- Supabase : Optimisé pour les lectures (PostgreSQL performant)
- Airtable : Interface no-code pour les admins
- Sync unidirectionnel : Airtable → Supabase

**Comment tester les RLS policies ?**
- Utiliser le SQL Editor avec `SET request.jwt.claim.sub`
- Tester depuis l'application avec différents users

**Puis-je utiliser Supabase sans RLS ?**
- Techniquement oui, mais **fortement déconseillé** (risque de data leak)

---

**Dernière mise à jour** : 25 novembre 2025  
**PostgreSQL Version** : 15.x  
**Basé sur** : [Documentation officielle Supabase](https://supabase.com/docs)

