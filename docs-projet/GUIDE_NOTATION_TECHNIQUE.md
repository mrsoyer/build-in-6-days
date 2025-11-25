# 📊 GUIDE DE NOTATION TECHNIQUE

> **Document étudiant** : Comment est évaluée votre note technique

---

## 🎯 PHILOSOPHIE DU SYSTÈME

Votre note technique (/20) évalue la **qualité d'exécution** de votre projet selon des critères objectifs.

**Principes** :
- ✅ **Transparent** : Tous les critères sont publics
- ✅ **Objectif** : Checklist mesurable (fait/pas fait)
- ✅ **Équitable** : Mêmes critères pour tous
- ✅ **Progressif** : Bonus pour aller plus loin

**Note finale** : `(Total points / 130) × 20 + Bonus`

---

## 📋 VUE D'ENSEMBLE DES CATÉGORIES

| Catégorie | Points | Poids | Difficulté |
|-----------|--------|-------|------------|
| 📚 Documentation Notion | /30 | 23% | ⭐⭐ |
| ⚙️ Cursor Rules | /25 | 19% | ⭐⭐⭐ |
| 🔌 MCP & Sync | /20 | 15% | ⭐⭐⭐ |
| 🔐 Authentification | /15 | 12% | ⭐⭐ |
| 🗄️ BDD & Fonctions | /15 | 12% | ⭐⭐⭐ |
| 🚀 Déploiement | /10 | 8% | ⭐ |
| 📦 GitHub | /10 | 8% | ⭐ |
| 🔄 Workflows | /5 | 4% | ⭐⭐ |
| **TOTAL** | **/130** | **100%** | - |

**Bonus disponibles** : +25 points max

---

## 📚 1. DOCUMENTATION NOTION (/30 points)

### Vue d'ensemble (/5)
- [ ] Page principale avec description (**2 pts**)
- [ ] Kanban (To Do/Doing/Done) (**1 pt**)
- [ ] Roadmap 6 jours (**1 pt**)
- [ ] Changelog (**1 pt**)

**Comment valider** :
- Créer pages dans Notion
- Structure claire et navigable
- Utiliser les templates fournis

---

### Documentation Technique (/5)
- [ ] Architecture documentée avec schéma (**2 pts**)
- [ ] Schema BDD (Airtable + Supabase) (**1 pt**)
- [ ] Guide d'installation (**1 pt**)
- [ ] Variables d'environnement listées (**1 pt**)

**Comment valider** :
- Suivre le template Notion fourni
- Inclure diagrammes/captures d'écran
- Tester que le guide d'installation fonctionne

---

### Accessibilité (/5)
- [ ] Compréhensible par un développeur (**2 pts**)
- [ ] Compréhensible par un non-tech (**2 pts**)
- [ ] Navigation intuitive (**1 pt**)

**Comment valider** :
- Éviter le jargon technique excessif
- Ajouter des explications claires
- Tester avec quelqu'un non-tech

---

### Présentation Équipe (/5)
- [ ] Nom + photo de chaque membre (**2 pts**)
- [ ] Rôles définis (**1 pt**)
- [ ] Contributions (qui a fait quoi) (**2 pts**)

**Comment valider** :
- Page dédiée à l'équipe
- Détail des contributions réelles
- Liens GitHub/LinkedIn

---

### MCP Notion (/5)
- [ ] MCP installé et configuré (**2 pts**)
- [ ] Documentation mise à jour via Cursor (**2 pts**)
- [ ] Exemple de commande fonctionnel (**1 pt**)

**Comment valider** :
```
@notion Crée une page test
@notion Update changelog avec [info]
```

---

### Mise à Jour Automatique (/5)
- [ ] Changelog auto-généré (**3 pts**)
- [ ] Roadmap synchronisée (**2 pts**)

**Comment valider** :
- Montrer historique de mises à jour
- Prouver que c'est automatisé

---

## ⚙️ 2. CURSOR RULES (/25 points)

### .cursorrules Principal (/5)
- [ ] Fichier complet (**1 pt**)
- [ ] Config MCP (3 MCP) (**1 pt**)
- [ ] Contraintes techniques (**1 pt**)
- [ ] Architecture documentée (**1 pt**)
- [ ] Liens vers autres rules (**1 pt**)

**Comment valider** :
- Créer à la racine du projet
- Suivre le template fourni
- Tester avec Cursor

---

### .cursorrules-docs (/3)
- [ ] Fichier existe (**1 pt**)
- [ ] Règles de documentation (**1 pt**)
- [ ] Intégration Notion (**1 pt**)

---

### Rules par Fonctionnalité (/7)
- [ ] Au moins 2 fichiers `.cursorrules-[feature]` (**3 pts**)
- [ ] Contenu pertinent (**2 pts**)
- [ ] Utilisés pendant le dev (**2 pts**)

**Exemples** :
- `.cursorrules-auth`
- `.cursorrules-dashboard`
- `.cursorrules-api`

---

