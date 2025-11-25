# 📚 COURS : SUPABASE

> Base de données PostgreSQL + Auth + API temps réel

---

## 🎯 OBJECTIFS

1. Setup projet Supabase
2. Authentification complète
3. Créer des fonctions PostgreSQL
4. Row Level Security (RLS)
5. Integration avec React

---

## 🚀 SETUP INITIAL

### 1. Créer le Projet

1. https://supabase.com → "New project"
2. Nom, password, région
3. Attendre ~2 min (provisioning)

### 2. Récupérer les Clés

Dashboard → Settings → API

- **URL** : `https://xxx.supabase.co`
- **anon/public key** : Pour le frontend
- **service_role key** : Pour les opérations admin (backend/MCP)

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

## 🔐 AUTHENTIFICATION

### Setup Auth

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
3. Configurer OAuth credentials

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

---

## 🗄️ BASE DE DONNÉES

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

**Insertion** :
```typescript
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

## ⚡ FONCTIONS POSTGRESQL

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
```

---

## 🔒 ROW LEVEL SECURITY (RLS)

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

---

## 🔄 SYNC AVEC AIRTABLE

### Configuration

1. Dashboard Supabase → SQL Editor
2. Créer tables identiques à Airtable
3. Dans Airtable → Extensions → Supabase
4. Configurer URL + Service Role Key
5. Mapper les champs

### Architecture

```
Airtable (Écriture) ─sync→ Supabase (Lecture)
       ↑                           ↓
     Admin                   Application
```

**Important** : App lit UNIQUEMENT depuis Supabase

---

## 🧪 EXERCICE

### Exercice 1 : Setup Complet

1. Créer projet Supabase
2. Configurer auth dans React
3. Créer pages Login/Signup
4. Tester l'authentification

### Exercice 2 : BDD + Fonctions

1. Créer 3 tables liées
2. Créer 2 fonctions PostgreSQL
3. Documenter les fonctions
4. Les appeler depuis React

---

## 📚 RESSOURCES

- [Supabase Docs](https://supabase.com/docs)
- [Auth Guide](https://supabase.com/docs/guides/auth)
- [PostgreSQL Functions](https://supabase.com/docs/guides/database/functions)

---

## ✅ VALIDATION

- [ ] Projet Supabase créé
- [ ] Auth complète fonctionnelle
- [ ] Tables créées
- [ ] 2-3 fonctions PostgreSQL
- [ ] RLS configuré
- [ ] Sync Airtable active

---

**Durée** : 3-4h  
**Niveau** : Intermédiaire  
**Version** : 1.0

