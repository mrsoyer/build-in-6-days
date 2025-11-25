# 📚 CURSOR RULES & FORMAT .MDC

> Documentation sur les Cursor Rules et le format Markdown Context

---

## 🔗 DOCUMENTATION OFFICIELLE

### Cursor Rules
- **Documentation** : https://docs.cursor.com/context/rules
- **Examples** : https://github.com/PatrickJS/awesome-cursorrules
- **Community Rules** : https://cursor.directory

---

## 📖 QU'EST-CE QU'UNE CURSOR RULE ?

Les **Cursor Rules** sont des fichiers qui définissent le contexte et les conventions pour l'IA.

**Avantages** :
- ✅ Cohérence du code généré
- ✅ Respect automatique des conventions
- ✅ Réduction des répétitions dans les prompts
- ✅ Meilleure qualité de code
- ✅ Onboarding facilité

---

## 📝 FORMAT .MDC (MARKDOWN CONTEXT)

### Définition
Le format **.mdc** est une extension de Markdown optimisée pour le contexte IA.

**Caractéristiques** :
- Syntaxe Markdown standard
- Métadonnées structurées
- Sections clairement définies
- Facilite la lecture par l'IA

### Structure Recommandée
```markdown
# [Titre du Rule]

## Context
[Description du contexte général]

## Technical Stack
- Framework: [...]
- Language: [...]
- Tools: [...]

## Conventions
### Naming
[Règles de nommage]

### Code Style
[Style de code]

### File Structure
[Organisation des fichiers]

## Examples
[Exemples concrets]
```

---

## 🎯 TYPES DE CURSOR RULES

### 1. `.cursorrules` (Principal)
**Usage** : Règles globales du projet

**Contenu typique** :
- Stack technique
- Architecture
- Conventions générales
- Configuration MCP
- Liens vers autres rules

**Exemple** :
```markdown
# Project: EventFlow
# Tech Stack: React + TypeScript + Supabase + Airtable

## Architecture
- Read: Supabase (PostgreSQL)
- Write: Airtable (No-code interface)
- Auth: Supabase Auth
- Deploy: Netlify

## MCP Configuration
- @notion: Project documentation
- @supabase: Database operations
- @airtable: Data entry

## Code Conventions
- Language: TypeScript (strict mode)
- Style: ESLint + Prettier
- Components: Functional components with hooks
- State: Zustand for global state

## File Structure
src/
  components/  # Reusable UI components
  pages/       # Page components
  hooks/       # Custom hooks
  utils/       # Helper functions
  types/       # TypeScript types

## Linked Rules
- @cursorrules-auth: Authentication features
- @cursorrules-dashboard: Dashboard features
- @cursorrules-docs: Documentation generation
```

### 2. `.cursorrules-[feature]` (Par Fonctionnalité)
**Usage** : Règles spécifiques à une feature

**Exemples** :
- `.cursorrules-auth` : Authentification
- `.cursorrules-dashboard` : Dashboard
- `.cursorrules-api` : API calls
- `.cursorrules-ui` : Composants UI

**Exemple `.cursorrules-auth`** :
```markdown
# Authentication Feature

## Context
Handle user authentication using Supabase Auth.

## Requirements
- Email/Password auth
- Protected routes
- Session persistence
- Role-based access

## Code Style
- All auth logic in src/auth/
- Use AuthContext for state
- Custom hook: useAuth()
- Types in src/types/auth.ts

## Protected Routes
```typescript
// Use ProtectedRoute HOC
<ProtectedRoute>
  <Dashboard />
</ProtectedRoute>

// Or useAuth hook
const { user, loading } = useAuth();
if (!user) return <Navigate to="/login" />;
```

## Error Handling
- Show user-friendly messages
- Log technical errors
- Redirect on auth failure

## Testing
- Test login/signup flows
- Test protected routes
- Test session persistence
```

### 3. `.cursorrules-installation` (Setup)
**Usage** : Installation automatisée du projet

**Objectif** : Un développeur peut installer le projet simplement en appelant ce rule.

