# 📋 EXIGENCES COMPLÈTES DU PROJET

> **Document de référence** : Liste exhaustive de tous les livrables attendus

---

## 🎯 VUE D'ENSEMBLE

Ce document recense **toutes les exigences** pour valider le projet étudiant. Chaque exigence est liée à des points de notation (voir [03-NOTATION-DETAILLEE.md](03-NOTATION-DETAILLEE.md)).

---

## 1️⃣ DOCUMENTATION NOTION

### 1.1 Structure Obligatoire

**Exigences minimales** :
- ✅ Page principale du projet avec présentation
- ✅ Kanban (To Do / Doing / Done)
- ✅ Roadmap des 6 jours
- ✅ Changelog (journal des modifications)
- ✅ Documentation technique

**Critères de qualité** :
- Navigation intuitive entre les pages
- Hiérarchie claire (pages, sous-pages)
- Utilisation des bases de données Notion si pertinent
- Mise à jour régulière

### 1.2 Documentation Technique

**Contenu attendu** :
- Architecture du projet (schéma clair)
- Choix technologiques justifiés
- Schema de base de données (Airtable + Supabase)
- Guide d'installation détaillé
- Guide d'utilisation des fonctionnalités
- API endpoints documentés (si applicable)
- Variables d'environnement nécessaires

**Accessibilité** :
- ✅ Compréhensible par un **tech** (développeur)
- ✅ Compréhensible par un **non-tech** (product manager, client)

### 1.3 Présentation de l'Équipe

**Informations à inclure** :
- Nom et photo de chaque membre
- Rôle dans le projet
- Contributions principales (qui a fait quoi)
- Liens GitHub/LinkedIn

**Format suggéré** :
```
👤 Alice Dupont
- Rôle : Frontend Lead
- Contributions :
  - Landing page design
  - Authentication UI
  - Dashboard components
- GitHub : @alicedupont
```

### 1.4 Intégration MCP Notion

**Exigences techniques** :
- MCP Notion installé et configuré
- Documentation mise à jour automatiquement depuis le code
- Exemples de commandes Cursor qui écrivent dans Notion
- Changelog généré automatiquement lors des commits

**Exemple d'intégration** :
```
Prompt Cursor :
"Mets à jour la documentation Notion avec l'architecture actuelle du projet"

→ Cursor utilise MCP Notion pour écrire directement dans la page
```

---

## 2️⃣ CURSOR RULES & ORGANISATION

### 2.1 Structure Hybride Obligatoire

Le projet doit contenir **4 fichiers Cursor Rules** :

#### `.cursorrules` (Principal)
**Contenu** :
- Configuration MCP (Notion, Supabase, Airtable)
- Contraintes techniques globales
- Stack technique
- Architecture (Read: Supabase, Write: Airtable)
- Liens vers les autres cursor rules

#### `.cursorrules-docs` (Documentation)
**Contenu** :
- Règles pour générer/maintenir la documentation
- Style de documentation (ton, format)
- Intégration avec Notion
- Conventions de commentaires dans le code

#### `.cursorrules-installation` (Setup)
**Contenu** :
- Commandes d'installation automatisées
- Vérification des dépendances
- Configuration de l'environnement
- Tests de validation post-installation

**Objectif** : Un autre développeur peut installer le projet en appelant simplement ce cursor rule.

#### `.cursorrules-[feature]` (Par Fonctionnalité)
**Exemples** :
- `.cursorrules-auth` : Règles pour l'authentification
- `.cursorrules-dashboard` : Règles pour le dashboard
- `.cursorrules-api` : Règles pour les API calls

**Contenu typique** :
- Contexte de la fonctionnalité
- Requirements spécifiques
- Code style pour cette feature
- Dépendances
- Tests associés

### 2.2 Qualité des Cursor Rules

**Critères d'évaluation** :
- ✅ Organisation claire et logique
- ✅ Commentaires explicatifs
- ✅ Évolution au fil du projet (pas statique)
- ✅ Utilisation effective pendant le développement
- ✅ Liens entre les rules fonctionnels

---

## 3️⃣ GITHUB & VERSIONING

### 3.1 Organisation du Repository

**Structure recommandée** :
```
project-name/
├── .cursorrules
├── .cursorrules-docs
├── .cursorrules-installation
├── .cursorrules-auth
├── .cursorrules-dashboard
├── README.md
├── package.json
├── src/
│   ├── components/
│   ├── pages/
│   ├── utils/
│   └── config/
├── public/
└── docs/
```

**Exigences** :
- Nommage cohérent des fichiers/dossiers
- Séparation claire (composants/pages/utils)
- Pas de fichiers "brouillon" ou "test123.js"
- `.gitignore` correctement configuré

### 3.2 README Complet

