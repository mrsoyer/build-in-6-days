# 📚 COURS : CURSOR RULES & OPTIMISATION

> Maîtriser les Cursor Rules, les modes d'IA, et optimiser la production

---

## 🎯 OBJECTIFS D'APPRENTISSAGE

À la fin de ce cours, vous saurez :
1. Créer et organiser des Cursor Rules efficaces
2. Choisir le bon mode Cursor (Agent, Task, Plan)
3. Optimiser vos prompts pour économiser tokens et temps
4. Produire du code rapidement et de qualité

---

## 📖 PARTIE 1 : PHILOSOPHIE DES CURSOR RULES

### Qu'est-ce qu'une Cursor Rule ?

Les **Cursor Rules** sont des fichiers qui définissent le **contexte** et les **conventions** pour l'IA.

**Analogie** : C'est comme donner un manuel d'instructions à un nouveau développeur qui rejoint l'équipe.

**Sans Cursor Rules** :
```
Vous : "Crée un composant Button"
Cursor : Crée un bouton basique en JavaScript
Vous : "Non, en TypeScript"
Cursor : Refait en TypeScript
Vous : "Utilise Tailwind"
Cursor : Refait avec Tailwind
Vous : "Follow nos conventions"
...
```

**Avec Cursor Rules** :
```
Vous : "Crée un composant Button"
Cursor : Crée directement en TypeScript + Tailwind + vos conventions ✅
```

### Avantages

- ✅ **Cohérence** : Même style de code partout
- ✅ **Rapidité** : Moins de corrections
- ✅ **Qualité** : Standards respectés automatiquement
- ✅ **Onboarding** : Nouveau dev = lire les rules
- ✅ **Économie** : Moins de tokens utilisés

---

## 📝 PARTIE 2 : STRUCTURE HYBRIDE

### Les 4 Fichiers Obligatoires

#### 1. `.cursorrules` (Principal)

**Rôle** : Règles globales du projet

**Contenu** :
```markdown
# Project: [Nom]
# Tech Stack: [Stack]

## MCP Configuration
- @notion: [Project ID]
- @supabase: [Project URL]
- @airtable: [Base ID]

## Architecture
- Read: Supabase (PostgreSQL)
- Write: Airtable (No-code)
- Auth: Supabase Auth

## Technical Constraints
- Language: TypeScript (strict mode)
- Framework: React 18
- Style: Tailwind CSS
- State: Zustand

## Code Conventions
- Functional components only
- Custom hooks for logic (src/hooks/)
- Types in src/types/
- Utils in src/utils/

## File Structure
src/
  components/  # Reusable UI
  pages/       # Page components
  hooks/       # Custom hooks
  utils/       # Helpers
  types/       # TypeScript types
  api/         # API calls

## Linked Rules
- @cursorrules-auth: Authentication
- @cursorrules-dashboard: Dashboard
- @cursorrules-installation: Setup
- @cursorrules-docs: Documentation
```

#### 2. `.cursorrules-docs` (Documentation)

**Rôle** : Génération et maintenance de la doc

**Contenu** :
```markdown
# Documentation Rules

## Style
- Tone: Professional but friendly
- Audience: Tech (devs) + Non-tech (PMs)
- Language: English

## Notion Integration
Use @notion MCP to update docs automatically.

## Sections
1. Overview
2. Architecture
3. Features
4. API Reference
5. Deployment

## Auto-Update
- New feature → Update features list
- Schema change → Update architecture
- New endpoint → Update API docs

## Comments
- Functions: JSDoc format
- Complex logic: Inline comments
- TODOs: // TODO: [desc]
```

#### 3. `.cursorrules-installation` (Setup)

**Rôle** : Installation automatisée

**Contenu** :
```markdown
# Installation Guide

## Prerequisites
- Node.js >= 18
- npm >= 9
- Git

## Steps
1. Clone: `git clone [URL]`
2. Install: `npm install`
3. Env: Copy `.env.example` to `.env`
4. Configure env variables
5. Start: `npm run dev`

## Required Env Variables
```env
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
VITE_AIRTABLE_API_KEY=
VITE_AIRTABLE_BASE_ID=
```

## Verification
- Run `npm run test`
- Access http://localhost:5173
- Login with test account

## Troubleshooting
- Port in use: Change in vite.config.ts
- Dependencies fail: `npm clean-install`
```

#### 4. `.cursorrules-[feature]` (Par Fonctionnalité)

**Exemples** :
- `.cursorrules-auth`
- `.cursorrules-dashboard`
- `.cursorrules-api`

**Contenu exemple (auth)** :
```markdown
# Authentication Feature

## Context
User auth with Supabase Auth.

## Requirements
- Email/Password auth
- Protected routes
- Session persistence
- Role-based access

## Code Style
- All auth logic in src/auth/
- Use AuthContext
- Custom hook: useAuth()
- Types: src/types/auth.ts

## Protected Routes
```typescript
<ProtectedRoute>
  <Dashboard />
