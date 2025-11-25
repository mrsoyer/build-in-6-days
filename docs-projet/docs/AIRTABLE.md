# 📚 Airtable - No-code Database

> Base de données collaborative pour les opérations admin

---

## 🎯 Vue d'ensemble

**Airtable** combine la simplicité d'un tableur avec la puissance d'une base de données. Dans le projet, Airtable sert d'interface d'administration no-code pour les opérations d'écriture.

**Site officiel** : https://airtable.com  
**Documentation** : https://airtable.com/developers  
**Dashboard** : https://airtable.com

### Pourquoi Airtable dans ce Projet ?

- **Écriture** : Interface no-code pour les admins
- **Synchronisation** : Sync automatique vers Supabase
- **Collaboration** : Équipe peut modifier les données facilement
- **Validation** : Règles de validation intégrées

---

## 🚀 Setup

### 1. Créer une Base

1. Aller sur https://airtable.com
2. "Create a base"
3. Nom : "[Votre Projet]"
4. Créer les tables

### 2. Configuration Tables

**Exemple : Events** :
```
Fields :
- Title (Single line text) - Primary field
- Description (Long text)
- Date (Date with time)
- Capacity (Number)
- Organizer (Link to Users)
- Status (Single select: Draft, Published, Completed)
- Created (Created time)
- Updated (Last modified time)
```

**Types de champs disponibles (20+)** :
- Text (single line, long text, rich text)
- Numbers, Currency, Percent
- Date, Duration
- Checkbox, Multiple select, Single select
- Link to another record
- Attachments (images, files)
- Formula, Rollup, Lookup
- Barcode, Rating, Button

### 3. Relations entre Tables

**Exemples** :
- Users ← 1:N → Projects
- Projects ← 1:N → Tasks
- Users ← 1:N → Tasks (assignee)

**Configuration** :
1. Créer field type "Link to another record"
2. Sélectionner table cible
3. Configurer relation (1:1, 1:N, N:N)

---

## 🔄 Synchronisation avec Supabase

### Architecture (Important !)

```
Airtable (Écriture) ─sync→ Supabase (Lecture)
       ↑                           ↓
     Admin                   Application
```

### Setup Sync

**Étape 1 : Extension Supabase dans Airtable**
1. Ouvrir votre base Airtable
2. Extensions → Marketplace
3. Chercher "Supabase" ou extensions de sync
4. Installer et configurer

**Étape 2 : Configuration**
- **Supabase Project URL** : Depuis votre dashboard Supabase
- **Service Role Key** : ⚠️ Utiliser la `service_role` key
- **Mapping** : Mapper chaque table Airtable → Table Supabase

**Étape 3 : Test**
1. Créer un record dans Airtable
2. Vérifier qu'il apparaît dans Supabase (< 5 secondes)
3. Tester une modification
4. Tester une suppression (si configuré)

**Documentation Sync** :
- Guide Supabase : https://supabase.com/docs/guides/integrations/airtable

---

## 💻 API Airtable

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

## 🤖 Automations

### Créer un Workflow

1. Airtable → Automations → Create
2. **Trigger** : Record created/updated
3. **Actions** : Email, Slack, Webhook, Script, etc.

### Exemples Utiles

**Email notification** :
```
Trigger: New event created
Action: Send email
To: {Organizer Email}
Subject: "Nouvel événement créé : {Title}"
Body: "Détails : {Description}"
```

**Update automatique** :
```
Trigger: Status = "Published"
Action: Update record
Set: published_at = NOW()
```

**Webhook vers Supabase** :
```
Trigger: Record enters view
Action: Run script
→ Appel API Supabase pour sync manuelle
```

---

## 📊 Vues (Views)

Airtable offre plusieurs types de vues :

| Vue | Usage | Idéal pour |
|-----|-------|------------|
| **Grid** | Table classique | Édition rapide |
| **Board** | Kanban | Gestion de status |
| **Calendar** | Calendrier | Événements par date |
| **Gallery** | Cards visuelles | Portfolios, images |
| **Form** | Formulaire d'entrée | Saisie externe |
| **Timeline** | Gantt | Planning projet |

