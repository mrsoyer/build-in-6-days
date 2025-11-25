# 📚 COURS : GITHUB

> Versioning et collaboration

---

## 🎯 OBJECTIFS

1. Initialiser un repository
2. Structurer le projet
3. Commits et collaboration
4. README complet

---

## 🚀 INITIALISATION

### Créer le Repository

**GitHub** :
1. https://github.com → New repository
2. Nom : `project-name`
3. Public/Private
4. Add README, .gitignore (Node)

**Local** :
```bash
git clone https://github.com/username/project-name.git
cd project-name
```

Ou initialiser localement :
```bash
git init
git remote add origin https://github.com/username/project-name.git
```

---

## 📂 STRUCTURE RECOMMANDÉE

```
project-name/
├── .cursorrules
├── .cursorrules-*
├── .env.example
├── .gitignore
├── README.md
├── package.json
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── utils/
│   ├── types/
│   └── config/
├── public/
└── docs/
```

### .gitignore

```
# Dependencies
node_modules/

# Build
dist/
build/

# Env
.env
.env.local

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db

# Logs
*.log
```

---

## 📝 README COMPLET

### Template

```markdown
# [Project Name]

## 📖 Description
[Problème résolu + solution]

## ✨ Features
- Feature 1
- Feature 2
- Feature 3

## 🛠️ Stack Technique
- Frontend: React + TypeScript + Tailwind
- Backend: Supabase (PostgreSQL + Auth)
- Database: Airtable (admin) + Supabase (app)
- Deployment: Netlify

## 🚀 Installation

### Prerequisites
- Node.js >= 18
- npm >= 9

### Steps
\`\`\`bash
git clone [URL]
cd project-name
npm install
cp .env.example .env
# Configure .env
npm run dev
\`\`\`

## 🔧 Environment Variables
\`\`\`env
VITE_SUPABASE_URL=
VITE_SUPABASE_ANON_KEY=
\`\`\`

## 📖 Usage
[Instructions d'utilisation]

## 🏗️ Architecture
[Schema ou description]

## 👥 Team
- **Alice** - Frontend Lead
- **Bob** - Backend
- **Charlie** - Design
- **David** - PM

## 📄 License
MIT
```

---

## 💾 WORKFLOW GIT

### Commits

**Format** :
```bash
git add .
git commit -m "feat: add user authentication"
git push origin main
```

**Convention** :
- `feat:` Nouvelle feature
- `fix:` Bug fix
- `docs:` Documentation
- `style:` Formatting
- `refactor:` Refactoring
- `test:` Tests

### Branches (Optionnel)

```bash
git checkout -b feature/auth
# Work...
git add .
git commit -m "feat: add login page"
git push origin feature/auth
# Create PR on GitHub
```

---

## 👥 COLLABORATION

### Tous les Membres Doivent Commit

**Vérification** :
```bash
git shortlog -sn --all
```

**Stratégie** :
- Diviser les tâches clairement
- Chaque membre travaille sur ses fichiers
- Commits réguliers

**Exemple répartition** :
- Alice : `src/components/`
- Bob : `src/api/`
- Charlie : `src/pages/`
- David : `docs/`, `README.md`

---

## 🧪 EXERCICE

1. Créer repository GitHub
2. Clone localement
3. Structure de base
4. README complet
5. Chaque membre fait 1 commit
6. Vérifier avec `git shortlog`

---

## ✅ VALIDATION

- [ ] Repository créé
- [ ] Structure organisée
- [ ] README complet (10 sections)
- [ ] .gitignore configuré
- [ ] Tous les membres ont commit (min 1)

---

**Durée** : 1h  
**Niveau** : Débutant  
**Version** : 1.0

