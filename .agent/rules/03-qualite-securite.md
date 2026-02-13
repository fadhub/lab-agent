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

---
type: rule
id: qualite-securite-2
---
# Qualité et Sécurité 2

## Qualité de Code
- **Clarté** : Les attributs Vue (`v-*`) doivent être clairs et concis.
- **Modularité** : Utiliser des composants Vue pour la logique réutilisable.
- **Isolation** : Les composants doivent être aussi isolés que possible du contexte global.

## Accessibilité (a11y)
- Utiliser les attributs ARIA appropriés pour les éléments interactifs créés avec Vue.js (ex: `aria-checked`, `aria-disabled` synchronisés avec `v-show` ou `v-bind`).
- S'assurer que les interactions sont accessibles au clavier.

## Sécurité
- **XSS** : Attention à l'utilisation de `v-html`. Ne jamais injecter de contenu non assaini.
- **CSRF** : S'assurer que les requêtes `axios` incluent le token CSRF de Symfony.
