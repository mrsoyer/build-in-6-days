# 📚 Cursor - IDE avec IA

> Documentation complète sur Cursor, ses modes, les Rules, et l'optimisation

---

## 🎯 Vue d'ensemble

**Cursor** est un IDE basé sur VS Code qui intègre des modèles d'IA (GPT-4, Claude 3.5 Sonnet) pour accélérer le développement.

**Site officiel** : https://cursor.com  
**Documentation** : https://cursor.com/docs  
**Version actuelle** : 0.43+ (novembre 2025)

---

## 🚀 Installation

### Téléchargement
- **macOS** : https://cursor.com/download/mac
- **Windows** : https://cursor.com/download/windows
- **Linux** : https://cursor.com/download/linux

### Migration depuis VS Code
Cursor importe automatiquement :
- Extensions
- Paramètres
- Raccourcis clavier
- Thèmes

**Documentation** : https://cursor.com/docs/get-started/migrate-from-vscode

---

## 🎯 Les Modes de Cursor

Cursor propose plusieurs modes d'interaction avec l'IA, chacun optimisé pour un type de tâche différent.

### 1. Mode Chat (`Cmd+L`)

**Quand l'utiliser** :
- Questions sur le code
- Demander des explications
- Discuter d'architecture
- Obtenir des suggestions

**Avantages** :
- Conversationnel
- Ne modifie pas le code directement
- Garde l'historique
- Permet d'affiner progressivement

**Exemple** :
```
Vous : "Comment structurer mon système d'auth avec Supabase ?"
Cursor : [Explique l'architecture, propose un plan]
Vous : "Et pour les roles ?"
Cursor : [Affine avec la gestion des rôles]
```

### 2. Mode Task / Inline Edit (`Cmd+I`)

**Quand l'utiliser** :
- Modification dans UN fichier
- Changement précis et ciblé
- Correction rapide
- Refactoring local

**Avantages** :
- Très rapide
- Économique en tokens
- Contrôle total
- Édition en place

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

### 3. Mode Composer (`Cmd+Shift+I`)

**Quand l'utiliser** :
- Tâches multi-fichiers
- Création de feature complète
- Refactoring important
- Modifications coordonnées

**Avantages** :
- Autonomie complète
- Gère plusieurs fichiers simultanément
- Planifie avant d'agir
- Vue d'ensemble du projet

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

**Documentation** : https://cursor.com/docs/modes/composer

---

## 📖 Cursor Rules

Les **Cursor Rules** sont le système de contexte persistant de Cursor. Elles permettent de définir des instructions, conventions et préférences qui s'appliquent automatiquement.

**Documentation officielle** : https://cursor.com/docs/context/rules

### Types de Rules

Cursor supporte 4 types de rules :

| Type | Emplacement | Portée | Usage |
|------|-------------|--------|-------|
| **Project Rules** | `.cursor/rules/` | Projet (versionné) | Conventions du projet |
| **User Rules** | Settings globaux | Tous vos projets | Préférences personnelles |
| **Team Rules** | Dashboard (payant) | Toute l'équipe | Standards d'équipe |
| **AGENTS.md** | Racine du projet | Projet | Alternative simple |

### Project Rules

Les Project Rules vivent dans `.cursor/rules/`. Chaque rule est un fichier écrit en **MDC** (`.mdc`).

#### Anatomie d'une Rule

Chaque fichier `.mdc` contient des métadonnées et du contenu :

```markdown
---
globs:
alwaysApply: false
---

- Use our internal RPC pattern when defining services
- Always use snake_case for service names

@service-template.ts
```

#### Types d'Application

Vous pouvez contrôler comment les rules sont appliquées :

| Type | Quand appliqué | Métadonnées |
|------|----------------|-------------|
| **Always Apply** | À chaque session chat | `alwaysApply: true` |
| **Apply Intelligently** | Quand l'IA juge pertinent | `description: "..."` |
| **Apply to Specific Files** | Sur pattern de fichiers | `globs: ["*.tsx"]` |
| **Apply Manually** | Quand @mentionné | Aucune |

#### Rules Imbriquées

Vous pouvez organiser vos rules en les plaçant dans des sous-dossiers `.cursor/rules/` :

