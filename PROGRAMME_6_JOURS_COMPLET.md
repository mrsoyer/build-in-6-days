# 🚀 PROGRAMME 6 JOURS - VIBE CODING & PRODUCTIVITÉ

> **Formation intensive : Création produit complet avec Cursor, Airtable, Supabase & Notion**

---

## 🎯 INFORMATIONS GÉNÉRALES

**Durée** : 6 jours (7h/jour = 42h total)  
**Étudiants** : 40 (10 équipes de 4)  
**Projets** : 10 projets libres  
**Format** : Présentiel intensif  

---

## 📊 SYSTÈME DE NOTATION

### **2 NOTES DISTINCTES**

#### **NOTE 1 : VIBE CODING (/20)**
```
Critères :
├─ Maîtrise Cursor (modes, rules, MCP) : /5
├─ Qualité du code : /4
├─ Résolution de bugs : /2
├─ Créativité : /3
├─ GitHub (commits réguliers) : /2
├─ Livrables : /4
```

#### **NOTE 2 : BASE DE DONNÉES & PRODUCTIVITÉ (/20)**
```
Critères :
├─ Architecture BDD (Supabase + Airtable) : /5
├─ Sync bidirectionnelle fonctionnelle : /5
├─ Workflows Airtable : /3
├─ Gestion projet Notion : /3
├─ Dashboard monitoring : /2
├─ Documentation : /2
```

### **PEER ASSESSMENT (ajustement ±20%)**

**Système de cotation entre membres d'équipe :**
```
Chaque membre a 100 points à distribuer aux 3 autres
└─ Ne peut pas se noter lui-même
└─ Doit justifier les notes extrêmes

Critères peer assessment :
├─ Contribution technique (30 points)
├─ Implication (25 points)
├─ Collaboration (25 points)
├─ Autonomie (20 points)

Calcul final :
Note finale = Note équipe × Coefficient peer
Coefficient = (Points reçus / 100)

Exemple :
- Équipe : 15/20
- Alice reçoit 110 points (très impliquée) → 15 × 1.1 = 16.5/20
- Bob reçoit 80 points (peu impliqué) → 15 × 0.8 = 12/20
```

### **ÉVALUATION MI-PARCOURS & FINALE**

**Mi-parcours (Jour 3, après-midi) :**
```
Note intermédiaire (/20) :
├─ Avancement projet : /10
├─ Livrables jours 1-3 : /6
├─ Peer assessment 1 : /4

→ Feedback détaillé par équipe
→ Ajustements possibles
```

**Évaluation finale (Jour 6) :**
```
Note finale = 40% Mi-parcours + 60% Final

Démo finale (Jour 6) :
├─ Pitch (5 min) : /4
├─ Démo live produit : /6
├─ Architecture technique : /4
├─ Q&A : /3
├─ Documentation Notion/GitHub : /3
```

---

## 📅 PROGRAMME JOUR PAR JOUR

### **JOUR 1 (19/11) - FONDATIONS & SETUP** 🏗️

#### **9h30-10h30 (1h) - STORYTELLING + INTRO CURSOR**

**Votre story captivante (30 min)**
```
"Il y a X temps..."
→ Votre parcours
→ Découverte de l'IA
→ Ce qu'elle a changé pour vous
→ Ce qu'ils vont créer en 6 jours
```

**Tour d'horizon Cursor (30 min)**
```
Démo live des 4 modes :
├─ Editor : Modifications en ligne
├─ Agent : Tâches autonomes multi-fichiers
├─ Browser : Recherche et intégration web
└─ Plan : Planification et architecture (NOUVEAUTÉ !)

"Aujourd'hui vous allez comprendre POURQUOI 
l'organisation et le contexte sont CRUCIAUX avec l'IA."
```

#### **10h30-11h00 (30 min) - FORMATION DES ÉQUIPES**

```
10 équipes de 4 étudiants
└─ VOUS décidez (mix de niveaux)

Brainstorming par équipe (15 min) :
"Quelle startup vous voulez créer ?"

Validation rapide (15 min) :
└─ Pitch 1 min par équipe
└─ Vous validez la faisabilité
```

#### **11h00-12h30 (1h30) - LANDING PAGE LOVABLE**

**Démo live (15 min)**
```
Vous créez une landing EN DIRECT devant eux
→ EFFET WHAOU

"Maintenant vous. Dans 1h, je veux voir 
10 landing pages qui déchirent."
```

