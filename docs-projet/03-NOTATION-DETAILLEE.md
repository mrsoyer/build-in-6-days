# 📊 SYSTÈME DE NOTATION DÉTAILLÉ

> **Note Technique** : /20 (ramenée depuis /130)

---

## 🎯 PHILOSOPHIE

Cette notation évalue la **qualité technique** du projet selon des critères objectifs et mesurables.

**Principes** :
- ✅ Transparence : Tous les critères sont publics
- ✅ Objectivité : Checklist claire (fait/pas fait)
- ✅ Progressivité : Points bonus pour aller plus loin
- ✅ Équité : Mêmes critères pour tous

---

## 📋 GRILLE DE NOTATION (/130 points → /20)

### 1. DOCUMENTATION NOTION (/30 points)

#### 1.1 Structure Générale (/5)
- [ ] Page principale du projet (titre, description, vision) : **2 pts**
- [ ] Kanban (To Do / Doing / Done) fonctionnel : **1 pt**
- [ ] Roadmap des 6 jours : **1 pt**
- [ ] Changelog (journal des modifications) : **1 pt**

#### 1.2 Documentation Technique (/5)
- [ ] Architecture du projet documentée (schéma clair) : **2 pts**
- [ ] Schema BDD (Airtable + Supabase) : **1 pt**
- [ ] Guide d'installation complet : **1 pt**
- [ ] Variables d'environnement listées : **1 pt**

#### 1.3 Accessibilité (/5)
- [ ] Documentation compréhensible par un **développeur** : **2 pts**
- [ ] Documentation compréhensible par un **non-tech** : **2 pts**
- [ ] Navigation intuitive entre pages : **1 pt**

#### 1.4 Présentation Équipe (/5)
- [ ] Nom + photo de chaque membre : **2 pts**
- [ ] Rôles clairement définis : **1 pt**
- [ ] Contributions principales (qui a fait quoi) : **2 pts**

#### 1.5 Intégration MCP Notion (/5)
- [ ] MCP Notion installé et configuré : **2 pts**
- [ ] Documentation mise à jour via Cursor (preuve) : **2 pts**
- [ ] Exemple de commande Cursor → Notion : **1 pt**

#### 1.6 Mise à Jour Automatique (/5)
- [ ] Changelog généré automatiquement : **3 pts**
- [ ] Roadmap synchronisée avec le projet : **2 pts**

---

### 2. CURSOR RULES & ORGANISATION (/25 points)

#### 2.1 `.cursorrules` Principal (/5)
- [ ] Fichier existe et est complet : **1 pt**
- [ ] Configuration MCP (Notion, Supabase, Airtable) : **1 pt**
- [ ] Contraintes techniques globales : **1 pt**
- [ ] Architecture documentée (Read/Write) : **1 pt**
- [ ] Liens vers autres cursor rules : **1 pt**

#### 2.2 `.cursorrules-docs` (/3)
- [ ] Fichier existe : **1 pt**
- [ ] Règles pour générer/maintenir doc : **1 pt**
- [ ] Intégration avec Notion : **1 pt**

#### 2.3 Cursor Rules par Fonctionnalité (/7)
- [ ] Au moins 2 fichiers `.cursorrules-[feature]` : **3 pts**
- [ ] Contenu pertinent et structuré : **2 pts**
- [ ] Utilisés effectivement pendant le développement : **2 pts**

#### 2.4 `.cursorrules-installation` (/5)
- [ ] Fichier existe : **2 pts**
- [ ] Commandes d'installation automatisées : **2 pts**
- [ ] Un autre dev peut installer facilement : **1 pt**

#### 2.5 Organisation et Clarté (/5)
- [ ] Structure logique et cohérente : **2 pts**
- [ ] Commentaires explicatifs : **1 pt**
- [ ] Évolution visible (pas statique) : **2 pts**

---

### 3. GITHUB & VERSIONING (/10 points)