**Exemple** :
```markdown
# Project Installation Guide

## Prerequisites Check
- Node.js >= 18.0.0
- npm >= 9.0.0
- Git

## Installation Steps
1. Clone repository
2. Install dependencies: `npm install`
3. Copy `.env.example` to `.env`
4. Configure environment variables
5. Run database migrations
6. Seed database (optional)
7. Start dev server: `npm run dev`

## Environment Variables Required
```env
VITE_SUPABASE_URL=https://xxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJ...
VITE_AIRTABLE_API_KEY=key...
VITE_AIRTABLE_BASE_ID=app...
```

## Verification
- Run `npm run test` (all tests pass)
- Access http://localhost:5173
- Login with test account

## Troubleshooting
- Port 5173 in use: Change in vite.config.ts
- Dependencies fail: Try `npm clean-install`
- Env vars missing: Check `.env` file
```

### 4. `.cursorrules-docs` (Documentation)
**Usage** : Génération et maintenance de la documentation

**Exemple** :
```markdown
# Documentation Rules

## Documentation Style
- Tone: Professional but friendly
- Audience: Developers (tech) and Product Managers (non-tech)
- Language: English for code, French for business docs

## Notion Integration
Use @notion MCP to update documentation automatically.

## Structure
Main sections:
1. Overview
2. Architecture
3. Features
4. API Reference
5. Deployment
6. Team & Contributions

## Auto-Update Triggers
- New feature merged → Update features list
- Database schema change → Update architecture
- New endpoint → Update API reference

## Code Comments
- Functions: JSDoc format
- Complex logic: Inline comments
- TODOs: // TODO: [description]
```

---

## 🎯 BEST PRACTICES

### 1. Clarté
- ✅ Titres descriptifs
- ✅ Sections bien définies
- ✅ Exemples concrets
- ❌ Éviter les ambiguïtés

### 2. Maintien
- ✅ Mettre à jour régulièrement
- ✅ Refléter l'état actuel du projet
- ✅ Supprimer les règles obsolètes
- ❌ Ne pas laisser vieillir

### 3. Organisation
- ✅ Un fichier par concern
- ✅ Hiérarchie logique
- ✅ Liens entre files
- ❌ Éviter la duplication

### 4. Exemples
- ✅ Code examples inclus
- ✅ Cas d'usage réels
- ✅ Anti-patterns à éviter
- ❌ Ne pas rester théorique

---

## 📚 EXEMPLES DE CURSOR RULES AVANCÉES

### Rule pour Testing
```markdown
# Testing Rules

## Framework
- Jest + React Testing Library
- Coverage minimum: 80%

## Structure
src/
  __tests__/
    unit/
    integration/
  components/__tests__/

## Naming
- Unit: [ComponentName].test.tsx
- Integration: [Feature].integration.test.tsx

## What to Test
✅ User interactions
✅ Data flows
✅ Error states
✅ Edge cases

❌ Implementation details
❌ Third-party libraries
```

### Rule pour API Calls
```markdown
# API Rules

## Architecture
- All API calls in src/api/
- Use custom hooks (useQuery, useMutation)
- Error handling centralized

## Example
```typescript
// src/api/users.ts
export const getUsers = async () => {
  const { data, error } = await supabase
    .from('users')
    .select('*');
  
  if (error) throw new Error(error.message);
  return data;
};

// Usage in component
const { data, isLoading, error } = useQuery('users', getUsers);
```

## Error Handling
- Show toast notification
- Log to monitoring (Sentry)
- Fallback UI
```

---

## 🔗 RESSOURCES

### Collections
- **awesome-cursorrules** : https://github.com/PatrickJS/awesome-cursorrules
- **cursor.directory** : https://cursor.directory
- **Cursor Community** : https://community.cursor.com

### Exemples par Stack
- **React + TypeScript** : https://cursor.directory/react-typescript
- **Next.js** : https://cursor.directory/nextjs
- **Vue** : https://cursor.directory/vue

---

**Dernière mise à jour** : 25 novembre 2025  
**Maintenu par** : Thomas Garcia

