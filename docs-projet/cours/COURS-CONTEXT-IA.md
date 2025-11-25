# 📚 COURS : CONTEXTE & IA

> Maîtriser l'art de donner le bon contexte à l'IA

---

## 🎯 OBJECTIFS

1. Comprendre l'importance du contexte
2. Maîtriser les context windows
3. Techniques de prompt engineering
4. Optimiser les résultats de l'IA

---

## 📏 CONTEXT WINDOWS

### Qu'est-ce qu'une Context Window ?

**Quantité d'information** que l'IA peut traiter en une fois.

**Limites** :
- Claude 3.5 Sonnet : 200K tokens (~150K mots)
- GPT-4 : 128K tokens
- 1 token ≈ 0.75 mots

### Implications

✅ **Faire** : Contexte essentiel et structuré  
❌ **Éviter** : Tout le codebase, infos non pertinentes

---

## 🎨 PROMPT ENGINEERING

### Structure Optimale

```
[RÔLE] + [CONTEXTE] + [TÂCHE] + [CONTRAINTES] + [FORMAT]
```

**Exemple** :
```
Tu es un développeur React/TypeScript expert.

Contexte :
- Projet : Gestion d'événements
- Stack : React, TypeScript, Supabase, Tailwind

Tâche :
Crée un composant EventCard

Contraintes :
- TypeScript strict
- Tailwind pour le style
- Responsive mobile-first
- Accessibilité (ARIA)

Format :
Fichier unique : src/components/EventCard.tsx
```

### Comparaison

❌ **Mauvais** : "Fais-moi un formulaire"

✅ **Bon** : "Crée un formulaire login avec validation Zod, Supabase Auth, loading state, error handling, style Tailwind"

---

## 🧠 TECHNIQUES AVANCÉES

### 1. Chain of Thought
Demander de raisonner étape par étape :
```
"Explique d'abord l'architecture, puis implémente"
```

### 2. Few-Shot Learning
Donner des exemples :
```
"Crée useAuth() similaire à cet exemple : [code]"
```

### 3. Iterative Refinement
Améliorer progressivement :
```
1. "Crée un bouton basique"
2. "Ajoute des variants"
3. "Ajoute sizes"
4. "Rends-le accessible"
```

### 4. Contexte Cumulatif
Référencer les échanges :
```
"En reprenant le Button créé, ajoute un loading state"
```

---

## 📂 CONTEXTE FICHIER

### Inclure

✅ Fichiers à modifier  
✅ Types/interfaces utilisés  
✅ Config pertinente  
✅ Exemples similaires

### Exclure

❌ Tout le codebase  
❌ Fichiers non liés  
❌ node_modules  
❌ Build artifacts

### @mentions dans Cursor

```
@src/types/user.ts Crée UserProfile utilisant ce type
```

---

## 🎯 CONTEXTE PAR MODE

**Task** : Minimal (sélection + instruction)  
**Agent** : Complet (fichiers, architecture, contraintes)  
**Plan** : Stratégique (objectif global, ressources)

---

## 🚫 ERREURS À ÉVITER

1. **Trop vague** : ❌ "Améliore le code"
2. **Contradictoire** : ❌ "TypeScript mais pas de types"
3. **Incomplet** : ❌ "Crée l'API users" (sans specs)
4. **Excessif** : ❌ [Coller 50 fichiers]

---

## 💡 TIPS

### Cursor Rules
Définir le contexte une fois dans `.cursorrules`

### Références Explicites
```
"Utilise le pattern de @src/components/UserCard.tsx"
```

### Contexte Progressif
Pour grandes tâches : Expliquer → Valider → Implémenter par parties

---

## 🧪 EXERCICE

**Tâche** : Créer un prompt optimal pour un composant Dashboard

Inclure :
- Rôle de l'IA
- Contexte projet
- Tâche précise
- Contraintes
- Format attendu

---

## ✅ VALIDATION

- [ ] Je comprends les context windows
- [ ] Je structure mes prompts (5 parties)
- [ ] J'utilise les @mentions
- [ ] J'évite les erreurs courantes
- [ ] Je sais itérer progressivement

---

**Durée** : 1h  
**Niveau** : Tous  
**Version** : 1.0

