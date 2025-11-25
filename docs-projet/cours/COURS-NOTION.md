# 📚 COURS : NOTION API & MCP

> Automatiser votre documentation avec Notion

---

## 🎯 OBJECTIFS

1. Créer une intégration Notion
2. Structurer la documentation projet
3. Utiliser MCP Notion dans Cursor
4. Automatiser les mises à jour

---

## 🔑 CONFIGURATION INITIALE

### 1. Créer une Intégration

1. Aller sur https://www.notion.so/my-integrations
2. Cliquer "New integration"
3. Nommer : "[Votre Projet] Integration"
4. Copier le token : `secret_...`

### 2. Partager les Pages

Pour chaque page à utiliser :
1. Ouvrir la page Notion
2. Cliquer "Share" → "Invite"
3. Chercher votre intégration
4. Partager

### 3. Configurer MCP

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

## 📋 STRUCTURE RECOMMANDÉE

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

## 🎯 UTILISATION DANS CURSOR

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

## 🔄 AUTOMATISATION

### Via Cursor Rules

**Dans `.cursorrules-docs`** :
```markdown
## Notion Integration

When you finish a feature:
1. Update Kanban (move to Done)
2. Add to Changelog
3. Update Roadmap

Use @notion automatically:
```
@notion Update Kanban: move "[Feature]" to Done
@notion Add to Changelog: "[Feature] completed"
```
```

### Prompts Automatiques

**Après chaque feature** :
```
@notion Documente la feature [X] dans la page Features avec :
- Description
- Usage
- Code examples
- Screenshots
```

---

## 📊 BASES DE DONNÉES NOTION

### Kanban

**Propriétés** :
- Titre (text)
- Status (select : To Do, Doing, Done)
- Assigné (person)
- Priorité (select : High, Medium, Low)
- Date (date)

**Vues** :
- Board (par Status)
- Table (tout)
- Calendar (par Date)

### Roadmap

**Propriétés** :
- Milestone (title)
- Description (text)
- Date début (date)
- Date fin (date)
- Status (select)

**Vue** : Timeline

---

## 🧪 EXERCICE

### Tâche 1 : Structure Complète

Créer dans Notion :
1. Page principale projet
2. Kanban avec 5 tâches
3. Roadmap 6 jours
4. Page Changelog
5. Page Architecture

### Tâche 2 : Automatisation

Utiliser `@notion` pour :
1. Créer une page technique
2. Mettre à jour le Changelog
3. Ajouter une tâche au Kanban

---

## 🔍 TROUBLESHOOTING

**"Page not found"** :
→ Vérifier que la page est partagée avec l'intégration

**"Unauthorized"** :
→ Vérifier le token API

**MCP ne répond pas** :
→ Redémarrer Cursor, vérifier config JSON

---

## 📚 RESSOURCES

- [Notion API](https://developers.notion.com)
- [MCP Notion](https://github.com/modelcontextprotocol/servers/tree/main/notion)
- [Templates](https://notion.so/templates)

---

## ✅ VALIDATION

- [ ] Intégration Notion créée
- [ ] Pages partagées avec intégration
- [ ] MCP configuré et testé
- [ ] Structure documentation complète
- [ ] Au moins 1 automatisation en place

---

**Durée** : 1-2h  
**Niveau** : Débutant  
**Version** : 1.0

