# 🚀 Configuration GitBook - Guide Pas à Pas

## ✅ ÉTAPE 1 : PUSH GITHUB - TERMINÉ ! 

Votre projet a été poussé avec succès sur GitHub :
- 📦 **108 fichiers** commitées
- 📊 **23,509 lignes** de documentation
- 🔗 **URL** : https://github.com/mrsoyer/build-in-6-days

```
✅ Repository initialisé
✅ Tous les fichiers ajoutés  
✅ Commit créé (d7bc60f)
✅ Branche main configurée
✅ Remote origin ajouté
✅ Push réussi
```

---

## 📋 ÉTAPE 2 : CRÉER UN COMPTE GITBOOK (2 min)

### 1. Aller sur GitBook
```
🌐 https://www.gitbook.com
```

### 2. S'inscrire
- Cliquez sur **"Sign up"**
- Options disponibles :
  - ✅ **Avec GitHub** (RECOMMANDÉ - connexion instantanée)
  - Email + mot de passe
  - Google

### 3. Plan gratuit
- Le plan **gratuit** suffit pour commencer
- Fonctionnalités incluses :
  - ✅ 1 espace public
  - ✅ Synchronisation GitHub
  - ✅ Recherche intégrée
  - ✅ Custom domain (optionnel)

---

## 📚 ÉTAPE 3 : CRÉER UN NOUVEL ESPACE (3 min)

### 1. Tableau de bord
Une fois connecté, vous verrez votre tableau de bord GitBook.

### 2. Créer un espace
- Cliquez sur **"+ New space"** (bouton en haut)
- Choisissez un nom :
  ```
  Build in 6 Days
  ```
  ou
  ```
  Bootcamp IA - M1 Eugenia School
  ```

### 3. Choisir le type
- Sélectionnez **"Import from Git"**
- ⚠️ Ne choisissez PAS "Start from scratch"

---

## 🔗 ÉTAPE 4 : CONNECTER GITHUB (5 min)

### 1. Autoriser GitBook
- GitBook va demander la permission d'accéder à votre GitHub
- Cliquez sur **"Install GitHub App"**
- Vous serez redirigé vers GitHub

### 2. Sur GitHub - Autoriser
Deux options :
- **Option A** : Donner accès à **tous** vos repos (plus simple)
- **Option B** : Donner accès **uniquement** à `build-in-6-days` (plus sécurisé)

**Je recommande l'Option B** :
```
☑️ Only select repositories
  └─ mrsoyer/build-in-6-days
```

### 3. Installer et autoriser
- Cliquez sur **"Install"**
- Confirmez votre mot de passe GitHub si demandé
- Vous serez redirigé vers GitBook

---

## ⚙️ ÉTAPE 5 : CONFIGURER LA SYNCHRONISATION (2 min)

### 1. Sélectionner le repository
De retour sur GitBook :
- Vous verrez une liste de vos repos
- Sélectionnez **`mrsoyer/build-in-6-days`**

### 2. Choisir la branche
```
Branch: main
```

### 3. Configuration de sync (Important !)
GitBook va détecter automatiquement votre configuration :
- ✅ `.gitbook.yaml` trouvé
- ✅ `SUMMARY.md` trouvé  
- ✅ `README.md` trouvé

**Mode de synchronisation recommandé** :
```
GitHub → GitBook (one-way)
```
ou
```
Bidirectionnel (two-way)
```

### 4. Confirmer l'import
- Cliquez sur **"Import"**
- ⏳ L'importation prend 30 secondes à 2 minutes

---

## 🎨 ÉTAPE 6 : VÉRIFIER L'IMPORTATION (3 min)

### 1. Navigation (Sidebar)
Vérifiez que vous voyez dans la sidebar gauche :
```
📖 Table des Matières
├── 🏠 Introduction
├── 📚 Syllabus Officiels
│   ├── Vibe Coding
│   ├── Productivity
│   └── Global
├── 📅 Programme Détaillé
├── 👨‍🏫 Guides Professeur
│   ├── Analyse Faisabilité
│   ├── Guide Préparation
│   └── Pense-Bête Jour 1
├── 📊 Outils d'Évaluation
│   ├── Grille Notation
│   └── Formulaire Peer Assessment
├── 📖 Documentation Technique (33 fichiers)
│   ├── Structure
│   ├── Exigences
│   ├── Sources (11 docs)
│   ├── Cours (9 cours)
│   └── Templates (6 templates)
└── ... (50+ pages au total)
```

### 2. Page d'accueil
- Cliquez sur **"Introduction"**
- Vous devriez voir votre `README.md` avec :
  - ✅ Badges (40 étudiants, 42h, M1)
  - ✅ Description du projet
  - ✅ Stack technique
  - ✅ Liens vers les sections

### 3. Test de navigation
Testez quelques pages :
- Programme 6 jours
- Un cours (ex: COURS-NOTION.md)
- Un template
- La documentation technique complète

---

## 🎨 ÉTAPE 7 : PERSONNALISATION (5 min) - OPTIONNEL

### 1. Settings → Theme
```
⚙️ Settings (en haut à droite)
└─ Theme
   ├── Primary color : #8B5CF6 (violet - thème Eugenia)
   ├── Logo : Ajoutez le logo Eugenia School
   └── Favicon : Ajoutez l'icône
```

