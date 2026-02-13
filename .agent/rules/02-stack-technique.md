---
name: Stack Technique
description: Architecture MVC + Services (3-tier) et standards de développement.
---

# Stack Technique et Architecture

Règles architecturales strictes pour assurer la cohérence du projet.

## Architecture 3-Tier (MVC + Services)
1. **Modèles (Models)** : Représentent les données et les relations Eloquent. Ne contiennent pas de logique métier complexe.
2. **Services** : Classes dédiées dans `app/Services`. Elles contiennent la logique métier, les calculs, l'interaction avec des APIs tierces, etc.
3. **Contrôleurs (Controllers)** : Gèrent les requêtes HTTP. Injectent les Services nécessaires. Ils doivent rester "fins" (Thin Controllers).

## Principes de Développement
- **DRY (Don't Repeat Yourself)** : Extraire le code répétitif dans des traits, des helpers ou des classes dédiées.
- **SOLID** : Appliquer les principes SOLID pour garantir la flexibilité du code.
- **Type Hinting** : Utiliser systématiquement le typage PHP (arguments et retours de fonctions).

---
type: rule
id: stack-technique-2
---
# Stack Technique 2

## Backend
- **Framework** : Symfony (PHP).
- **Templating** : Twig.

## Frontend
- **Framework JS** : Vue.js.
- **CSS** : Bootstrap.
- **Build Tool** : Webpack.

## Architecture
- **SPA (Single-Page Application)** : Le rendu est fait côté client (Vue.js), avec des appels API pour les données.
- **Composants** : Utilisation de `v-bind` et `v-model` pour gérer l'état des composants UI (Formulaires, Modales, Listes dynamiques).

## Conventions
- Nommage des variables JS : snake_case.
- Organisation Vue : Utiliser des fichiers de composants séparés pour chaque UI, plutôt que de tout inliner dans le HTML.
