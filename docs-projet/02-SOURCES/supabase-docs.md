# 📚 DOCUMENTATION SUPABASE

**Site officiel** : https://supabase.com  
**Documentation** : https://supabase.com/docs  
**Dashboard** : https://supabase.com/dashboard

---

## 🎯 RESSOURCES PRINCIPALES

### Getting Started
- **Quick Start** : https://supabase.com/docs/guides/getting-started
- **Architecture** : https://supabase.com/docs/guides/getting-started/architecture
- **Auth Quickstart** : https://supabase.com/docs/guides/auth/quickstarts
- **Database Quickstart** : https://supabase.com/docs/guides/database/overview

### Authentication (Supabase Auth)
- **Auth Overview** : https://supabase.com/docs/guides/auth
- **Email/Password** : https://supabase.com/docs/guides/auth/auth-email
- **Magic Link** : https://supabase.com/docs/guides/auth/auth-magic-link
- **OAuth Providers** : https://supabase.com/docs/guides/auth/social-login
  - Google : https://supabase.com/docs/guides/auth/social-login/auth-google
  - Facebook : https://supabase.com/docs/guides/auth/social-login/auth-facebook
  - GitHub : https://supabase.com/docs/guides/auth/social-login/auth-github
- **Protected Routes** : https://supabase.com/docs/guides/auth/managing-user-data
- **Server-Side Auth** : https://supabase.com/docs/guides/auth/server-side

### Database (PostgreSQL 15+)
- **PostgreSQL Overview** : https://supabase.com/docs/guides/database/overview
- **Tables & Data** : https://supabase.com/docs/guides/database/tables
- **Functions** : https://supabase.com/docs/guides/database/functions
- **Triggers** : https://supabase.com/docs/guides/database/triggers
- **RLS (Row Level Security)** : https://supabase.com/docs/guides/database/postgres/row-level-security
- **Extensions** : https://supabase.com/docs/guides/database/extensions

### API
- **Auto-generated REST API** : https://supabase.com/docs/guides/api
- **Realtime** : https://supabase.com/docs/guides/realtime
- **GraphQL** : https://supabase.com/docs/guides/api/graphql
- **Webhooks** : https://supabase.com/docs/guides/database/webhooks

### Storage
- **File Storage** : https://supabase.com/docs/guides/storage
- **Image Transformations** : https://supabase.com/docs/guides/storage/serving/image-transformations

### Edge Functions
- **Overview** : https://supabase.com/docs/guides/functions
- **Quickstart** : https://supabase.com/docs/guides/functions/quickstart
- **Deploy** : https://supabase.com/docs/guides/functions/deploy

---

## 💻 CLIENT LIBRARIES & INTEGRATION

### JavaScript / TypeScript
- **supabase-js** : https://supabase.com/docs/reference/javascript/introduction
- **Installation** : `npm install @supabase/supabase-js`
- **TypeScript Support** : Full, avec types auto-générés

### Framework Quickstarts (2025)
- **React** : https://supabase.com/docs/guides/getting-started/quickstarts/reactjs
- **Next.js** : https://supabase.com/docs/guides/getting-started/quickstarts/nextjs
- **Vite** : https://supabase.com/docs/guides/getting-started/quickstarts/react
- **React Native / Expo** : https://supabase.com/docs/guides/getting-started/quickstarts/react-native
- **Vue** : https://supabase.com/docs/guides/getting-started/quickstarts/vue
- **Svelte** : https://supabase.com/docs/guides/getting-started/quickstarts/sveltekit

### MCP Supabase (Cursor)
- **GitHub** : https://github.com/modelcontextprotocol/servers/tree/main/supabase
- **Installation** : Voir cours MCP
- **Usage** : Intégration directe dans Cursor

---

## 🔧 SETUP RAPIDE

### 1. Créer un Projet
1. Aller sur https://supabase.com/dashboard
2. "New Project"
3. Noter l'URL et l'anon key

### 2. Installation Client
```bash
npm install @supabase/supabase-js
```

### 3. Configuration
```typescript
// lib/supabase.ts
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = process.env.VITE_SUPABASE_URL!
const supabaseAnonKey = process.env.VITE_SUPABASE_ANON_KEY!

export const supabase = createClient(supabaseUrl, supabaseAnonKey)
```

### 4. Premier Query
```typescript
// Lire des données
const { data, error } = await supabase
  .from('users')
  .select('*')

// Insérer (via Airtable pour le cours!)
// Ne PAS faire d'insert direct dans Supabase
```

---

## 🔐 AUTHENTIFICATION EXEMPLE

