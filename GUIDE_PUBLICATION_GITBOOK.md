# 📖 Guide de Publication GitBook

> Comment publier "Build in 6 Days" sur GitBook

---

## ✅ Fichiers Créés pour GitBook

Tous les fichiers nécessaires ont été créés :

- ✅ **SUMMARY.md** - Table des matières GitBook
- ✅ **README.md** - Page d'accueil améliorée
- ✅ **.gitbook.yaml** - Configuration GitBook
- ✅ **.gitignore** - Fichiers à ignorer

---

## 🚀 Étapes de Publication

### 1. Push sur GitHub

```bash
# Ajouter tous les fichiers
git add .

# Commit
git commit -m "feat: Add GitBook structure (SUMMARY.md, README, config)"

# Push vers GitHub
git push origin main
```

### 2. Créer un Compte GitBook

1. Aller sur https://gitbook.com
2. S'inscrire (gratuit pour documentation publique)
3. Se connecter

### 3. Créer un Nouveau Space

1. Cliquer sur **"+ New space"** ou **"Create new"**
2. Choisir un nom : **"Build in 6 Days"**
3. Choisir **"Empty space"** (on va sync avec GitHub)

### 4. Activer GitHub Sync

1. Dans votre space, cliquer sur **⚙️ Settings** (en haut à droite)
2. Dans le menu latéral, cliquer sur **"Integrations"**
3. Chercher **"GitHub"** et cliquer sur **"Connect"**
4. Autoriser GitBook à accéder à votre compte GitHub
5. Installer l'app GitBook sur votre compte GitHub

### 5. Configurer la Synchronisation

1. Sélectionner le repository : **mrsoyer/build-in-6-days**
2. Sélectionner la branche : **main**
3. Choisir le mode de sync :
   - **GitHub → GitBook** (recommandé pour la première fois)
4. Cliquer sur **"Sync"**

### 6. Première Synchronisation

GitBook va importer :
- ✅ README.md → Page d'accueil
- ✅ SUMMARY.md → Navigation
- ✅ Tous les fichiers .md

**Temps estimé** : 1-2 minutes

### 7. Vérifier la Navigation

1. Vérifier que la navigation (SUMMARY.md) s'affiche correctement
2. Tester quelques liens
3. Vérifier l'affichage des pages

### 8. Personnaliser le Space

#### Paramètres du Site
1. **Settings → Site settings**
2. Configurer :
   - **Title** : "Build in 6 Days - Bootcamp IA"
   - **Description** : "Bootcamp intensif : De l'idée au produit en 6 jours"
   - **Logo** : Ajouter un logo si disponible
   - **Favicon** : Ajouter une favicon

#### Thème
1. **Settings → Appearance**
2. Choisir :
   - **Theme** : Light/Dark ou Auto
   - **Primary color** : Choisir votre couleur
   - **Font** : Par défaut OK

#### Domaine (Optionnel)
1. **Settings → Domain**
2. URL par défaut : `https://votre-space.gitbook.io`
3. Domaine custom : Possible avec plan Pro

### 9. Publier

1. Cliquer sur **"Publish"** en haut à droite
2. Votre documentation est maintenant **publique** ! 🎉

---

## 🔄 Workflow de Mise à Jour

### Après Configuration Initiale

1. **Modifier localement** vos fichiers .md
2. **Commit et push** sur GitHub :
   ```bash
   git add .
   git commit -m "docs: Update X"
   git push origin main
   ```
3. **Sync automatique** : GitBook se met à jour automatiquement (1-2 min)

### Modifier Directement dans GitBook

Vous pouvez aussi :
1. Éditer dans l'interface GitBook
2. Les changements seront **synchronisés vers GitHub**
3. Bidirectionnel ! 🔄

---

## ✅ Checklist de Vérification

Après publication, vérifier :

- [ ] Page d'accueil s'affiche correctement
- [ ] Navigation (sidebar) fonctionne
- [ ] Tous les liens internes fonctionnent
- [ ] Code blocks sont bien formatés
- [ ] Images s'affichent (si vous en avez)
- [ ] Tables sont lisibles
- [ ] Emojis s'affichent 😊
- [ ] URL publique fonctionne

