# ✅ CHECKLIST PROJET - AUTO-ÉVALUATION

> Utilisez cette checklist pour suivre votre progression et vous auto-évaluer

---

## 📊 PROGRESSION GLOBALE

**Total Points** : _____ / 130  
**Bonus** : _____ / 25  
**Note Estimée** : _____ / 20

---

## 📚 1. DOCUMENTATION NOTION (/30 points)

### Structure Générale (/5)
- [ ] Page principale du projet (titre, description, vision) — **2 pts**
- [ ] Kanban (To Do / Doing / Done) fonctionnel — **1 pt**
- [ ] Roadmap des 6 jours — **1 pt**
- [ ] Changelog (journal des modifications) — **1 pt**

**Sous-total** : _____ / 5

### Documentation Technique (/5)
- [ ] Architecture du projet documentée (schéma clair) — **2 pts**
- [ ] Schema BDD (Airtable + Supabase) — **1 pt**
- [ ] Guide d'installation complet — **1 pt**
- [ ] Variables d'environnement listées — **1 pt**

**Sous-total** : _____ / 5

### Accessibilité (/5)
- [ ] Documentation compréhensible par un développeur — **2 pts**
- [ ] Documentation compréhensible par un non-tech — **2 pts**
- [ ] Navigation intuitive entre pages — **1 pt**

**Sous-total** : _____ / 5

### Présentation Équipe (/5)
- [ ] Nom + photo de chaque membre — **2 pts**
- [ ] Rôles clairement définis — **1 pt**
- [ ] Contributions principales (qui a fait quoi) — **2 pts**

**Sous-total** : _____ / 5

### Intégration MCP Notion (/5)
- [ ] MCP Notion installé et configuré — **2 pts**
- [ ] Documentation mise à jour via Cursor (preuve) — **2 pts**
- [ ] Exemple de commande Cursor → Notion — **1 pt**

**Sous-total** : _____ / 5

### Mise à Jour Automatique (/5)
- [ ] Changelog généré automatiquement — **3 pts**
- [ ] Roadmap synchronisée avec le projet — **2 pts**

**Sous-total** : _____ / 5

**TOTAL NOTION** : _____ / 30

---

## ⚙️ 2. CURSOR RULES & ORGANISATION (/25 points)

### .cursorrules Principal (/5)
- [ ] Fichier existe et est complet — **1 pt**
- [ ] Configuration MCP (Notion, Supabase, Airtable) — **1 pt**
- [ ] Contraintes techniques globales — **1 pt**
- [ ] Architecture documentée (Read/Write) — **1 pt**
- [ ] Liens vers autres cursor rules — **1 pt**

**Sous-total** : _____ / 5

### .cursorrules-docs (/3)
- [ ] Fichier existe — **1 pt**
- [ ] Règles pour générer/maintenir doc — **1 pt**
- [ ] Intégration avec Notion — **1 pt**

**Sous-total** : _____ / 3

### Cursor Rules par Fonctionnalité (/7)
- [ ] Au moins 2 fichiers `.cursorrules-[feature]` — **3 pts**
- [ ] Contenu pertinent et structuré — **2 pts**
- [ ] Utilisés effectivement pendant le développement — **2 pts**

**Sous-total** : _____ / 7

### .cursorrules-installation (/5)
- [ ] Fichier existe — **2 pts**
- [ ] Commandes d'installation automatisées — **2 pts**
- [ ] Un autre dev peut installer facilement — **1 pt**

**Sous-total** : _____ / 5

### Organisation et Clarté (/5)
- [ ] Structure logique et cohérente — **2 pts**
- [ ] Commentaires explicatifs — **1 pt**
- [ ] Évolution visible (pas statique) — **2 pts**

**Sous-total** : _____ / 5

**TOTAL CURSOR RULES** : _____ / 25

---

## 🔌 3. MCP & SYNCHRONISATION (/20 points)

### MCP Notion (/4)
- [ ] MCP installé — **1 pt**
- [ ] Configuration correcte (API key) — **1 pt**
- [ ] Test de connexion validé — **1 pt**
- [ ] Documentation de l'utilisation — **1 pt**

