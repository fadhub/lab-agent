---
name: Configuration Environnement
description: Règles de configuration de l'environnement et respect du .gitignore.
---

# Configuration de l'Environnement

Ces règles définissent comment l'agent interagit avec l'environnement de développement.

## Respect du .gitignore
- **Strict Respect** : L'agent ne doit jamais modifier, ajouter ou lire des fichiers exclus par le fichier `.gitignore` (ex: `.env`, `vendor/`, `node_modules/`, `storage/*.log`).
- **Fichiers Sensibles** : Ne jamais exposer de clés API, mots de passe ou secrets dans le code source.

## Structure du Projet
- Respecter la structure standard de Laravel.
- Utiliser les chemins absolus pour les outils système si nécessaire, mais privilégier les chemins relatifs au projet pour le code.

## Dépendances
- Toujours vérifier si une dépendance est déjà installée avant de suggérer son installation.
- Utiliser `composer` pour le PHP et `npm` pour le JavaScript/CSS.