#### 3.1 Repository Bien Organisé (/3)
- [ ] Structure de fichiers claire : **1 pt**
- [ ] Nommage cohérent : **1 pt**
- [ ] Pas de fichiers brouillon ("test123.js") : **1 pt**

#### 3.2 README Complet (/3)
- [ ] Sections obligatoires présentes (10 sections) : **2 pts**
- [ ] Instructions d'installation claires : **1 pt**

#### 3.3 Commits par Membre (/4)
- [ ] **Tous les membres** ont fait au moins 1 commit : **4 pts**
  - 0 pt si un membre n'a pas commit
  - Vérifiable via `git shortlog -sn`

---

### 4. MCP & SYNCHRONISATION (/20 points)

#### 4.1 MCP Notion (/4)
- [ ] MCP installé : **1 pt**
- [ ] Configuration correcte (API key) : **1 pt**
- [ ] Test de connexion validé : **1 pt**
- [ ] Documentation de l'utilisation : **1 pt**

#### 4.2 MCP Supabase (/4)
- [ ] MCP installé : **1 pt**
- [ ] Configuration correcte (URL + keys) : **1 pt**
- [ ] Test de connexion validé : **1 pt**
- [ ] Documentation de l'utilisation : **1 pt**

#### 4.3 MCP Airtable (/4)
- [ ] MCP installé : **1 pt**
- [ ] Configuration correcte (API key + Base ID) : **1 pt**
- [ ] Test de connexion validé : **1 pt**
- [ ] Documentation de l'utilisation : **1 pt**

#### 4.4 Sync Airtable ↔ Supabase (/5)
- [ ] Extension Supabase installée dans Airtable : **1 pt**
- [ ] Mapping tables/champs correct : **2 pts**
- [ ] Test INSERT : données apparaissent dans Supabase : **1 pt**
- [ ] Test UPDATE : modifications synchronisées : **1 pt**

#### 4.5 Architecture Respectée (/3)
- [ ] App lit UNIQUEMENT depuis Supabase : **2 pts**
- [ ] Admin écrit UNIQUEMENT dans Airtable : **1 pt**

---

### 5. AUTHENTIFICATION (/15 points)

#### 5.1 Auth Client Fonctionnelle (/10)
- [ ] Page Login (email + password) : **2 pts**
- [ ] Page Signup (inscription) : **2 pts**
- [ ] Logout fonctionnel : **2 pts**
- [ ] Protected routes (redirect si non-auth) : **2 pts**
- [ ] Gestion session (persist après refresh) : **2 pts**

#### 5.2 Protected Routes (/5)
- [ ] Implémentation correcte : **3 pts**
- [ ] Redirection vers /login si non-auth : **2 pts**

#### 5.3 BONUS : Gestion des Rôles (+3)
- [ ] Rôles différents (user/admin) : **+2 pts**
- [ ] Permissions par rôle : **+1 pt**

#### 5.4 BONUS : OAuth (+5)
- [ ] OAuth Google et/ou Facebook : **+3 pts**
- [ ] Configuration Supabase OAuth : **+2 pts**

---

### 6. BASE DE DONNÉES & FONCTIONS (/15 points)

#### 6.1 Schema Airtable Cohérent (/5)
- [ ] Minimum 3 tables : **2 pts**
- [ ] Relations entre tables configurées : **2 pts**
- [ ] Minimum 15 données mockées par table : **1 pt**

#### 6.2 Fonctions PostgreSQL (/7)
- [ ] 2-3 fonctions créées : **3 pts**
- [ ] Fonctions documentées (commentaires SQL) : **2 pts**
- [ ] Documentation dans Notion : **2 pts**

#### 6.3 Fonctions Utilisées dans l'App (/3)
- [ ] Fonctions appelées depuis l'application : **3 pts**

#### 6.4 BONUS : Dashboard avec Filtres PostgreSQL (+5)
- [ ] Dashboard admin avec KPIs : **+2 pts**
- [ ] Filtres dynamiques utilisant PostgreSQL : **+2 pts**
- [ ] Graphiques/charts : **+1 pt**

---

