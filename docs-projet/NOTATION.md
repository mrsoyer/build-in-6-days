# 📊 Notation Technique

> **Note Technique** : /20 (calculée sur /130 points)  
> **Note Jury** : /20 (créativité, design, impact business)  
> **Note Peers** : /20 (évaluation individuelle par vos camarades)

---

## 🎯 Votre Note Finale

```
NOTE FINALE = (Note Technique + Note Jury + Note Peers) / 3
```

**Jury final** : Présentation de 5 minutes devant le jury le dernier jour

---

## 📋 Grille Technique (/130 points → /20)

### 1. DOCUMENTATION NOTION (/30 points)

| Critère | Points |
|---------|--------|
| Page principale + Kanban + Roadmap + Changelog | 5 pts |
| Documentation technique (architecture, BDD, install) | 5 pts |
| Accessible tech ET non-tech | 5 pts |
| Présentation équipe (nom, photo, rôle, contributions) | 5 pts |
| MCP Notion configuré + preuve d'utilisation | 5 pts |
| Changelog auto-généré + roadmap sync | 5 pts |

### 2. CURSOR RULES & ORGANISATION (/25 points)

| Critère | Points |
|---------|--------|
| `.cursorrules` principal complet | 5 pts |
| `.cursorrules-docs` présent et utilisé | 3 pts |
| Minimum 2 `.cursorrules-[feature]` | 7 pts |
| `.cursorrules-installation` fonctionnel | 5 pts |
| Organisation claire et évolution visible | 5 pts |

### 3. GITHUB & VERSIONING (/10 points)

| Critère | Points |
|---------|--------|
| Repository bien organisé et nommage cohérent | 3 pts |
| README complet (10 sections obligatoires) | 3 pts |
| **TOUS les membres ont commit** (sinon 0 pt) | 4 pts |

### 4. MCP & SYNCHRONISATION (/20 points)

| Critère | Points |
|---------|--------|
| MCP Notion installé + configuré + testé | 4 pts |
| MCP Supabase installé + configuré + testé | 4 pts |
| MCP Airtable installé + configuré + testé | 4 pts |
| Sync Airtable → Supabase fonctionnelle | 5 pts |
| Architecture respectée (Read: Supabase, Write: Airtable) | 3 pts |

### 5. AUTHENTIFICATION (/15 points)

| Critère | Points |
|---------|--------|
| Login + Signup + Logout | 6 pts |
| Protected routes + session persistante | 4 pts |
| **BONUS** : Gestion des rôles (user/admin) | **+3 pts** |
| **BONUS** : OAuth Google/Facebook | **+5 pts** |

### 6. BASE DE DONNÉES & FONCTIONS (/15 points)

| Critère | Points |
|---------|--------|
| Schema Airtable (3 tables + relations + 15 données) | 5 pts |
| 2-3 Fonctions PostgreSQL documentées | 7 pts |
| Fonctions appelées depuis l'app | 3 pts |
| **BONUS** : Dashboard avec filtres PostgreSQL | **+5 pts** |

### 7. DÉPLOIEMENT & PRODUCTION (/10 points)

| Critère | Points |
|---------|--------|
| App déployée sur Netlify (URL fonctionnelle) | 7 pts |
| Configuration `netlify.toml` correcte | 3 pts |
| **BONUS** : App mobile Expo fonctionnelle | **+7 pts** |

### 8. WORKFLOWS & AUTOMATISATIONS (/5 points)

| Critère | Points |
|---------|--------|
| 1-2 workflows Supabase configurés et fonctionnels | 5 pts |

### 9. OUTILS COMPLÉMENTAIRES (BONUS)

| Critère | Points |
|---------|--------|
| **BONUS** : Intégration pertinente (Make, n8n, Claude...) | **+5 pts** |

---

## 🧮 Calcul de la Note

### Formule
```
NOTE TECHNIQUE /20 = (TOTAL POINTS / 130) × 20
```

**Bonus** : Les points bonus s'ajoutent au total (max +25 pts)  
**Note plafonnée** : Maximum 20/20

### Exemples

**Exemple 1 : Projet Complet**
```
Base : 122/130 points
Bonus : +8 points (rôles + dashboard)
Total : 130/130
→ NOTE = 20/20 ✅
```

**Exemple 2 : Projet Basique**
```
Base : 98/130 points
Bonus : 0
→ NOTE = (98/130) × 20 = 15.08/20
```

**Exemple 3 : Projet Minimum**
```
Base : 92/130 points (seuil critique)
→ NOTE = (92/130) × 20 = 14.15/20
```

---

## ✅ Seuil pour 15/20 Minimum

Pour obtenir **15/20**, vous devez avoir minimum :

| Catégorie | Points Min |
|-----------|------------|
| Documentation Notion | 20/30 |
| Cursor Rules | 15/25 |
| GitHub (tous ont commit !) | 8/10 |
| MCP (3 installés) | 12/12 |
| Sync Airtable-Supabase | 5/5 |
| Auth complète | 12/15 |
| BDD avec données | 10/15 |
| App déployée | 7/10 |
| 1 workflow | 3/5 |
| **TOTAL** | **92/130** |

→ **14.15/20** (proche de 15)

---

## 🎯 Stratégie pour Maximiser votre Note

### Priorités (par ordre d'importance)

1. **Livrables obligatoires** : Assurez-vous d'avoir les 92 points minimum
2. **Commits** : TOUS les membres doivent commit (sinon -4 pts)
3. **Auth complète** : Login/Signup/Logout + protected routes (10 pts faciles)
4. **Déploiement** : Netlify est rapide à configurer (7-10 pts)
5. **Bonus stratégiques** : OAuth (+5) ou Dashboard (+5) pour passer à 18-20/20

### Pièges à Éviter

❌ **Oublier** qu'un membre de l'équipe doit commit → **-4 pts**  
❌ **Ne pas tester** les MCP → Risque de 0 pt si non fonctionnel  
❌ **Documentation incomplète** → Perte de points faciles (30 pts disponibles)  
❌ **Pas de déploiement** → **-10 pts**

---

## 📚 Ressources

- **Liste complète des livrables** : Voir [LIVRABLES.md](LIVRABLES.md)
- **Auto-évaluation** : Voir [CHECKLIST_PROJET.md](CHECKLIST_PROJET.md)
- **Jury final** : Voir [JURY.md](JURY.md)

---

**Conseil** : Utilisez la [CHECKLIST_PROJET.md](CHECKLIST_PROJET.md) pour calculer votre note en temps réel !

