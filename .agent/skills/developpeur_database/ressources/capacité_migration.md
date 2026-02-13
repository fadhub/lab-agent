# Capacité : Concevoir et faire évoluer le schéma (Migrations)

🎯 Contexte
Les migrations permettent de piloter l'évolution du schéma de base de données comme on pilote du code : traçabilité, versioning et possibilité de revenir en arrière. Une fois appliquée en production, une migration doit être traitée comme immuable.

📋 Checklist avant toute création
- Le besoin est formalisé (diagramme ou description des champs)
- Aucune migration identique n'existe déjà
- Les relations et contraintes attendues sont identifiées
- Les impacts sur les données sont évalués

🔧 Procédure recommandée

Étape 1 — Analyser le besoin
- Quel(s) table(s) seront concernées ?
- S'agit‑il d'ajout, modification ou suppression de colonne(s) ?
- Types attendus : `string`, `integer`, `json`, `boolean`, etc.
- Contraintes : `unique`, `nullable`, `default`, `foreign key` ?

Étape 2 — Générer le squelette
Exemples de commandes :

```bash
php artisan make:migration create_users_table
# ou
php artisan make:migration add_email_to_users_table
```

Étape 3 — Écrire `up()` et `down()`
- `up()` : décrire l'opération (création de table, ajout de colonne, index…)
- `down()` : fournir l'opposé exact (drop, suppression de colonne)
- Veiller à ce que `down()` restaure l'état précédent (réversibilité complète)

Étape 4 — Valider localement
```bash
php artisan migrate
php artisan migrate:rollback
php artisan migrate  # ré-appliquer
```

⚠️ Points d'attention

À respecter impérativement
- ✅ Ajouter les index et contraintes nécessaires (`foreignId()->constrained()`, `->unique()`, `->index()`).
- ✅ Inclure `timestamps()` pour suivre les créations/modifs.
- ✅ Documenter précisément les colonnes non triviales (JSON, enum) et leur usage.
- ✅ Tester le `up()` et le `down()` en environnement de dev.

À ne surtout pas faire
- ❌ Modifier une migration déjà appliquée en production (créer une nouvelle migration à la place).
- ❌ Omettre `down()` ou laisser un `down()` incomplet.
- ❌ Nommer les migrations ou colonnes avec des noms vagues (`data`, `value`).
- ❌ Grouper trop de changements hétérogènes dans une seule migration.

💡 Cas d'usage fréquents
- Créer une table : `Schema::create()`
- Ajouter une colonne : `Schema::table()` + `$table->...`
- Modifier un type de colonne : utiliser les helpers de modification/pack supplémentaires si nécessaire
- Index/unique : définir directement sur la colonne (`->unique()`, `->index()`)
- Clé étrangère : `$table->foreignId('user_id')->constrained()`

✅ Critères de validation finale (avant commit)
- La migration s'applique sans erreur
- Le rollback s'effectue sans erreur
- La migration peut être ré-exécutée (idempotence du processus global)
- Le nom de fichier est explicite et descriptif
- Aucune donnée sensible ou codée en dur n'est insérée dans la migration

---

Si tu veux, je peux :
- adapter ce document au style de ton dépôt (format, emplacement exact),
- créer une checklist automatisée (script) pour vérifier `up()`/`down()`,
- ou générer un exemple concret de migration pour un cas précis.
Indique ce que tu préfères comme suite.
