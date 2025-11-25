# 📋 Livrables Attendus

> Ce que vous devez rendre pour valider le projet

---

## ⏱️ Contexte

- ✅ **Jour 1** : Landing page avec Lovable (terminé)
- **Jours 2-5** : Développement du projet
- **Jour 6** : Jury final

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
- Exemple de commande Cursor → Notion fonctionnelle

---

## 2. Cursor Rules & Organisation

### Fichiers `.cursor/rules/`

**Règle principale** (`.cursor/rules/main.mdc`)
- Configuration MCP (Notion, Supabase, Airtable)
- Contraintes techniques globales
- Stack technique
- Architecture (Read: Supabase, Write: Airtable)

**Rules par fonctionnalité** (`.cursor/rules/[feature].mdc`)
- Minimum 2-3 fichiers de rules
- Exemples : `auth.mdc`, `dashboard.mdc`, `api.mdc`
- Rules pour l'installation et la documentation

### Bonne Organisation
- Rules bien documentées
- Pas de duplication
- Contexte clair pour l'IA

---

## 3. GitHub & Versioning

### Repository Bien Organisé
- Structure de fichiers claire
- Nommage cohérent
- Pas de fichiers brouillon ("test123.js")
- `.gitignore` configuré

### README Complet
- Description du projet
- Instructions d'installation claires
- Variables d'environnement
- Stack technique
- Commandes disponibles
- Lien vers la démo

### Commits par Membre
**CRITIQUE** : Tous les membres doivent avoir fait au moins 1 commit
- Vérifiable via `git shortlog -sn`
- Commits réguliers (pas tout le dernier jour)
- Messages de commit clairs

---

## 4. MCP & Synchronisation

### 3 MCP Installés
- MCP Notion (+ test de connexion)
- MCP Supabase (+ test de connexion)
- MCP Airtable (+ test de connexion)

### Configuration MCP
- Fichier de config MCP présent
- Clés API configurées (pas commitées !)
- Tests de connexion réussis

### Sync Airtable ↔ Supabase
- Extension Supabase installée dans Airtable
- Mapping tables/champs correct
- Test INSERT : données apparaissent dans Supabase
- Test UPDATE : modifications synchronisées

### Architecture Respectée
- **App** lit UNIQUEMENT depuis **Supabase**
- **Admin** écrit UNIQUEMENT dans **Airtable**
- Pas d'insert direct dans Supabase depuis l'app

---

## 5. Authentification

### Auth Client Fonctionnelle
- Page Login (email + password)
- Page Signup (inscription)
- Logout fonctionnel
- Protected routes (redirect si non-auth)
- Gestion session (persist après refresh)
- Error handling (messages clairs)

### BONUS
- Gestion des rôles (user/admin) : **+3 pts**
- OAuth Google et/ou Facebook : **+5 pts**

---

## 6. Base de Données & Fonctions

### Schema Airtable
- Minimum 3 tables
- Relations entre tables configurées
- Minimum 15 données mockées par table
- Types de champs appropriés

### Fonctions PostgreSQL
- 2-3 fonctions créées dans Supabase
- Fonctions documentées (commentaires SQL)
- Documentation dans Notion
- Fonctions appelées depuis l'app
- Exemple : fonctions de stats, agrégation, recherche

### BONUS
- Dashboard admin avec KPIs et filtres PostgreSQL : **+5 pts**
- Plus de 3 fonctions PostgreSQL complexes : **+2 pts**

---

## 7. Déploiement & Production

### App Déployée sur Netlify
- URL fonctionnelle et accessible
- Build réussi sans erreurs
- Variables d'environnement configurées
- Configuration `netlify.toml` correcte
- Pas d'erreurs console critiques

### Configuration
- Variables d'env Netlify configurées
- Build settings corrects
- Redirects configurés si nécessaire

### BONUS
- App mobile créée avec Expo : **+7 pts**
- Custom domain : **+1 pt**

