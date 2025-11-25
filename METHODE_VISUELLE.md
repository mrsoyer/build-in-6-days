# 🎯 MÉTHODE PÉDAGOGIQUE - VUE D'ENSEMBLE

> **One-pager : La méthode en un coup d'œil**

---

## 📊 FORMAT DE TRAVAIL

```
40 ÉTUDIANTS
     ↓
8 GROUPES DE 5
     ↓
8 PROJETS COMPLETS
```

### Pourquoi des groupes de 5 ?

| Taille | Avantages | Inconvénients |
|--------|-----------|---------------|
| **Individuel (40)** | Autonomie max | ❌ Impossible à gérer seul |
| **Binômes (20)** | Pair programming | ⚠️ 20 projets = charge lourde |
| **Groupes de 5 (8)** ✅ | Gérable + Production max | Risque free-riding (gérable) |

---

## 🏗️ COMPOSITION D'UN GROUPE

```
┌─────────────────────────────────────┐
│         GROUPE DE 5 ÉTUDIANTS        │
├─────────────────────────────────────┤
│ 1. Product Owner (rôle rotatif)     │
│ 2. Tech Lead (rôle rotatif)         │
│ 3. Developer Frontend (rotatif)     │
│ 4. Developer Backend (rotatif)      │
│ 5. Ops & Documentation (rotatif)    │
└─────────────────────────────────────┘

✅ Tous les rôles tournent à chaque séance
✅ Mix de niveaux : 1 fort + 2 moyens + 2 débutants
```

---

## 📚 APPROCHE PÉDAGOGIQUE

### 🔄 CLASSE INVERSÉE (Flipped Classroom)

```
AVANT LA SÉANCE (48h avant)          PENDANT LA SÉANCE (7h)
├─ Vidéo 10-15 min                   ├─ 100% pratique
├─ Tutoriels écrits                  ├─ Travail en groupe
├─ Quiz de préparation               ├─ Vous aidez quand bloqué
└─ Documentation                     └─ Démos + feedback
```

**Résultat** : +40% de rétention vs cours magistral

---

## ⏰ STRUCTURE D'UNE SÉANCE (7h)

```
9h30  ├─ Quiz recap (10 min)
      ├─ Clarifications (20 min)
      ├─ Daily Standup 8 groupes (15 min)
      │
10h15 ├─────────────────────────────────────┐
      │   TRAVAIL EN GROUPE (2h)            │
      │   • Vous faites le tour (15min/gp)  │
12h15 ├─────────────────────────────────────┘
      ├─ Checkpoint matin (15 min)
      │
12h30 ├─ PAUSE DÉJEUNER (1h)
      │
13h30 ├─ Théorie ou Expert Groups (30 min)
      │
14h00 ├─────────────────────────────────────┐
      │   PRODUCTION INTENSIVE (2h40)       │
      │   • Office hours (vous disponible)  │
16h40 ├─────────────────────────────────────┘
      ├─ Démos (4 groupes, 35 min)
17h15 ├─ Wrap-up (10 min)
17h25 ├─ Peer Assessment (5 min)
17h30 └─ FIN
```

---

## 🎓 MÉTHODE JIGSAW (Expert Groups)

### Exemple : Séance 4 avec 5 concepts techniques

```
PHASE 1 : EXPERT GROUPS (45 min)
┌──────────────┬──────────────┬──────────────┬──────────────┬──────────────┐
│ 8 étudiants  │ 8 étudiants  │ 8 étudiants  │ 8 étudiants  │ 8 étudiants  │
│ Experts      │ Experts      │ Experts      │ Experts      │ Experts      │
│ MCP Supabase │ MCP Notion   │ Sync Airtable│ Cursor Rules │ Auth Supabase│
└──────────────┴──────────────┴──────────────┴──────────────┴──────────────┘
       ↓              ↓              ↓              ↓              ↓

PHASE 2 : RETOUR AUX GROUPES PROJETS (60 min)
┌────────────────────────────────────────────────────────────────┐
│                    GROUPE PROJET 1                              │
├────────────────────────────────────────────────────────────────┤
│ • 1 expert MCP Supabase enseigne aux 4 autres (12 min)        │
│ • 1 expert MCP Notion enseigne aux 4 autres (12 min)          │
│ • 1 expert Sync Airtable enseigne aux 4 autres (12 min)       │
│ • 1 expert Cursor Rules enseigne aux 4 autres (12 min)        │
│ • 1 expert Auth Supabase enseigne aux 4 autres (12 min)       │
│ → Puis implémentation collective                               │
└────────────────────────────────────────────────────────────────┘
```

