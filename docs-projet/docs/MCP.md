# 📚 Model Context Protocol (MCP)

> Connecter l'IA (Cursor, Claude) à des sources de données externes

---

## 🎯 Vue d'ensemble

**MCP** (Model Context Protocol) est un protocole standard pour connecter les modèles d'IA (comme Cursor ou Claude) à des sources de données externes (Notion, Supabase, Airtable, etc.).

**Sans MCP** :
```
Vous → Cursor → Code
```

**Avec MCP** :
```
Vous → Cursor → MCP → Notion/Supabase/Airtable → Données
              ↓
            Code + Données enrichies
```

### Avantages

- ✅ **Accès direct aux données** : L'IA peut lire/écrire dans vos bases
- ✅ **Automatisation** : Documentation auto-générée dans Notion
- ✅ **Contexte enrichi** : L'IA connaît votre schéma de BDD
- ✅ **Moins de copier-coller** : L'IA récupère les données directement
- ✅ **Workflow amélioré** : Synchronisation automatique

---

## 📖 Documentation Officielle

### Sites Principaux
- **Spec officielle** : https://modelcontextprotocol.io
- **GitHub** : https://github.com/modelcontextprotocol
- **Documentation** : https://modelcontextprotocol.io/docs
- **SDK TypeScript** : https://github.com/modelcontextprotocol/typescript-sdk

### Guides
- **Introduction** : https://modelcontextprotocol.io/introduction
- **Architecture** : https://modelcontextprotocol.io/docs/concepts/architecture
- **Use Cases** : https://modelcontextprotocol.io/docs/concepts/use-cases
- **Getting Started** : https://modelcontextprotocol.io/docs/getting-started
- **Building MCP Servers** : https://modelcontextprotocol.io/docs/building-servers

---

## 🔌 Les 3 MCP Obligatoires du Projet

### 1. MCP Notion

**Usage** : Lire/écrire dans Notion

**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/notion

**Installation** :
```bash
npm install -g @modelcontextprotocol/server-notion
```

**Configuration** :

1. Créer une intégration Notion : https://www.notion.so/my-integrations
2. Copier le token d'intégration
3. Partager vos pages Notion avec l'intégration
4. Configurer dans Cursor (`~/.cursor/mcp-settings.json`) :

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

**Fonctionnalités** :
- Lire/écrire des pages Notion
- Créer des bases de données
- Mettre à jour du contenu
- Rechercher dans Notion
- Automatiser la documentation

**Test** :
```
@notion Crée une page "Test MCP" avec le texte "Hello World"
```

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/notion/README.md

---

### 2. MCP Supabase

**Usage** : Requêtes SQL, CRUD, Auth, Storage

**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/supabase

**Installation** :
```bash
npm install -g @modelcontextprotocol/server-supabase
```

**Configuration** :

1. Récupérer URL + Service Role Key depuis Supabase Dashboard
2. Configurer dans Cursor :

```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-supabase"],
      "env": {
        "SUPABASE_URL": "https://xxx.supabase.co",
        "SUPABASE_SERVICE_KEY": "eyJ..."
      }
    }
  }
}
```

**Fonctionnalités** :
- Requêtes SQL
- CRUD operations
- Auth management
- Storage access
- Edge Functions
- Schema introspection

**Test** :
```
@supabase List all tables in the database
```

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/supabase/README.md

---

### 3. MCP Airtable

**Usage** : CRUD dans Airtable

**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/airtable

**Installation** :
```bash
npm install -g @modelcontextprotocol/server-airtable
```

**Configuration** :

1. Récupérer API Key : https://airtable.com/create/tokens
2. Récupérer Base ID (dans l'URL de la base)
3. Configurer dans Cursor :

```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-airtable"],
      "env": {
        "AIRTABLE_API_KEY": "key...",
        "AIRTABLE_BASE_ID": "app..."
      }
    }
  }
}
```

**Fonctionnalités** :
- Lire/écrire des records
- Créer/modifier des tables
- Gérer les relations
- Filtrer et trier
- Automatiser les workflows

**Test** :
```
@airtable List all tables in the base
```

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/airtable/README.md

---

## 📁 Configuration Complète

### Fichier : `~/.cursor/mcp-settings.json`

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "secret_xxxxxxxxxxxxx"
      }
    },
    "supabase": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-supabase"],
      "env": {
        "SUPABASE_URL": "https://xxxxx.supabase.co",
        "SUPABASE_SERVICE_KEY": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
      }
    },
    "airtable": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-airtable"],
      "env": {
        "AIRTABLE_API_KEY": "keyxxxxxxxxxxxxx",
        "AIRTABLE_BASE_ID": "appxxxxxxxxxxxxx"
      }
    }
  }
}
```

### Emplacement du Fichier

- **macOS/Linux** : `~/.cursor/mcp-settings.json`
- **Windows** : `%APPDATA%\.cursor\mcp-settings.json`

### Test de Configuration

```bash
# Vérifier que les MCP sont reconnus
cursor --list-mcp

# Tester un MCP spécifique
cursor --test-mcp notion
```

---

## 🎯 Utilisation dans Cursor

### Syntaxe de Base

```
@[mcp_name] [your command]
```

### Exemples Pratiques

**Notion** :
```
@notion Crée une page "Documentation API" avec sections : Overview, Endpoints, Examples

@notion Met à jour la roadmap avec les features terminées aujourd'hui

@notion Ajoute dans le changelog : "Version 1.2 - Auth OAuth ajoutée"
```

**Supabase** :
```
@supabase Show me the schema of the 'users' table

