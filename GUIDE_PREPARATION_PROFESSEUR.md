# 🎯 GUIDE DE PRÉPARATION CRITIQUE - PROFESSEUR

> **Formation 6 jours : Growth Hacking + Vibe Coding avec IA**

---

## ⏰ TIMELINE DE PRÉPARATION

### **2 SEMAINES AVANT (5-12 novembre)**

#### **🔴 CRITIQUE : Tester VOUS-MÊME tout le parcours**

**Jour 1 : Landing Page Lovable (1h)**
```
✅ Créer un compte Lovable
✅ Créer une landing page complète (test)
✅ Exporter le code
✅ Déployer la landing
✅ Tester sur mobile et desktop
✅ Chronométrer : combien de temps réel ?
```

**Jour 2 : Setup Cursor + MCP (2-3h)**
```
✅ Installer Cursor
✅ Configurer MCP Supabase
   └─ Créer projet test Supabase
   └─ Récupérer API keys
   └─ Tester connexion
✅ Configurer MCP Airtable
   └─ Créer base test Airtable
   └─ Récupérer API key
   └─ Tester connexion
✅ Configurer MCP Notion
   └─ Créer page test Notion
   └─ Créer intégration Notion
   └─ Récupérer token
   └─ Tester connexion
✅ Tester les 4 modes Cursor :
   └─ Editor : modification simple
   └─ Agent : tâche multi-fichiers
   └─ Plan : planification feature
   └─ Browser : recherche web

⚠️ NOTER LES PROBLÈMES RENCONTRÉS
   (ce qui bloque = ce qui bloquera les étudiants)
```

**Jour 3 : Sync Airtable/Supabase (3-4h) ⚠️ CRITIQUE**
```
✅ Créer base Airtable test (2-3 tables, relations)
✅ Créer projet Supabase
✅ Reproduire schéma dans Supabase
✅ Installer extension Supabase dans Airtable
✅ Configurer synchronisation
✅ TESTER 5× MINIMUM :
   Test 1 : Insert simple
   Test 2 : Insert avec relations
   Test 3 : Update
   Test 4 : Delete
   Test 5 : Sync bidirectionnelle

⚠️ DOCUMENTER CHAQUE ÉTAPE
   └─ Captures d'écran
   └─ Problèmes rencontrés
   └─ Solutions trouvées

🔴 CRÉER SCRIPT DE FALLBACK
   Si la sync officielle ne marche pas :
   └─ Webhook Airtable → Fonction serverless
   └─ Fonction appelle API Supabase
   └─ Tester ce backup aussi
```

**Auth Supabase (1-2h)**
```
✅ Configurer Supabase Auth
✅ Créer pages Login/Signup
✅ Protected routes
✅ Gestion des rôles
✅ Tester le flow complet
```

**Workflows Airtable (1h)**
```
✅ Créer 3 workflows test
✅ Tester déclencheurs
✅ Tester actions
```

---

### **1 SEMAINE AVANT (13-18 novembre)**

#### **📹 Créer guides vidéo courts (FLIPPED CLASSROOM)**

**Vidéos à préparer (15 min chacune max) :**

```
1. "Installation Cursor + MCP" (15 min)
   └─ Screencast pas à pas
   └─ Montrer où trouver les API keys
   └─ Montrer la configuration
   
2. "Sync Airtable/Supabase" (15 min)
   └─ Chaque étape en détail
   └─ Les pièges courants
   └─ Comment vérifier que ça marche

3. "Supabase Auth basics" (10 min)
   └─ Configuration
   └─ Login/Signup
   └─ Protected routes

4. "Workflows Airtable" (10 min)
   └─ Créer un workflow
   └─ Triggers et actions
   └─ Tests

⚠️ Upload sur YouTube (unlisted)
   └─ Donnez les liens aux étudiants
   └─ Ils regardent AVANT le cours
```

#### **📋 Préparer templates par type de projet**