**Résultat** : Peer teaching = 90% de rétention vs 20% cours magistral

---

## 🛡️ ANTI-FREE-RIDING (Combat le parasitisme)

```
┌─────────────────────────────────────────────────────────────┐
│ 1. ✅ Commits Git individuels obligatoires (3-5/séance)     │
│ 2. ✅ Rôles rotatifs tracés (tableau de suivi)             │
│ 3. ✅ Peer Assessment après chaque séance                   │
│ 4. ✅ Interviews flash (vous interrogez aléatoirement)      │
│ 5. ✅ Team Charter signé (règles + conséquences)            │
│ 6. ✅ Démos rotatives (pas toujours le même qui présente)   │
└─────────────────────────────────────────────────────────────┘
```

### 📊 Calcul de la note individuelle :

```
Note finale = Note du groupe × Coefficient peer assessment

Coefficient = Moyenne peer assessment / 5

Exemple :
• Projet du groupe : 16/20
• Alice : peer assessment = 4.8/5 → Note = 16 × 0.96 = 15.4/20
• Bob : peer assessment = 3/5 → Note = 16 × 0.6 = 9.6/20
```

**Résultat** : -60% de free-riding

---

## 📊 OUTILS DE SUIVI EN TEMPS RÉEL

### 1. Kanban Board Collectif (Notion/Airtable)

```
┌────────┬─────────────────┬────────────┬──────────┬─────────┐
│ Groupe │ Tâche actuelle  │ Status     │ Bloqué ? │ Commits │
├────────┼─────────────────┼────────────┼──────────┼─────────┤
│ G1     │ Auth Supabase   │ In Progress│ Non      │ 3       │
│ G2     │ MCP Notion      │ Blocked    │ OUI 🚨   │ 1       │
│ G3     │ Landing Lovable │ Done ✅    │ Non      │ 5       │
└────────┴─────────────────┴────────────┴──────────┴─────────┘
```

→ **Vous priorisez les groupes "Blocked"**

### 2. Peer Assessment (Google Forms automatique)

```
Formulaire envoyé à 17h25 (anonyme)

Notez vos coéquipiers sur :
├─ Contribution technique (1-5)
├─ Implication (1-5)
├─ Collaboration (1-5)
└─ Autonomie (1-5)
```

---

## 🎯 PROGRESSIVE AUTONOMY (Échafaudage)

```
SÉANCES 1-2          SÉANCES 3-4          SÉANCES 5-6
Guidage fort         Semi-autonome        Autonomie totale
     │                    │                     │
     ├─ Tutos détaillés  ├─ Objectifs clairs   ├─ Vous = consultant
     ├─ Checkpoints 30min├─ Pas de tuto        ├─ Ils décident tout
     ├─ Vous circulez ++  ├─ Aide à la demande  ├─ Debug seuls IA
     └─ Démos fréquentes  └─ Solutions créatives└─ Prépa monde pro
```

**Résultat** : Développement progressif de l'autonomie

---

## 🔄 CODE REVIEW CROISÉE

### Séance 3-4 : Inter-groupes (45 min)

```
Groupe 1 ↔ Groupe 2
    │
    ├─ G1 présente son code à G2 (20 min)
    ├─ G2 présente son code à G1 (20 min)
    └─ Feedback écrit mutuel (5 min)
       • 3 points forts
       • 3 points d'amélioration
```