**Production (1h15)**
```
Les 10 équipes créent leur landing Lovable
VOUS : Circulez, guidez, challengez
```

#### **13h30-15h00 (1h30) - GESTION DE PROJET NOTION**

**Enseignement (30 min)**
```
"Un projet sans organisation = chaos.
Avec l'IA, l'organisation devient CRITIQUE."

Démo live :
├─ Créer workspace Notion
├─ Structure de projet
├─ Roadmap
├─ Backlog
└─ Documentation

"L'IA est puissante, mais elle a besoin de CONTEXTE.
Plus votre projet est organisé, plus l'IA est efficace."
```

**Production (1h)**
```
Chaque équipe crée son workspace Notion :
├─ Page projet (brief)
├─ Roadmap 6 jours
├─ Backlog features
├─ Documentation technique
└─ Journal de bord
```

#### **15h00-16h30 (1h30) - ORGANISATION PROJET & CURSOR RULES**

**Enseignement CRUCIAL (45 min)**
```
"LE SECRET du bon vibe coding : L'ORGANISATION"

Démonstration :
├─ Structure de dossiers claire
│   src/
│   ├─ components/
│   ├─ pages/
│   ├─ lib/
│   ├─ types/
│   └─ utils/
│
├─ Nommage cohérent
│   ❌ comp1.tsx, thing.ts
│   ✅ UserProfile.tsx, apiClient.ts
│
├─ Variables explicites
│   ❌ const x = getData()
│   ✅ const userData = fetchUserProfile()
│
└─ POURQUOI ? → L'IA comprend mieux !

"Si vous nommez mal vos fichiers, l'IA va générer
du code incohérent et casser votre projet."
```

**Introduction Cursor Rules (MDC) (30 min)**
```
"Les Cursor Rules = Instructions permanentes pour l'IA"

Démo création .cursorrules :

```
# Project: [Nom du projet]
# Stack: React, TypeScript, Supabase, Airtable

## Code Style
- Use TypeScript strict mode
- Functional components only
- Use Tailwind for styling
- Follow ESLint Airbnb config

## Naming Conventions
- Components: PascalCase (UserProfile.tsx)
- Utilities: camelCase (formatDate.ts)
- Constants: UPPER_SNAKE_CASE (API_URL)

## File Structure
- One component per file
- Components in src/components/
- Types in src/types/
- Utils in src/utils/

## Best Practices
- Always handle errors with try/catch
- Add TypeScript types to all functions
- Use async/await (not .then)
- Add comments for complex logic

## Database
- Supabase for READ operations only
- Airtable for WRITE operations (insert, update, delete)
```

"Ces règles vont GUIDER l'IA tout le temps.
L'IA va respecter votre style automatiquement."
```

**Production (15 min)**
```
Chaque équipe crée son .cursorrules de base
VOUS : Validez que c'est cohérent
```

#### **16h30-17h30 (1h) - SETUP GITHUB + PREMIER LIVRABLE**

**Setup GitHub (30 min)**
```
Chaque équipe :
├─ Crée un repo GitHub
├─ Configure .gitignore
├─ Premier commit (landing + cursorrules)
└─ README initial

"À partir de maintenant : COMMIT RÉGULIER.
Votre GitHub = votre journal de bord technique."
```

**Démos rapides (30 min)**
```
Chaque équipe montre (3 min) :
├─ Landing page Lovable (URL)
├─ Workspace Notion
├─ Repo GitHub
└─ Leur .cursorrules
```

**🎯 LIVRABLE JOUR 1 :**
```
✅ Landing page déployée (Lovable)
✅ Workspace Notion structuré
✅ Repo GitHub initialisé
✅ .cursorrules créé
✅ Organisation projet claire
```

---

### **JOUR 2 (26/11) - SETUP TECHNIQUE COMPLET** ⚙️

#### **9h30-10h00 (30 min) - RECAP + INTRO JOURNÉE**

**Daily standup (15 min)**
```
Chaque équipe (90 sec) :
"Hier on a fait X, aujourd'hui on fait Y, on a besoin d'aide sur Z"
```

**Intro du jour (15 min)**
```
"Aujourd'hui = Setup technique COMPLET.
Vous allez apprendre à configurer une stack pro :
React + Vite + Supabase + Airtable + MCP

C'est technique mais CRUCIAL.
Prenez le temps de bien comprendre."
```

#### **10h00-12h00 (2h) - SETUP REACT/VITE + SUPABASE**

