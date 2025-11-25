# 📚 Notion - Documentation Collaborative

> Automatiser votre documentation avec Notion

---

## 🎯 Vue d'ensemble

**Notion** est un outil tout-en-un pour la prise de notes, la documentation et la gestion de projet. Dans ce projet, Notion sert de hub central de documentation, avec mise à jour automatisée via MCP.

**Site officiel** : https://notion.so  
**Documentation Dev** : https://developers.notion.com  
**Dashboard** : https://www.notion.so

### Composants Principaux

- **Pages** : Documents riches (texte, images, code)
- **Databases** : Tables, Kanban, Calendar, Timeline
- **Templates** : Structures réutilisables
- **API** : Intégration programmatique
- **Integrations** : Connexions externes

---

## 🔑 Configuration Initiale

### 1. Créer une Intégration

1. Aller sur https://www.notion.so/my-integrations
2. Cliquer "+ New integration"
3. Nommer : "[Votre Projet] Integration"
4. Type : Internal integration
5. Copier le **Internal Integration Secret** (API Key)

### 2. Permissions Nécessaires

Pour le cours, activer :
- ✅ Read content
- ✅ Update content
- ✅ Insert content
- ✅ Read comments
- ✅ Insert comments (optionnel)

### 3. Partager les Pages

⚠️ **Important** : L'intégration ne peut accéder qu'aux pages partagées explicitement

Pour chaque page à utiliser :
1. Ouvrir la page Notion
2. Cliquer "..." (menu) → "Add connections"
3. Sélectionner votre intégration
4. Confirmer

### 4. Configurer MCP (pour Cursor)

Dans `~/.cursor/mcp-settings.json` :
```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "secret_..."
      }
    }
  }
}
```

---

## 📋 Structure Recommandée

### Pages Obligatoires

```
📁 [Nom du Projet]
├── 📄 Vue d'ensemble
│   ├── Description
│   ├── Vision
│   └── Équipe
├── 📋 Kanban (Base de données)
│   ├── To Do
│   ├── Doing
│   └── Done
├── 🗓️ Roadmap (Timeline)
│   ├── Semaine 1
│   ├── ...
│   └── Demo Day
├── 📝 Changelog
│   └── Entrées par date
├── 🏗️ Architecture
│   ├── Stack Technique
│   ├── Schema BDD
│   └── Flow Authentification
└── 📚 Documentation Technique
    ├── Installation
    ├── API Reference
    └── Déploiement
```

### Templates de Pages

**Vue d'ensemble** :
```markdown
# [Nom du Projet]

## 🎯 Vision
[Description du problème résolu]

## ✨ Features Principales
- Feature 1
- Feature 2
- Feature 3

## 👥 Équipe
[Membres avec rôles]

## 🔗 Liens
- GitHub : [URL]
- App : [URL]
- Figma : [URL]
```

**Changelog** :
```markdown
# Changelog

## [Date]
### Added
- Feature X

### Changed
- Amélioration Y

### Fixed
- Bug Z
```

---

## 🗄️ Databases Notion

### Database : Kanban

**Propriétés** :
- `Name` (Title)
- `Status` (Select : To Do, Doing, Done)
- `Assignee` (Person)
- `Priority` (Select : Low, Medium, High)
- `Created` (Created time)
- `Updated` (Last edited time)

**Vues** :
- Board (par Status) - Vue Kanban
- Table (tout) - Vue grille
- Calendar (par Date) - Vue calendrier

### Database : Roadmap

**Propriétés** :
- `Milestone` (Title)
- `Description` (Text)
- `Start Date` (Date)
- `End Date` (Date)
- `Status` (Select : Planned, In Progress, Completed)
- `Owner` (Person)

**Vue** : Timeline (Gantt)

---

## 💻 Utilisation de l'API

### Installation SDK

```bash
npm install @notionhq/client
```

### Configuration

```typescript
// lib/notion.ts
import { Client } from '@notionhq/client';

export const notion = new Client({
  auth: process.env.NOTION_API_KEY,
});
```

### Exemples

#### Créer une Page

```typescript
const response = await notion.pages.create({
  parent: {
    database_id: 'votre-database-id',
  },
  properties: {
    Name: {
      title: [
        {
          text: {
            content: 'Nouvelle page',
          },
        },
      ],
    },
    Status: {
      select: {
        name: 'In Progress',
      },
    },
  },
});
```

#### Lire une Database

```typescript
const response = await notion.databases.query({
  database_id: 'votre-database-id',
  filter: {
    property: 'Status',
    select: {
      equals: 'Active',
    },
  },
  sorts: [
    {
      property: 'Created',
      direction: 'descending',
    },
  ],
});
```

#### Mettre à Jour une Page