---

## 💡 Bonnes Pratiques

### Structure des Liens

✅ **Bon** : Liens relatifs
```markdown
[Documentation](docs-projet/DOCUMENTATION_TECHNIQUE_COMPLETE.md)
```

❌ **Mauvais** : Liens absolus GitHub
```markdown
[Documentation](https://github.com/mrsoyer/build-in-6-days/blob/main/...)
```

### Organisation

- ✅ Garder SUMMARY.md à jour
- ✅ Organiser par public cible (étudiants/profs)
- ✅ Utiliser des emojis pour la clarté
- ✅ Ajouter des descriptions courtes

### Contenu

- ✅ Markdown pur (pas de HTML complexe)
- ✅ Code blocks avec langage spécifié
- ✅ Tables pour les comparaisons
- ✅ Callouts GitBook pour les notes importantes

---

## 🎨 Fonctionnalités GitBook Avancées

### Hints (Callouts)

```markdown
{% hint style="info" %}
Information importante
{% endhint %}

{% hint style="warning" %}
Attention !
{% endhint %}

{% hint style="success" %}
Bravo !
{% endhint %}

{% hint style="danger" %}
Danger / Erreur
{% endhint %}
```

### Tabs

```markdown
{% tabs %}
{% tab title="JavaScript" %}
\`\`\`javascript
console.log("Hello");
\`\`\`
{% endtab %}

{% tab title="TypeScript" %}
\`\`\`typescript
console.log("Hello");
\`\`\`
{% endtab %}
{% endtabs %}
```

### API Methods

```markdown
{% swagger method="get" path="/api/users" summary="Get users" %}
...
{% endswagger %}
```

---

## 🆓 Plans GitBook

### Free (Idéal pour vous)
- ✅ Documentation publique illimitée
- ✅ GitHub Sync
- ✅ 1 space
- ✅ Collaboration limitée

### Plus ($12/mois)
- ✅ Documentation privée
- ✅ Spaces illimités
- ✅ Custom domain
- ✅ Analytics

### Pro ($45/mois)
- ✅ Tout Plus +
- ✅ Advanced analytics
- ✅ SSO
- ✅ Priority support

**Recommandation** : Commencer avec **Free**, upgrader si besoin

---

## 🐛 Troubleshooting

### Sync ne fonctionne pas

1. Vérifier que l'app GitBook est installée sur GitHub
2. Vérifier les permissions
3. Force sync : Settings → Integrations → GitHub → "Sync now"

### Navigation ne s'affiche pas

1. Vérifier que SUMMARY.md est à la racine
2. Vérifier la syntaxe du SUMMARY.md
3. Re-sync

### Liens cassés

1. Utiliser des chemins relatifs
2. Vérifier l'orthographe des fichiers
3. Tester localement avant push

### Images ne s'affichent pas

1. Vérifier le chemin
2. Utiliser des URLs absolues ou chemins relatifs
3. Placer les images dans `.gitbook/assets/`

---

## 📊 Statistiques

Après publication, GitBook fournit :
- 👥 Nombre de visiteurs
- 📄 Pages les plus consultées
- 🌍 Pays des visiteurs
- 🔍 Termes de recherche

---

## 🔗 Liens Utiles

- **GitBook Docs** : https://docs.gitbook.com
- **GitHub Sync** : https://docs.gitbook.com/integrations/git-sync
- **Markdown Guide** : https://docs.gitbook.com/content-editor/markdown
- **Support** : https://gitbook.com/support

---

## ✅ Résultat Final

Votre documentation sera accessible sur :
```
https://votre-space.gitbook.io/build-in-6-days
```

Avec :
- ✅ Navigation claire et intuitive
- ✅ Design professionnel
- ✅ Recherche intégrée
- ✅ Mobile-friendly
- ✅ SEO optimisé
- ✅ Sync automatique avec GitHub

---

**🎉 Votre projet est prêt pour GitBook !**

**Questions ?** Consultez la documentation officielle ou le support GitBook.

**Dernière MAJ** : 25 novembre 2025