### .cursorrules-installation (/5)
- [ ] Fichier existe (**2 pts**)
- [ ] Commandes d'installation (**2 pts**)
- [ ] Facile pour un autre dev (**1 pt**)

**Comment valider** :
- Tester sur une machine vierge
- Suivre les instructions
- Doit installer en < 10 min

---

### Organisation (/5)
- [ ] Structure logique (**2 pts**)
- [ ] Commentaires clairs (**1 pt**)
- [ ] Évolution visible (**2 pts**)

**Comment valider** :
- Git history montre l'évolution
- Rules cohérentes entre elles

---

## 🔌 3. MCP & SYNCHRONISATION (/20 points)

### MCP Notion (/4)
- [ ] Installé (**1 pt**)
- [ ] Configuré (API key) (**1 pt**)
- [ ] Test connexion OK (**1 pt**)
- [ ] Documentation usage (**1 pt**)

**Test** : `@notion Create page test`

---

### MCP Supabase (/4)
- [ ] Installé (**1 pt**)
- [ ] Configuré (URL + keys) (**1 pt**)
- [ ] Test connexion OK (**1 pt**)
- [ ] Documentation usage (**1 pt**)

**Test** : `@supabase List tables`

---

### MCP Airtable (/4)
- [ ] Installé (**1 pt**)
- [ ] Configuré (API key + Base ID) (**1 pt**)
- [ ] Test connexion OK (**1 pt**)
- [ ] Documentation usage (**1 pt**)

**Test** : `@airtable List tables`

---

### Sync Airtable ↔ Supabase (/5)
- [ ] Extension Supabase installée (**1 pt**)
- [ ] Mapping correct (**2 pts**)
- [ ] Test INSERT OK (**1 pt**)
- [ ] Test UPDATE OK (**1 pt**)

**Comment valider** :
1. Insérer dans Airtable
2. Vérifier dans Supabase (< 5 sec)
3. Modifier dans Airtable
4. Vérifier sync dans Supabase

---

### Architecture Respectée (/3)
- [ ] App lit depuis Supabase uniquement (**2 pts**)
- [ ] Admin écrit dans Airtable uniquement (**1 pt**)

**Comment valider** :
- Code review : pas de `insert` vers Supabase
- Toutes les lectures via Supabase

---

## 🔐 4. AUTHENTIFICATION (/15 points)

### Auth Client (/10)
- [ ] Page Login (**2 pts**)
- [ ] Page Signup (**2 pts**)
- [ ] Logout fonctionnel (**2 pts**)
- [ ] Protected routes (**2 pts**)
- [ ] Session persistante (**2 pts**)

**Comment valider** :
1. S'inscrire → reçoit email
2. Se connecter → accède au dashboard
3. Refresh page → toujours connecté
4. Accès route protégée sans auth → redirect login
5. Logout → redirect home

---

### Protected Routes (/5)
- [ ] Implémentation correcte (**3 pts**)
- [ ] Redirection automatique (**2 pts**)

---

### 🎁 BONUS : Gestion Rôles (+3)
- [ ] Rôles différents (user/admin) (**+2 pts**)
- [ ] Permissions par rôle (**+1 pt**)

---

### 🎁 BONUS : OAuth (+5)
- [ ] Google et/ou Facebook (**+3 pts**)
- [ ] Configuration Supabase (**+2 pts**)

---

## 🗄️ 5. BDD & FONCTIONS (/15 points)

### Schema Airtable (/5)
- [ ] 3+ tables (**2 pts**)
- [ ] Relations configurées (**2 pts**)
- [ ] 15+ données par table (**1 pt**)

**Comment valider** :
- Compter les tables
- Vérifier les Linked Records
- Compter les entrées

---

### Fonctions PostgreSQL (/7)
- [ ] 2-3 fonctions créées (**3 pts**)
- [ ] Commentaires SQL (**2 pts**)
- [ ] Documentation Notion (**2 pts**)

**Comment valider** :
```sql
COMMENT ON FUNCTION get_user_data IS 'Description';
```

---

### Fonctions Utilisées (/3)
- [ ] Appelées depuis l'app (**3 pts**)

**Comment valider** :
```typescript
const { data } = await supabase.rpc('get_user_data', { ... });
```

---

### 🎁 BONUS : Dashboard Filtres (+5)
- [ ] Dashboard admin (**+2 pts**)
- [ ] Filtres PostgreSQL (**+2 pts**)
- [ ] Graphiques (**+1 pt**)

---

## 🚀 6. DÉPLOIEMENT (/10 points)

### Netlify (/7)
- [ ] URL fonctionnelle (**3 pts**)
- [ ] Build réussi (**2 pts**)
- [ ] Variables d'env configurées (**2 pts**)

**Comment valider** :
- Partager l'URL
- App accessible et fonctionne
- Pas d'erreurs en console

---

### Production (/3)
- [ ] `netlify.toml` correct (**2 pts**)
- [ ] Redirects SPA (**1 pt**)

---