```bash
project/
  .cursor/rules/        # Rules globales
  backend/
    .cursor/rules/      # Rules spécifiques backend
  frontend/
    .cursor/rules/      # Rules spécifiques frontend
```

Les rules imbriquées s'appliquent automatiquement quand vous travaillez sur des fichiers dans leur répertoire.

#### Créer une Rule

**Via commande** : `New Cursor Rule`  
**Via settings** : `Cursor Settings > Rules`

Cela crée un nouveau fichier dans `.cursor/rules/`.

### AGENTS.md (Alternative Simple)

Si vous préférez un fichier unique simple, utilisez `AGENTS.md` à la racine de votre projet :

```markdown
# Project Instructions

## Code Style
- Use TypeScript for all new files
- Prefer functional components in React
- Use snake_case for database columns

## Architecture
- Follow the repository pattern
- Keep business logic in service layers
```

**Avantages** :
- ✅ Simple (Markdown pur)
- ✅ Lisible
- ✅ Pas de métadonnées

**Inconvénients** :
- ❌ Moins de contrôle (toujours appliqué)
- ❌ Pas de conditions (globs, etc.)

**Support des sous-dossiers** : Vous pouvez placer des `AGENTS.md` dans des sous-dossiers pour des instructions spécifiques.

### User Rules

Les **User Rules** sont globales à votre environnement Cursor. Configurez-les dans `Cursor Settings → Rules`.

**Usage** :
- Style de communication préféré
- Conventions personnelles
- Langage préféré

**Exemple** :
```markdown
Please reply in a concise style. Avoid unnecessary repetition or filler language.
```

**Note** : Les User Rules s'appliquent uniquement au Chat, pas au Inline Edit (Cmd+K).

### Team Rules (Plans Team/Enterprise)

Les **Team Rules** permettent aux admins de définir des rules obligatoires pour toute l'équipe.

**Configuration** : https://cursor.com/dashboard?tab=team-content

**Caractéristiques** :
- Appliquées à tous les membres
- Peuvent être obligatoires (non désactivables)
- Format texte libre (pas de MDC)
- Priorité : Team Rules → Project Rules → User Rules

---

## 💡 Best Practices pour les Rules

### 1. Restez Concis
- ✅ Rules < 500 lignes
- ✅ Divisez les grandes rules en plusieurs
- ❌ Évitez les monolithes

### 2. Soyez Spécifique
- ✅ Instructions claires et actionnables
- ✅ Exemples concrets
- ❌ Guidance vague

### 3. Réutilisez
- ✅ Créez une rule si vous répétez le même prompt
- ✅ Référencez des fichiers avec `@filename.ts`

### 4. Organisez
- ✅ Une rule par concern
- ✅ Hiérarchie logique (rules imbriquées)
- ✅ Nommage descriptif

---

## 🎯 Exemples de Rules

### Rule pour Standards Frontend

```markdown
---
globs: ["src/components/**/*.tsx"]
alwaysApply: false
---

When working in components directory:
- Always use Tailwind for styling
- Use Framer Motion for animations
- Follow component naming conventions (PascalCase)
```

### Rule pour API Validation

```markdown
---
globs: ["src/api/**/*.ts"]
alwaysApply: false
---

In API directory:
- Use zod for all validation
- Define return types with zod schemas
- Export types generated from schemas
```

### Rule pour Documentation

```markdown
---
alwaysApply: true
---

Help draft documentation by:
- Extracting code comments
- Analyzing README.md
- Generating markdown documentation

Use @notion MCP to update automatically.
```

---

## ⚡ Optimisation & Performance

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
- Feature moyenne → **Composer**
- Questions → **Chat**

✅ **4. Itération Progressive**

❌ "Refais tout le composant"  
✅ "1. Ajoute validation" → "2. Ajoute loading state" → "3. Style"

✅ **5. Cursor Rules**

❌ Répéter les conventions à chaque prompt  
✅ Définir une fois dans `.cursor/rules/`

#### Comparaison Coûts

**Scénario** : Créer un formulaire de login

