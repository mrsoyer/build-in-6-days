# 📋 DOCUMENT DE DEMANDE INITIALE - COURS M1

> **"IA-Driven Product Building – De l'idée au déploiement avec Cursor & No-Code Tools"**

## 📊 RÉSUMÉ EXÉCUTIF

| Élément | Détail |
|---------|--------|
| **Durée totale** | 42 heures (6 séances de 7h) |
| **Étudiants** | 40 (7-8 groupes de 5-6) |
| **Dates** | 19/11, 26/11, 03/12, 10/12, 17/12, 28/01 |
| **Outil central** | **Cursor** (modes Browser, Agent, Ask, Plan) |
| **Stack** | Lovable, Supabase, Airtable, Notion |
| **Objectif** | 1 produit complet déployé par groupe |
| **Livrables** | Landing + App + Dashboard + Sync + Doc |

### 🎯 Ce que les étudiants vont construire :
✅ Landing page avec **Lovable**  
✅ App full-stack avec **Cursor + Supabase**  
✅ Authentification et **dashboard client**  
✅ Base opérationnelle **Airtable** synchronisée  
✅ Documentation **Notion** via MCP  
✅ Déploiement en production  

---

## 🎯 CONTEXTE

**Établissement** : Master 1  
**Nombre d'étudiants** : 40  
**Volume horaire total** : 42 heures (6 séances de 7h)  
**Dates** : 19/11, 26/11, 03/12, 10/12, 17/12, 28/01  
**Horaires** : 9h30-12h30 / 13h30-17h30  
**Tarif** : 100€ TTC/h  
**Langue** : Français  
**Modalité** : Présentiel  

---

## ✅ ÉLÉMENTS TECHNIQUES OBLIGATOIRES

Chaque projet doit **OBLIGATOIREMENT** inclure les éléments suivants :

### 🔧 Cursor - Maîtrise complète
- [ ] Tour d'horizon complet de Cursor
- [ ] Utilisation des **4 modes** : Browser, Agent, Ask, Plan
- [ ] Configuration **Cursor Rules** (.cursorrules)
- [ ] Installation et utilisation **MCP Supabase**
- [ ] Installation et utilisation **MCP Notion**

### 🌐 Landing & Interface
- [ ] **Landing page avec Lovable** (OBLIGATOIRE)
- [ ] **Dashboard client** avec authentification
- [ ] Accès personnalisé par utilisateur

### 🔐 Backend & Data
- [ ] **Authentification Supabase** (signup/login)
- [ ] Base de données Supabase structurée
- [ ] **Synchronisation Supabase ↔ Airtable** (plugin officiel)

### 📊 Operations
- [ ] Base Airtable opérationnelle
- [ ] Workflows et automatisations
- [ ] Documentation Notion complète

---

## 🚀 VISION DU COURS

**Titre proposé** : **"IA-Driven Product Building – De l'idée au déploiement avec Cursor & No-Code Tools"**

**Philosophie** : Apprendre en faisant  
**ADN** : Créer un produit complet fonctionnel en 6 séances

---

## 🎓 OBJECTIF PÉDAGOGIQUE GLOBAL

Former des étudiants capables de **concevoir, développer et déployer un produit digital complet** en utilisant l'IA comme accélérateur principal, tout en comprenant :
- L'architecture d'un produit
- La gestion des données
- L'automatisation des workflows
- Le déploiement en production

---

## 🛠️ STACK TECHNOLOGIQUE

**Au centre : CURSOR (outil principal)**
- Génération de code assistée par IA
- Prompt engineering avancé
- Debug et refactoring IA-first
- Architecture multi-fichiers
- **Modes Cursor** : Browser, Agent, Ask, Plan
- **MCP (Model Context Protocol)** : Supabase, Notion
- **Cursor Rules** : Configuration personnalisée (.cursorrules)

**Outils complémentaires :**
- **Lovable** : Génération rapide de landing pages (OBLIGATOIRE)
- **Supabase** : Base de données, authentification, API temps réel, MCP
- **Airtable** : Gestion opérationnelle, CMS no-code, workflows, sync Supabase
- **Notion** : Documentation, knowledge management, process, MCP

---

## 📚 CHANGEMENTS PAR RAPPORT AUX SYLLABUS INITIAUX

### ❌ Ce qu'on abandonne :
- Séparation artificielle entre "productivité" et "développement"
- Approche théorique des outils
- Projets déconnectés les uns des autres