**Sous-total** : _____ / 4

### MCP Supabase (/4)
- [ ] MCP installé — **1 pt**
- [ ] Configuration correcte (URL + keys) — **1 pt**
- [ ] Test de connexion validé — **1 pt**
- [ ] Documentation de l'utilisation — **1 pt**

**Sous-total** : _____ / 4

### MCP Airtable (/4)
- [ ] MCP installé — **1 pt**
- [ ] Configuration correcte (API key + Base ID) — **1 pt**
- [ ] Test de connexion validé — **1 pt**
- [ ] Documentation de l'utilisation — **1 pt**

**Sous-total** : _____ / 4

### Sync Airtable ↔ Supabase (/5)
- [ ] Extension Supabase installée dans Airtable — **1 pt**
- [ ] Mapping tables/champs correct — **2 pts**
- [ ] Test INSERT : données apparaissent dans Supabase — **1 pt**
- [ ] Test UPDATE : modifications synchronisées — **1 pt**

**Sous-total** : _____ / 5

### Architecture Respectée (/3)
- [ ] App lit UNIQUEMENT depuis Supabase — **2 pts**
- [ ] Admin écrit UNIQUEMENT dans Airtable — **1 pt**

**Sous-total** : _____ / 3

**TOTAL MCP & SYNC** : _____ / 20

---

## 🔐 4. AUTHENTIFICATION (/15 points)

### Auth Client Fonctionnelle (/10)
- [ ] Page Login (email + password) — **2 pts**
- [ ] Page Signup (inscription) — **2 pts**
- [ ] Logout fonctionnel — **2 pts**
- [ ] Protected routes (redirect si non-auth) — **2 pts**
- [ ] Gestion session (persist après refresh) — **2 pts**

**Sous-total** : _____ / 10

### Protected Routes (/5)
- [ ] Implémentation correcte — **3 pts**
- [ ] Redirection vers /login si non-auth — **2 pts**

**Sous-total** : _____ / 5

### BONUS : Gestion des Rôles
- [ ] Rôles différents (user/admin) — **+2 pts**
- [ ] Permissions par rôle — **+1 pt**

### BONUS : OAuth
- [ ] OAuth Google et/ou Facebook — **+3 pts**
- [ ] Configuration Supabase OAuth — **+2 pts**

**TOTAL AUTH** : _____ / 15 + _____ bonus

---

## 🗄️ 5. BASE DE DONNÉES & FONCTIONS (/15 points)

### Schema Airtable Cohérent (/5)
- [ ] Minimum 3 tables — **2 pts**
- [ ] Relations entre tables configurées — **2 pts**
- [ ] Minimum 15 données mockées par table — **1 pt**

**Sous-total** : _____ / 5

### Fonctions PostgreSQL (/7)
- [ ] 2-3 fonctions créées — **3 pts**
- [ ] Fonctions documentées (commentaires SQL) — **2 pts**
- [ ] Documentation dans Notion — **2 pts**

**Sous-total** : _____ / 7

### Fonctions Utilisées dans l'App (/3)
- [ ] Fonctions appelées depuis l'application — **3 pts**

**Sous-total** : _____ / 3

### BONUS : Dashboard avec Filtres PostgreSQL
- [ ] Dashboard admin avec KPIs — **+2 pts**
- [ ] Filtres dynamiques utilisant PostgreSQL — **+2 pts**
- [ ] Graphiques/charts — **+1 pt**

**TOTAL BDD** : _____ / 15 + _____ bonus

---

## 🚀 6. DÉPLOIEMENT & PRODUCTION (/10 points)

### App Déployée sur Netlify (/7)
- [ ] URL fonctionnelle et accessible — **3 pts**
- [ ] Build réussi sans erreurs — **2 pts**
- [ ] Variables d'environnement configurées — **2 pts**

**Sous-total** : _____ / 7

### Environnement de Production (/3)
- [ ] Configuration `netlify.toml` correcte — **2 pts**
- [ ] Redirects configurés (SPA) — **1 pt**

