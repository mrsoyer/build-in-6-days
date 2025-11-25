# 📚 COURS : MODEL CONTEXT PROTOCOL (MCP)

> Connecter l'IA à des sources de données externes

---

## 🎯 OBJECTIFS

À la fin de ce cours :
1. Comprendre ce qu'est MCP
2. Installer et configurer les 3 MCP obligatoires
3. Utiliser les MCP dans Cursor
4. Troubleshooter les problèmes courants

---

## 📖 QU'EST-CE QUE MCP ?

**MCP** (Model Context Protocol) = Protocol pour connecter l'IA (Cursor, Claude) à des sources de données externes (Notion, Supabase, Airtable, etc.)

**Sans MCP** :
```
Vous → Cursor → Code
```

**Avec MCP** :
```
Vous → Cursor → MCP → Notion/Supabase/Airtable → Données
              ↓
            Code + Données
```

### Avantages

- ✅ **Accès direct aux données** : L'IA peut lire/écrire dans vos bases
- ✅ **Automatisation** : Documentation auto-générée dans Notion
- ✅ **Contexte enrichi** : L'IA connaît votre schéma de BDD
- ✅ **Moins de copier-coller** : L'IA récupère les données directement

---

## 🔌 LES 3 MCP OBLIGATOIRES

### 1. MCP Notion

**Usage** : Lire/écrire dans Notion

**Installation** :
```bash
npm install -g @modelcontextprotocol/server-notion
```

**Configuration** :

1. Créer une intégration Notion : https://www.notion.so/my-integrations
2. Copier le token
3. Partager vos pages avec l'intégration
4. Configurer dans Cursor :

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

**Test** :
```
@notion Crée une page "Test MCP" avec le texte "Hello World"
```

### 2. MCP Supabase

**Usage** : Requêtes SQL, CRUD, Auth

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

**Test** :
```
@supabase List all tables in the database
```

### 3. MCP Airtable

**Usage** : CRUD dans Airtable

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

**Test** :
```
@airtable List all tables in the base
```

---

## 📁 CONFIGURATION COMPLÈTE

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

---

## 🎯 UTILISATION DANS CURSOR

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

**`.cursorrules` principal** :
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

## 🔍 TROUBLESHOOTING

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

**"Timeout"** :
- Vérifier connexion internet
- Vérifier status du service (Notion/Supabase/Airtable)

---

## 🧪 EXERCICE PRATIQUE

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

## 📚 RESSOURCES

- [MCP Specification](https://modelcontextprotocol.io)
- [MCP Servers GitHub](https://github.com/modelcontextprotocol/servers)
- [Notion API](https://developers.notion.com)
- [Supabase Docs](https://supabase.com/docs)
- [Airtable API](https://airtable.com/developers/web/api)

---

## ✅ CHECKLIST DE VALIDATION

- [ ] 3 MCP installés
- [ ] Configuration JSON créée
- [ ] API keys configurées
- [ ] Tests de connexion réussis
- [ ] Documentation d'utilisation écrite
- [ ] Au moins 1 automatisation mise en place

---

**Durée** : 1-2 heures  
**Niveau** : Intermédiaire  
**Prérequis** : Cursor installé, comptes Notion/Supabase/Airtable  
**Version** : 1.0