### Signup
```typescript
const { data, error } = await supabase.auth.signUp({
  email: 'user@example.com',
  password: 'password123'
})
```

### Login
```typescript
const { data, error } = await supabase.auth.signInWithPassword({
  email: 'user@example.com',
  password: 'password123'
})
```

### OAuth (Google)
```typescript
const { data, error } = await supabase.auth.signInWithOAuth({
  provider: 'google',
  options: {
    redirectTo: 'http://localhost:5173/auth/callback'
  }
})
```

### Logout
```typescript
await supabase.auth.signOut()
```

### Protected Route
```typescript
const { data: { session } } = await supabase.auth.getSession()
if (!session) {
  // Redirect to login
}
```

---

## 🗄️ DATABASE FUNCTIONS

### Créer une Fonction SQL
```sql
CREATE OR REPLACE FUNCTION get_user_stats(user_id UUID)
RETURNS TABLE(
  total_posts INT,
  total_likes INT
) AS $$
BEGIN
  RETURN QUERY
  SELECT 
    COUNT(DISTINCT p.id)::INT as total_posts,
    COUNT(DISTINCT l.id)::INT as total_likes
  FROM users u
  LEFT JOIN posts p ON p.user_id = u.id
  LEFT JOIN likes l ON l.post_id = p.id
  WHERE u.id = $1;
END;
$$ LANGUAGE plpgsql;

COMMENT ON FUNCTION get_user_stats IS 'Retourne les statistiques d''un utilisateur';
```

### Appeler depuis le Code
```typescript
const { data, error } = await supabase
  .rpc('get_user_stats', { user_id: 'uuid-here' })
```

---

## 🔒 ROW LEVEL SECURITY (RLS)

### Activer RLS
```sql
ALTER TABLE posts ENABLE ROW LEVEL SECURITY;
```

### Policy Exemple
```sql
-- Les utilisateurs voient uniquement leurs posts
CREATE POLICY "Users can view own posts"
ON posts FOR SELECT
USING (auth.uid() = user_id);

-- Les utilisateurs peuvent créer leurs posts
CREATE POLICY "Users can create own posts"
ON posts FOR INSERT
WITH CHECK (auth.uid() = user_id);
```

---

## 🔄 SYNCHRONISATION AIRTABLE ↔ SUPABASE

### Architecture (Important pour le cours)
- **Lecture** : Application → Supabase (rapide)
- **Écriture** : Admin → Airtable → Sync → Supabase

### Setup Sync
1. **Airtable** : Installer extension "Supabase Sync"
2. **Configuration** : Entrer URL + Service Role Key Supabase
3. **Mapping** : Mapper tables Airtable → Supabase
4. **Test** : Insert dans Airtable → Vérifier Supabase

### Documentation Sync
- Guide Supabase : https://supabase.com/docs/guides/integrations/airtable
- Extension Airtable Marketplace

---

## 📚 TUTORIELS OFFICIELS

### Essentiels
- **User Management** : https://supabase.com/docs/guides/getting-started/tutorials/with-react
- **Database Design** : https://supabase.com/docs/guides/database/design
- **Auth Deep Dive** : https://supabase.com/docs/guides/auth/auth-deep-dive

### Avancés
- **Multi-tenancy avec RLS** : https://supabase.com/docs/guides/database/postgres/row-level-security
- **Realtime Subscriptions** : https://supabase.com/docs/guides/realtime/postgres-changes

---

## 💡 TIPS POUR LE COURS

### Best Practices
- ✅ Toujours activer RLS sur les tables
- ✅ Utiliser les fonctions PostgreSQL pour logique complexe
- ✅ Lire depuis Supabase, écrire dans Airtable
- ✅ Tester les policies RLS avant déploiement
- ⚠️ Ne JAMAIS exposer la `service_role` key côté client

### Common Pitfalls
- ❌ Oublier d'activer RLS → data leak
- ❌ Insert direct dans Supabase → contourne Airtable
- ❌ Mauvaise configuration OAuth redirect URLs
- ❌ Ne pas gérer les erreurs d'auth

---

## 🔗 RESSOURCES COMPLÉMENTAIRES

### Community
- **Discord** : https://discord.supabase.com
- **GitHub** : https://github.com/supabase/supabase
- **Twitter/X** : https://twitter.com/supabase
- **Blog** : https://supabase.com/blog

### Tools
- **SQL Editor** : Dans le dashboard
- **Table Editor** : Interface no-code
- **API Docs** : Auto-générées par projet
- **CLI** : https://supabase.com/docs/guides/cli

---

**Dernière MAJ** : 25 novembre 2025  
**PostgreSQL Version** : 15.x  
**Maintenu par** : Thomas Garcia

