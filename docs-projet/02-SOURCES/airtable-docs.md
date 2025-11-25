# 📚 DOCUMENTATION AIRTABLE

**Site officiel** : https://airtable.com  
**Documentation** : https://airtable.com/developers  
**Dashboard** : https://airtable.com

---

## 🎯 RESSOURCES PRINCIPALES

### Getting Started
- **Airtable Basics** : https://support.airtable.com/docs/getting-started-with-airtable
- **Create a Base** : https://support.airtable.com/docs/creating-a-new-base
- **API Documentation** : https://airtable.com/developers/web/api/introduction
- **JavaScript SDK** : https://github.com/Airtable/airtable.js

### Database Design
- **Tables & Fields** : https://support.airtable.com/docs/tables-primers
- **Views** : https://support.airtable.com/docs/views-overview
- **Field Types (20+)** : https://support.airtable.com/docs/supported-field-types-overview
- **Linked Records** : https://support.airtable.com/docs/linked-record-fields
- **Formulas** : https://support.airtable.com/docs/formula-field-reference
- **Rollups** : https://support.airtable.com/docs/rollup-field

### Automations & Workflows
- **Automations Overview** : https://support.airtable.com/docs/automations-overview
- **Triggers** : https://support.airtable.com/docs/automation-triggers
- **Actions** : https://support.airtable.com/docs/automation-actions
- **Scripting** : https://support.airtable.com/docs/scripting-overview
- **Extensions** : https://airtable.com/developers/extensions

### API & Integration
- **REST API** : https://airtable.com/developers/web/api
- **API Authentication** : https://airtable.com/developers/web/api/authentication
- **Webhooks** : https://airtable.com/developers/web/api/webhooks-overview
- **Rate Limits** : https://airtable.com/developers/web/api/rate-limits
  - 5 requêtes/seconde par base
  - 50,000 requêtes/jour (Free plan)

---

## 🔄 SYNC AVEC SUPABASE (Important pour le cours)

### Configuration de la Synchronisation

**Étape 1 : Extension Supabase dans Airtable**
1. Ouvrir votre base Airtable
2. Extensions → Marketplace
3. Chercher "Supabase" ou extensions de sync
4. Installer et configurer

**Étape 2 : Configuration**
- **Supabase Project URL** : Depuis votre dashboard Supabase
- **Service Role Key** : ⚠️ Utiliser la `service_role` key (JAMAIS la exposer côté client)
- **Mapping** : Mapper chaque table Airtable → Table Supabase

**Étape 3 : Test**
1. Créer un record dans Airtable
2. Vérifier qu'il apparaît dans Supabase (< 5 secondes)
3. Tester une modification
4. Tester une suppression (si configuré)

### Documentation Sync
- **Guide Supabase** : https://supabase.com/docs/guides/integrations/airtable
- **Alternative** : Webhooks + Edge Functions

---

## 💻 UTILISATION DE L'API

### Installation SDK
```bash
npm install airtable
```

### Configuration
```javascript
// lib/airtable.js
const Airtable = require('airtable');

const base = new Airtable({
  apiKey: process.env.AIRTABLE_API_KEY
}).base('appXXXXXXXXXXXXXX'); // Base ID

module.exports = base;
```

### Exemples CRUD

#### READ (Liste)
```javascript
const records = await base('TableName')
  .select({
    maxRecords: 10,
    view: 'Grid view',
    filterByFormula: '{Status} = "Active"'
  })
  .firstPage();

records.forEach(record => {
  console.log(record.get('FieldName'));
});
```

#### CREATE
```javascript
const newRecord = await base('TableName').create([
  {
    fields: {
      'Name': 'John Doe',
      'Email': 'john@example.com',
      'Status': 'Active'
    }
  }
]);
```

#### UPDATE
```javascript
await base('TableName').update([
  {
    id: 'recXXXXXXXXXXXXXX',
    fields: {
      'Status': 'Inactive'
    }
  }
]);
```

