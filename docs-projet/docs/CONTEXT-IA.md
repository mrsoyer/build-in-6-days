# 📚 Context IA & Prompt Engineering

> Maîtriser l'art de donner le bon contexte à l'IA pour des résultats optimaux

---

## 🎯 Vue d'ensemble

L'IA (Cursor, Claude, etc.) génère du code basé sur le **contexte** que vous lui donnez.

**Contexte insuffisant** → Résultats vagues, erreurs, code incomplet  
**Bon contexte** → Code précis, fonctionnel, adapté à vos besoins

### Objectifs

1. Comprendre l'importance du contexte
2. Maîtriser les context windows
3. Techniques de prompt engineering
4. Optimiser les résultats de l'IA

---

## 📏 Context Windows

### Qu'est-ce qu'une Context Window ?

La **context window** est la **quantité d'information** que l'IA peut traiter en une seule fois.

**Limites typiques** :
- Claude 3.5 Sonnet : 200K tokens (~150K mots)
- GPT-4 : 128K tokens
- GPT-3.5 : 16K tokens

**1 token** ≈ 0.75 mots en anglais

### Implications Pratiques

✅ **Faire** :
- Donner le contexte essentiel et structuré
- Référencer les fichiers pertinents avec @mentions
- Organiser l'information de manière hiérarchique

❌ **Éviter** :
- Inclure tout le codebase
- Dupliquer l'information
- Contexte non pertinent
- Build artifacts, node_modules

---

## 🎨 Prompt Engineering

### Structure d'un Bon Prompt

```
[RÔLE] + [CONTEXTE] + [TÂCHE] + [CONTRAINTES] + [FORMAT]
```

**Exemple Complet** :
```
Tu es un développeur React/TypeScript expert.

Contexte :
- Projet : App de gestion d'événements
- Stack : React, TypeScript, Supabase, Tailwind
- Architecture : Lecture Supabase, Écriture Airtable

Tâche :
Crée un composant EventCard qui affiche un événement.

Contraintes :
- Utilise TypeScript avec types stricts
- Style avec Tailwind
- Responsive (mobile-first)
- Accessibilité (ARIA labels)
- Loading state et error handling

Format :
Fichier unique src/components/EventCard.tsx
```

### Comparaison : Mauvais vs Bons Prompts

❌ **Mauvais** :
```
"Fais-moi un formulaire"
"Améliore le code"
"Crée l'API users"
```

✅ **Bon** :
```
"Crée un formulaire de login avec :
- Champs : email (validation), password (min 8 chars)
- Validation avec Zod
- Submit vers Supabase Auth
- Loading state et error handling
- Style Tailwind
Fichier : src/components/LoginForm.tsx"
```

---

## 🧠 Techniques Avancées

### 1. Chain of Thought (CoT)

Demander à l'IA de **raisonner étape par étape**.

**Exemple** :
```
"Avant de coder, explique-moi :
1. L'architecture que tu proposes
2. Les composants nécessaires
3. Les dépendances requises
Puis implémente."
```

**Avantages** :
- Meilleure compréhension du problème
- Détection précoce d'erreurs
- Code plus réfléchi

### 2. Few-Shot Learning

Donner des **exemples** de ce que vous voulez.

**Exemple** :
```
"Crée un hook useAuth() similaire à cet exemple :

```typescript
// Exemple de hook existant
export const useUser = () => {
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  
  useEffect(() => {
    // fetch user
  }, []);
  
  return { user, loading };
};
```

Applique ce pattern pour l'authentification avec Supabase."
```

**Avantages** :
- Cohérence de style
- Réutilisation de patterns
- Moins d'explications nécessaires

### 3. Iterative Refinement

Améliorer **progressivement** au lieu de tout refaire.

**Exemple** :
```
1. "Crée un bouton basique"
2. "Ajoute des variants (primary, secondary, ghost)"
3. "Ajoute des sizes (sm, md, lg)"
4. "Rends-le accessible (ARIA, keyboard navigation)"
5. "Ajoute un loading state"
```

**Avantages** :
- Contrôle granulaire
- Économie de tokens
- Résultats plus précis

### 4. Contexte Cumulatif

L'IA garde le contexte de la conversation.

**Astuce** : Référencer les échanges précédents
```
"En reprenant le composant Button qu'on a créé,
ajoute maintenant un loading state avec spinner"
```

---

## 📂 Donner le Bon Contexte Fichier

### Inclure les Fichiers Pertinents

✅ **Inclure** :
- Fichiers à modifier
- Types/interfaces utilisés
- Configuration pertinente
- Exemples similaires existants