### ✅ Ce qu'on gagne :
- **Un seul projet fil rouge** qui évolue sur 6 séances
- Stack technique professionnelle et moderne
- Cursor comme hub central de création
- Compétences immédiatement valorisables sur le marché

---

## 🎯 PROJET FIL ROUGE PROPOSÉ

**Concept** : Chaque groupe (5-6 étudiants) crée une **mini-startup complète** avec :

1. **Landing Page** (générée avec Lovable) - **OBLIGATOIRE**
   - Design moderne et responsive
   - Call-to-action clair
   - Lien vers l'application

2. **Application web fonctionnelle** (générée avec Cursor)
   - Frontend moderne (Next.js/React)
   - Backend Supabase avec MCP
   - **Authentification Supabase** (signup/login)
   - **Dashboard client** avec accès personnalisé
   - CRUD complet

3. **Système opérationnel Airtable**
   - Gestion clients/users
   - Tracking des KPIs
   - Automatisations business
   - **Synchronisation Supabase ↔ Airtable** (plugin officiel)

4. **Documentation Notion** (via MCP Notion)
   - Wiki produit
   - Process internes
   - Roadmap
   - Intégration avec Cursor

5. **Déploiement live**
   - Landing page publique (Lovable)
   - App déployée (Vercel/Netlify)
   - Démo fonctionnelle

---

## 📅 DÉROULÉ PÉDAGOGIQUE (6 séances)

### **SÉANCE 1 (19/11) – Foundations & Setup**

**Matin (3h)**
- **Tour d'horizon complet Cursor** :
  - Interface et fonctionnalités IA
  - **Les 4 modes** : Browser, Agent, Ask, Plan
  - Premier prompt : générer une page web simple
  - Comprendre le code généré
- **Cursor Rules** : Configuration .cursorrules
- Setup environnement (Node, Git, Cursor)

**Après-midi (4h)**
- **Landing Page avec Lovable** (OBLIGATOIRE)
  - Création compte Lovable
  - Génération d'une landing page moderne
  - Export et customisation
  - Déploiement
- Introduction Supabase : création compte, premier projet
- Introduction Notion : création du workspace projet

**🎯 Livrable séance 1** : Landing page Lovable déployée + workspace Notion initialisé + .cursorrules configuré

---

### **SÉANCE 2 (26/11) – Database & Authentication**

**Matin (3h)**
- **Installation et configuration MCP Supabase** dans Cursor
  - Configuration du MCP
  - Test de la connexion
- Design de la base de données dans Supabase
- Génération des schémas avec Cursor + MCP
- Comprendre les relations (tables, foreign keys)

**Après-midi (4h)**
- **Implémentation authentification Supabase** (OBLIGATOIRE)
  - Configuration Supabase Auth
  - Génération des pages login/signup avec Cursor
  - Sécurisation des routes
  - Tests utilisateurs
- **Début du dashboard client** avec accès personnalisé

**🎯 Livrable séance 2** : App avec auth Supabase fonctionnelle + base de données structurée + MCP Supabase installé

---

### **SÉANCE 3 (03/12) – Core Features & CRUD**

**Matin (3h)**
- Définition des fonctionnalités principales du produit
- Génération du CRUD complet avec Cursor
- **Finalisation du dashboard client** (OBLIGATOIRE)
  - Affichage des données personnalisées
  - Gestion des permissions
  - Interface utilisateur intuitive

**Après-midi (4h)**
- Intégration API externes (OpenAI ou autres selon projet)
- Gestion d'erreurs et edge cases
- Amélioration UX/UI
- Tests en mode Browser de Cursor

**🎯 Livrable séance 3** : MVP fonctionnel avec dashboard client complet et features principales

---

### **SÉANCE 4 (10/12) – Operations & Airtable**

**Matin (3h)**
- **Installation et configuration MCP Notion** dans Cursor
  - Configuration du MCP
  - Test de la connexion
  - Utilisation du MCP pour documenter le projet
- Introduction Airtable orientée business ops
- Création base Airtable pour gérer le produit
- Relations entre tables (users, transactions, support...)

**Après-midi (4h)**
- Interfaces Airtable par rôle (admin, support, sales)
- Automations natives Airtable
- **Synchronisation Supabase ↔ Airtable** (OBLIGATOIRE)
  - Installation du plugin officiel Supabase pour Airtable
  - Configuration de la sync bidirectionnelle
  - Tests et validation des données

**🎯 Livrable séance 4** : Système opérationnel Airtable synchronisé avec Supabase + MCP Notion installé

---