</ProtectedRoute>
```

## Error Handling
- User-friendly messages
- Log technical errors
- Redirect on failure
```

---

## ⚡ PARTIE 3 : LES 3 MODES DE CURSOR

### Comprendre les Modes

| Mode | Usage | Vitesse | Coût | Contrôle |
|------|-------|---------|------|----------|
| **Task (Editor)** | Edit précis | ⚡⚡⚡ | 💰 | 🎯🎯🎯 |
| **Agent** | Tâche autonome | ⚡⚡ | 💰💰 | 🎯 |
| **Plan** | Feature complexe | ⚡ | 💰💰💰 | 🎯🎯 |

### 1. Mode Task (Editor) - `Cmd+I`

**Quand l'utiliser** :
- ✅ Modification dans UN fichier
- ✅ Changement précis et ciblé
- ✅ Correction rapide
- ✅ Refactoring local

**Avantages** :
- Très rapide
- Économique en tokens
- Contrôle total

**Comment optimiser** :
1. **Sélectionner** le code à modifier
2. Prompt **court et précis**
3. **Une seule action** à la fois
4. **Vérifier** immédiatement

**Exemples** :

❌ **Mauvais** :
```
"Améliore ce code"
```

✅ **Bon** :
```
"Ajoute la validation Zod sur email et password"
```

❌ **Mauvais** :
```
"Refactorise tout ce composant pour qu'il soit mieux"
```

✅ **Bon** :
```
"Extract la logique de fetch dans un custom hook useUsers"
```

### 2. Mode Agent - `Cmd+L`

**Quand l'utiliser** :
- ✅ Tâche multi-fichiers
- ✅ Création de feature complète
- ✅ Refactoring important
- ✅ Modifications coordonnées

**Avantages** :
- Autonomie complète
- Gère plusieurs fichiers
- Planifie avant d'agir

**Comment optimiser** :
1. **Contexte clair** et complet
2. **Spécifier les fichiers** concernés
3. **Définir les contraintes**
4. **Laisser travailler** sans interrompre

**Exemples** :

❌ **Mauvais** :
```
"Fais l'auth"
```

✅ **Bon** :
```
"Crée un système d'authentification complet :
- Pages Login et Signup (src/pages/auth/)
- AuthContext (src/contexts/AuthContext.tsx)
- Hook useAuth (src/hooks/useAuth.ts)
- ProtectedRoute HOC (src/components/ProtectedRoute.tsx)
- Types (src/types/auth.ts)

Utilise Supabase Auth.
Style avec Tailwind.
Intègre avec React Router."
```

❌ **Mauvais** :
```
"Crée des composants"
```

✅ **Bon** :
```
"Crée les composants UI manquants :
- Button (variants: primary, secondary, ghost)
- Input (avec validation visuelle)
- Card (avec header, body, footer)

Fichiers : src/components/ui/
Style : Tailwind
Types : TypeScript strict
Accessibilité : ARIA labels"
```

### 3. Mode Plan - `Cmd+Shift+L`

**Quand l'utiliser** :
- ✅ Feature complexe majeure
- ✅ Architecture importante
- ✅ Refactoring massif
- ✅ Besoin de planification

**Avantages** :
- Planifie AVANT d'agir
- Vous gardez le contrôle
- Modifications coordonnées
- Architecture réfléchie

**Comment optimiser** :
1. **Décrire l'objectif global**
2. **Laisser Cursor planifier**
3. **Valider le plan**
4. **Ajuster si nécessaire**
5. **Exécuter étape par étape**

**Exemples** :

❌ **Mauvais** :
```
"Fais un dashboard"
```

✅ **Bon** :
```
"En mode Plan, crée un dashboard admin complet :

Features :
- Vue d'ensemble avec KPIs (users, events, revenue)
- Liste des utilisateurs avec filtres
- Graphiques de stats (Chart.js)
- Filtres par date (date picker)
- Export CSV
- Responsive

Architecture :
- Page : src/pages/admin/Dashboard.tsx
- Components : src/components/admin/
- API calls : src/api/admin.ts
- Hooks : src/hooks/useAdminData.ts

Data source : Supabase (fonctions PostgreSQL)

Propose un plan AVANT d'exécuter."
```

---

## 💰 PARTIE 4 : OPTIMISATION & ÉCONOMIE

### Économie de Tokens

**1 token** ≈ 0.75 mots  
**Context window** : ~200K tokens (Claude 3.5 Sonnet)

#### Techniques d'Économie

✅ **1. Contexte Minimal**

❌ Inclure tout le codebase  
✅ Inclure seulement les fichiers pertinents

```
# Mauvais
[Colle 50 fichiers]

# Bon
@src/types/user.ts
@src/api/users.ts
"Crée le composant UserList qui utilise ces fichiers"
```

✅ **2. Prompts Précis**

❌ "Fais quelque chose avec le formulaire"  
✅ "Ajoute validation Zod : email (format) + password (min 8 chars)"