**Démo live (30 min)**
```
VOUS créez le setup complet EN DIRECT :

1. Créer projet Vite + React + TypeScript
   npm create vite@latest mon-projet -- --template react-ts

2. Setup Supabase
   ├─ Créer compte/projet
   ├─ Créer table users
   ├─ Configuration Auth
   └─ Variables d'environnement

3. Intégration dans React
   ├─ Install @supabase/supabase-js
   ├─ Créer lib/supabase.ts
   └─ Test connexion

"Le but : Supabase pour la LECTURE uniquement.
Plus tard, Airtable pour l'ÉCRITURE."
```

**Production guidée (1h30)**
```
Chaque équipe setup son projet :
├─ Création projet Vite
├─ Configuration Supabase
├─ Première connexion testée
└─ Commit GitHub

VOUS : Tour de table rapide (9 min par équipe)
       Débloquer les problèmes
```

#### **13h30-15h30 (2h) - AIRTABLE + SYNC BIDIRECTIONNELLE**

**Enseignement CRUCIAL (45 min)**
```
"ARCHITECTURE IMPORTANTE :

Airtable = ÉCRITURE (Insert, Update, Delete)
Supabase = LECTURE (Read)

POURQUOI cette séparation ?
├─ Airtable : Interface no-code pour ops/admin
├─ Supabase : Performance pour lecture en masse
├─ Sync automatique : Le meilleur des 2 mondes

Comment ça marche :
1. User crée donnée → Airtable (interface facile)
2. Webhook Airtable → Déclenche fonction
3. Fonction → Copie dans Supabase
4. App lit depuis Supabase (rapide)

Avantages :
✅ Admin peut gérer depuis Airtable (no-code)
✅ Devs lisent depuis Supabase (SQL rapide)
✅ Séparation des responsabilités
✅ Backup automatique (2 BDD)
```

**Démo live sync (45 min)**
```
VOUS montrez EN DIRECT :

1. Créer base Airtable
2. Installer extension Supabase dans Airtable
3. Configurer la synchronisation
4. Test : Insert dans Airtable → Apparait dans Supabase
5. Test : Read depuis Supabase dans React

"Maintenant vous voyez : 
Airtable = Votre interface d'admin
Supabase = Votre API de lecture"
```

**Production (30 min)**
```
Chaque équipe :
├─ Crée sa base Airtable
├─ Configure la sync avec Supabase
├─ Teste l'insertion
└─ Vérifie dans Supabase
```

#### **15h30-17h00 (1h30) - MCP SUPABASE + AIRTABLE**

**Enseignement MCP (30 min)**
```
"MCP = Model Context Protocol
→ Donne à l'IA un accès DIRECT à vos outils

Sans MCP :
"Cursor, crée-moi une table dans Supabase"
→ Il génère du code que VOUS devez exécuter

Avec MCP :
"Cursor, crée-moi une table dans Supabase"
→ Il le fait DIRECTEMENT dans Supabase !

C'est RÉVOLUTIONNAIRE."

Types de MCP :
├─ MCP automatiques (toujours actifs)
│   └─ Lecture de données en continu
│
├─ MCP manuels (déclenchés par vous)
│   └─ Debug, modifications de schéma
│
└─ MCP contextuels (selon besoin)
    └─ Documentation, analyse
```

**Installation MCP (1h)**
```
Démo + Installation :

1. MCP Supabase
   ├─ Configuration dans Cursor
   ├─ Connexion à la BDD
   └─ Test : "Cursor, montre-moi mes tables"

2. MCP Airtable
   ├─ Configuration API key
   ├─ Connexion base
   └─ Test : "Cursor, liste mes records"

Production :
Chaque équipe installe et teste ses MCP
```

#### **17h00-17h30 (30 min) - PREMIER CHECKPOINT**

**Publication résumé Notion (MCP Notion) (15 min)**
```
"Maintenant, habitude CRUCIALE :
À la fin de chaque jour, publier résumé sur Notion"

Démo MCP Notion :
├─ Configuration MCP
├─ "Cursor, crée un résumé de ce qu'on a fait aujourd'hui"
└─ Il crée la page Notion automatiquement !

Chaque équipe publie son résumé Jour 2
```

**Commit GitHub (15 min)**
```
Chaque équipe commit son avancement
```