### **SÉANCE 5 (17/12) – Polish & Documentation**

**Matin (3h)**
- Refactoring code avec Cursor
- Optimisations et best practices
- Tests et debugging

**Après-midi (4h)**
- Documentation complète dans Notion
- Création de tutoriels internes
- Préparation pitch et démo
- Vidéo de démo (optionnel)

**🎯 Livrable séance 5** : Produit finalisé + documentation complète

---

### **SÉANCE 6 (28/01) – Demo Day & Advanced Topics**

**Matin (3h)**
- **DEMO DAY** : Chaque groupe présente son produit (15 min/groupe)
- Pitch + démo live + Q&A

**Après-midi (4h)**
- Retours sur les projets
- Sujets avancés selon besoins identifiés :
  - Lovable/Bolt pour prototypage rapide
  - Scaling et optimisation
  - Monétisation et growth
- Perspectives professionnelles

**🎯 Livrable final** : PDF complet + code GitHub + app déployée + démo

---

## 📦 LIVRABLE FINAL ATTENDU

**PDF comprenant :**

1. **Executive Summary**
   - Concept du produit
   - Problème résolu
   - Cible utilisateur

2. **Architecture technique**
   - Stack utilisée (Cursor + MCP Supabase + MCP Notion)
   - Schéma base de données Supabase
   - Flow de données
   - Configuration .cursorrules

3. **Code & Prompts Cursor**
   - Repository GitHub
   - **Prompts Cursor clés utilisés** (pour chaque mode : Agent, Ask, Browser, Plan)
   - Explications des choix techniques
   - Documentation de l'utilisation des MCP

4. **Interfaces & Pages** (OBLIGATOIRE)
   - **Landing page Lovable** (lien + screenshots)
   - **Dashboard client** avec auth Supabase (screenshots + démo)
   - Pages principales de l'app

5. **Système opérationnel**
   - Base Airtable (lien de partage)
   - **Preuve de synchronisation Supabase ↔ Airtable**
   - Workflows et automatisations
   - KPIs trackés

6. **Documentation Notion** (via MCP)
   - Workspace Notion (lien)
   - Guide d'utilisation
   - Process internes
   - Captures d'écran de l'utilisation du MCP Notion

7. **Démo & Déploiement**
   - URL landing page (Lovable)
   - URL de l'app déployée (Vercel/Netlify)
   - Vidéo démo (3-5 min) montrant :
     - Landing page
     - Auth Supabase
     - Dashboard client
     - Sync Airtable
   - Screenshots clés

---

## 🎯 COMPÉTENCES ACQUISES

**Cursor & IA :**
- Maîtrise complète des **4 modes Cursor** (Browser, Agent, Ask, Plan)
- Configuration et optimisation des **Cursor Rules** (.cursorrules)
- Installation et utilisation des **MCP** (Supabase, Notion)
- Prompt engineering avancé pour génération de code
- Debug et refactoring assisté par IA

**Techniques Full-Stack :**
- Architecture full-stack moderne (Next.js/React)
- Gestion base de données relationnelle (Supabase)
- **Authentification utilisateur** (Supabase Auth)
- Création de **dashboards clients** personnalisés
- Déploiement en production (Vercel/Netlify)
- APIs et intégrations externes

**No-Code & Automatisation :**
- Génération rapide de landing pages (**Lovable**)
- Gestion opérationnelle avec **Airtable**
- **Synchronisation Supabase ↔ Airtable** (plugin officiel)
- Workflows et automatisations business
- Documentation structurée avec **Notion**

**Business & Soft Skills :**
- Product thinking et conception UX
- Operations management et KPIs
- Documentation professionnelle
- Présentation et pitch produit
- Travail en équipe agile

---

## 💡 EXEMPLES DE PROJETS ÉTUDIANTS

1. **SaaS Tool** : Générateur de pitch deck IA
2. **Marketplace** : Location d'équipement entre étudiants
3. **Content Platform** : Plateforme de micro-learning
4. **Booking System** : Réservation de salles/équipements
5. **Community App** : Réseau social de niche
6. **Productivity Tool** : Task manager avec IA
7. **E-commerce** : Mini-boutique avec paiement
8. **Dashboard Analytics** : Outil de data viz personnalisé

---

## 📊 ÉVALUATION (note sur 20)

**Critères :**

### Éléments obligatoires (/12)
- **Landing page Lovable** fonctionnelle : /2
- **Authentification Supabase** opérationnelle : /2
- **Dashboard client** avec accès personnalisé : /2
- **Synchronisation Supabase ↔ Airtable** : /2
- **MCP Supabase et Notion** installés et utilisés : /2
- **Utilisation des 4 modes Cursor** (démontrée) : /2