**Bénéfices** : 
- Apprendre en lisant code des autres
- Détection bugs/mauvaises pratiques
- Émulation positive

---

## 📈 FORMATION DES GROUPES (CRUCIAL)

### ❌ À ÉVITER :
```
• Laisser les étudiants se choisir
• Groupes d'amis
• Tirage au sort pur
```

### ✅ MÉTHODE RECOMMANDÉE :

```
1. QUESTIONNAIRE PRÉ-COURS (1 semaine avant)
   ├─ Niveau technique (1-5)
   ├─ Connaissances outils
   ├─ Préférences (dev/design/gestion)
   └─ Disponibilités

2. FORMATION STRATÉGIQUE (vous décidez)
   ├─ Chaque groupe = hétérogène
   │   • 1 étudiant niveau avancé
   │   • 2 étudiants niveau intermédiaire
   │   • 2 étudiants niveau débutant
   └─ Mix profils : technique + créatif + organisateur

3. TEAM CHARTER (Séance 1, 20 min)
   ├─ Règles de fonctionnement
   ├─ Objectifs communs
   ├─ Gestion des conflits
   └─ Signature de tous
```

---

## 📚 VALIDATION SCIENTIFIQUE

| Méthode | Source | Résultat |
|---------|--------|----------|
| **Groupes 4-6** | Michaelsen (Team-Based Learning) | Taille optimale |
| **Flipped Classroom** | Eric Mazur (Harvard) | +40% rétention |
| **Project-Based** | Buck Institute | +25% engagement |
| **Peer Learning** | Vygotsky | 90% rétention (vs 20%) |
| **Peer Assessment** | Black & Wiliam | -60% free-riding |
| **Jigsaw** | Aronson (1978) | Efficacité prouvée |

---

## ✅ POURQUOI ÇA MARCHE

### Pour VOUS (prof) :
```
✅ 8 projets au lieu de 40          → Gérable
✅ Kanban visible en temps réel     → Vous aidez où nécessaire
✅ Peer support entre groupes       → Scalable
✅ Tracking clair                   → Contrôle total
```

### Pour les ÉTUDIANTS :
```
✅ Peer teaching                    → Rétention 90%
✅ 5 cerveaux > 1                   → Production max
✅ Travail équipe                   → Professionnalisation
✅ Dynamique groupe                 → Motivation
✅ Autonomie progressive            → Prépa monde pro
```

### Pour les PROJETS :
```
✅ Plus de temps par projet         → Qualité ++
✅ Projets ambitieux possibles      → Complexité technique
✅ Brainstorming collectif          → Innovation
✅ Résilience (si 1 absent)         → Continuité
```

---

## 🎯 EN RÉSUMÉ : LA FORMULE GAGNANTE

```
GROUPES DE 5 (hétérogènes)
    +
CLASSE INVERSÉE (vidéos avant)
    +
PEER LEARNING (Jigsaw + Code review)
    +
PEER ASSESSMENT (anti-free-riding)
    +
PROGRESSIVE AUTONOMY (scaffolding)
    =
APPRENTISSAGE MAX + PRODUCTION MAX + GESTION RÉALISTE
```

---

## 📋 CHECKLIST RAPIDE

### Avant le cours :
- [ ] Questionnaire formation groupes
- [ ] Vidéos pré-séances (6 × 15 min)
- [ ] Setup Kanban + Dashboard + Peer assessment

### Chaque séance :
- [ ] Vidéo envoyée 48h avant
- [ ] Daily standup (15 min)
- [ ] Tour de table (15 min/groupe)
- [ ] Peer assessment en fin (5 min)

### Après chaque séance :
- [ ] Analyser peer assessments
- [ ] Vérifier commits GitHub
- [ ] Identifier étudiants en difficulté

---

**Version** : 1.0 - Vue d'ensemble visuelle  
**Date** : 29/10/2025


