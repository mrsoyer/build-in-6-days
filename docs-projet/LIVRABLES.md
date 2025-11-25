# 📋 Livrables Attendus

> Ce que vous devez rendre pour valider le projet

---

## 1. Documentation Notion

### Structure Obligatoire
- Page principale (titre, description, vision)
- Kanban (To Do / Doing / Done)
- Roadmap projet
- Changelog (journal des modifications)

### Documentation Technique
- Architecture du projet (schéma clair)
- Schema base de données (Airtable + Supabase)
- Guide d'installation complet
- Variables d'environnement listées
- **Accessible** : lisible par un dev ET un non-tech

### Présentation Équipe
- Nom + photo de chaque membre
- Rôle dans le projet
- Contributions (qui a fait quoi)
- Liens GitHub/LinkedIn

### Intégration MCP Notion
- MCP Notion installé et configuré
- Documentation mise à jour via Cursor (preuve)
- Exemple de commande Cursor → Notion

---

## 2. Cursor Rules & Organisation

### 4 Fichiers Obligatoires

**`.cursorrules` (Principal)**
- Configuration MCP (Notion, Supabase, Airtable)
- Contraintes techniques globales
- Stack technique
- Architecture (Read: Supabase, Write: Airtable)

**`.cursorrules-docs` (Documentation)**
- Règles pour générer/maintenir la doc
- Intégration avec Notion

**`.cursorrules-installation` (Setup)**
- Commandes d'installation automatisées
- Un autre dev peut installer facilement

**`.cursorrules-[feature]` (Fonctionnalités)**
- Minimum 2 fichiers par fonctionnalité
- Exemples : `-auth`, `-dashboard`, `-api`

---

## 3. GitHub & Versioning

### Repository Bien Organisé
- Structure de fichiers claire
- Nommage cohérent
- Pas de fichiers brouillon ("test123.js")

### README Complet
- 10 sections obligatoires
- Instructions d'installation claires
- Template fourni dans `templates/`

### Commits par Membre
**CRITIQUE** : Tous les membres doivent avoir fait au moins 1 commit
- Vérifiable via `git shortlog -sn`
- 0 point si un membre n'a pas commit

---

## 4. MCP & Synchronisation

### 3 MCP Installés
- MCP Notion (+ test de connexion)
- MCP Supabase (+ test de connexion)
- MCP Airtable (+ test de connexion)

### Sync Airtable ↔ Supabase
- Extension Supabase installée dans Airtable
- Mapping tables/champs correct
- Test INSERT : données apparaissent dans Supabase
- Test UPDATE : modifications synchronisées

### Architecture Respectée
- **App** lit UNIQUEMENT depuis **Supabase**
- **Admin** écrit UNIQUEMENT dans **Airtable**

---

## 5. Authentification

### Auth Client Fonctionnelle
- Page Login (email + password)
- Page Signup (inscription)
- Logout fonctionnel
- Protected routes (redirect si non-auth)
- Gestion session (persist après refresh)

### BONUS
- Gestion des rôles (user/admin) : **+3 pts**
- OAuth Google et/ou Facebook : **+5 pts**

---

## 6. Base de Données & Fonctions

### Schema Airtable
- Minimum 3 tables
- Relations entre tables configurées
- Minimum 15 données mockées par table

### Fonctions PostgreSQL
- 2-3 fonctions créées
- Fonctions documentées (commentaires SQL)
- Documentation dans Notion
- Fonctions appelées depuis l'app

### BONUS
- Dashboard admin avec KPIs et filtres PostgreSQL : **+5 pts**

---

## 7. Déploiement & Production

### App Déployée sur Netlify
- URL fonctionnelle et accessible
- Build réussi sans erreurs
- Variables d'environnement configurées
- Configuration `netlify.toml` correcte

### BONUS
- App mobile créée avec Expo : **+7 pts**

---

## 8. Workflows & Automatisations

### Workflows Supabase
- Minimum 1-2 workflows configurés
- Triggers fonctionnels
- Actions pertinentes

---

## 9. Outils Complémentaires (BONUS)

### Intégration Pertinente (+5 max)
- Outil intégré (Make, n8n, Claude, etc.)
- Intégration fonctionnelle
- Documentation de l'intégration
- **Condition** : Justification claire de la valeur ajoutée

---

## ✅ Checklist Minimum pour 15/20

Pour avoir une note correcte (15/20 minimum), vous devez avoir :
- ✅ Documentation Notion complète
- ✅ 4 Cursor Rules présentes
- ✅ GitHub organisé + tous les membres ont commit
- ✅ 3 MCP installés et configurés
- ✅ Sync Airtable-Supabase fonctionnelle
- ✅ Auth complète (login/signup/logout)
- ✅ Base de données avec données mockées
- ✅ App déployée sur Netlify
- ✅ 1 workflow Supabase

---

## 📚 Ressources

- **Détail de la notation** : Voir [NOTATION.md](NOTATION.md)
- **Auto-évaluation** : Voir [CHECKLIST_PROJET.md](CHECKLIST_PROJET.md)
- **Cours techniques** : Dossier `cours/`
- **Templates** : Dossier `templates/`

---

**Conseil** : Utilisez la [CHECKLIST_PROJET.md](CHECKLIST_PROJET.md) régulièrement pour ne rien oublier !