| Approche | Tokens | Temps | Qualité |
|----------|--------|-------|---------|
| Sans rules, prompts vagues | ~15K | 20 min | ⭐⭐ |
| Avec rules, mode Composer | ~8K | 10 min | ⭐⭐⭐⭐ |
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
| `Cmd+K` | Chat rapide |
| `Cmd+L` | Mode Chat |
| `Cmd+I` | Mode Task (inline edit) |
| `Cmd+Shift+I` | Mode Composer |
| `Cmd+/` | Toggle Copilot |
| `Tab` | Accept suggestion |
| `Esc` | Dismiss suggestion |

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

Changer de contexte rapidement avec @mentions de rules spécifiques.

---

## 🔍 Troubleshooting

### Problèmes Courants

**Ma rule n'est pas appliquée**
- ✅ Vérifier le type de rule (Always Apply, Intelligently, etc.)
- ✅ Pour "Apply Intelligently", ajouter une `description`
- ✅ Pour "Apply to Specific Files", vérifier les `globs`

**Cursor ne répond pas**
- ✅ Vérifier la connexion internet
- ✅ Redémarrer Cursor
- ✅ Vérifier les API keys

**Prompts ignorés**
- ✅ Contexte trop large → Réduire
- ✅ Prompt ambigu → Préciser
- ✅ Contradiction dans les rules → Corriger

---

## 💰 Tarification (2025)

### Free Tier
- **Prix** : Gratuit
- **Inclus** : 
  - 2000 completions/mois
  - 50 slow premium requests/mois
  - Accès à GPT-4

### Pro ($20/mois)
- **Inclus** :
  - 500 fast premium requests/mois
  - Unlimited slow requests
  - GPT-4, Claude 3.5 Sonnet
  - Mode Composer illimité
  - Privacy mode

### Business ($40/user/mois)
- Tout Pro +
- Admin dashboard
- Centralized billing
- Team Rules
- Priority support

### Étudiants
- **GitHub Student Pack** : 6 mois Pro gratuits
- URL : https://education.github.com/pack

---

## 🆕 Nouveautés 2025

### Cursor Composer (Stable)
- Édition multi-fichiers améliorée
- Meilleure compréhension du contexte projet
- Support des projets > 100K lignes

### Performance
- Réponses 30% plus rapides
- Cache context amélioré
- Consommation tokens optimisée

### Nouvelles Fonctionnalités
- Rules imbriquées (`.cursor/rules/` dans sous-dossiers)
- `AGENTS.md` dans sous-dossiers
- Team Rules avec enforcement
- Amélioration des globs patterns

---

## 📚 Ressources

### Documentation Officielle
- **Site** : https://cursor.com
- **Docs** : https://cursor.com/docs
- **Blog** : https://cursor.com/blog
- **Changelog** : https://cursor.com/changelog

### Community
- **Discord** : https://discord.gg/cursor
- **Forum** : https://community.cursor.com
- **Twitter/X** : https://twitter.com/cursor_ai

### Exemples de Rules
- **awesome-cursorrules** : https://github.com/PatrickJS/awesome-cursorrules
- **cursor.directory** : https://cursor.directory

---

## ❓ FAQ

**Puis-je référencer des fichiers dans mes rules ?**  
✅ Oui, utilisez `@filename.ts` pour inclure des fichiers dans le contexte de la rule.

**Puis-je créer une rule depuis le chat ?**  
✅ Oui, demandez simplement à l'agent de créer une nouvelle rule.

**Les rules impactent-elles Cursor Tab (autocomplétion) ?**  
❌ Non, les rules n'affectent que le Chat et le Composer.

**Les User Rules s'appliquent au Inline Edit ?**  
❌ Non, uniquement au Chat.

**Puis-je désactiver une Team Rule ?**  
✅ Oui, sauf si elle est "enforced" par l'admin.

---

## 🎓 Conseils Finaux

1. **Commencez simple** : Un `AGENTS.md` suffit au début
2. **Évoluez progressivement** : Ajoutez des Project Rules quand nécessaire
3. **Documentez** : Vos rules sont aussi pour vos coéquipiers
4. **Testez** : Vérifiez que vos rules produisent l'effet voulu
5. **Itérez** : Ajustez vos rules en fonction des résultats

---

**Dernière mise à jour** : 25 novembre 2025  
**Version Cursor** : 0.43+  
**Basé sur** : [Documentation officielle Cursor](https://cursor.com/docs/context/rules)