**🎯 LIVRABLE JOUR 2 :**
```
✅ Projet React/Vite configuré
✅ Supabase connecté
✅ Airtable connecté
✅ Sync bidirectionnelle fonctionnelle
✅ MCP Supabase + Airtable installés
✅ Résumé Notion publié
✅ Commits GitHub réguliers
```

---

### **JOUR 3 (03/12) - DÉVELOPPEMENT CORE + MI-PARCOURS** 🚀

#### **9h30-10h00 (30 min) - MODE PLAN DE CURSOR**

**NOUVEAUTÉ ! (30 min)**
```
"Mode Plan = LA nouveauté de Cursor

Avant de coder, l'IA PLANIFIE :
├─ Analyse votre demande
├─ Propose une architecture
├─ Décompose en étapes
└─ PUIS génère le code

Pourquoi c'est game-changer :
✅ Évite de casser le projet
✅ Architecture réfléchie
✅ Modifications coordonnées
✅ Moins d'erreurs

Démonstration live :
"Cursor, en mode Plan, crée-moi un système d'auth complet"

→ Il vous montre le PLAN avant d'exécuter
→ Vous validez
→ Il exécute de façon coordonnée
```

**Production (immédiate)**
```
"Aujourd'hui, utilisez le mode Plan
pour toutes vos grosses features."
```

#### **10h00-12h30 (2h30) - DÉVELOPPEMENT FEATURES PRINCIPALES**

**Mode Agent + Mode Editor (15 min)**
```
Rappel des modes :

Editor : Modifications précises
└─ "Change cette fonction pour X"

Agent : Tâches autonomes
└─ "Crée toute l'architecture auth de A à Z"

Plan : Planification avant action
└─ "Montre-moi le plan avant de créer X"

"Utilisez le BON mode selon la tâche."
```

**Production intensive (2h15)**
```
Chaque équipe code ses features principales :
├─ Système d'auth (login/signup)
├─ Gestion des droits utilisateurs
├─ CRUD principal
├─ Dashboard utilisateur
└─ Intégration Airtable/Supabase

VOUS : Circulez, debuggez, guidez

Rappel constant :
"Utilisez le mode Plan pour les grosses features !"
"Committez régulièrement !"
"Mettez à jour vos .cursorrules si besoin !"
```

#### **13h30-15h00 (1h30) - DEBUG & CONSOLE.LOG**

**Enseignement debug (30 min)**
```
"Le debug = 50% du temps d'un dev.
Avec l'IA, on peut debug PLUS VITE."

Techniques :
├─ Console.log stratégiques
├─ Debugger Chrome
├─ Error handling propre
└─ Cursor pour debug

Créer un MCP DEBUG manuel :

```
# MCP Debug
Trigger: @debug

Actions:
1. Analyse le code sélectionné
2. Identifie les bugs potentiels
3. Propose des solutions
4. Ajoute des console.log stratégiques
5. Teste les edge cases

Style:
- Explique POURQUOI le bug
- Propose 2-3 solutions
- Code propre et lisible
```

"Ce MCP, vous le déclenchez MANUELLEMENT
quand vous avez un bug. Il ne tourne pas tout le temps."
```

**Session debug guidée (1h)**
```
Chaque équipe :
├─ Identifie ses bugs actuels
├─ Utilise le MCP debug
├─ Résout avec l'IA
└─ Documente la solution

VOUS : Aide au debug des cas complexes
```

#### **15h00-16h00 (1h) - CURSOR RULES AVANCÉES**

**Enseignement (30 min)**
```
"Vos .cursorrules doivent ÉVOLUER avec votre projet.

Au début : Règles générales
Maintenant : Règles spécifiques à votre projet

Ajoutez :
├─ Architecture de votre app
├─ Logique métier spécifique
├─ Règles de sécurité
└─ Patterns à respecter

Exemple règles avancées :

```
## Auth Rules
- Never store passwords in plain text
- Always use Supabase Auth
- Check user permissions before actions
- Redirect unauthorized users to /login

## Database Rules
- READ from Supabase only
- WRITE to Airtable only
- Always check if record exists before update
- Handle API errors gracefully

## Component Rules
- Use React.memo for heavy components
- Lazy load routes
- Keep components under 200 lines
- Extract logic to custom hooks

## Debug Rules
- Remove console.log before commit
- Use proper error boundaries
- Log errors to monitoring service
```

"Plus vos rules sont précises,
moins l'IA fera d'erreurs."
```

**Production (30 min)**
```
Chaque équipe met à jour ses .cursorrules
└─ Ajout règles spécifiques à leur projet
└─ Validation par vous
```