**Sections obligatoires** :
1. Titre et description
2. Problème résolu
3. Fonctionnalités principales
4. Stack technique
5. Installation (commandes exactes)
6. Variables d'environnement
7. Utilisation
8. Architecture
9. Équipe et contributions
10. Licence (optionnel)

**Template fourni** : Voir [templates/README-TEMPLATE.md](templates/README-TEMPLATE.md)

### 3.3 Commits par Membre

**Exigence stricte** :
- ✅ **Tous les membres** de l'équipe doivent avoir fait **au moins 1 commit**
- Les commits doivent être significatifs (pas juste un espace)
- Messages de commit clairs

**Vérification** :
```bash
git shortlog -sn --all
```

---

## 4️⃣ MCP & SYNCHRONISATION

### 4.1 Installation MCP

**3 MCP obligatoires** :
1. **MCP Notion**
   - Installation via Cursor settings
   - Token d'intégration Notion configuré
   - Test de connexion validé

2. **MCP Supabase**
   - API keys Supabase configurées
   - Connexion au projet validée
   - Accès aux tables confirmé

3. **MCP Airtable**
   - API key Airtable configurée
   - Base ID correctement renseigné
   - Accès aux tables confirmé

### 4.2 Documentation des MCP

**Pour chaque MCP, documenter** :
- Comment l'installer
- Configuration (API keys, IDs)
- Exemples d'utilisation dans Cursor
- Troubleshooting commun

### 4.3 Synchronisation Airtable ↔ Supabase

**Architecture obligatoire** :
```
┌─────────────┐         ┌──────────────┐
│  AIRTABLE   │ ──────→ │   SUPABASE   │
│  (Écriture) │ ←────── │   (Lecture)  │
└─────────────┘  Sync   └──────────────┘
       ↓                        ↑
   Admin/Ops              Application
```

**Exigences techniques** :
- Sync bidirectionnelle fonctionnelle
- Insert dans Airtable → apparaît dans Supabase
- Update dans Airtable → mis à jour dans Supabase
- Delete dans Airtable → supprimé dans Supabase (optionnel)
- Temps de sync < 5 secondes

**Configuration** :
- Extension Supabase installée dans Airtable
- Mapping tables/champs correct
- Tests de sync validés

### 4.4 Respect de l'Architecture

**Règle stricte** :
- ✅ **Application lit UNIQUEMENT depuis Supabase**
- ✅ **Admin/Ops écrit UNIQUEMENT dans Airtable**
- ❌ Jamais écrire directement dans Supabase depuis l'app
- ❌ Jamais lire depuis Airtable dans l'app

**Justification** :
- Performance (PostgreSQL > Airtable pour lecture)
- Séparation des responsabilités
- Interface no-code pour non-devs

---

## 5️⃣ AUTHENTIFICATION

### 5.1 Auth Client (Obligatoire)

**Fonctionnalités minimales** :
- ✅ Page Login (email + password)
- ✅ Page Signup (inscription)
- ✅ Logout fonctionnel
- ✅ Protected routes (redirect si non-auth)
- ✅ Gestion session (persist après refresh)

**Implémentation** :
- Utiliser **Supabase Auth** uniquement
- Pas d'auth custom (sauf justification exceptionnelle)

### 5.2 Gestion des Rôles (BONUS +3 points)

**Fonctionnalités avancées** :
- Rôles différents (user, admin, super-admin)
- Permissions par rôle
- UI adaptée selon le rôle
- Protected routes par rôle

**Exemple** :
```javascript
// User : voit son dashboard
// Admin : voit tous les dashboards
// Super-admin : peut modifier la config
```

### 5.3 OAuth Google/Facebook (BONUS +5 points)

**Implémentation** :
- OAuth Google et/ou Facebook Connect
- Configuration Supabase OAuth
- Boutons "Sign in with Google/Facebook"
- Gestion du profil OAuth

---

## 6️⃣ BASE DE DONNÉES & FONCTIONS

### 6.1 Schéma Airtable

**Exigences minimales** :
- ✅ Minimum **3 tables**
- ✅ Relations entre tables configurées (Linked Records)
- ✅ Types de champs appropriés
- ✅ Minimum **15 données mockées par table**

**Critères de qualité** :
- Schéma cohérent et normalisé
- Pas de redondance excessive
- Relations logiques
- Nommage clair (en anglais de préférence)

### 6.2 Fonctions PostgreSQL

**Exigences** :
- ✅ **2 à 3 fonctions PostgreSQL** créées
- ✅ Fonctions **documentées** (commentaires SQL)
- ✅ Fonctions **utilisées dans l'application**