```typescript
await notion.pages.update({
  page_id: 'votre-page-id',
  properties: {
    Status: {
      select: {
        name: 'Completed',
      },
    },
  },
});
```

#### Ajouter du Contenu (Blocks)

```typescript
await notion.blocks.children.append({
  block_id: 'votre-page-id',
  children: [
    {
      object: 'block',
      type: 'heading_2',
      heading_2: {
        rich_text: [
          {
            type: 'text',
            text: {
              content: 'Nouveau titre',
            },
          },
        ],
      },
    },
    {
      object: 'block',
      type: 'paragraph',
      paragraph: {
        rich_text: [
          {
            type: 'text',
            text: {
              content: 'Nouveau paragraphe.',
            },
          },
        ],
      },
    },
  ],
});
```

---

## 🎯 Utilisation dans Cursor (MCP)

### Syntaxe de Base

```
@notion [commande]
```

### Exemples Pratiques

**Créer du contenu** :
```
@notion Crée une page "API Documentation" avec :
- Section Overview
- Section Endpoints (GET /users, POST /users)
- Section Authentication
- Exemples de requêtes
```

**Mettre à jour** :
```
@notion Mets à jour le Changelog avec :
Version 1.2.0 - [Date]
- Added: OAuth Google
- Fixed: Bug login redirect
```

**Générer automatiquement** :
```
@notion Documente l'architecture actuelle :
- Stack : [liste depuis package.json]
- Schema BDD : [depuis Supabase]
- Déploiement : Netlify
```

---

## 🔄 Automatisation

### Via Cursor Rules

**Dans `.cursor/rules/docs.mdc`** :
```markdown
## Notion Integration

When you finish a feature:
1. Update Kanban (move to Done)
2. Add to Changelog
3. Update Roadmap

Use @notion automatically:
@notion Update Kanban: move "[Feature]" to Done
@notion Add to Changelog: "[Feature] completed"
```

### Workflow Automatique

**Après chaque feature** :
```
@notion Documente la feature [X] dans la page Features avec :
- Description
- Usage
- Code examples
- Screenshots
```

---

## 💡 Best Practices

### Pour le Projet

- ✅ **Structure claire** : Kanban, Roadmap, Changelog
- ✅ **Documentation complète** : Technique + non-tech
- ✅ **Présentation équipe** : Avec photos et rôles
- ✅ **MCP configuré** : Notion accessible depuis Cursor
- ✅ **Mise à jour automatique** : Changelog auto-généré

### Organisation

- ✅ Organiser en workspace dédié au projet
- ✅ Utiliser des templates pour cohérence
- ✅ Icônes et covers pour navigation visuelle
- ✅ Relations entre databases pour liens
- ✅ Views multiples (Kanban, Timeline, Table)

### Sécurité

- ✅ Ne jamais commit l'API key
- ✅ Limiter les permissions de l'intégration
- ✅ Partager uniquement les pages nécessaires
- ✅ Documenter les accès dans le README

---

## 📚 Ressources

### Documentation Officielle

- **Notion API** : https://developers.notion.com/docs/getting-started
- **API Reference** : https://developers.notion.com/reference
- **Working with Pages** : https://developers.notion.com/docs/working-with-pages
- **Working with Databases** : https://developers.notion.com/docs/working-with-databases

### SDK & Tools

- **JavaScript/TypeScript SDK** : https://github.com/makenotion/notion-sdk-js
- **MCP Notion** : https://github.com/modelcontextprotocol/servers/tree/main/notion

### Community

- **Twitter/X** : https://twitter.com/NotionHQ
- **Reddit** : https://reddit.com/r/Notion
- **Templates** : https://www.notion.so/templates
- **Help Center** : https://www.notion.so/help

---

## 💰 Tarification (2025)

### Free (Personnel)

- Pages illimitées
- Blocks illimités
- Collaborateurs limités
- ✅ **Suffisant pour le cours**

### Plus ($10/user/mois)

- Collaboration illimitée
- Historique 30 jours
- Invités illimités

### Education (Gratuit pour étudiants)

- Plus features gratuites
- Demander avec email étudiant
- URL : https://www.notion.so/students

---

## 🔍 Troubleshooting

**"Page not found"** :
→ Vérifier que la page est partagée avec l'intégration

**"Unauthorized"** :
→ Vérifier le token API dans la config

**MCP ne répond pas** :
→ Redémarrer Cursor, vérifier config JSON

**Rate limits (3 req/sec)** :
→ Throttle les requêtes, batch les opérations

---

**Dernière mise à jour** : 25 novembre 2025  
**API Version** : 2022-06-28 (stable)  
**Basé sur** : [Documentation officielle Notion](https://developers.notion.com)