#### **16h00-17h30 (1h30) - ÉVALUATION MI-PARCOURS**

**Format (10 min par équipe)**
```
Chaque équipe présente :
├─ Démo de l'avancement (5 min)
├─ Explication architecture (2 min)
├─ Difficultés rencontrées (1 min)
└─ Plan jours 4-6 (2 min)

VOUS notez :
├─ Avancement (/10)
├─ Qualité technique (/5)
├─ Organisation (/5)
```

**Feedback détaillé**
```
Après les présentations :
└─ Feedback individuel par équipe
└─ Points à améliorer
└─ Encouragements

"Vous êtes à mi-parcours. 
Il reste 3 jours pour finaliser.
Vous pouvez le faire !"
```

**Peer Assessment 1**
```
Chaque étudiant remplit (anonyme) :
└─ Note ses 3 coéquipiers
└─ Justification courte
```

**🎯 LIVRABLE JOUR 3 :**
```
✅ Features principales codées
✅ Système d'auth fonctionnel
✅ Dashboard utilisateur
✅ .cursorrules mis à jour
✅ MCP debug créé
✅ Résumé Notion publié
✅ Note mi-parcours reçue
✅ Peer assessment 1 complété
```

---

### **JOUR 4 (10/12) - WORKFLOWS & MONITORING** 📊

#### **9h30-10h00 (30 min) - RETOURS MI-PARCOURS**

**Débriefing collectif (30 min)**
```
"Points communs à toutes les équipes :
├─ Ce qui marche bien
├─ Les difficultés communes
└─ Les bonnes pratiques à partager

Aujourd'hui : WORKFLOWS & MONITORING
→ Automatisation
→ Suivi des données
→ Optimisation
```

#### **10h00-12h00 (2h) - WORKFLOWS AIRTABLE**

**Enseignement (30 min)**
```
"Workflows = Automatisations business

Exemples :
├─ User s'inscrit → Email de bienvenue
├─ Commande créée → Notification admin
├─ Paiement reçu → Mise à jour statut
└─ Deadline proche → Rappel automatique

Airtable Automations :
├─ Déclencheur (trigger)
├─ Conditions
├─ Actions
└─ Tests
```

**Démo live (30 min)**
```
VOUS créez workflows EN DIRECT :

1. Workflow inscription :
   Trigger : Nouveau record dans table Users
   Action : Envoyer email bienvenue

2. Workflow notification :
   Trigger : Statut change
   Condition : Si statut = "Terminé"
   Action : Webhook vers API

3. Workflow rappel :
   Trigger : Tous les jours 9h
   Condition : Si deadline dans 2 jours
   Action : Créer tâche de rappel
```

**Production (1h)**
```
Chaque équipe crée 3-5 workflows pertinents :
└─ Adaptés à leur projet spécifique
└─ Testés et fonctionnels
```

#### **13h30-15h00 (1h30) - MINI DASHBOARD MONITORING**

**Enseignement (30 min)**
```
"Monitoring = Suivre ce qui se passe dans votre app

Pourquoi c'est crucial :
├─ Voir les bugs en temps réel
├─ Suivre l'usage
├─ Détecter les problèmes
└─ Optimiser les performances

Ce qu'on va créer :
├─ Dashboard dans votre app
├─ Affiche KPIs en temps réel
├─ Données depuis Supabase/Airtable
└─ Design simple mais efficace
```

**Production (1h)**
```
Chaque équipe crée son dashboard :
├─ Page /admin/dashboard
├─ KPIs pertinents (users, actions, etc.)
├─ Graphiques simples (si temps)
└─ Refresh automatique

Utiliser Mode Agent :
"Crée-moi un dashboard admin avec 
les statistiques suivantes : [...]"
```

#### **15h00-17h00 (2h) - GESTION PROJET NOTION AVANCÉE**

**MCP Notion avancé (30 min)**
```
"MCP Notion = Automatisation de votre doc

Usages :
├─ Créer pages automatiquement
├─ Mettre à jour roadmap
├─ Générer rapports
└─ Synchroniser avec code

Configuration MCP avancé :

Types de pages à créer auto :
├─ Résumé quotidien (fin de journée)
├─ Documentation features (quand codées)
├─ Bugs tracker (quand bug détecté)
└─ Changelog (à chaque version)
```