❌ **Ne pas inclure** :
- Tout le codebase
- Fichiers non liés à la tâche
- Node_modules
- Build artifacts
- Tests (sauf si c'est le sujet)

### Utiliser @mentions dans Cursor

```
@src/types/user.ts Crée un composant UserProfile
qui utilise le type User défini ici

@src/components/Card.tsx Crée EventCard en suivant
le même pattern que ce composant
```

**Avantages** :
- Références explicites
- Économie de contexte
- Cohérence du code

---

## 🎯 Contexte selon le Mode Cursor

### Mode Task (Editor) - `Cmd+I`

**Contexte minimal** : Sélection de code + instruction précise

```
[Sélectionner le code]
"Ajoute la validation Zod sur email et password"
```

**Optimisation** :
- Prompts courts
- Une action à la fois
- Contexte implicite (code sélectionné)

### Mode Chat - `Cmd+L`

**Contexte conversationnel** : Questions, clarifications, explications

```
"Comment structurer mon système d'authentification avec Supabase ?
Dois-je utiliser Context API ou Zustand pour l'état ?"
```

**Optimisation** :
- Dialogue itératif
- Clarifications progressives
- Validation d'approche

### Mode Composer - `Cmd+Shift+I`

**Contexte complet** : Fichiers, architecture, contraintes

```
"Crée un système d'authentification complet :
- Pages Login et Signup (src/pages/auth/)
- AuthContext (src/contexts/AuthContext.tsx)
- Hook useAuth (src/hooks/useAuth.ts)
- ProtectedRoute HOC (src/components/ProtectedRoute.tsx)
- Types (src/types/auth.ts)

Stack : Supabase Auth
Voir @src/config/supabase.ts pour la config"
```

**Optimisation** :
- Spécifier tous les fichiers
- Définir l'architecture
- Contraintes claires

---

## 🚫 Erreurs Courantes à Éviter

### 1. Contexte Trop Vague

❌ "Améliore le code"  
❌ "Fais un dashboard"  
✅ "Optimise la performance de cette fonction en utilisant useMemo pour éviter les re-renders"  
✅ "Crée un dashboard admin avec KPIs (users, events, revenue), user list avec filtres, et graphiques Chart.js"

### 2. Contexte Contradictoire

❌ "Utilise TypeScript. Pas besoin de types."  
❌ "Fais simple mais avec toutes les features avancées"  
✅ "Utilise TypeScript avec types stricts pour tous les props et retours de fonction"  
✅ "Crée un MVP avec auth basique, on ajoutera OAuth plus tard"

### 3. Contexte Incomplet

❌ "Crée l'API pour les users"  
❌ "Fais l'authentification"  
✅ "Crée l'API users avec CRUD complet, validation Zod, RLS Supabase, et rate limiting"  
✅ "Implémente l'auth Supabase avec email/password, session persistence, protected routes, et error handling"

### 4. Contexte Excessif

❌ [Coller 50 fichiers]  
❌ [Inclure tout le historique de conversation]  
✅ "Référence ces 3 fichiers clés : @types/user.ts @config/supabase.ts @components/UserCard.tsx"  
✅ "En reprenant notre conversation sur l'auth, implémente maintenant le ProtectedRoute"

---

## 💡 Tips & Tricks

### Utiliser les Cursor Rules

Au lieu de répéter le contexte, définissez-le dans `.cursor/rules/` :

```markdown
---
alwaysApply: true
---

## Stack
- React 18 + TypeScript (strict mode)
- Supabase (read) + Airtable (write)
- Tailwind CSS

## Conventions
- Functional components only
- Custom hooks for logic (src/hooks/)
- Types in src/types/
- API calls in src/api/

## Code Style
- ESLint + Prettier
- TypeScript strict
- ARIA labels for accessibility
```

Puis dans vos prompts :
```
"Crée un composant EventList (respecte nos conventions)"
```

### Références Explicites

✅ "Utilise le même pattern que @src/components/UserCard.tsx"  
✅ "Suis l'architecture définie dans @docs/architecture.md"  
✅ "Applique le style de @src/components/ui/Button.tsx"

### Contexte Progressif

Pour les grandes tâches :
1. **Expliquer** : "Explique-moi comment tu ferais un dashboard admin"
2. **Valider** : [Discuter de l'approche]
3. **Planifier** : "OK, crée un plan d'implémentation"
4. **Implémenter par parties** : "Commence par la structure de base"
5. **Itérer** : "Maintenant ajoute les KPIs"

---

## 📚 Ressources

### Prompt Engineering

- **OpenAI Guide** : https://platform.openai.com/docs/guides/prompt-engineering
- **Anthropic Guide** : https://docs.anthropic.com/claude/docs/prompt-engineering
- **Learn Prompting** : https://learnprompting.org
- **Prompt Engineering Guide** : https://github.com/dair-ai/Prompt-Engineering-Guide

### Context Best Practices

- **Cursor Docs** : https://docs.cursor.com/context/best-practices
- **AI Context Guide** : https://github.com/brexhq/prompt-engineering

### Advanced Techniques

- **Chain of Thought** : https://arxiv.org/abs/2201.11903
- **Few-Shot Learning** : https://arxiv.org/abs/2005.14165

---

## 🧪 Exercice Pratique

**Tâche** : Créer un prompt optimal pour un composant Dashboard

Votre prompt doit inclure :
1. **Rôle** : Définir l'expertise de l'IA
2. **Contexte** : Projet, stack, architecture
3. **Tâche** : Composant Dashboard avec spécifications
4. **Contraintes** : TypeScript, style, responsive, accessibilité
5. **Format** : Structure de fichiers attendue

**Validation** :
- [ ] Les 5 parties sont présentes
- [ ] Les contraintes sont spécifiques
- [ ] Les fichiers sont référencés avec @mentions
- [ ] Le format de sortie est clair

---

## ✅ Checklist de Validation

**Pour un bon contexte, vérifiez** :
- [ ] Prompt structuré (5 parties)
- [ ] Contexte pertinent et minimal
- [ ] Instructions claires et précises
- [ ] Contraintes spécifiques
- [ ] @mentions pour les fichiers
- [ ] Pas d'informations contradictoires
- [ ] Format de sortie défini

---

**Dernière mise à jour** : 25 novembre 2025  
**Basé sur** : Best practices OpenAI, Anthropic, Cursor