@supabase Create a PostgreSQL function get_active_users()

@supabase List all users with role='admin'
```

**Airtable** :
```
@airtable Create a new record in Events table with title "Workshop AI"

@airtable Show me all records from Users table

@airtable Update the record with ID rec123 to set status='completed'
```

### Dans les Cursor Rules

**`.cursor/rules/main.mdc`** :
```markdown
## MCP Configuration
- @notion: Project documentation (Page ID: xxx)
- @supabase: Database operations (Project: xxx)
- @airtable: Data entry (Base: xxx)

When generating documentation:
→ Use @notion to update automatically

When querying database:
→ Use @supabase for reads
→ Use @airtable for writes (architecture rule)
```

---

## 🔌 Autres MCP Utiles

### MCP GitHub
**Usage** : Intégration avec GitHub (repos, issues, PRs)
- **Repository** : https://github.com/modelcontextprotocol/servers/tree/main/github
- **Installation** : `npm install @modelcontextprotocol/server-github`

### MCP Filesystem
**Usage** : Accès au système de fichiers local
- **Repository** : https://github.com/modelcontextprotocol/servers/tree/main/filesystem
- **Installation** : `npm install @modelcontextprotocol/server-filesystem`

### MCP Slack
**Usage** : Intégration Slack (messages, channels)
- **Repository** : https://github.com/modelcontextprotocol/servers/tree/main/slack
- **Installation** : `npm install @modelcontextprotocol/server-slack`

### MCP PostgreSQL
**Usage** : Connexion directe à PostgreSQL
- **Repository** : https://github.com/modelcontextprotocol/servers/tree/main/postgresql
- **Installation** : `npm install @modelcontextprotocol/server-postgresql`

---

## 💡 Best Practices

### Sécurité
- ✅ Ne jamais commit les API keys
- ✅ Utiliser des variables d'environnement
- ✅ Limiter les permissions (read-only si possible)
- ✅ Rotations régulières des clés
- ✅ Utiliser Service Role Key uniquement côté serveur

### Performance
- ✅ Batch les opérations quand possible
- ✅ Cache les résultats fréquents
- ✅ Limiter le nombre de requêtes
- ✅ Utiliser les filtres côté serveur
- ✅ Optimiser les queries complexes

### Organisation
- ✅ Documenter chaque MCP utilisé
- ✅ Centraliser la configuration
- ✅ Tester après chaque modification
- ✅ Logs pour debugging
- ✅ Documenter les permissions nécessaires

---

## 🔍 Troubleshooting

### Problème : MCP ne fonctionne pas

**Vérifications** :
1. ✅ Configuration JSON valide
2. ✅ API keys correctes
3. ✅ Permissions suffisantes
4. ✅ Connexion internet
5. ✅ Version Cursor à jour

**Debug** :
```bash
# Logs Cursor
tail -f ~/.cursor/logs/mcp.log

# Test manuel
npx @modelcontextprotocol/server-notion
```

### Erreurs Communes

**"MCP not found"** :
```bash
# Réinstaller
npm install -g @modelcontextprotocol/server-notion
```

**"Authentication failed"** :
- Vérifier l'API key
- Régénérer la clé si nécessaire
- Pour Notion : vérifier que les pages sont partagées avec l'intégration
- Pour Supabase : vérifier que c'est bien la Service Role Key

**"Timeout"** :
- Vérifier connexion internet
- Vérifier status du service (Notion/Supabase/Airtable)
- Augmenter le timeout dans la config

**"Permission denied"** :
- Vérifier les scopes de l'API key
- Pour Notion : vérifier les pages partagées
- Pour Supabase : vérifier les RLS policies
- Pour Airtable : vérifier les permissions de la base

---

## 🧪 Exercices Pratiques

### Exercice 1 : Installation Complète

**Tâche** : Installer et configurer les 3 MCP

1. Installer les 3 packages
2. Créer/obtenir les API keys
3. Configurer `mcp-settings.json`
4. Tester chaque MCP

**Validation** :
```
@notion Test connection
@supabase Test connection
@airtable Test connection
```

### Exercice 2 : Automatisation Documentation

**Tâche** : Utiliser MCP Notion pour automatiser la doc

1. Créer une page "Architecture" dans Notion
2. Utiliser Cursor + @notion pour générer le contenu
3. Mettre à jour automatiquement lors des changements

**Prompt exemple** :
```
@notion Documente l'architecture actuelle du projet dans la page "Architecture" :
- Stack technique
- Schema BDD
- Flow d'authentification
- Déploiement
```

---

## 📚 Ressources

### Documentation
- **MCP Specification** : https://spec.modelcontextprotocol.io
- **Servers Repository** : https://github.com/modelcontextprotocol/servers
- **Examples** : https://github.com/modelcontextprotocol/servers/tree/main/examples
- **SDK Documentation** : https://github.com/modelcontextprotocol/typescript-sdk

### Community
- **Discord** : https://discord.gg/modelcontextprotocol
- **GitHub Discussions** : https://github.com/modelcontextprotocol/specification/discussions

### Integrations
- **Notion API** : https://developers.notion.com
- **Supabase Docs** : https://supabase.com/docs
- **Airtable API** : https://airtable.com/developers/web/api

---

**Dernière mise à jour** : 25 novembre 2025  
**MCP Spec Version** : 1.0  
**Basé sur** : [Documentation officielle MCP](https://modelcontextprotocol.io)

