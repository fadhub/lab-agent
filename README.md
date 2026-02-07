# Documentation du Dossier `.agent`

Ce projet utilise un dossier `.agent/` pour centraliser l'intelligence locale de l'assistant IA. Ce dossier définit comment l'agent doit coder, les outils qu'il maîtrise et les processus qu'il doit suivre.

## 🏗️ Structure Globale

Le dossier est divisé en trois piliers fondamentaux :

### 1. 📜 Rules (`.agent/rules/`)
Les **Rules** sont les directives permanentes. Elles définissent l'éthique de travail et les standards architecturaux.
- `00-config-environnement.md` : Gestion du `.gitignore`, sécurité des secrets et structure du projet.
- `01-identite-persona.md` : Définit l'agent comme un **Expert Laravel Pragmatique**.
- `02-stack-technique.md` : Impose l'architecture **3-Tier (MVC + Services)** et les principes SOLID/DRY.
- `03-qualite-securite.md` : Standards de sécurité (CSRF, XSS) et de validation des données.

### 2. 🛠️ Skills (`.agent/skills/`)
Les **Skills** sont des guides techniques que l'agent consulte pour implémenter des fonctionnalités spécifiques avec les meilleures pratiques.
- `laravel-basics/` : Principes fondamentaux du framework.
- `eloquent-orm/` : Gestion optimisée de la base de données.
- `tailwind-css/` & `preline/` : Système de design et composants UI.
- `alpinejs/` : Interactivité frontend légère.
- `lucide/` : Standard d'iconographie.
- `spatie/` : Intégration des packages essentiels de l'écosystème Laravel.

### 3. 🔄 Workflows (`.agent/workflows/`)
Les **Workflows** sont des processus automatisés ou guidés pour des tâches complexes.
- `create-crud-module.md` : Guide pas à pas pour générer un module CRUD complet (Migration → Modèle → Service → Contrôleur → Vues).

---

## 🚀 Comment l'utiliser ?
L'assistant IA lit automatiquement ces fichiers pour s'assurer que chaque ligne de code produite est cohérente avec les standards du projet. Si vous souhaitez modifier une règle ou ajouter un nouveau skill, faites-le directement dans ces dossiers.