**Exemples de fonctions** :
```sql
-- Fonction 1 : get_user_data
CREATE OR REPLACE FUNCTION get_user_data(user_id UUID)
RETURNS TABLE (...)
AS $$
  -- Récupère toutes les données d'un utilisateur
$$;

-- Fonction 2 : list_items_filtered
CREATE OR REPLACE FUNCTION list_items_filtered(
  category TEXT,
  min_price NUMERIC
)
RETURNS TABLE (...)
AS $$
  -- Liste les items selon filtres
$$;

-- Fonction 3 : aggregate_stats
CREATE OR REPLACE FUNCTION aggregate_stats()
RETURNS JSON
AS $$
  -- Calcule les statistiques globales
$$;
```

**Documentation** :
- Commentaires dans le code SQL
- Documentation dans Notion (usage, paramètres, retour)
- Exemples d'appel depuis l'app

### 6.3 Dashboard avec Filtres PostgreSQL (BONUS +5 points)

**Fonctionnalités avancées** :
- Dashboard admin avec KPIs
- Filtres dynamiques (dates, catégories, etc.)
- Utilisation des fonctions PostgreSQL
- Graphiques/charts (optionnel)
- Données en temps réel

---

## 7️⃣ DÉPLOIEMENT & PRODUCTION

### 7.1 Déploiement Netlify (Obligatoire)

**Exigences** :
- ✅ Application déployée sur **Netlify**
- ✅ URL fonctionnelle et accessible
- ✅ Environnement de production configuré
- ✅ Variables d'environnement correctement configurées
- ✅ Build réussi sans erreurs

**Configuration** :
```toml
# netlify.toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

**Variables d'environnement** :
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`
- `VITE_AIRTABLE_API_KEY` (si nécessaire côté client)

### 7.2 App Mobile Expo (BONUS +7 points)

**Implémentation** :
- App mobile créée avec **Expo/React Native**
- Même backend (Supabase/Airtable)
- Auth fonctionnelle sur mobile
- Features principales disponibles
- Build réussi (TestFlight/APK)

---

## 8️⃣ WORKFLOWS & AUTOMATISATIONS

### 8.1 Workflows Supabase

**Exigences** :
- Minimum **1 à 2 workflows** configurés
- Triggers fonctionnels
- Actions pertinentes pour le projet

**Exemples** :
```sql
-- Trigger : Après inscription
CREATE TRIGGER after_user_signup
AFTER INSERT ON auth.users
FOR EACH ROW
EXECUTE FUNCTION create_user_profile();

-- Trigger : Avant suppression
CREATE TRIGGER before_delete_item
BEFORE DELETE ON items
FOR EACH ROW
EXECUTE FUNCTION archive_item();
```

### 8.2 Workflows Airtable (Optionnel)

**Exemples d'automatisations** :
- Nouveau record → Email notification
- Statut change → Update autre table
- Date approche → Rappel
- Record créé → Slack notification

---

## 9️⃣ OUTILS COMPLÉMENTAIRES (BONUS)

### 9.1 Critères Génériques

**Conditions pour valider** :
- ✅ Outil pertinent pour le projet (justification requise)
- ✅ Intégration fonctionnelle
- ✅ Documentation de l'intégration
- ✅ Apporte une valeur ajoutée claire

### 9.2 Exemples d'Outils Acceptés

**Automation** :
- Make (ex-Integromat)
- n8n
- Zapier

**Communication** :
- Slack integration
- Discord webhooks
- Email automation (SendGrid, Resend)

**Analytics** :
- Plausible
- PostHog
- Mixpanel

**Autre** :
- Stripe (paiements)
- Twilio (SMS)
- Cloudinary (images)

**Points bonus** : Jusqu'à +5 points selon la complexité et la pertinence

---

## 🎯 RÉSUMÉ DES LIVRABLES

### Obligatoires (pour avoir 20/20)

| Livrable | Détails |
|----------|---------|
| Documentation Notion | Structure complète, tech doc, présentation équipe |
| Cursor Rules | 4 fichiers (principal, docs, installation, features) |
| GitHub | Repo organisé, README, tous les membres ont commit |
| MCP | 3 MCP installés et documentés |
| Sync | Airtable ↔ Supabase fonctionnelle |
| Auth | Login/Signup/Logout + protected routes |
| BDD | 3+ tables Airtable, 15+ données mockées |
| Fonctions SQL | 2-3 fonctions PostgreSQL documentées |
| Déploiement | App sur Netlify (URL live) |
| Workflows | 1-2 workflows Supabase |

### Bonus (pour dépasser 20/20)

| Bonus | Points |
|-------|--------|
| Gestion des rôles utilisateurs | +3 |
| OAuth (Google/Facebook) | +5 |
| Dashboard avec filtres PostgreSQL | +5 |
| App mobile Expo déployée | +7 |
| Outils complémentaires pertinents | +5 |
| **TOTAL BONUS MAX** | **+25** |

---

**Date de création** : 25 novembre 2024  
**Version** : 1.0  
**Auteur** : Thomas Garcia

