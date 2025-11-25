# 📚 DOCUMENTATION CLAUDE (Anthropic)

**Site officiel** : https://www.anthropic.com  
**Console** : https://console.anthropic.com  
**Documentation** : https://docs.anthropic.com  
**API Reference** : https://docs.anthropic.com/en/api

---

## 🎯 MODÈLES DISPONIBLES (Novembre 2025)

### Claude Sonnet 4.5 (Recommandé) 🆕

**Dernière version** (sortie septembre 2025)

- **Le plus performant** pour le code, finance, et cybersécurité
- **Utilisé par défaut dans Cursor**
- Context window : **200K tokens**
- Autonomie : Peut travailler **+30 heures** sur tâches complexes
- API : `claude-sonnet-4-5`

**Nouvelles Fonctionnalités** :
- ✨ **Memory Tool (Beta)** : Stockage d'informations hors contexte
- ⚡ **Context Editing** : Gestion intelligente du contexte (suppression auto d'anciens appels)
- 🎯 **Meilleur alignement** : Réduction flatterie excessive et tromperie
- 💻 **Codage amélioré** : Performances accrues sur tâches de programmation
- 🤖 **Agents complexes** : Meilleur pour tâches informatiques avancées

**Documentation** : https://docs.anthropic.com/en/docs/about-claude/models/whats-new-sonnet-4-5

### Claude 4 Opus (Tâches très complexes)

- Maximum de capacités pour tâches extrêmement complexes
- Plus coûteux mais plus puissant
- Context window : 200K tokens
- API : `claude-4-opus`

### Claude 3.7 Sonnet (Version précédente)

- Toujours disponible
- Balance performance/coût
- Context window : 200K tokens
- API : `claude-3-7-sonnet`

### Claude Haiku (Rapide et économique)

- Plus rapide et économique
- Bon pour tâches simples
- Context window : 200K tokens
- API : `claude-haiku`

---

## 📚 RESSOURCES OFFICIELLES

### Documentation Principale
- **Getting Started** : https://docs.anthropic.com/en/docs/quickstart
- **What's New Claude 4.5** : https://docs.claude.com/fr/docs/about-claude/models/whats-new-claude-4-5
- **Migration Guide** : https://docs.claude.com/fr/docs/about-claude/models/whats-new-claude-4-5
- **Prompt Engineering** : https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering
- **Best Practices** : https://docs.anthropic.com/en/docs/test-and-evaluate
- **Vision** : https://docs.anthropic.com/en/docs/build-with-claude/vision

### API & SDKs
- **API Reference** : https://docs.anthropic.com/en/api
- **Python SDK** : https://github.com/anthropics/anthropic-sdk-python
- **TypeScript SDK** : https://github.com/anthropics/anthropic-sdk-typescript
- **Rate Limits** : https://docs.anthropic.com/en/api/rate-limits

### Guides Avancés
- **System Prompts** : https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/system-prompts
- **Few-shot Prompting** : https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/few-shot-prompting
- **Chain of Thought** : https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/chain-of-thought
- **Tool Use (Function Calling)** : https://docs.anthropic.com/en/docs/build-with-claude/tool-use
- **Memory Tool (New)** : https://docs.claude.com/en/docs/about-claude/models/whats-new-sonnet-4-5

### Exemples & Cookbook
- **Anthropic Cookbook** : https://github.com/anthropics/anthropic-cookbook
- **Prompt Library** : https://docs.anthropic.com/en/prompt-library/library

---

## 💡 POUR CURSOR

**Claude Sonnet 4.5** est le modèle par défaut dans Cursor depuis novembre 2025.

### Avantages
- ✅ Utiliser les modes Agent/Task/Plan sans configuration
- ✅ Le modèle s'adapte automatiquement au contexte
- ✅ Support natif des MCPs
- ✅ Context window de 200K tokens
- ✅ Memory tool pour projets longs
- ✅ Meilleur pour génération de code

**Pricing Cursor** : Inclus dans l'abonnement Cursor Pro ($20/mois)

**Optimisation** :
- Context window étendu permet de donner plus de fichiers en contexte
- Memory tool garde les informations importantes entre sessions
- Context editing automatique = moins de gestion manuelle du contexte

---

## 🔑 UTILISATION DIRECTE (hors Cursor)

### Installation SDK

```bash
# Python
pip install anthropic

# TypeScript/JavaScript  
npm install @anthropic-ai/sdk
```

### Exemple Python (Claude 4.5)

```python
import anthropic

client = anthropic.Anthropic(api_key="votre-clé-api")

message = client.messages.create(
    model="claude-sonnet-4-5",  # Nouveau modèle
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Explique-moi les nouvelles features de Claude 4.5"}
    ]
)

print(message.content)
```

### Exemple TypeScript (Claude 4.5)

```typescript
import Anthropic from '@anthropic-ai/sdk';

const client = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY,
});

const message = await client.messages.create({
  model: 'claude-sonnet-4-5',  // Nouveau modèle
  max_tokens: 1024,
  messages: [
    { role: 'user', content: 'Génère un composant React avec TypeScript' }
  ],
});

console.log(message.content);
```

### Utilisation du Memory Tool (Beta)

```python
# Activer le memory tool pour stocker des informations
message = client.messages.create(
    model="claude-sonnet-4-5",
    max_tokens=2048,
    system=[
        {
            "type": "text",
            "text": "Tu es un assistant de développement. Utilise le memory tool pour retenir les préférences du projet."
        }
    ],
    tools=[
        {
            "name": "memory",
            "description": "Store and retrieve important information"
        }
    ],
    messages=[
        {"role": "user", "content": "Je préfère React avec TypeScript et Tailwind"}
    ]
)
```

---

## 📊 TARIFICATION (Novembre 2025)

| Modèle | Input ($/MTok) | Output ($/MTok) | Context |
|--------|----------------|-----------------|---------|
| **Claude Sonnet 4.5** | $3.00 | $15.00 | 200K |
| Claude 4 Opus | $15.00 | $75.00 | 200K |
| Claude 3.7 Sonnet | $3.00 | $15.00 | 200K |
| Claude Haiku | $0.25 | $1.25 | 200K |

**Économies Possibles** :
- 💰 **Prompt Caching** : Réduction jusqu'à 90% sur tokens répétés
- 📦 **Batch Processing** : Réduction de 50% sur traitement par lots
- 🎓 **Student Discount** : 15% avec email .edu (code **STUDENT15**)

*Tarifs indicatifs, vérifier sur https://www.anthropic.com/pricing*

---

## 🆕 NOUVEAUTÉS CLAUDE SONNET 4.5

### Memory Tool (Beta)
- Stockage d'informations hors fenêtre de contexte
- Construction de bases de connaissances au fil du temps
- Récupération intelligente d'informations pertinentes

### Context Editing
- Suppression automatique d'anciens appels d'outils
- Optimisation pour sessions d'agents longue durée
- Meilleure gestion de la mémoire

### Amélioration du Codage
- Performances accrues sur génération de code
- Meilleure compréhension des architectures complexes
- Moins d'erreurs de syntaxe

### Agents Autonomes
- Peut travailler +30 heures sur une tâche
- Meilleur raisonnement multi-étapes
- Gestion automatique de tâches complexes

---

## 🎓 RESSOURCES COMPLÉMENTAIRES

### Community & Support
- **Discord** : https://discord.gg/anthropic
- **Twitter/X** : https://twitter.com/AnthropicAI
- **Support** : support@anthropic.com

### News & Updates
- **Blog** : https://www.anthropic.com/news
- **Research** : https://www.anthropic.com/research
- **Release Notes** : https://docs.claude.com/fr/docs/about-claude/models/whats-new-claude-4-5

### Vidéos
- **Claude Sonnet 4.5 Overview** : Rechercher sur YouTube "Claude Sonnet 4.5"
- **Coding with Claude** : Tutoriels disponibles sur le blog Anthropic

---

## 💡 TIPS POUR CURSOR + CLAUDE 4.5

### Profiter du Context Window
- Donnez plus de fichiers en contexte (@mentions)
- Le context editing gère automatiquement l'optimisation
- 200K tokens = ~150K mots de contexte

### Utiliser le Memory Tool
- Pour projets longs, activez le memory tool
- Stocke préférences, architecture, décisions
- Récupération automatique quand pertinent

### Optimiser les Prompts
- Claude 4.5 comprend mieux les instructions complexes
- Moins besoin de répéter le contexte
- Chain of thought plus efficace

---

**Dernière MAJ** : 25 novembre 2025  
**Version Claude** : Sonnet 4.5 (sortie septembre 2025)  
**Maintenu par** : Thomas Garcia  
**Sources** : [Anthropic Official](https://www.anthropic.com/claude/sonnet)