**Production (1h30)**
```
Chaque équipe améliore son Notion :
├─ Structure avancée
├─ Documentation technique complète
├─ Roadmap mise à jour
├─ Changelog généré
└─ Wiki interne

Utiliser MCP Notion pour automatiser
```

#### **17h00-17h30 (30 min) - RÉSUMÉ NOTION + COMMITS**

**Publication automatisée (30 min)**
```
"Cursor, via MCP Notion, crée le résumé du jour 4
avec les éléments suivants :
- Workflows créés
- Dashboard implémenté
- Améliorations Notion
- Difficultés rencontrées
- Plan jour 5"

Commits GitHub + Push
```

**🎯 LIVRABLE JOUR 4 :**
```
✅ 3-5 workflows Airtable fonctionnels
✅ Mini dashboard monitoring
✅ Notion structuré et documenté
✅ MCP Notion configuré
✅ Résumé automatique publié
✅ Commits réguliers
```

---

### **JOUR 5 (17/12) - FINALISATION & POLISH** ✨

#### **9h30-10h00 (30 min) - DERNIÈRE LIGNE DROITE**

**Motivation (30 min)**
```
"Demain = Demo Day.
Aujourd'hui = Finalisation.

Checklist :
├─ Code fonctionne parfaitement
├─ Design est propre
├─ Documentation est complète
├─ GitHub est à jour
└─ Notion est finalisé

Vous avez 7h pour rendre votre projet IMPECCABLE."
```

#### **10h00-12h30 (2h30) - PRODUCTION INTENSIVE**

**Finalisation libre (2h30)**
```
Chaque équipe travaille sur :
├─ Bug fixing (prioritaire)
├─ Design/UX
├─ Performance
├─ Gestion d'erreurs
├─ Loading states
└─ Messages utilisateurs

VOUS : Disponible pour debug et conseils

Rappels :
"Mettez à jour vos .cursorrules en continu"
"Committez toutes les heures"
"Testez sur mobile aussi"
```

#### **13h30-15h30 (2h) - DOCUMENTATION FINALE**

**GitHub README (1h)**
```
Chaque équipe finalise son README :

## [Nom du projet]

### Concept
[Description 2-3 lignes]

### Stack technique
- React + Vite + TypeScript
- Supabase (lecture)
- Airtable (écriture)
- Cursor + MCP

### Architecture
[Schéma ou explication]

### Installation
```bash
npm install
npm run dev
```

### Fonctionnalités
- [Feature 1]
- [Feature 2]
- etc.

### Équipe
- [Membre 1] - [Rôle]
- [Membre 2] - [Rôle]
- etc.

### Demo
[URL de la démo live]
```

**Notion documentation (1h)**
```
Finaliser la documentation Notion :
├─ Guide d'utilisation
├─ Documentation technique
├─ Architecture décisions
├─ Changelog complet
└─ Lessons learned
```

#### **15h30-17h00 (1h30) - PRÉPARATION PITCH**

**Template pitch (30 min)**
```
Structure obligatoire (5 min total) :

1. Problème (30 sec)
   "Aujourd'hui, les [users] ont du mal à [problème]"

2. Solution (1 min)
   "Notre produit [nom] permet de [solution]
   grâce à [technologie/approche]"

3. Démo live (2 min)
   Montrer le produit en action
   Scénario utilisateur complet

4. Architecture technique (1 min)
   Stack, choix techniques, points forts

5. Perspectives (30 sec)
   "Dans le futur, on pourrait [vision]"

Conseils :
✅ Répétez plusieurs fois
✅ Testez la démo (pas de bugs en live !)
✅ Préparez plan B si problème technique
✅ Tous les membres parlent
```

**Répétitions (1h)**
```
Chaque équipe répète son pitch
VOUS : Donnez du feedback immédiat
└─ "Trop long ici"
└─ "Insistez plus sur X"
└─ "La démo doit être plus rapide"
```

#### **17h00-17h30 (30 min) - DERNIERS COMMITS**

**Vérifications finales (30 min)**
```
Checklist finale :
├─ ✅ Code commit et push
├─ ✅ README complet
├─ ✅ Notion finalisé
├─ ✅ App déployée et accessible
├─ ✅ Pitch répété
└─ ✅ Peer assessment 2 rempli

"Demain, on présente. Reposez-vous bien !"
```

**Peer Assessment 2 (final)**
```
Chaque étudiant note ses coéquipiers
└─ Formulaire final plus détaillé
```