### Exemple : Board View (Kanban)

**Configuration** :
1. Créer vue "Board"
2. Group by : "Status"
3. Champs affichés : Title, Assignee, Due Date
4. Drag & drop pour changer status

---

## 🏗️ Schema Recommandé pour le Projet

### Table : Users

- `id` (Auto number ou Formula)
- `email` (Email)
- `name` (Single line text)
- `role` (Single select : User, Admin)
- `created_at` (Created time)
- `updated_at` (Last modified time)

### Table : Events

- `id` (Auto number)
- `title` (Single line text)
- `description` (Long text)
- `date` (Date with time)
- `capacity` (Number)
- `organizer` (Link to Users)
- `status` (Single select : Draft, Published, Completed)
- `created_at` (Created time)

### Table : Tickets

- `id` (Auto number)
- `event` (Link to Events)
- `user` (Link to Users)
- `quantity` (Number)
- `price` (Currency)
- `status` (Single select : Pending, Paid, Cancelled)
- `created_at` (Created time)

### Relations

- Users ← 1:N → Events (organizer)
- Users ← 1:N → Tickets (user)
- Events ← 1:N → Tickets (event)

---

## 💡 Best Practices

### Pour le Projet

- ✅ **Données mockées** : Minimum 15 entrées par table
- ✅ **Relations** : Bien configurer les linked records
- ✅ **Views** : Créer Board, Calendar, Grid
- ✅ **Sync active** : Vérifier régulièrement
- ✅ **Documentation** : Schéma dans Notion

### Sécurité

- ✅ Ne jamais commit l'API key
- ✅ Utiliser variables d'environnement
- ✅ Limiter les permissions (read-only si possible)
- ✅ Partager la base avec seulement l'équipe

### Performance

- ✅ Batch les opérations (max 10 records/call)
- ✅ Respecter rate limits (5 req/sec par base)
- ✅ Cache les résultats fréquents
- ✅ Filtrer côté serveur avec `filterByFormula`

---

## 📚 Ressources

### Documentation Officielle

- **API Documentation** : https://airtable.com/developers/web/api
- **API Authentication** : https://airtable.com/developers/web/api/authentication
- **Field Types** : https://support.airtable.com/docs/supported-field-types-overview
- **Webhooks** : https://airtable.com/developers/web/api/webhooks-overview

### JavaScript SDK

- **GitHub** : https://github.com/Airtable/airtable.js
- **Installation** : `npm install airtable`

### Templates

- **Template Gallery** : https://airtable.com/templates
- **Universe (Community)** : https://airtable.com/universe

### Community

- **Community Forum** : https://community.airtable.com
- **Twitter/X** : https://twitter.com/airtable
- **YouTube** : https://www.youtube.com/@airtable
- **Status Page** : https://status.airtable.com

---

## 💰 Tarification (2025)

### Free

- Bases illimitées
- 1,200 records/base
- 2 GB attachments/base
- ✅ **Suffisant pour le cours**

### Team ($20/user/mois)

- 50,000 records/base
- 20 GB attachments/base
- Automations avancées
- Extensions premium
- Support prioritaire

---

## ❓ FAQ

**Pourquoi Airtable pour l'écriture ?**
- Interface no-code facile pour les admins
- Validation de données intégrée
- Collaboration en temps réel
- Historique des modifications

**Comment fonctionne la sync avec Supabase ?**
- Unidirectionnelle : Airtable → Supabase
- Automatique (via extension ou webhook)
- Temps de sync : < 5 secondes

**Puis-je utiliser Airtable comme seule BDD ?**
- Oui, mais moins performant pour les lectures
- Architecture recommandée : Airtable (write) + Supabase (read)

---

**Dernière mise à jour** : 25 novembre 2025  
**Basé sur** : [Documentation officielle Airtable](https://airtable.com/developers)