#### DELETE
```javascript
await base('TableName').destroy(['recXXXXXXXXXXXXXX']);
```

---

## 🏗️ SCHEMA RECOMMANDÉ POUR LE COURS

### Table : Users
- `id` (Auto number ou Formula)
- `email` (Email)
- `name` (Single line text)
- `created_at` (Created time)
- `updated_at` (Last modified time)

### Table : Projects
- `id` (Auto number)
- `title` (Single line text)
- `description` (Long text)
- `owner` (Link to Users)
- `status` (Single select : Draft, Active, Completed)
- `created_at` (Created time)

### Table : Tasks
- `id` (Auto number)
- `title` (Single line text)
- `project` (Link to Projects)
- `assignee` (Link to Users)
- `status` (Single select : To Do, In Progress, Done)
- `priority` (Single select : Low, Medium, High)
- `due_date` (Date)

### Relations
- Users ← 1:N → Projects
- Projects ← 1:N → Tasks
- Users ← 1:N → Tasks (assignee)

---

## ⚙️ AUTOMATIONS UTILES

### 1. Envoyer notification à Supabase
**Trigger** : When record created  
**Action** : Run script (appel webhook)

### 2. Mise à jour timestamp
**Trigger** : When record updated  
**Action** : Update field (`updated_at`)

### 3. Validation email
**Trigger** : When record enters view  
**Action** : Send email

---

## 💡 TIPS POUR LE COURS

### Best Practices
- ✅ Utiliser des noms de champs clairs (sans espaces si possible)
- ✅ Configurer les "Views" pour différents usages
- ✅ Ajouter 15+ records par table pour les démos
- ✅ Utiliser Linked Records pour les relations
- ✅ Documenter le schéma dans Notion

### Common Issues
- ❌ Oublier la sync → data désynchronisée
- ❌ Rate limits dépassés → throttle les requêtes
- ❌ API key exposée → utiliser variables d'environnement
- ❌ Mauvais mapping → erreurs de sync

### Pour la Note Technique
- **Minimum 3 tables** avec relations
- **15+ données mockées** par table
- **Sync fonctionnelle** avec Supabase
- **Extension Supabase** installée et configurée
- **Documentation** du schéma dans Notion

---

## 📚 RESSOURCES AVANCÉES

### Templates & Inspiration
- **Template Gallery** : https://airtable.com/templates
- **Universe (Community)** : https://airtable.com/universe

### Extensions Utiles
- **Chart** : Visualisation de données
- **Page Designer** : Impression/PDF
- **Sync** : Synchronisation entre bases
- **Supabase Connector** : Pour le cours

### Formulas Examples
```javascript
// Calculer nombre de jours jusqu'à deadline
DATETIME_DIFF({Due Date}, TODAY(), 'days')

// Concaténer prénom + nom
{First Name} & ' ' & {Last Name}

// Status badge conditionnel
IF({Status} = 'Done', '✅', 
   IF({Status} = 'In Progress', '🔄', '⏸️'))
```

---

## 🔗 RESSOURCES COMPLÉMENTAIRES

### Community
- **Community Forum** : https://community.airtable.com
- **Twitter/X** : https://twitter.com/airtable
- **YouTube** : https://www.youtube.com/@airtable

### Support
- **Help Center** : https://support.airtable.com
- **API Docs (par base)** : Airtable.com → Base → Help → API documentation
- **Status Page** : https://status.airtable.com

---

## 📊 TARIFICATION (2025)

### Free
- Bases illimitées
- 1,200 records/base
- 2 GB attachments/base
- ✅ Suffisant pour le cours

### Team ($20/user/mois)
- 50,000 records/base
- 20 GB attachments/base
- Automations avancées
- Extensions premium

---

**Dernière MAJ** : 25 novembre 2025  
**Maintenu par** : Thomas Garcia