**🎯 LIVRABLE JOUR 5 :**
```
✅ Produit finalisé et fonctionnel
✅ Documentation complète (GitHub + Notion)
✅ Pitch préparé et répété
✅ App déployée
✅ Peer assessment 2 complété
✅ Prêt pour Demo Day
```

---

### **JOUR 6 (28/01) - DEMO DAY** 🎤🔥

#### **9h30-10h00 (30 min) - DERNIERS RÉGLAGES**

```
Temps libre pour :
├─ Tests finaux
├─ Corrections de dernière minute
├─ Répétition pitch
└─ Setup technique pour démo
```

#### **10h00-13h00 (3h) - DEMO DAY - PARTIE 1**

**Format (15 min par équipe)**
```
5 premières équipes présentent :

├─ Pitch + Démo (5 min)
├─ Questions (3 min)
│   └─ Vous + autres étudiants
├─ Feedback (3 min)
│   └─ Vous donnez feedback public
└─ Setup équipe suivante (4 min)

Ambiance :
├─ Chaque équipe a un "stand"
├─ Laptop + écran si possible
├─ URL app accessible à tous
└─ Atmosphere startup / pitch contest
```

#### **13h00-14h00 - PAUSE DÉJEUNER** 🍔

#### **14h00-16h30 (2h30) - DEMO DAY - PARTIE 2**

**5 dernières équipes (15 min chacune)**
```
Même format que le matin
```

#### **16h30-17h30 (1h) - AWARDS & CLOSING**

**Délibération (15 min)**
```
Vous vous isolez et calculez :
├─ Notes Vibe Coding
├─ Notes Base de données
├─ Ajustements peer assessment
└─ Prix spéciaux
```

**Awards Cérémonie (30 min)**
```
Prix officiels :
🏆 Best Technical Achievement
🎨 Best Design/UX
💡 Most Innovative
🚀 Best Business Potential
❤️ Coup de cœur du prof

+ Mention des notes finales
(sans dévoiler les notes individuelles)
```

**Message final (15 min)**
```
Votre discours de clôture :

"Il y a 6 jours, vous découvriez Cursor.
Aujourd'hui, vous avez créé 10 produits 
qui pourraient être lancés demain.

Ce que vous avez appris :
├─ Vibe coding avec IA
├─ Architecture de données
├─ Travail en équipe
├─ Gestion de projet
└─ Capacité de création

Maintenant ? 
Vous êtes des PRODUCT BUILDERS.

À VOUS DE JOUER. 🚀"

Photo de groupe !
```

**🎯 LIVRABLE FINAL (JOUR 6) :**
```
✅ Pitch professionnel effectué
✅ Démo live réussie
✅ Feedback reçu
✅ Notes finales calculées
✅ Portfolio complet (GitHub + Notion)
✅ 10 produits créés et déployés
```

---

## 📊 GRILLE DE NOTATION DÉTAILLÉE

### **NOTATION VIBE CODING (/20)**

#### **Maîtrise Cursor (/5)**
```
/1 - Modes (Editor, Agent, Browser, Plan)
     └─ Utilisation variée et pertinente

/1 - Cursor Rules (.cursorrules)
     └─ Qualité et évolution des rules

/1 - MCP (Supabase, Airtable, Notion)
     └─ Installation et utilisation

/1 - Mode Plan
     └─ Utilisation pour architecture

/1 - MCP custom (debug, etc.)
     └─ Création et utilisation
```

#### **Qualité du code (/4)**
```
/1 - Organisation fichiers/dossiers
     └─ Structure claire et logique

/1 - Nommage (variables, fonctions, fichiers)
     └─ Cohérent et explicite

/1 - Gestion d'erreurs
     └─ Try/catch, error boundaries

/1 - Propreté (pas de console.log, code commenté)
     └─ Code production-ready
```

#### **Résolution de bugs (/2)**
```
/1 - Utilisation MCP debug
     └─ Efficacité du debugging

/1 - Correction effective
     └─ Bugs résolus
```

#### **Créativité (/3)**
```
/1 - Originalité du concept
/1 - Innovation technique
/1 - UX/UI design
```

#### **GitHub (/2)**
```
/1 - Commits réguliers (min 1/jour)
/1 - README complet et clair
```

#### **Livrables (/4)**
```
/0.5 - Livrable jour 1
/0.5 - Livrable jour 2
/0.5 - Livrable jour 3
/0.5 - Livrable jour 4
/0.5 - Livrable jour 5
/1.5 - Livrable final (jour 6)
```