**Schémas BDD pré-conçus**
```
Template 1 : Marketplace
├─ Users (buyers + sellers)
├─ Products
├─ Orders
└─ Reviews

Template 2 : Event Platform
├─ Users (organizers + participants)
├─ Events
├─ Tickets
└─ Venues

Template 3 : SaaS Tool
├─ Users
├─ Organizations
├─ Projects
└─ Tasks

Template 4 : Content Platform
├─ Users (creators + consumers)
├─ Content
├─ Categories
└─ Comments

→ Avoir ces templates PRÊTS
   Si une équipe galère sur son schéma,
   vous pouvez leur proposer un template
```

#### **📧 Email aux étudiants (à envoyer 1 semaine avant)**

```
Objet : Préparation Formation Growth Hacking + IA (IMPORTANT)

Bonjour à tous,

La formation commence le [DATE]. Pour maximiser notre temps en classe,
voici ce que vous devez faire AVANT :

🔧 CRÉER LES COMPTES (30 min) :
- Cursor (https://cursor.sh)
- Lovable (https://lovable.dev)
- Supabase (https://supabase.com)
- Airtable (https://airtable.com)
- Notion (https://notion.so)
- GitHub (https://github.com)

📹 REGARDER LES VIDÉOS (1h) :
[Lien playlist YouTube]

💻 INSTALLER (15 min) :
- Cursor IDE
- Node.js (version LTS)
- Git

⚠️ IMPORTANT : Si vous avez des problèmes d'installation,
contactez-moi AVANT le premier jour.

À très vite,
Thomas
```

---

### **48H AVANT (17-18 novembre)**

#### **✅ Checklist finale**

**Matériel**
```
✅ Laptop + chargeur
✅ HDMI/adaptateur pour projection
✅ Backup : clé USB avec tous les guides
✅ Backup : hotspot 4G (si WiFi plante)
```

**Comptes test**
```
✅ 2-3 comptes test pour chaque outil
   (pour montrer features pendant cours)
✅ Vérifier que tous fonctionnent
```

**Documents**
```
✅ Imprimer grille d'évaluation
✅ Imprimer formulaires peer assessment
✅ Avoir README avec tous les liens
```

**Préparation des 10 équipes**
```
✅ Liste des 40 étudiants
✅ Répartition en 10 équipes (4 personnes)
   └─ Mixer les niveaux si vous les connaissez
✅ Numéroter les équipes (1-10)
```

**Storytelling**
```
✅ Préparer slides Jour 1 :
   └─ Photos adopteunecougar
   └─ Chiffres clés
   └─ Votre parcours
✅ Préparer slides Jour 2 :
   └─ Histoire École 42
   └─ Le "hack"
   └─ La leçon
```

---

### **JOUR J - Arriver 30 min avant**

**Setup salle (15 min)**
```
✅ Tester projection
✅ Tester WiFi
✅ Tester son (si vidéos)
✅ Vérifier tables pour 10 équipes
```

**Vérifier sur votre machine (15 min)**
```
✅ Cursor fonctionne
✅ Tous les MCP connectés
✅ Lovable accessible
✅ Tous les liens marchent
```

---

## 🚨 FALLBACKS CRITIQUES

### **Si la sync Airtable/Supabase ne marche pas**

**Option 1 : Extension officielle**
```
→ Troubleshooting systématique
→ Refaire mapping
→ Tester avec 1 table simple d'abord
```

**Option 2 : Webhook + Fonction (backup)**
```
1. Créer webhook dans Airtable
2. Créer fonction Supabase Edge Function
3. Webhook appelle la fonction
4. Fonction insère dans Supabase

Code fonction à avoir PRÊT :
[Voir annexe Code Fallback]
```

**Option 3 : Sync manuelle temporaire**
```
"Pour aujourd'hui, on met les données
manuellement dans Supabase.
Demain on automatise."

→ Permet de continuer sans bloquer
```

