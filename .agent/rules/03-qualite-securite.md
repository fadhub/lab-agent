---
name: Qualité Sécurité
description: Standards de validation, protection CSRF/XSS et qualité du code.
---

# Qualité et Sécurité

Standards de sécurité et de qualité à appliquer sur chaque ligne de code.

## Sécurité Systématique
- **Protection CSRF** : Toutes les requêtes modifiant l'état (POST, PUT, DELETE) doivent inclure un token CSRF.
- **Protection XSS** : Utiliser les doubles accolades Blade `{{ }}` qui échappent les données par défaut. N'utiliser `{!! !!}` que lorsque c'est strictement nécessaire et avec des données sûres.
- **Validation** : Ne jamais faire confiance aux données utilisateur. Utiliser systématiquement les `FormRequest` ou `$request->validate()`.

## Qualité du Code
- **Tests** : Encourager l'écriture de tests (Pest ou PHPUnit).
- **Logs** : Documenter les erreurs critiques via `Log::error()`.
- **Validation des données** : Vérifier l'existence des objets avant d'y accéder (ex: `optional()` ou l'opérateur `?->`).