**Sous-total** : _____ / 3

### BONUS : App Mobile Expo
- [ ] App mobile créée avec Expo — **+3 pts**
- [ ] Auth fonctionnelle sur mobile — **+2 pts**
- [ ] Features principales disponibles — **+2 pts**

**TOTAL DÉPLOIEMENT** : _____ / 10 + _____ bonus

---

## 📦 7. GITHUB & VERSIONING (/10 points)

### Repository Bien Organisé (/3)
- [ ] Structure de fichiers claire — **1 pt**
- [ ] Nommage cohérent — **1 pt**
- [ ] Pas de fichiers brouillon ("test123.js") — **1 pt**

**Sous-total** : _____ / 3

### README Complet (/3)
- [ ] Sections obligatoires présentes (10 sections) — **2 pts**
- [ ] Instructions d'installation claires — **1 pt**

**Sous-total** : _____ / 3

### Commits par Membre (/4)
- [ ] **TOUS les membres** ont fait au moins 1 commit — **4 pts**

⚠️ Vérifiable via `git shortlog -sn`

**Sous-total** : _____ / 4

**TOTAL GITHUB** : _____ / 10

---

## 🔄 8. WORKFLOWS & AUTOMATISATIONS (/5 points)

### Workflows Supabase (/5)
- [ ] Minimum 1-2 workflows configurés — **3 pts**
- [ ] Triggers fonctionnels — **1 pt**
- [ ] Actions pertinentes — **1 pt**

**TOTAL WORKFLOWS** : _____ / 5

---

## 🎁 9. OUTILS COMPLÉMENTAIRES (BONUS)

### Intégration Pertinente (+5 max)
- [ ] Outil intégré (Make, n8n, etc.) — **+2 pts**
- [ ] Intégration fonctionnelle — **+2 pts**
- [ ] Documentation de l'intégration — **+1 pt**

**Condition** : Justification claire de la valeur ajoutée

**TOTAL BONUS OUTILS** : _____ / 5

---

## 📊 RÉCAPITULATIF FINAL

| Catégorie | Points Obtenus | Points Max |
|-----------|----------------|------------|
| Documentation Notion | _____ | 30 |
| Cursor Rules | _____ | 25 |
| MCP & Sync | _____ | 20 |
| Authentification | _____ | 15 |
| BDD & Fonctions | _____ | 15 |
| Déploiement | _____ | 10 |
| GitHub | _____ | 10 |
| Workflows | _____ | 5 |
| **TOTAL OBLIGATOIRE** | **_____** | **130** |
| **BONUS** | **_____** | **25** |

---

## 🧮 CALCUL NOTE FINALE

```
NOTE /20 = (Total obligatoire / 130) × 20 + (Bonus / 130) × 20
```

**Votre calcul** :
```
NOTE = (_____ / 130) × 20 + (_____ / 130) × 20 = _____ / 20
```

*Note plafonnée à 20/20*

---

## 🎯 OBJECTIFS À ATTEINDRE

- [ ] **12/20** : Au moins 78 points
- [ ] **15/20** : Au moins 98 points  
- [ ] **18/20** : Au moins 117 points + bonus

---

## 💡 ACTIONS PRIORITAIRES

### Si score < 12/20
Focalisez-vous sur :
1. Documentation Notion basique
2. Les 3 MCP installés
3. Auth fonctionnelle
4. App déployée
5. Tous les membres commit

### Si score 12-15/20
Améliorez :
1. Documentation Notion complète
2. Cursor Rules organisées
3. Fonctions SQL
4. Sync parfaite

### Si score > 15/20
Activez les bonus :
1. Gestion des rôles
2. Dashboard avec filtres
3. OAuth
4. App mobile

---

## 📅 MOMENTS CLÉS

- **Jour 3** : Auto-évaluation 1 (objectif : 50 pts)
- **Jour 5** : Auto-évaluation 2 (objectif : 100 pts)
- **Jour 6** : Évaluation finale

---

**Dernière mise à jour** : [DATE]  
**Équipe** : [NOMS]