---

### **NOTATION BASE DE DONNÉES & PRODUCTIVITÉ (/20)**

#### **Architecture BDD (/5)**
```
/2 - Supabase (tables, relations, RLS)
     └─ Structure cohérente

/2 - Airtable (organisation, champs)
     └─ Adapté aux besoins métier

/1 - Séparation lecture/écriture
     └─ Respect de l'architecture
```

#### **Sync bidirectionnelle (/5)**
```
/2 - Configuration sync Airtable → Supabase
     └─ Fonctionnelle

/2 - Test et validation
     └─ Données cohérentes

/1 - Gestion des erreurs
     └─ Robustesse
```

#### **Workflows Airtable (/3)**
```
/1 - Nombre de workflows (min 3)
/1 - Pertinence business
/1 - Fonctionnement
```

#### **Gestion projet Notion (/3)**
```
/1 - Structure et organisation
/1 - Documentation technique
/1 - Mise à jour régulière
```

#### **Dashboard monitoring (/2)**
```
/1 - Présence et design
/1 - KPIs pertinents
```

#### **Documentation (/2)**
```
/1 - Qualité documentation GitHub
/1 - Qualité documentation Notion
```

---

### **PEER ASSESSMENT - FORMULAIRE**

```
=== FORMULAIRE PEER ASSESSMENT ===

Votre nom : [_______________]
Équipe : [_______________]

Notez vos 3 coéquipiers (vous ne pouvez pas vous noter)

Pour chaque critère, donnez un nombre de points :
- Contribution technique : /30
- Implication : /25
- Collaboration : /25
- Autonomie : /20

MEMBRE 1 : [Nom]
├─ Contribution technique : [___/30]
├─ Implication : [___/25]
├─ Collaboration : [___/25]
├─ Autonomie : [___/20]
└─ TOTAL : [___/100]

Justification (obligatoire si <80 ou >110) :
[________________________]

MEMBRE 2 : [Nom]
[même format]

MEMBRE 3 : [Nom]
[même format]

Note : Les notes extrêmes (<80 ou >110) doivent être justifiées.
```

---

## 📋 CHECKLIST ORGANISATION PROFESSEUR

### **Avant le cours**
```
Semaine avant :
├─ ✅ Envoyer email préparation aux étudiants
│   └─ Comptes à créer (Cursor, Supabase, Airtable, Notion, Lovable)
│   └─ Installations (Node.js, Git)
│   └─ Brief du cours
├─ ✅ Préparer vos démos (test tout avant)
├─ ✅ Créer formulaires peer assessment (Google Forms)
├─ ✅ Préparer grilles de notation (Excel/Sheets)
└─ ✅ Setup vidéoprojecteur et matériel

Jour J :
├─ ✅ Arriver 30 min avant
├─ ✅ Tester WiFi et projecteur
└─ ✅ Avoir vos démos prêtes
```

### **Pendant le cours**
```
Chaque jour :
├─ ✅ Daily standup (noter les blocages)
├─ ✅ Circuler entre les équipes
├─ ✅ Noter avancement (suivi individuel)
├─ ✅ Prendre photos du travail (portfolio)
└─ ✅ Vérifier commits GitHub

Fin de journée :
├─ ✅ Vérifier livrables
├─ ✅ Noter points d'attention
└─ ✅ Préparer le lendemain
```

### **Après le cours**
```
Jour 3 :
├─ ✅ Calculer notes mi-parcours
├─ ✅ Analyser peer assessment 1
└─ ✅ Préparer feedback individuels

Jour 6 :
├─ ✅ Calculer notes finales
│   └─ Note équipe + coefficient peer
├─ ✅ Préparer certificats (si applicable)
└─ ✅ Envoyer feedback final par email
```

---

## 🎯 LIVRABLES RÉCAPITULATIFS

**Par équipe, à la fin du cours :**
```
1. Produit déployé (URL)
2. Repository GitHub complet
3. Workspace Notion documenté
4. Pitch deck (optionnel)
5. Vidéo démo 3 min (optionnel)
```

**Par vous (professeur) :**
```
1. Notes individuelles (2 notes/étudiant)
2. Feedback écrit par équipe
3. Photos/vidéos du cours
4. Retour d'expérience (pour amélioration)
```

---

**Date de création** : 29/10/2025  
**Version** : 1.0 - Programme 6 jours intensif  
**Auteur** : Thomas