### 2. Settings → General
```
└─ Space details
   ├── Name : Build in 6 Days
   ├── Description : Bootcamp IA - De l'idée au produit en 6 jours
   └── Visibility : Public
```

### 3. Settings → Advanced
```
└─ Search : Activé (par défaut)
└─ Table of Contents : Activé (par défaut)
```

---

## 🚀 ÉTAPE 8 : PUBLICATION (1 min)

### 1. Bouton Publish
- En haut à droite de GitBook, cliquez sur **"Publish"**
- Confirmez la publication

### 2. Obtenir l'URL
Votre documentation sera accessible à :
```
https://[votre-space].gitbook.io/build-in-6-days

Exemple :
https://thomassoyer.gitbook.io/build-in-6-days
ou
https://mrsoyer.gitbook.io/build-in-6-days
```

### 3. Partager
- Copiez l'URL
- Partagez-la avec vos étudiants
- Ajoutez-la dans votre syllabus

---

## 🔄 ÉTAPE 9 : SYNCHRONISATION AUTOMATIQUE

### Comment ça marche ?

#### De GitHub → GitBook
Chaque fois que vous faites un `git push` sur la branche `main` :
1. GitBook reçoit une notification (webhook)
2. Il télécharge les changements
3. Il re-génère la documentation
4. ⏱️ Délai : 1-3 minutes

#### De GitBook → GitHub (si bidirectionnel)
Si vous éditez directement dans GitBook :
1. GitBook commit les changements
2. Les changements sont poussés vers GitHub
3. ⏱️ Délai : instantané

### Tester la synchronisation
1. Sur votre machine :
```bash
cd /Users/thomas/schoocursor
echo "Test sync" >> README.md
git add README.md
git commit -m "test: GitBook sync"
git push
```

2. Attendez 2 minutes
3. Rafraîchissez votre GitBook
4. ✅ Les changements devraient apparaître

---

## 📊 ÉTAPE 10 : ANALYTICS (OPTIONNEL)

### Activer les statistiques
```
⚙️ Settings → Integrations
└─ Google Analytics
   └─ Ajoutez votre ID de suivi
```

Vous pourrez voir :
- 👥 Nombre de visiteurs
- 📄 Pages les plus consultées
- 🌍 Géolocalisation
- ⏱️ Temps passé

---

## ✅ CHECKLIST FINALE

- [x] Push sur GitHub réussi (108 fichiers)
- [ ] Compte GitBook créé
- [ ] Espace "Build in 6 Days" créé
- [ ] GitHub connecté à GitBook
- [ ] Repository `build-in-6-days` synchronisé
- [ ] Structure de navigation vérifiée (50+ pages)
- [ ] Page d'accueil affichée correctement
- [ ] Thème personnalisé (optionnel)
- [ ] Documentation publiée
- [ ] URL publique obtenue
- [ ] Test de synchronisation effectué

---

## 🎯 RÉSULTAT ATTENDU

Après ces 10 étapes, vous aurez :

### ✅ Une Documentation Professionnelle
- 📱 **Responsive** : Mobile + Desktop
- 🔍 **Searchable** : Recherche full-text
- 🎨 **Beautiful** : Design moderne
- 📊 **Organized** : 50+ pages structurées

### ✅ Une URL Publique
```
https://[votre-nom].gitbook.io/build-in-6-days
```

### ✅ Une Synchronisation Automatique
- Modifiez sur GitHub → GitBook se met à jour
- Modifiez sur GitBook → GitHub se met à jour

### ✅ Un Outil Pédagogique Complet
- Étudiants : Accès facile à toute la documentation
- Professeurs : Guides, grilles, pense-bêtes
- Technique : Cours détaillés, templates, sources

---

## 🆘 BESOIN D'AIDE ?

### Documentation Officielle
- **GitBook Docs** : https://docs.gitbook.com
- **GitHub Integration** : https://docs.gitbook.com/integrations/git-sync

### Problèmes Courants

#### 1. "SUMMARY.md not found"
✅ **Solution** : Le fichier existe déjà à la racine

#### 2. "Invalid SUMMARY.md syntax"
✅ **Solution** : La syntaxe a été vérifiée et est correcte

#### 3. "Files not syncing"
- Vérifiez que vous êtes sur la branche `main`
- Attendez 3-5 minutes
- Vérifiez les webhooks dans Settings → Integrations

#### 4. "Images not displaying"
- Les images doivent être dans le repo GitHub
- Utilisez des chemins relatifs

---

## 🎉 PROCHAINES ÉTAPES

Une fois GitBook publié :

### 1. Partagez l'URL
- Ajoutez dans votre email à Stéphane
- Partagez avec vos étudiants
- Mettez dans le syllabus officiel

### 2. Mettez à jour régulièrement
```bash
# Après chaque modification
git add .
git commit -m "docs: Update [nom-du-fichier]"
git push
```

### 3. Collectez les retours
- Ajoutez un formulaire de feedback
- Notez les pages les plus consultées (Analytics)
- Améliorez en continu

---

**🚀 Temps estimé total : 20 minutes**

**Vous êtes maintenant prêt à avoir une documentation GitBook professionnelle !**

---

**Créé le** : 25 novembre 2025  
**Version** : 1.0

