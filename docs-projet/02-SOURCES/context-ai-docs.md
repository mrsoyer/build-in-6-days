# 📚 CONTEXTE & IA - BEST PRACTICES

> Comment donner le bon contexte à l'IA pour des résultats optimaux

---

## 🎯 POURQUOI LE CONTEXTE EST CRUCIAL

L'IA (Cursor, Claude, etc.) génère du code basé sur le **contexte** que vous lui donnez.

**Contexte insuffisant** → Résultats vagues, erreurs, incomplet  
**Bon contexte** → Code précis, fonctionnel, adapté

---

## 📏 CONTEXT WINDOWS

### Qu'est-ce qu'une Context Window ?

La **context window** est la quantité d'information que l'IA peut traiter en une seule fois.

**Limites typiques** :
- Claude 3.5 Sonnet : 200K tokens (~150K mots)
- GPT-4 : 128K tokens
- GPT-3.5 : 16K tokens

**1 token** ≈ 0.75 mots en anglais

### Implications Pratiques

✅ **Faire** :
- Donner le contexte essentiel
- Structurer l'information
- Référencer les fichiers pertinents

❌ **Éviter** :
- Inclure tout le codebase
- Dupliquer l'information
- Contexte non pertinent

---

## 🎨 PROMPT ENGINEERING

### Structure d'un Bon Prompt

```
[RÔLE] + [CONTEXTE] + [TÂCHE] + [CONTRAINTES] + [FORMAT]
```

**Exemple** :
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

Format :
Fichier unique src/components/EventCard.tsx
```

### Prompts Optimisés vs Non-Optimisés

❌ **Mauvais** :
```
"Fais-moi un formulaire"
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

## 🧠 TECHNIQUES AVANCÉES

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

Applique ce pattern pour l'authentification."
```

### 3. Iterative Refinement

Améliorer **progressivement** au lieu de tout refaire.

**Exemple** :
```
1. "Crée un bouton basique"
2. "Ajoute des variants (primary, secondary)"
3. "Ajoute des sizes (sm, md, lg)"
4. "Rends-le accessible (ARIA)"
```

### 4. Contexte Cumulatif

L'IA garde le contexte de la conversation.

**Astuce** : Référencer les échanges précédents
```
"En reprenant le composant Button qu'on a créé,
ajoute maintenant un loading state"
```

---

## 📂 DONNER LE BON CONTEXTE FICHIER

### Inclure les Fichiers Pertinents

✅ **Inclure** :
- Fichiers à modifier
- Types/interfaces utilisés
- Configuration pertinente
- Exemples similaires

❌ **Ne pas inclure** :
- Tout le codebase
- Fichiers non liés
- Node_modules
- Build artifacts

### Utiliser @mentions dans Cursor

```
@src/types/user.ts Crée un composant UserProfile
qui utilise le type User défini ici
```

---

## 🎯 CONTEXTE SELON LE MODE CURSOR

### Mode Task (Editor)
**Contexte minimal** : Sélection de code + instruction précise

```
[Sélectionner le code]
"Ajoute la validation email"
```

### Mode Agent
**Contexte complet** : Fichiers, architecture, contraintes

```
"Crée un système d'auth complet.
Stack : Supabase Auth
Fichiers : src/auth/
Voir @src/types/auth.ts pour les types"
```

### Mode Plan
**Contexte stratégique** : Objectif global, ressources disponibles

```
"Planifie un dashboard admin.
Features : KPIs, user list, charts
Data source : Supabase (voir @src/api/)
Design system : @src/components/ui/"
```

---

## 🚫 ERREURS COURANTES À ÉVITER

### 1. Contexte Trop Vague
❌ "Améliore le code"  
✅ "Optimise la performance de cette fonction en utilisant useMemo"

### 2. Contexte Contradictoire
❌ "Utilise TypeScript. Pas besoin de types."  
✅ "Utilise TypeScript avec types stricts pour tous les props"

### 3. Contexte Incomplet
❌ "Crée l'API pour les users"  
✅ "Crée l'API pour les users avec CRUD complet, validation Zod, et auth middleware"

### 4. Contexte Excessif
❌ [Coller 50 fichiers]  
✅ "Référence ces 3 fichiers clés : @types, @config, @example"

---

## 💡 TIPS & TRICKS

### Utiliser les Cursor Rules

Au lieu de répéter le contexte, définissez-le dans `.cursorrules` :

```markdown
# .cursorrules
## Stack
- React 18 + TypeScript
- Supabase + Airtable
- Tailwind CSS

## Conventions
- Functional components only
- Custom hooks for logic
- Types in src/types/
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
1. "Explique-moi comment tu ferais"
2. [Valider l'approche]
3. "OK, implémente la partie 1"
4. [Vérifier]
5. "Maintenant la partie 2"

---

## 📚 RESSOURCES

### Prompt Engineering
- **OpenAI Guide** : https://platform.openai.com/docs/guides/prompt-engineering
- **Anthropic Guide** : https://docs.anthropic.com/claude/docs/prompt-engineering
- **Learn Prompting** : https://learnprompting.org

### Context Best Practices
- **Cursor Docs** : https://docs.cursor.com/context/best-practices
- **AI Context Guide** : https://github.com/brexhq/prompt-engineering

---

**Dernière mise à jour** : 25 novembre 2025  
**Maintenu par** : Thomas Garcia