### Qualité du projet (/8)
- Fonctionnalité globale du produit : /2
- Qualité technique (code, architecture, .cursorrules) : /2
- Système opérationnel Airtable : /1
- Documentation Notion complète : /1
- Démo et présentation : /2

**Bonus (points supplémentaires)**
- Créativité et originalité : +1
- Complexité technique avancée : +1
- UX/UI exceptionnelle : +1

---

## ⚠️ POINTS D'ATTENTION

**Logistique :**
- 40 étudiants = 7-8 groupes de 5-6
- Besoin de salles avec WiFi et prises
- Chaque étudiant doit avoir un laptop
- Vidéoprojecteur pour les démos

**Prérequis techniques étudiants :**
- Laptop avec macOS, Windows ou Linux
- Minimum 8GB RAM
- Connexion internet stable
- Navigateur moderne (Chrome/Firefox)

**Comptes à créer (gratuits) :**
- [ ] **Cursor** (plan gratuit ou Pro recommandé)
- [ ] **Lovable** (compte gratuit)
- [ ] **Supabase** (plan gratuit)
- [ ] **Airtable** (plan gratuit)
- [ ] **Notion** (plan gratuit)
- [ ] **Vercel** ou **Netlify** (déploiement gratuit)
- [ ] **GitHub** (gestion de code)

**Installations requises :**
- [ ] Node.js (version LTS)
- [ ] Git
- [ ] Cursor IDE
- [ ] Terminal/Console

**Pédagogie :**
- Alternance théorie/pratique (20/80)
- Support en temps réel pendant les TPs
- Encourager l'autonomie et la débrouillardise
- Valoriser l'erreur comme apprentissage

**Technique :**
- Prévoir plan B si Cursor down
- Documentation de secours
- Templates de démarrage pour gagner du temps

---

## ✅ PROCHAINES ÉTAPES

### Phase 1 : Validation (Semaine du 29/10)
- [ ] ✅ Validation du syllabus global avec Stéphane
- [ ] Feedback sur les éléments obligatoires
- [ ] Confirmation des dates et logistique

### Phase 2 : Préparation pédagogique (Semaines 1-2 Novembre)
- [ ] Création des **supports de cours détaillés** par séance (6 séances)
- [ ] Rédaction des **tutoriels pas-à-pas** pour :
  - Installation MCP Supabase
  - Installation MCP Notion
  - Configuration .cursorrules
  - Sync Supabase ↔ Airtable
  - Utilisation des 4 modes Cursor
- [ ] Création des **exercices pratiques** pour chaque séance

### Phase 3 : Ressources techniques (Semaines 2-3 Novembre)
- [ ] Préparation des **templates de démarrage** :
  - Template Next.js avec Supabase
  - Template .cursorrules optimisé
  - Template base Airtable
  - Template Notion workspace
- [ ] Création d'un **repo GitHub avec toutes les ressources**
- [ ] Setup des comptes démo pour les démos en cours

### Phase 4 : Test & Ajustements (Semaine du 11 Novembre)
- [ ] **Test du parcours complet** en conditions réelles
- [ ] Vérification de tous les éléments obligatoires
- [ ] Ajustements finaux basés sur les tests
- [ ] Préparation des slides de présentation

### Phase 5 : Kit étudiant (Avant le 19/11)
- [ ] Guide de préparation pour les étudiants
- [ ] Checklist des comptes à créer
- [ ] Checklist des installations requises
- [ ] FAQ anticipée

---

## 📧 CONTACT & VALIDATION

**Enseignant** : Thomas  
**Coordinateur** : Stéphane  
**Email** : [À compléter]

**Date de création** : 29/10/2025  
**Dernière mise à jour** : 29/10/2025  
**Version** : 2.0 - Intégration éléments techniques obligatoires

---

## 📝 NOTES & MODIFICATIONS

**v2.0 (29/10/2025)** :
- Intégration des éléments techniques obligatoires
- Ajout MCP Supabase et MCP Notion
- Ajout Landing page Lovable obligatoire
- Ajout Dashboard client avec auth
- Ajout Sync Supabase ↔ Airtable
- Ajout des 4 modes Cursor
- Restructuration du déroulé pédagogique
- Mise à jour des critères d'évaluation

**v1.0 (29/10/2025)** :
- Version initiale basée sur les 2 syllabus originaux