---

### **Si Lovable est down (Jour 1)**

**Alternative : Bolt.new**
```
✅ Fonctionne pareil
✅ Landing page rapide
✅ Export code
```

**Alternative 2 : V0.dev (Vercel)**
```
✅ Génération composants React
✅ Copy-paste dans projet
✅ Deploy Vercel
```

---

### **Si un étudiant n'a pas de compte / installation**

**Solution rapide (15 min)**
```
Pendant que vous faites l'intro :
└─ Demandez à un autre étudiant de l'aider
└─ Ou : donnez-lui un compte test temporaire
```

---

## 📊 ESTIMATION RÉALISTE DES PROBABILITÉS

### **Jour 1 : Landing Page** 
✅ **Probabilité succès : 95%**
- C'est simple
- Lovable marche bien
- Peu de bugs possibles

### **Jour 2 : Setup Cursor + MCP**
⚠️ **Probabilité succès : 75%**
- MCP peut être capricieux
- API keys peuvent poser problème
- Mais récupérable rapidement

### **Jour 3 : Sync + Auth**
🔴 **Probabilité succès : 65% → 85% (avec ajustements)**
- Sync = point le plus risqué
- Auth = complexe mais faisable
- AVEC plus de temps + fallback = 85%

### **Jour 4-5 : Features + Polish**
✅ **Probabilité succès : 90%**
- Les fondations sont posées
- Chaque équipe à son rythme
- Récupérable même si retard

### **Jour 6 : Demo Day**
✅ **Probabilité succès : 100%**
- Quoi qu'il arrive, ils démontrent
- Même si bugs, ils pitchent
- C'est le moment de gloire

---

## ✅ RÉSUMÉ : LES 5 ACTIONS CRITIQUES

```
1. TESTER la sync Airtable/Supabase 5× minimum
   └─ C'est LE point le plus risqué

2. CRÉER les guides vidéo
   └─ Gagne 2h par jour en classe

3. PRÉPARER les fallbacks
   └─ Sync alternative prête à l'emploi

4. ENVOYER l'email de préparation 1 semaine avant
   └─ Les comptes créés = gain de temps énorme

5. TESTER votre propre setup 48h avant
   └─ Pas de surprise le jour J
```

---

## 🎯 VOTRE RÔLE PENDANT LE COURS

### **Vous n'êtes PAS un prof classique, vous êtes :**

**1. Storyteller (10%)**
```
Captiver avec vos histoires
Inspirer les étudiants
Montrer que c'est possible
```

**2. Facilitator (60%)**
```
Débloquer les problèmes
Guider sans faire à leur place
Challenger leurs choix
Valider les directions
```

**3. Coach (30%)**
```
Motiver
Donner feedback
Pousser à se dépasser
Célébrer les victoires
```

### **Vous ne codez PAS pour eux**
```
❌ "Regarde, je vais le faire"
✅ "Qu'est-ce que tu as essayé ?"
✅ "Quel message d'erreur tu as ?"
✅ "Demande à Cursor de t'aider"
```

---

## 📞 CONTACTS UTILES

**Support technique si besoin :**
```
Cursor : support@cursor.sh
Lovable : [à trouver]
Supabase : support@supabase.io
Airtable : support@airtable.com
```

---

## 🎯 MINDSET

**Rappelez-vous :**

```
Le but N'EST PAS que tout soit parfait.
Le but EST qu'ils apprennent à construire avec l'IA.

Si 80% des équipes ont tout qui marche = SUCCÈS.
Si 100% des équipes ont appris = SUCCÈS TOTAL.

Quelques bugs = Normal.
Apprentissage = Objectif.

🚀 ILS VONT CRÉER 10 PRODUITS EN 6 JOURS.
   C'EST DÉJÀ INCROYABLE.
```

---

**Date de création** : 2 novembre 2025  
**Version** : 1.0  
**Auteur** : Assistant (pour Thomas)

