# 📚 DOCUMENTATION CURSOR

> Sources officielles et ressources pour Cursor IDE

---

## 🔗 DOCUMENTATION OFFICIELLE

### Site Principal
- **URL** : https://cursor.com
- **Documentation** : https://docs.cursor.com
- **Blog** : https://cursor.com/blog
- **Changelog** : https://cursor.com/changelog
- **Pricing** : https://cursor.com/pricing

### Getting Started
- **Installation** : https://docs.cursor.com/get-started/installation
- **Premier projet** : https://docs.cursor.com/get-started/first-project
- **Configuration** : https://docs.cursor.com/get-started/configuration
- **Migration depuis VS Code** : https://docs.cursor.com/get-started/migrate-from-vscode

---

## 🎯 LES 3 MODES DE CURSOR

### 1. Mode Agent
**Documentation** : https://docs.cursor.com/modes/agent

**Quand l'utiliser** :
- Tâches autonomes multi-fichiers
- Refactoring complexe
- Création de features complètes
- Modifications coordonnées

**Avantages** :
- Autonomie complète
- Gère plusieurs fichiers
- Planifie avant d'agir

**Optimisation** :
- Donner un contexte clair et complet
- Spécifier les fichiers concernés
- Définir les contraintes et limites
- Laisser l'agent travailler sans interrompre

**Exemple de prompt optimisé** :
```
"Crée un système d'authentification complet :
- Pages Login et Signup
- Utilise Supabase Auth
- Intègre avec le router
- Ajoute protected routes
- Style avec Tailwind

Fichiers à créer : src/auth/, src/components/auth/
Respecte les conventions du projet"
```

### 2. Mode Task (Editor)
**Documentation** : https://docs.cursor.com/modes/editor

**Quand l'utiliser** :
- Modifications précises
- Edit dans un seul fichier
- Changements ciblés
- Corrections rapides

**Avantages** :
- Rapide
- Précis
- Économique en tokens
- Contrôle total

**Optimisation** :
- Sélectionner le code à modifier
- Prompt court et précis
- Une seule action à la fois
- Vérifier immédiatement

**Exemple de prompt optimisé** :
```
"Ajoute la validation email dans ce formulaire"
```

### 3. Mode Plan
**Documentation** : https://docs.cursor.com/modes/plan

**Quand l'utiliser** :
- Architecture complexe
- Nouvelles features majeures
- Refactoring important
- Besoin de planification

**Avantages** :
- Planifie avant d'agir
- Vous gardez le contrôle
- Architecture réfléchie
- Modifications coordonnées

**Optimisation** :
- Décrire l'objectif global
- Laisser Cursor planifier
- Valider le plan
- Ajuster si nécessaire
- Exécuter étape par étape

**Exemple de prompt optimisé** :
```
"En mode Plan, crée un dashboard admin avec :
- Vue d'ensemble (KPIs)
- Liste des utilisateurs
- Graphiques de stats
- Filtres par date
- Export CSV

Propose un plan avant d'exécuter"
```

---

## ⚡ OPTIMISATION & PERFORMANCE

### Économie de Tokens

**Techniques** :
1. **Contexte minimal** : Ne donner que le nécessaire
2. **Prompts précis** : Éviter les formulations vagues
3. **Mode approprié** : Task pour petites modifs, Agent pour grandes
4. **Itération** : Corriger progressivement plutôt que tout refaire
5. **Cache context** : Réutiliser le contexte existant

**Exemple MAUVAIS (coûteux)** :
```
"Fais quelque chose avec le formulaire pour que ça marche mieux"
```

**Exemple BON (économique)** :
```
"Ajoute la validation Zod sur les champs email et password"
```

### Production Rapide

**Techniques** :
1. **Prompts séquentiels** : Une action après l'autre
2. **Templates** : Réutiliser des structures
3. **Cursor Rules** : Définir les conventions une fois
4. **MCP** : Automatiser les intégrations
5. **Keyboard shortcuts** : Maîtriser les raccourcis

**Raccourcis utiles** :
- `Cmd+K` / `Ctrl+K` : Chat rapide
- `Cmd+L` / `Ctrl+L` : Mode Composer
- `Cmd+I` / `Ctrl+I` : Inline edit (Task mode)
- `Cmd+Shift+L` / `Ctrl+Shift+L` : Generate/Refactor
- `Cmd+Shift+I` / `Ctrl+Shift+I` : Mode Plan (Composer multi-file)
- `Cmd+/` / `Ctrl+/` : Toggle Copilot
- `Tab` : Accept suggestion
- `Esc` : Dismiss suggestion

---

## 📖 CURSOR RULES (.cursorrules)

