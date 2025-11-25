# 📚 DOCUMENTATION MCP (Model Context Protocol)

> Protocol pour connecter l'IA à des sources de données externes

---

## 🔗 DOCUMENTATION OFFICIELLE

### Site Principal
- **Spec officielle** : https://modelcontextprotocol.io
- **GitHub** : https://github.com/modelcontextprotocol
- **Documentation** : https://modelcontextprotocol.io/docs

### Introduction
- **Qu'est-ce que MCP** : https://modelcontextprotocol.io/introduction
- **Architecture** : https://modelcontextprotocol.io/docs/concepts/architecture
- **Use Cases** : https://modelcontextprotocol.io/docs/concepts/use-cases

---

## 🎯 MCP DISPONIBLES POUR LE PROJET

### 1. MCP Notion
**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/notion

**Installation** :
```bash
npm install @modelcontextprotocol/server-notion
```

**Configuration** :
```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "your-notion-integration-token"
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

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/notion/README.md

---

### 2. MCP Supabase
**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/supabase

**Installation** :
```bash
npm install @modelcontextprotocol/server-supabase
```

**Configuration** :
```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-supabase"],
      "env": {
        "SUPABASE_URL": "https://your-project.supabase.co",
        "SUPABASE_SERVICE_KEY": "your-service-role-key"
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

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/supabase/README.md

---

### 3. MCP Airtable
**Repository** : https://github.com/modelcontextprotocol/servers/tree/main/airtable

**Installation** :
```bash
npm install @modelcontextprotocol/server-airtable
```

**Configuration** :
```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-airtable"],
      "env": {
        "AIRTABLE_API_KEY": "your-airtable-api-key",
        "AIRTABLE_BASE_ID": "your-base-id"
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

**Documentation** : https://github.com/modelcontextprotocol/servers/blob/main/airtable/README.md

---

## 🔌 AUTRES MCP UTILES

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

## 🛠️ CONFIGURATION DANS CURSOR

### Fichier de Configuration
**Emplacement** : `~/.cursor/mcp-settings.json` (macOS/Linux) ou `%APPDATA%\.cursor\mcp-settings.json` (Windows)

**Structure** :
```json
{
  "mcpServers": {
    "notion": { 
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-notion"],
      "env": {
        "NOTION_API_KEY": "secret_..."
      }
    },
    "supabase": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-supabase"],
      "env": {
        "SUPABASE_URL": "https://xxx.supabase.co",
        "SUPABASE_SERVICE_KEY": "eyJ..."
      }
    },
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

### Test de Configuration
```bash
# Vérifier que les MCP sont reconnus
cursor --list-mcp

# Tester un MCP spécifique
cursor --test-mcp notion
```

---

## 📖 UTILISATION DANS CURSOR

### Appeler un MCP dans les Prompts

**Syntaxe** :
```
@notion [votre commande]
@supabase [votre requête]
@airtable [votre action]
```

**Exemples** :
```
@notion Crée une page "Documentation API" avec ces sections : [...]
@supabase Récupère tous les users avec role='admin'
@airtable Insert un nouveau record dans la table Events
```

### Dans les Cursor Rules

**Exemple dans `.cursorrules`** :
```markdown
## MCP Configuration

When working with documentation:
- Use @notion to create/update doc pages
- Follow our Notion structure

When working with database:
- Use @supabase for reads
- Use @airtable for writes
- Respect the sync architecture
```

---

## 🎯 BEST PRACTICES

### Sécurité
- ✅ Ne jamais commit les API keys
- ✅ Utiliser des variables d'environnement
- ✅ Limiter les permissions (read-only si possible)
- ✅ Rotations régulières des clés

### Performance
- ✅ Batch les opérations quand possible
- ✅ Cache les résultats fréquents
- ✅ Limiter le nombre de requêtes
- ✅ Utiliser les filtres côté serveur

### Organisation
- ✅ Documenter chaque MCP utilisé
- ✅ Centraliser la configuration
- ✅ Tester après chaque modification
- ✅ Logs pour debugging

---

## 🔍 TROUBLESHOOTING

### MCP ne fonctionne pas

**Vérifications** :
1. Configuration JSON valide
2. API keys correctes
3. Permissions suffisantes
4. Connexion internet
5. Version de Cursor à jour

**Commandes de debug** :
```bash
# Vérifier les logs
tail -f ~/.cursor/logs/mcp.log

# Tester manuellement
npx @modelcontextprotocol/server-notion
```

### Erreurs Communes

**"MCP not found"** :
- Vérifier le chemin dans la config
- Réinstaller le package : `npm install -g @modelcontextprotocol/server-notion`

**"Authentication failed"** :
- Vérifier l'API key
- Vérifier les permissions
- Régénérer la clé si nécessaire

**"Timeout"** :
- Vérifier la connexion internet
- Augmenter le timeout dans la config
- Vérifier le status du service (Notion/Supabase/Airtable)

---

## 📚 RESSOURCES COMPLÉMENTAIRES

### Documentation
- **MCP Specification** : https://spec.modelcontextprotocol.io
- **SDK Documentation** : https://github.com/modelcontextprotocol/typescript-sdk
- **Examples** : https://github.com/modelcontextprotocol/servers/tree/main/examples

### Community
- **Discord** : https://discord.gg/modelcontextprotocol
- **GitHub Discussions** : https://github.com/modelcontextprotocol/specification/discussions

### Tutorials
- **Getting Started** : https://modelcontextprotocol.io/docs/getting-started
- **Building MCP Servers** : https://modelcontextprotocol.io/docs/building-servers
- **Integration Guide** : https://modelcontextprotocol.io/docs/integration

---

**Dernière mise à jour** : 25 novembre 2025  
**MCP Spec Version** : 1.0  
**Maintenu par** : Thomas Garcia