✅ **3. Mode Approprié**

- Petite modif → **Task** (économique)
- Feature moyenne → **Agent**
- Feature complexe → **Plan**

✅ **4. Itération Progressive**

❌ "Refais tout le composant"  
✅ "1. Ajoute validation" → "2. Ajoute loading state" → "3. Style"

✅ **5. Cursor Rules**

❌ Répéter les conventions à chaque prompt  
✅ Définir une fois dans `.cursorrules`

#### Comparaison Coûts

**Scénario** : Créer un formulaire de login

| Approche | Tokens | Temps | Qualité |
|----------|--------|-------|---------|
| Sans rules, prompts vagues | ~15K | 20 min | ⭐⭐ |
| Avec rules, mode Agent | ~8K | 10 min | ⭐⭐⭐⭐ |
| Avec rules, mode Task (itératif) | ~5K | 8 min | ⭐⭐⭐⭐⭐ |

**Économie** : 60-70% de tokens avec bonne méthode !

### Production Rapide

#### Workflow Optimisé

```
1. Définir Cursor Rules (1 fois) ✅
2. Utiliser @mentions pour contexte
3. Choisir le bon mode selon la tâche
4. Prompts précis et structurés
5. Itérer progressivement
6. Vérifier et ajuster
```

#### Raccourcis Clavier

| Raccourci | Action |
|-----------|--------|
| `Cmd+K` | Ouvrir chat Cursor |
| `Cmd+L` | Mode Agent |
| `Cmd+I` | Mode Task (inline edit) |
| `Cmd+Shift+L` | Mode Plan |
| `Cmd+/` | Toggle comments |
| `Cmd+P` | Quick open file |

#### Techniques de Speed

**1. Templates réutilisables**

Créer des components/hooks de base, puis les adapter :
```
"Crée UserList similaire à @src/components/EventList.tsx"
```

**2. Batch operations**

❌ Un composant à la fois  
✅ Plusieurs composants similaires ensemble

```
"Crée 3 composants UI :
- Button (primary, secondary)
- Input (text, email, password)
- Card (simple, with header)"
```

**3. Cursor Rules par feature**

Changer de context rapidement :
```
@cursorrules-auth "Crée LoginForm"
@cursorrules-dashboard "Crée DashboardStats"
```

---

## 🎯 PARTIE 5 : FORMAT .MDC

### Qu'est-ce que .mdc ?

**MDC** = Markdown Context  
Extension de Markdown optimisée pour le contexte IA.

### Structure Recommandée

```markdown
# [Titre du Rule]

## Context
[Description générale]

## Technical Stack
- Framework: React
- Language: TypeScript
- Style: Tailwind

## Conventions
### Naming
- Components: PascalCase
- Files: kebab-case
- Variables: camelCase

### Code Style
- Functional components
- Custom hooks for logic
- TypeScript strict mode

### File Structure
src/
  components/
  pages/
  hooks/

## Examples
[Code examples]

## Anti-Patterns
❌ Class components
❌ Inline styles
❌ Any types
```

### Best Practices

✅ **Clarté** : Titres descriptifs, sections définies  
✅ **Exemples** : Code concret, pas que théorie  
✅ **Évolution** : Mettre à jour régulièrement  
✅ **Liens** : Références entre rules

---

## 🧪 EXERCICE PRATIQUE

### Exercice 1 : Créer vos Cursor Rules

**Tâche** : Créer les 4 fichiers Cursor Rules pour votre projet

1. `.cursorrules` (principal)
2. `.cursorrules-docs`
3. `.cursorrules-installation`
4. `.cursorrules-auth` (ou autre feature)

**Durée** : 30 minutes

**Checklist** :
- [ ] Stack technique défini
- [ ] MCP configurés
- [ ] Architecture documentée
- [ ] Conventions claires
- [ ] Exemples inclus

### Exercice 2 : Tester les Modes

**Tâche** : Créer un composant Button en utilisant les 3 modes

1. **Mode Task** : Ajouter une variante "ghost"
2. **Mode Agent** : Créer Button + Input + Card
3. **Mode Plan** : Créer un design system complet

**Comparer** : Vitesse, qualité, tokens utilisés

---

## 📚 RESSOURCES

- [Cursor Docs](cursor-docs.md)
- [Cursor Rules Examples](cursorrules-mdc-docs.md)
- [Context & AI](context-ai-docs.md)
- [MCP Documentation](mcp-docs.md)

---

## ✅ CHECKLIST DE VALIDATION

**Pour valider ce cours** :
- [ ] J'ai créé mes 4 Cursor Rules
- [ ] Je comprends les 3 modes (Task, Agent, Plan)
- [ ] Je sais optimiser mes prompts
- [ ] J'ai testé les différents modes
- [ ] Je peux expliquer l'économie de tokens

---

**Durée du cours** : 2-3 heures  
**Niveau** : Intermédiaire  
**Prérequis** : Cursor installé  
**Version** : 1.0  
**Date** : 25 novembre 2024