### 7. DÉPLOIEMENT & PRODUCTION (/10 points)

#### 7.1 App Déployée sur Netlify (/7)
- [ ] URL fonctionnelle et accessible : **3 pts**
- [ ] Build réussi sans erreurs : **2 pts**
- [ ] Variables d'environnement configurées : **2 pts**

#### 7.2 Environnement de Production (/3)
- [ ] Configuration `netlify.toml` correcte : **2 pts**
- [ ] Redirects configurés (SPA) : **1 pt**

#### 7.3 BONUS : App Mobile Expo (+7)
- [ ] App mobile créée avec Expo : **+3 pts**
- [ ] Auth fonctionnelle sur mobile : **+2 pts**
- [ ] Features principales disponibles : **+2 pts**

---

### 8. WORKFLOWS & AUTOMATISATIONS (/5 points)

#### 8.1 Workflows Supabase (/5)
- [ ] Minimum 1-2 workflows configurés : **3 pts**
- [ ] Triggers fonctionnels : **1 pt**
- [ ] Actions pertinentes : **1 pt**

---

### 9. OUTILS COMPLÉMENTAIRES (BONUS)

#### 9.1 Intégration Pertinente (+5 max)
- [ ] Outil intégré (Make, n8n, etc.) : **+2 pts**
- [ ] Intégration fonctionnelle : **+2 pts**
- [ ] Documentation de l'intégration : **+1 pt**

**Condition** : Justification claire de la valeur ajoutée

---

## 🧮 CALCUL FINAL

### Total des Points
```
TOTAL = Somme des points obtenus sur /130
```

### Conversion en Note sur 20
```
NOTE TECHNIQUE /20 = (TOTAL / 130) × 20 + BONUS
```

**BONUS plafonnés** : Maximum +25 points, mais note finale plafonnée à 20/20

### Exemples de Calcul

**Exemple 1 : Projet Complet**
```
Documentation Notion : 28/30
Cursor Rules : 23/25
GitHub : 9/10
MCP & Sync : 19/20
Auth : 14/15
BDD : 14/15
Déploiement : 10/10
Workflows : 5/5
TOTAL : 122/130

Bonus :
- Gestion des rôles : +3
- Dashboard filtres : +5
TOTAL BONUS : +8

Note = (122/130) × 20 + (8/130) × 20
Note = 18.77 + 1.23 = 20/20 ✅
```

**Exemple 2 : Projet Basique**
```
Documentation Notion : 22/30
Cursor Rules : 18/25
GitHub : 8/10
MCP & Sync : 16/20
Auth : 12/15
BDD : 12/15
Déploiement : 7/10
Workflows : 3/5
TOTAL : 98/130

Pas de bonus

Note = (98/130) × 20 = 15.08/20
```

---

## 📊 RÉPARTITION DES POINTS

| Catégorie | Points | % |
|-----------|--------|---|
| Documentation Notion | 30 | 23% |
| Cursor Rules | 25 | 19% |
| MCP & Sync | 20 | 15% |
| Auth | 15 | 12% |
| BDD & Fonctions | 15 | 12% |
| Déploiement | 10 | 8% |
| GitHub | 10 | 8% |
| Workflows | 5 | 4% |
| **TOTAL** | **130** | **100%** |

**Bonus disponibles** : +25 points max

---

## ✅ CHECKLIST VALIDATION

Pour avoir **15/20 minimum** :
- [ ] Documentation Notion complète (20/30)
- [ ] Cursor Rules présentes (15/25)
- [ ] GitHub organisé + tous les membres commit (8/10)
- [ ] 3 MCP installés (12/12)
- [ ] Sync Airtable-Supabase fonctionnelle (5/5)
- [ ] Auth complète (12/15)
- [ ] BDD avec données (10/15)
- [ ] App déployée (7/10)
- [ ] 1 workflow (3/5)

**Total minimum** : 92/130 → **14.15/20**

---

**Date de création** : 25 novembre 2024  
**Version** : 1.0  
**Auteur** : Thomas Garcia

