# 📚 COURS : AIRTABLE

> Base de données no-code pour les opérations
nous sommmes le 25 Novembre 2025
---

## 🎯 OBJECTIFS

1. Créer une base Airtable
2. Configurer les relations
3. Sync avec Supabase
4. Workflows et automatisations

---

## 🚀 SETUP

### 1. Créer une Base

1. https://airtable.com → "Create a base"
2. Nom : "[Votre Projet]"
3. Créer les tables

### 2. Configuration Tables

**Exemple : Events** :
```
Fields :
- Title (Single line text) - Primary
- Description (Long text)
- Date (Date with time)
- Capacity (Number)
- Organizer (Link to Users)
- Status (Single select: Draft, Published, Completed)
- Created (Created time)
```

**Relations** :
- Users → Events (One to many)
- Events → Tickets (One to many)

### 3. Données Mockées

Minimum **15 entrées par table**

Utiliser :
- Générateurs (Mockaroo, Faker.js)
- Copier-coller avec variantes
- Extension "Generate data"

---

## 🔗 SYNC AVEC SUPABASE

### Installation Extension

1. Airtable → Extensions → Add extension
2. Chercher "Supabase"
3. Installer

### Configuration

1. **Supabase URL** : `https://xxx.supabase.co`
2. **Service Role Key** : Dashboard Supabase → Settings → API
3. **Mapping** :
   - Airtable Table → Supabase Table
   - Champs → Colonnes (vérifier types)

### Tests

- Insert dans Airtable → Vérifier Supabase
- Update dans Airtable → Vérifier sync
- Temps de sync : < 5 secondes

---

## 🤖 AUTOMATISATIONS

### Créer un Workflow

1. Airtable → Automations → Create
2. **Trigger** : Record created/updated
3. **Actions** : Email, Slack, Webhook, etc.

### Exemples

**Email notification** :
```
Trigger: New event created
Action: Send email
To: organizer@email.com
Subject: "Nouvel événement créé : {Title}"
```

**Update automatique** :
```
Trigger: Status = "Published"
Action: Update record
Set: published_at = NOW()
```

---

## 📊 VUES

**Board** : Kanban (par Status)  
**Grid** : Table classique  
**Calendar** : Par date  
**Gallery** : Cards visuelles  
**Form** : Formulaire d'entrée

---

## 🧪 EXERCICE

1. Créer 3 tables avec relations
2. 15+ données par table
3. Configurer sync Supabase
4. Tester la sync
5. Créer 1 automatisation

---

## ✅ VALIDATION

- [ ] Base Airtable créée
- [ ] 3+ tables avec relations
- [ ] 15+ données par table
- [ ] Sync Supabase active
- [ ] Tests sync réussis
- [ ] 1 workflow configuré

---

**Durée** : 2h  
**Niveau** : Débutant  
**Version** : 1.0

