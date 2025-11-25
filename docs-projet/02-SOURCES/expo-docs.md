# 📚 DOCUMENTATION EXPO (React Native)

**Site officiel** : https://expo.dev  
**Documentation** : https://docs.expo.dev  
**Dashboard EAS** : https://expo.dev/accounts/[your-account]/projects

---

## 🎯 RESSOURCES PRINCIPALES

### Getting Started
- **Introduction** : https://docs.expo.dev/get-started/introduction
- **Installation** : https://docs.expo.dev/get-started/set-up-your-environment
- **Create First App** : https://docs.expo.dev/tutorial/introduction
- **Expo Go App** : https://expo.dev/go

### Core Concepts (2025)
- **Project Structure** : https://docs.expo.dev/workflow/overview
- **Expo Router** : https://docs.expo.dev/router/introduction (⭐ Nouveau standard)
- **Styling** : https://docs.expo.dev/develop/user-interface/styling
- **TypeScript** : https://docs.expo.dev/guides/typescript

### Features Essentielles
- **Authentication** : https://docs.expo.dev/guides/authentication
- **Storage** : https://docs.expo.dev/versions/latest/sdk/async-storage
- **API Calls** : https://docs.expo.dev/guides/using-network
- **Camera** : https://docs.expo.dev/versions/latest/sdk/camera
- **Notifications** : https://docs.expo.dev/versions/latest/sdk/notifications

### Navigation
- **Expo Router (Recommandé)** : https://docs.expo.dev/router/introduction
- **React Navigation** : https://reactnavigation.org/docs/getting-started

### Integration Supabase
- **Supabase + Expo** : https://supabase.com/docs/guides/getting-started/quickstarts/react-native
- **Auth avec Expo** : https://supabase.com/docs/guides/auth/social-login/auth-google?queryGroups=platform&platform=react-native

---

## 🔧 INSTALLATION & SETUP (2025)

### Prérequis
```bash
# Node.js 18+ recommandé
node --version

# Installation globale Expo CLI (optionnelle)
npm install -g eas-cli
```

### Créer un Projet
```bash
# Méthode recommandée (2025)
npx create-expo-app@latest my-app

# Avec template TypeScript + Expo Router
npx create-expo-app@latest my-app --template tabs

# Naviguer dans le projet
cd my-app
```

### Lancer le Projet
```bash
# Démarre Metro bundler
npx expo start

# Options :
# - Scan QR code avec Expo Go (iOS/Android)
# - Presser 'i' pour iOS Simulator
# - Presser 'a' pour Android Emulator
# - Presser 'w' pour web (si supporté)
```

---

## 📱 TEST SUR MOBILE

### Expo Go App (Développement)
- **iOS** : App Store → "Expo Go"
- **Android** : Play Store → "Expo Go"
- Scanner le QR code affiché dans le terminal
- Hot reload automatique

### Limites Expo Go
- Ne supporte pas toutes les bibliothèques natives
- Pas de custom native code
- Pour dépasser : utiliser **Development Builds**

### Development Builds (Avancé)
```bash
# Créer un build de dev avec custom native code
npx expo install expo-dev-client
eas build --profile development --platform ios
```

---

## 🚀 BUILD & DEPLOY (EAS)

### Configuration EAS
```bash
# Login
eas login

# Configuration initiale
eas build:configure
```

### Build pour Production
```bash
# Android (APK/AAB)
eas build --platform android --profile production

# iOS (IPA)
eas build --platform ios --profile production

# Les deux
eas build --platform all --profile production
```

### Configuration eas.json
```json
{
  "build": {
    "development": {
      "developmentClient": true,
      "distribution": "internal"
    },
    "preview": {
      "distribution": "internal",
      "android": {
        "buildType": "apk"
      }
    },
    "production": {
      "android": {
        "buildType": "app-bundle"
      }
    }
  },
  "submit": {
    "production": {}
  }
}
```

### Soumettre aux Stores
```bash
# Google Play Store
eas submit --platform android

# Apple App Store
eas submit --platform ios
```

---

## 📦 BIBLIOTHÈQUES ESSENTIELLES

### UI Components
- **React Native Paper** : https://reactnativepaper.com
- **Tamagui** : https://tamagui.dev (moderne, performant)
- **NativeWind** : https://www.nativewind.dev (Tailwind pour RN)

### State Management
- **Zustand** : https://zustand-demo.pmnd.rs
- **Redux Toolkit** : https://redux-toolkit.js.org
- **TanStack Query** : https://tanstack.com/query

### Backend
- **Supabase** : Recommandé pour le cours
- **Firebase** : Alternative classique

---

## 🎓 POUR LE COURS (BONUS)

### Checklist Projet Mobile
- [ ] Projet Expo créé avec Expo Router
- [ ] Auth Supabase intégrée
- [ ] Navigation fonctionnelle
- [ ] UI responsive (iOS + Android)
- [ ] Build APK créé avec EAS
- [ ] Testé sur device physique

### Workflow Recommandé
1. **Jour 1-2** : Setup + Auth
2. **Jour 3-4** : Features principales
3. **Jour 5** : UI/UX polish
4. **Jour 6** : Build + test

### Exemple App Simple
```typescript
// app/index.tsx (Expo Router)
import { View, Text } from 'react-native';
import { Link } from 'expo-router';

export default function Home() {
  return (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text>Welcome to My App!</Text>
      <Link href="/profile">Go to Profile</Link>
    </View>
  );
}
```

---

## 💡 TIPS & TRICKS

### Performance
- Utiliser `React.memo` pour les composants
- `useMemo` et `useCallback` pour optimisations
- FlatList plutôt que ScrollView pour longues listes
- Image optimization avec `expo-image`

### Debugging
```bash
# Logs en temps réel
npx expo start --dev-client

# React DevTools
npx react-devtools
```

### Common Issues
- **Metro bundler cache** : `npx expo start -c`
- **Node modules** : `rm -rf node_modules && npm install`
- **iOS build fails** : Vérifier Xcode + CocoaPods

---

## 📊 EXPO SDK VERSIONS (2025)

| SDK | React Native | Release | Status |
|-----|--------------|---------|--------|
| SDK 52 | 0.76.x | Jan 2025 | ✅ Latest |
| SDK 51 | 0.74.x | Juil 2024 | ✅ Supporté |
| SDK 50 | 0.73.x | Jan 2024 | ⚠️ Bientôt obsolète |

**Recommandation** : Utiliser SDK 52 (latest)

---

## 🔗 RESSOURCES COMPLÉMENTAIRES

### Community
- **Discord** : https://chat.expo.dev
- **Forum** : https://forums.expo.dev
- **Twitter/X** : https://twitter.com/expo
- **Blog** : https://blog.expo.dev

### Tutoriels
- **Expo Docs** : Documentation complète officielle
- **React Native School** : https://www.reactnativeschool.com
- **William Candillon** : https://www.youtube.com/@wcandillon

### Exemples
- **Expo Examples** : https://github.com/expo/examples
- **Ignite** : https://github.com/infinitered/ignite (boilerplate)

---

**Dernière MAJ** : 25 novembre 2025  
**SDK Actuel** : Expo SDK 52  
**Maintenu par** : Thomas Garcia

