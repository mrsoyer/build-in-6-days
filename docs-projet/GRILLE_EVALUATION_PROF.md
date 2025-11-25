# 📊 GRILLE D'ÉVALUATION PROFESSEUR

> Outil d'évaluation rapide pour le Demo Day

---

## 📋 INFORMATIONS PROJET

**Équipe** : ________________________________  
**Projet** : ________________________________  
**Date** : ________________  
**URL Live** : ________________________________  
**GitHub** : ________________________________

---

## ✅ ÉVALUATION RAPIDE

### 1. DOCUMENTATION NOTION (/30)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Structure générale (Kanban, Roadmap, Changelog) | /5 | | |
| Documentation technique complète | /5 | | |
| Accessible tech + non-tech | /5 | | |
| Présentation équipe + contributions | /5 | | |
| MCP Notion fonctionnel | /5 | | |
| Mise à jour automatique | /5 | | |
| **SOUS-TOTAL** | **/30** | | |

**Commentaires** :




---

### 2. CURSOR RULES (/25)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| .cursorrules principal complet | /5 | | |
| .cursorrules-docs | /3 | | |
| Rules par fonctionnalité (2+) | /7 | | |
| .cursorrules-installation | /5 | | |
| Organisation et clarté | /5 | | |
| **SOUS-TOTAL** | **/25** | | |

**Commentaires** :




---

### 3. MCP & SYNCHRONISATION (/20)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| MCP Notion (installé + doc) | /4 | | |
| MCP Supabase (installé + doc) | /4 | | |
| MCP Airtable (installé + doc) | /4 | | |
| Sync Airtable ↔ Supabase | /5 | | |
| Architecture respectée | /3 | | |
| **SOUS-TOTAL** | **/20** | | |

**Tests de sync** :
- [ ] INSERT dans Airtable → Supabase OK
- [ ] UPDATE dans Airtable → Supabase OK
- [ ] Temps sync < 5 secondes

**Commentaires** :




---

### 4. AUTHENTIFICATION (/15)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Auth client (login/signup/logout) | /10 | | |
| Protected routes | /5 | | |
| **SOUS-TOTAL** | **/15** | | |
| **BONUS : Gestion rôles** | **+3** | | |
| **BONUS : OAuth** | **+5** | | |

**Tests** :
- [ ] Signup fonctionne
- [ ] Login fonctionne
- [ ] Protected route redirige si non-auth
- [ ] Session persiste après refresh
- [ ] Logout fonctionne

**Commentaires** :




---

### 5. BASE DE DONNÉES & FONCTIONS (/15)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Schema Airtable (3+ tables, relations, données) | /5 | | |
| Fonctions PostgreSQL (2-3, documentées) | /7 | | |
| Fonctions utilisées dans l'app | /3 | | |
| **SOUS-TOTAL** | **/15** | | |
| **BONUS : Dashboard filtres PostgreSQL** | **+5** | | |

**Vérifications** :
- Nombre de tables : _____
- Nombre de fonctions SQL : _____
- Fonctions appelées : ☐ Oui ☐ Non

**Commentaires** :




---

### 6. DÉPLOIEMENT (/10)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| App déployée sur Netlify (URL + build OK) | /7 | | |
| Environnement production (netlify.toml, redirects) | /3 | | |
| **SOUS-TOTAL** | **/10** | | |
| **BONUS : App mobile Expo** | **+7** | | |

**Tests** :
- [ ] URL accessible
- [ ] Pas d'erreurs console
- [ ] Mobile responsive
- [ ] Fonctionnalités principales OK

**Commentaires** :




---

### 7. GITHUB (/10)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Repository bien organisé | /3 | | |
| README complet et clair | /3 | | |
| Tous les membres ont commit | /4 | | |
| **SOUS-TOTAL** | **/10** | | |

**Vérification commits** :
```bash
git shortlog -sn --all
```

Membres :
- ☐ Membre 1 : _____ commits
- ☐ Membre 2 : _____ commits
- ☐ Membre 3 : _____ commits
- ☐ Membre 4 : _____ commits

⚠️ **0 point si un membre n'a pas commit**

**Commentaires** :




---

### 8. WORKFLOWS (/5)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Workflows Supabase (1-2 configurés) | /5 | | |
| **SOUS-TOTAL** | **/5** | | |

**Commentaires** :




---

### 9. OUTILS COMPLÉMENTAIRES (BONUS)

| Critère | Points | Obtenu | Notes |
|---------|--------|--------|-------|
| Intégration pertinente (Make, n8n, etc.) | +5 max | | |

**Outil utilisé** : ________________________________  
**Justification valable** : ☐ Oui ☐ Non

**Commentaires** :




---

## 📊 RÉCAPITULATIF

| Catégorie | Points Obtenus | Max |
|-----------|----------------|-----|
| 1. Documentation Notion | _____ | 30 |
| 2. Cursor Rules | _____ | 25 |
| 3. MCP & Sync | _____ | 20 |
| 4. Authentification | _____ | 15 |
| 5. BDD & Fonctions | _____ | 15 |
| 6. Déploiement | _____ | 10 |
| 7. GitHub | _____ | 10 |
| 8. Workflows | _____ | 5 |
| **TOTAL OBLIGATOIRE** | **_____** | **130** |
| **BONUS** | **_____** | **+25** |

---

## 🧮 CALCUL NOTE TECHNIQUE

```
NOTE TECHNIQUE /20 = (Total / 130) × 20 + (Bonus / 130) × 20
```

**Calcul** :
```
NOTE = (_____ / 130) × 20 + (_____ / 130) × 20 = _____ / 20
```

*Plafonnée à 20/20*

---

## 🏆 POINTS FORTS DU PROJET

1. ____________________________________________
2. ____________________________________________
3. ____________________________________________

---

## 🔧 AXES D'AMÉLIORATION

1. ____________________________________________
2. ____________________________________________
3. ____________________________________________

---

## 💬 COMMENTAIRE GÉNÉRAL




---

## 🎯 PRIX SPÉCIAUX (À décerner en fin de Demo Day)

- [ ] 🏆 **Best Technical Achievement** : Pour l'excellence technique
- [ ] 🎨 **Best Design/UX** : Pour le design et l'expérience utilisateur
- [ ] 💡 **Most Innovative** : Pour l'originalité et la créativité
- [ ] 🚀 **Best Business Potential** : Pour le potentiel commercial
- [ ] ❤️ **Coup de cœur du prof** : Pour le projet préféré

**Prix attribué** : ________________________________

**Justification** :




---

## 📝 NOTES ADDITIONNELLES




---

**Évaluateur** : ________________________________  
**Signature** : ________________________________  
**Date** : ________________

