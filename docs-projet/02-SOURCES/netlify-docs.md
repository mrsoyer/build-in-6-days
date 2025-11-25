# 📚 DOCUMENTATION NETLIFY

**Site officiel** : https://netlify.com  
**Documentation** : https://docs.netlify.com  
**Dashboard** : https://app.netlify.com

---

## 🎯 RESSOURCES PRINCIPALES

### Getting Started
- **Quick Start** : https://docs.netlify.com/get-started
- **Deploy Guide** : https://docs.netlify.com/site-deploys/create-deploys
- **CLI** : https://docs.netlify.com/cli/get-started

### Configuration
- **netlify.toml** : https://docs.netlify.com/configure-builds/file-based-configuration
- **Build Settings** : https://docs.netlify.com/configure-builds/get-started
- **Environment Variables** : https://docs.netlify.com/environment-variables/get-started
- **Redirects & Rewrites** : https://docs.netlify.com/routing/redirects

### Features Principales
- **Custom Domains** : https://docs.netlify.com/domains-https/custom-domains
- **HTTPS/SSL** : Automatique et gratuit
- **Forms** : https://docs.netlify.com/forms/setup
- **Functions (Serverless)** : https://docs.netlify.com/functions/overview
- **Edge Functions** : https://docs.netlify.com/edge-functions/overview
- **Split Testing (A/B)** : https://docs.netlify.com/site-deploys/split-testing

### Frameworks Supportés (2025)
- **React/Vite** : https://docs.netlify.com/integrations/frameworks/vite
- **Next.js** : https://docs.netlify.com/integrations/frameworks/next-js
- **Remix** : https://docs.netlify.com/integrations/frameworks/remix
- **Astro** : https://docs.netlify.com/integrations/frameworks/astro
- **SvelteKit** : https://docs.netlify.com/integrations/frameworks/sveltekit
- **Nuxt** : https://docs.netlify.com/integrations/frameworks/nuxt

---

## 🔧 DÉPLOIEMENT RAPIDE

### Méthode 1 : Depuis GitHub (Recommandé)
1. Pusher code sur GitHub
2. Se connecter à Netlify
3. "Add new site" → "Import from Git"
4. Sélectionner repository
5. Configure build settings (auto-détecté)
6. Deploy !

**Avantage** : Déploiement automatique à chaque push

### Méthode 2 : CLI
```bash
# Installation
npm install -g netlify-cli

# Connexion
netlify login

# Initialisation
netlify init

# Déploiement
netlify deploy --prod
```

### Méthode 3 : Drag & Drop
- Dashboard → "Add new site" → "Drag & drop"
- Glisser le dossier `dist/` ou `build/`
- Déploiement instantané

---

## 📝 CONFIGURATION TYPIQUE

### netlify.toml (React/Vite)
```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200

[build.environment]
  NODE_VERSION = "20"
```

### netlify.toml (Next.js)
```toml
[build]
  command = "npm run build"
  publish = ".next"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

### Variables d'Environnement
Dans le Dashboard :
- Site settings → Environment variables
- Ajouter :
  - `VITE_SUPABASE_URL`
  - `VITE_SUPABASE_ANON_KEY`
  - etc.

---

## ⚡ FONCTIONNALITÉS AVANCÉES

### Netlify Functions (Serverless)
```javascript
// netlify/functions/hello.js
exports.handler = async (event, context) => {
  return {
    statusCode: 200,
    body: JSON.stringify({ message: "Hello from Netlify!" })
  };
};
```

Accessible sur : `https://votresite.netlify.app/.netlify/functions/hello`

### Netlify Edge Functions (2025)
- Plus rapides que Functions classiques
- Exécutées au plus près de l'utilisateur
- Basées sur Deno
- Documentation : https://docs.netlify.com/edge-functions/overview

### Split Testing (A/B Testing)
- Tester différentes versions du site
- Répartition du trafic configurée
- Analytics intégrés

---

## 💡 TIPS & TRICKS

### Build Optimization
- Activer "Build plugins" pour optimisation automatique
- Utiliser le cache : `npm ci` au lieu de `npm install`
- Build time < 10min sur le plan gratuit

### Domaines Personnalisés
- Gratuit (DNS uniquement)
- HTTPS automatique
- Configuration simple dans Dashboard

### Preview Deployments
- Chaque PR → preview URL
- Parfait pour les reviews
- Nettoyage automatique après merge

---

## 📊 TARIFICATION (2025)

### Free Tier (Idéal pour étudiants)
- 300 build minutes/mois
- 100 GB bandwidth/mois
- Déploiements illimités
- HTTPS automatique
- 1 membre d'équipe

### Pro ($19/mois)
- 1000 build minutes/mois
- 400 GB bandwidth/mois
- Analytics avancés
- Split testing
- Équipe jusqu'à 5 membres

---

## 🎓 POUR LE COURS

### Checklist Déploiement Projet
- [ ] Repository GitHub créé
- [ ] Code pushed sur `main`
- [ ] `netlify.toml` configuré
- [ ] Variables d'env ajoutées dans Dashboard
- [ ] Site déployé et accessible
- [ ] URL partagée dans Notion

### Troubleshooting Commun
- **Build fails** : Vérifier `netlify.toml` et commandes
- **404 sur routes** : Ajouter redirect `/* → /index.html`
- **Env vars non détectées** : Préfixe `VITE_` pour Vite

---

## 🔗 RESSOURCES COMPLÉMENTAIRES

### Community
- **Blog** : https://www.netlify.com/blog
- **Forum** : https://answers.netlify.com
- **Twitter/X** : https://twitter.com/netlify

### Tutoriels
- **Deployment guides** : https://docs.netlify.com/integrations/frameworks
- **Jamstack** : https://jamstack.org

---

**Dernière MAJ** : 25 novembre 2025  
**Maintenu par** : Thomas Garcia

