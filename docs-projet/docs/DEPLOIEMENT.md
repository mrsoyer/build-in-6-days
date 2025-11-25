# 📚 COURS : DÉPLOIEMENT

> Mettre votre application en production sur Netlify

---

## 🎯 OBJECTIFS

1. Configurer Netlify
2. Déployer l'application
3. Variables d'environnement
4. BONUS : App mobile Expo

---

## 🚀 DÉPLOIEMENT NETLIFY

### Méthode 1 : Via GitHub (Recommandé)

1. https://netlify.com → "Add new site" → "Import from Git"
2. Connecter GitHub
3. Sélectionner repository
4. **Build settings** :
   ```
   Build command: npm run build
   Publish directory: dist
   ```
5. Deploy

### Méthode 2 : Via CLI

```bash
# Install
npm install -g netlify-cli

# Login
netlify login

# Init
netlify init

# Deploy
netlify deploy --prod
```

---

## ⚙️ CONFIGURATION

### netlify.toml

Créer à la racine :
```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

**Pourquoi les redirects** ?  
Pour les SPA (React Router) : toutes les routes → index.html

---

## 🔐 VARIABLES D'ENVIRONNEMENT

### Configuration

1. Site settings → Environment variables
2. Add variables :
   ```
   VITE_SUPABASE_URL = https://xxx.supabase.co
   VITE_SUPABASE_ANON_KEY = eyJ...
   ```

### Dans le Code

```typescript
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;
```

### .env.example

Créer pour documentation :
```env
# Supabase
VITE_SUPABASE_URL=your_url_here
VITE_SUPABASE_ANON_KEY=your_key_here

# Airtable (si utilisé côté client)
VITE_AIRTABLE_API_KEY=your_key_here
```

---

## 🔄 DÉPLOIEMENTS AUTOMATIQUES

**Push sur main** → Netlify rebuild automatiquement

```bash
git add .
git commit -m "feat: add feature X"
git push origin main
# → Netlify détecte et déploie
```

**Preview deployments** : Branches → Preview URL

---

## 🐛 TROUBLESHOOTING

### Build fails

**Erreur commune** : Linter errors

**Solution** :
```json
// package.json
"scripts": {
  "build": "vite build --mode production",
  // ou
  "build": "tsc && vite build"
}
```

Ou désactiver temporairement :
```json
"build": "vite build --no-lint"
```

### 404 sur routes

**Problème** : Redirects non configurés

**Solution** : Ajouter `netlify.toml` avec redirects

### Variables d'environnement non trouvées

**Vérifier** :
1. Préfixe `VITE_` (pour Vite)
2. Configuration dans Netlify
3. Rebuild après ajout de variables

---

## 📱 BONUS : APP MOBILE EXPO

### Setup

```bash
# Install Expo CLI
npm install -g expo-cli

# Create app
npx create-expo-app mobile-app

cd mobile-app
```

### Configuration Supabase

```bash
npm install @supabase/supabase-js
```

**`config/supabase.ts`** :
```typescript
import { createClient } from '@supabase/supabase-js';
import Constants from 'expo-constants';

const supabaseUrl = Constants.expoConfig?.extra?.supabaseUrl;
const supabaseKey = Constants.expoConfig?.extra?.supabaseAnonKey;

export const supabase = createClient(supabaseUrl, supabaseKey);
```

**`app.config.js`** :
```javascript
export default {
  expo: {
    extra: {
      supabaseUrl: process.env.EXPO_PUBLIC_SUPABASE_URL,
      supabaseAnonKey: process.env.EXPO_PUBLIC_SUPABASE_ANON_KEY,
    }
  }
};
```

### Auth Mobile

Même code que web avec adaptation UI :
```typescript
import { useAuth } from '@/contexts/AuthContext';

export function LoginScreen() {
  const { signIn } = useAuth();
  
  // UI avec React Native components
}
```

### Build & Deploy

**iOS (TestFlight)** :
```bash
eas build --platform ios
eas submit --platform ios
```

**Android (APK)** :
```bash
eas build --platform android
# Download APK or submit to Play Store
```

---

## 🧪 EXERCICE

### Exercice 1 : Deploy Web

1. Connecter GitHub à Netlify
2. Configurer build settings
3. Ajouter variables d'environnement
4. Déployer
5. Tester URL live

### Exercice 2 : Mobile (Bonus)

1. Créer app Expo
2. Intégrer Supabase Auth
3. Build pour iOS ou Android
4. Tester sur mobile physique

---

## ✅ VALIDATION

**Web** :
- [ ] App déployée sur Netlify
- [ ] URL fonctionnelle
- [ ] Variables d'env configurées
- [ ] Redirects SPA actifs
- [ ] Build sans erreurs

**Mobile (Bonus)** :
- [ ] App Expo créée
- [ ] Auth fonctionnelle
- [ ] Build réussi
- [ ] Test sur device

---

## 📚 RESSOURCES

- [Netlify Docs](https://docs.netlify.com)
- [Expo Docs](https://docs.expo.dev)
- [EAS Build](https://docs.expo.dev/build/introduction)

---

**Durée** : 1-2h (web) + 3-4h (mobile)  
**Niveau** : Intermédiaire  
**Version** : 1.0