### 🎁 BONUS : App Mobile (+7)
- [ ] Expo créée (**+3 pts**)
- [ ] Auth mobile OK (**+2 pts**)
- [ ] Features principales (**+2 pts**)

---

## 📦 7. GITHUB (/10 points)

### Repository (/3)
- [ ] Structure claire (**1 pt**)
- [ ] Nommage cohérent (**1 pt**)
- [ ] Pas de fichiers brouillon (**1 pt**)

---

### README (/3)
- [ ] 10 sections présentes (**2 pts**)
- [ ] Instructions claires (**1 pt**)

---

### Commits par Membre (/4)
- [ ] **TOUS les membres ont commit** (**4 pts**)

**Vérification** : `git shortlog -sn`

⚠️ **CRITIQUE** : 0 point si un membre n'a pas commit

---

## 🔄 8. WORKFLOWS (/5 points)

### Supabase Workflows (/5)
- [ ] 1-2 workflows configurés (**3 pts**)
- [ ] Triggers fonctionnels (**1 pt**)
- [ ] Actions pertinentes (**1 pt**)

**Exemples** :
```sql
CREATE TRIGGER after_user_signup
AFTER INSERT ON auth.users
FOR EACH ROW EXECUTE FUNCTION create_profile();
```

---

## 🎁 9. OUTILS COMPLÉMENTAIRES (BONUS)

### Integration (+5 max)
- [ ] Outil intégré (Make, n8n, etc.) (**+2 pts**)
- [ ] Intégration fonctionnelle (**+2 pts**)
- [ ] Documentation (**+1 pt**)

**Condition** : Justification claire de la valeur ajoutée

---

## 🧮 CALCUL DE VOTRE NOTE

### Formule
```
NOTE /20 = (Total points / 130) × 20 + (Bonus / 130) × 20
```

**Note plafonnée à 20/20**

### Exemples

**Projet Basique (98/130, pas de bonus)** :
```
Note = (98 / 130) × 20 = 15.08/20
```

**Projet Complet (122/130, +8 bonus)** :
```
Note = (122 / 130) × 20 + (8 / 130) × 20
Note = 18.77 + 1.23 = 20/20 ✅
```

**Projet Excellent (110/130, +15 bonus)** :
```
Note = (110/130) × 20 + (15/130) × 20
Note = 16.92 + 2.31 = 19.23/20
```

---

## ✅ OBJECTIFS PAR NIVEAU

### Pour avoir 12/20 (Minimum)
**~78 points requis**
- Documentation Notion basique (20/30)
- Cursor Rules présentes (15/25)
- 3 MCP installés (12/20)
- Auth basique (10/15)
- BDD avec données (10/15)
- App déployée (7/10)
- GitHub organisé (7/10)

### Pour avoir 15/20 (Bien)
**~98 points requis**
- Documentation Notion complète (25/30)
- Cursor Rules organisées (20/25)
- MCP + Sync fonctionnels (18/20)
- Auth complète (14/15)
- BDD + fonctions SQL (13/15)
- Déploiement propre (9/10)
- GitHub + commits tous membres (10/10)
- Workflows (3/5)

### Pour avoir 18/20+ (Excellent)
**~117 points + bonus**
- Tout complété
- Documentation exemplaire
- Cursor Rules avancées
- Fonctions SQL optimisées
- Au moins 2-3 bonus activés

---

## 📅 TIMELINE RECOMMANDÉE

**Jour 2** : Setup (20 pts)
- Cursor + MCP installés
- GitHub initialisé
- Notion structuré

**Jour 3** : Fondations (25 pts)
- BDD Airtable
- Sync Supabase
- Auth basique

**Jour 4** : Développement (30 pts)
- Features principales
- Cursor Rules par fonctionnalité
- Fonctions SQL

**Jour 5** : Finalisation (35 pts)
- Documentation complète
- Tests et debug
- Déploiement

**Jour 6** : Polish (20 pts)
- Derniers commits
- Vérification checklist
- Bonus si temps

---

## 💡 CONSEILS STRATÉGIQUES

### Prioriser
1. ✅ Faire tous les obligatoires d'abord
2. ✅ Viser 15/20 minimum
3. ✅ Bonus seulement si temps

### Répartir le Travail
- **Documentation** : 1 personne
- **Backend** : 1 personne
- **Frontend** : 1-2 personnes
- **Tous** : Au moins 1 commit chacun

### Éviter les Pièges
- ❌ Passer trop de temps sur les bonus
- ❌ Négliger la documentation
- ❌ Oublier que tous doivent commit
- ❌ Ne pas tester la sync régulièrement

---

## 📚 RESSOURCES

- [Checklist Auto-Évaluation](CHECKLIST_PROJET.md)
- [Système de Notation Détaillé](03-NOTATION-DETAILLEE.md)
- [Cours par Technologie](cours/)
- [Templates](templates/)

---

**Bonne chance ! 🚀**

**Questions** ? Consultez la documentation ou demandez au professeur.