---

## 8. Workflows & Automatisations

### Workflows Supabase
- Minimum 1-2 workflows configurés
- Triggers fonctionnels (ex: après insert)
- Actions pertinentes (ex: envoi email, mise à jour)
- Documentation des workflows

### Exemples de Workflows
- Notification après création d'événement
- Mise à jour automatique de timestamps
- Validation de données
- Synchronisation entre tables

---

## 9. Outils Complémentaires (BONUS)

### Intégration Pertinente (+5 max)
- Outil intégré (Make, n8n, Claude API, etc.)
- Intégration fonctionnelle et démontrée
- Documentation de l'intégration dans Notion
- **Condition** : Justification claire de la valeur ajoutée

**Exemples** :
- Workflow Make pour automatisations complexes
- Claude API pour features IA
- Service externe pertinent pour le projet

---

## ✅ Checklist Minimum pour 15/20

Pour avoir une note correcte (15/20 minimum), vous devez avoir :

### Obligatoires
- ✅ Documentation Notion complète et lisible
- ✅ Cursor Rules organisées (`.cursor/rules/`)
- ✅ GitHub organisé + **tous** les membres ont commit
- ✅ 3 MCP installés et testés
- ✅ Sync Airtable-Supabase fonctionnelle
- ✅ Auth complète (login/signup/logout/protected routes)
- ✅ Base de données avec 3 tables et données mockées
- ✅ 2 fonctions PostgreSQL documentées
- ✅ App déployée sur Netlify (URL accessible)
- ✅ Au moins 1 workflow Supabase

### Recommandés pour 17+/20
- Au moins 1 bonus technique (OAuth, rôles, ou dashboard)
- Plus de 3 fonctions PostgreSQL
- Documentation Notion exemplaire
- Code propre et bien organisé

---

## 📚 Documentation Disponible

Toute la documentation technique est dans le dossier **`docs/`** :

### Setup Initial
- [CURSOR.md](docs/CURSOR.md) - Cursor, Rules, Modes
- [MCP.md](docs/MCP.md) - Configuration des 3 MCP
- [CONTEXT-IA.md](docs/CONTEXT-IA.md) - Prompt engineering

### Backend & Données
- [SUPABASE.md](docs/SUPABASE.md) - Base de données + Auth + Fonctions SQL
- [AIRTABLE.md](docs/AIRTABLE.md) - Interface no-code + Sync
- [POSTGRESQL.md](docs/POSTGRESQL.md) - Fonctions SQL avancées
- [NOTION.md](docs/NOTION.md) - Documentation + API

### Déploiement
- [DEPLOIEMENT.md](docs/DEPLOIEMENT.md) - Guide complet
- [NETLIFY.md](docs/NETLIFY.md) - Hébergement web
- [EXPO.md](docs/EXPO.md) - App mobile (bonus)
- [GITHUB.md](docs/GITHUB.md) - Versioning

---

## 💡 Conseils Finaux

### Priorités
1. **MVP fonctionnel** avant les bonus
2. **Documentation** au fur et à mesure (pas à la fin)
3. **Tous les membres commitent** dès le début
4. **Tester régulièrement** les MCP et la sync

### Timing Recommandé
- **Jour 2** : Setup complet (MCP, Cursor Rules, Notion, Sync)
- **Jours 3-4** : Features principales + Auth + Fonctions SQL
- **Jour 5** : Polish + Documentation + Bonus
- **Jour 6** : Préparation démo + Tests finaux

### Éviter
- ❌ Attendre le dernier jour pour documenter
- ❌ Oublier qu'un membre doit commit
- ❌ Négliger la sync Airtable-Supabase
- ❌ Ne pas tester les MCP

---

**Bon courage ! 🚀**

_Vous avez toute la documentation nécessaire dans le dossier `docs/`. Utilisez Cursor et les MCP à fond !_
