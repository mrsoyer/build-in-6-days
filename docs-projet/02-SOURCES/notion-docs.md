# 📚 DOCUMENTATION NOTION

**Site officiel** : https://notion.so  
**Documentation Dev** : https://developers.notion.com  
**Dashboard** : https://www.notion.so

---

## 🎯 RESSOURCES PRINCIPALES

### Getting Started
- **Notion API** : https://developers.notion.com/docs/getting-started
- **Créer une Intégration** : https://www.notion.so/my-integrations
- **Authorization** : https://developers.notion.com/docs/authorization
- **Working with Pages** : https://developers.notion.com/docs/working-with-pages
- **Working with Databases** : https://developers.notion.com/docs/working-with-databases

### API Reference Complète
- **Pages** : https://developers.notion.com/reference/page
- **Databases** : https://developers.notion.com/reference/database
- **Blocks** : https://developers.notion.com/reference/block
- **Users** : https://developers.notion.com/reference/user
- **Search** : https://developers.notion.com/reference/post-search
- **Comments** : https://developers.notion.com/reference/create-a-comment

### SDK & Tools
- **JavaScript/TypeScript SDK** : https://github.com/makenotion/notion-sdk-js
- **Python SDK** : https://github.com/ramnes/notion-sdk-py
- **MCP Notion (Cursor)** : https://github.com/modelcontextprotocol/servers/tree/main/notion

### Examples & Templates
- **Official Examples** : https://developers.notion.com/docs/examples
- **Community Examples** : https://github.com/makenotion/notion-sdk-js/tree/main/examples
- **API Playground** : Dans la documentation officielle

---

## 🔧 CONFIGURATION

### 1. Créer une Intégration
1. Aller sur https://www.notion.so/my-integrations
2. "+ New integration"
3. Nom : "Mon Projet Bootcamp"
4. Type : Internal integration
5. Copier le **Internal Integration Secret** (API Key)

### 2. Partager Pages avec l'Intégration
⚠️ **Important** : L'intégration ne peut accéder qu'aux pages partagées explicitement

1. Ouvrir une page Notion
2. Click "..." (menu) → "Add connections"
3. Sélectionner votre intégration
4. Confirmer

### 3. Permissions Nécessaires
Pour le cours, activer :
- ✅ Read content
- ✅ Update content
- ✅ Insert content
- ✅ Read comments
- ✅ Insert comments (optionnel)

---

## 💻 UTILISATION DE L'API

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

### Exemples d'Utilisation

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
              content: 'Nouveau paragraphe avec du contenu.',
            },
          },
        ],
      },
    },
  ],
});
```

#### Rechercher
```typescript
const response = await notion.search({
  query: 'projet',
  filter: {
    property: 'object',
    value: 'page',
  },
  sort: {
    direction: 'descending',
    timestamp: 'last_edited_time',
  },
});
```

---

## 🗄️ STRUCTURE RECOMMANDÉE POUR LE COURS

### Database : Projet (Kanban)
**Properties** :
- `Name` (Title)
- `Status` (Select : To Do, Doing, Done)
- `Assignee` (Person)
- `Priority` (Select : Low, Medium, High)
- `Created` (Created time)
- `Updated` (Last edited time)

### Database : Roadmap (Timeline)
**Properties** :
- `Milestone` (Title)
- `Description` (Text)
- `Start Date` (Date)
- `End Date` (Date)
- `Status` (Select : Planned, In Progress, Completed)
- `Owner` (Person)

### Page : Documentation Technique
**Structure** :
- Vue d'ensemble
- Architecture (avec diagramme)
- Schema BDD
- Guide d'installation
- API Reference

### Page : Changelog
**Structure** :
```markdown
# Changelog

## [1.2.0] - 2025-01-25
### Added
- Feature X
- Feature Y

### Changed
- Amélioration Z

### Fixed
- Bug A
```

---

## 🔄 MISE À JOUR AUTOMATIQUE

### Avec MCP Notion (Recommandé pour Cursor)
```bash
# Dans Cursor
@notion Create page "Test" in database [database-id]
@notion Update changelog with [new-entry]
```

### Avec Code (Workflow d'automatisation)
```typescript
// Exemple : Ajouter une entrée de changelog
async function addChangelogEntry(version: string, changes: string[]) {
  const changelogPageId = 'votre-changelog-page-id';
  
  const blocks = [
    {
      object: 'block',
      type: 'heading_2',
      heading_2: {
        rich_text: [{ text: { content: `[${version}] - ${new Date().toISOString().split('T')[0]}` } }],
      },
    },
    ...changes.map(change => ({
      object: 'block',
      type: 'bulleted_list_item',
      bulleted_list_item: {
        rich_text: [{ text: { content: change } }],
      },
    })),
  ];
  
  await notion.blocks.children.append({
    block_id: changelogPageId,
    children: blocks,
  });
}
```

---

## 💡 TIPS POUR LE COURS

### Best Practices
- ✅ Organiser en workspace dédié au projet
- ✅ Utiliser des templates pour cohérence
- ✅ Icônes et covers pour navigation visuelle
- ✅ Relations entre databases pour liens
- ✅ Views multiples (Kanban, Timeline, Table)

### Pour la Note Technique
- **Structure claire** : Kanban, Roadmap, Changelog
- **Documentation complète** : Technique + non-tech
- **Présentation équipe** : Avec photos et rôles
- **MCP configuré** : Notion accessible depuis Cursor
- **Mise à jour automatique** : Démontrer changelog auto-généré

### Common Issues
- ❌ Oublier de partager pages → API ne peut pas y accéder
- ❌ Mauvais database_id → erreurs 404
- ❌ Properties mal typées → erreurs de validation
- ❌ Rate limits (3 req/sec) → throttle les requêtes

---

## 📚 RESSOURCES AVANCÉES

### Types de Blocks Disponibles
- `paragraph`, `heading_1/2/3`
- `bulleted_list_item`, `numbered_list_item`
- `to_do`, `toggle`
- `code`, `quote`, `callout`
- `divider`, `table_of_contents`
- `image`, `video`, `file`
- `bookmark`, `embed`

### Formulas dans Databases
```javascript
// Date dans X jours
dateAdd(now(), 7, "days")

// Calculer durée
dateBetween(prop("End"), prop("Start"), "days")

// Condition
if(prop("Status") == "Done", "✅", "⏸️")
```

### Relations entre Databases
- Créer property type "Relation"
- Sélectionner database cible
- Ajouter "Rollup" pour agréger données

---

## 🔗 RESSOURCES COMPLÉMENTAIRES

### Community
- **Twitter/X** : https://twitter.com/NotionHQ
- **Reddit** : https://reddit.com/r/Notion
- **Templates** : https://www.notion.so/templates

### Tools
- **Notion Web Clipper** : Extension Chrome
- **Notion Calendar** : Gestion calendrier
- **Notion AI** : Assistant IA intégré (payant)

### Support
- **Help Center** : https://www.notion.so/help
- **API Status** : https://status.notion.so
- **Changelog** : https://www.notion.so/releases

---

## 📊 TARIFICATION (2025)

### Free (Personnel)
- Pages illimitées
- Blocks illimités
- Collaborateurs limités
- ✅ Suffisant pour le cours

### Plus ($10/user/mois)
- Collaboration illimitée
- Historique 30 jours
- Invités illimités

### Education (Gratuit pour étudiants)
- Plus features gratuites
- Demander avec email étudiant

---

**Dernière MAJ** : 25 novembre 2025  
**API Version** : 2022-06-28 (stable)  
**Maintenu par** : Thomas Garcia