### Documentation
- **Format** : https://docs.cursor.com/context/rules
- **Exemples** : https://github.com/PatrickJS/awesome-cursorrules

### Best Practices
- Structure claire et organisée
- Commentaires explicatifs
- Évolution avec le projet
- Liens entre rules
- Tests des rules

### Format .mdc (Markdown Context)
- Extension de Markdown
- Contexte structuré
- Facilite la lecture par l'IA
- Support des métadonnées

---

## 🔌 MCP (Model Context Protocol)

### Documentation MCP
- **Spec** : https://modelcontextprotocol.io
- **GitHub** : https://github.com/modelcontextprotocol
- **Cursor Integration** : https://docs.cursor.com/context/mcp

### Configuration
- Settings → Extensions → MCP
- Configuration JSON
- API keys et tokens
- Test de connexion

---

## 🎓 RESSOURCES D'APPRENTISSAGE

### Tutoriels Vidéo
- **YouTube Cursor** : https://www.youtube.com/@cursor
- **Playlist Getting Started** : https://www.youtube.com/playlist?list=...

### Articles & Guides
- **Blog officiel** : https://cursor.com/blog
- **Community guides** : https://community.cursor.com

### Exemples de Projets
- **GitHub Examples** : https://github.com/getcursor/cursor-examples
- **Templates** : https://github.com/getcursor/templates

---

## 💡 TIPS & TRICKS

### Contexte Efficace
1. **Inclure** : Fichiers pertinents, structure, contraintes
2. **Exclure** : Détails inutiles, code non lié
3. **Organiser** : Hiérarchie claire, séparation des concerns
4. **Mettre à jour** : Garder le contexte à jour

### Prompts Performants
```
✅ BON :
"Crée un composant Button React avec variants (primary, secondary)
et sizes (sm, md, lg) en utilisant Tailwind et TypeScript"

❌ MAUVAIS :
"Fais-moi un bouton"
```

### Debugging avec Cursor
- Utiliser `@debug` dans les cursor rules
- Demander des explications : "Explique ce bug"
- Suggestions de fixes : "Propose 3 solutions"
- Tests automatiques : "Écris les tests pour cette fonction"

---

## 🔍 TROUBLESHOOTING

### Problèmes Courants

**Cursor ne répond pas** :
- Vérifier la connexion internet
- Redémarrer Cursor
- Vérifier les API keys

**MCP ne fonctionne pas** :
- Vérifier la configuration JSON
- Tester les API keys
- Consulter les logs

**Prompts ignorés** :
- Contexte trop large → Réduire
- Prompt ambigu → Préciser
- Contradiction dans les rules → Corriger

---

## 📚 RESSOURCES COMPLÉMENTAIRES

### Community
- **Discord** : https://discord.gg/cursor
- **Forum** : https://community.cursor.com
- **Twitter/X** : https://twitter.com/cursor_ai

### Updates
- **Changelog** : https://cursor.com/changelog
- **Release Notes** : https://github.com/getcursor/cursor/releases

---

## 💰 TARIFICATION (2025)

### Free Tier
- **Prix** : Gratuit
- **Inclus** : 
  - 2000 completions/mois
  - 50 slow premium requests/mois
  - Accès à GPT-4
- **Limites** : Pas de fast requests

### Pro ($20/mois)
- **Inclus** :
  - 500 fast premium requests/mois
  - Unlimited slow requests
  - GPT-4, Claude 3.5 Sonnet
  - Mode Agent/Plan illimité
  - Privacy mode
- **Idéal pour** : Développeurs professionnels, étudiants sérieux

### Business ($40/user/mois)
- Tout Pro +
- Admin dashboard
- Centralized billing
- Usage analytics
- Priority support

### Étudiants
- **GitHub Student Pack** : 6 mois Pro gratuits
- URL : https://education.github.com/pack

---

**Dernière mise à jour** : 25 novembre 2025  
**Version Cursor** : 0.43+ (novembre 2025)  
**Maintenu par** : Thomas Garcia

---

## 🆕 NOUVEAUTÉS 2025

### Cursor Composer (Beta)
- **Multi-file editing** amélioré
- Édition simultanée de plusieurs fichiers
- Meilleure compréhension du contexte projet
- Accès : `Cmd+Shift+I`

### Performance
- Réponses 30% plus rapides
- Cache context amélioré
- Consommation tokens optimisée
- Support projets > 100K lignes

### Nouveaux Shortcuts
- `Cmd+K` : Chat rapide
- `Cmd+L` : Mode Composer
- `Cmd+I` : Inline edit
- `Cmd+Shift+L` : Generate/Refactor
- `Cmd+/` : Toggle AI features

