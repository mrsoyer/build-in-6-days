# 📚 DOCUMENTATION CLAUDE (Anthropic)

**Site officiel** : https://www.anthropic.com  
**Console** : https://console.anthropic.com  
**Documentation** : https://docs.anthropic.com  
**API Reference** : https://docs.anthropic.com/en/api

---

## 🎯 MODÈLES DISPONIBLES (2025)

### Claude 3.5 Sonnet (Recommandé)
- **Le plus performant** actuellement
- Utilisé par défaut dans Cursor
- Excellent pour le code et le raisonnement
- Context window : 200K tokens
- API : `claude-3-5-sonnet-20241022`

### Claude 3 Opus
- Maximum de capacités
- Meilleur pour tâches complexes
- Plus coûteux
- Context window : 200K tokens
- API : `claude-3-opus-20240229`

### Claude 3 Sonnet
- Balance performance/coût
- Bon pour usage quotidien
- Context window : 200K tokens
- API : `claude-3-sonnet-20240229`

### Claude 3 Haiku
- Plus rapide et économique
- Bon pour tâches simples
- Context window : 200K tokens
- API : `claude-3-haiku-20240307`

---

## 📚 RESSOURCES OFFICIELLES

### Documentation Principale
- **Getting Started** : https://docs.anthropic.com/en/docs/quickstart
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

### Exemples & Cookbook
- **Anthropic Cookbook** : https://github.com/anthropics/anthropic-cookbook
- **Prompt Library** : https://docs.anthropic.com/en/prompt-library/library

---

## 💡 POUR CURSOR

Claude 3.5 Sonnet est le modèle par défaut dans Cursor. Vous pouvez :
- Utiliser les modes Agent/Task/Plan sans configuration
- Le modèle s'adapte automatiquement au contexte
- Support natif des MCPs

**Pricing Cursor** : Inclus dans l'abonnement Cursor Pro

---

## 🔑 UTILISATION DIRECTE (hors Cursor)

### Installation SDK
```bash
# Python
pip install anthropic

# TypeScript/JavaScript  
npm install @anthropic-ai/sdk
```

### Exemple Python
```python
import anthropic

client = anthropic.Anthropic(api_key="votre-clé")
message = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    messages=[
        {"role": "user", "content": "Hello, Claude!"}
    ]
)
print(message.content)
```

### Exemple TypeScript
```typescript
import Anthropic from '@anthropic-ai/sdk';

const client = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY,
});

const message = await client.messages.create({
  model: 'claude-3-5-sonnet-20241022',
  max_tokens: 1024,
  messages: [{ role: 'user', content: 'Hello, Claude!' }],
});

console.log(message.content);
```

---

## 📊 TARIFICATION (2025)

| Modèle | Input ($/MTok) | Output ($/MTok) |
|--------|----------------|-----------------|
| Claude 3.5 Sonnet | $3.00 | $15.00 |
| Claude 3 Opus | $15.00 | $75.00 |
| Claude 3 Sonnet | $3.00 | $15.00 |
| Claude 3 Haiku | $0.25 | $1.25 |

*Tarifs indicatifs, vérifier sur le site officiel*

---

## 🎓 RESSOURCES COMPLÉMENTAIRES

### Community & Support
- **Discord** : https://discord.gg/anthropic
- **Twitter/X** : https://twitter.com/AnthropicAI
- **Support** : support@anthropic.com

### News & Updates
- **Blog** : https://www.anthropic.com/news
- **Research** : https://www.anthropic.com/research
- **Changelog** : Voir documentation officielle

---

**Dernière MAJ** : 25 novembre 2025  
**Maintenu par** : Thomas Garcia

