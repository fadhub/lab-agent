# Capacité : Alimenter la base (Seeders)

🎯 Contexte
Les seeders permettent de peupler la base avec des jeux de données utiles pour le développement, les tests ou l'initialisation d'un environnement. Ils doivent être reproductibles, sûrs et évitables en production si nécessaire.

📋 Checklist préalable
- Le schéma cible existe (migrations appliquées)
- Les factories nécessaires sont disponibles
- Les données sensibles ne sont pas incluses en clair
- Le comportement est idempotent ou documenté

🔧 Procédure recommandée

Étape 1 — Préparer les sources de données
- Privilégier les `Factory` Laravel pour générer des données réalistes.
- Si import depuis CSV/externes, documenter le format et vérifier l'encodage.

Étape 2 — Générer un seeder

```bash
php artisan make:seeder UserSeeder
# exécution ciblée
php artisan db:seed --class=UserSeeder
```

Étape 3 — Implémenter le seeder
- Utiliser les `Model::factory()` pour créer des enregistrements.
- Prévoir des options pour mode `dev/test` vs `prod` (par ex. variable d’environnement).
- Éviter d’écraser des données réelles en production : utiliser des conditions ou flags.

Exemple succinct :

```php
public function run()
{
    // créer 50 utilisateurs fictifs
    User::factory()->count(50)->create();

    // ou importer depuis un CSV sans écraser les enregistrements existants
    // collect(Storage::disk('local')->get('users.csv')->lines())->each(...)
}
```

Étape 4 — Valider et exécuter
```bash
php artisan db:seed --class=UserSeeder
php artisan db:seed  # exécute DatabaseSeeder
```

⚠️ Points de vigilance

À faire
- ✅ Utiliser `factories` pour garder les seeders simples et testables.
- ✅ Vérifier l'absence de données sensibles en clair.
- ✅ Documenter la provenance des jeux de données (CSV, API, générés).
- ✅ Rendre les seeders idempotents ou prévoir une étape d'effacement explicite.

À éviter
- ❌ Insérer des données de production sensibles via un seeder.
- ❌ Ecrire des seeders non réentrants qui provoquent des doublons.
- ❌ Exécuter des seeders destructeurs directement en production sans garde-fous.

💡 Bonnes pratiques
- Centraliser la logique de génération dans des `Factory`.
- Proposer des flags d'exécution (`--env=local`), ou vérifier `app()->environment()`.
- Pour des imports volumineux, utiliser des jobs/queues afin d’éviter des timeouts.
- Versionner les fichiers sources (CSV) si pertinents pour la traçabilité.

✅ Critères de validation
- Le seeder s'exécute sans erreur
- Le seeder peut être relancé sans produire d'effets indésirables (ou son comportement est documenté)
- Les données insérées sont cohérentes avec le schéma et les contraintes
- Aucune donnée sensible n'est exposée

---

Souhaites‑tu que je génère un exemple concret (`UserSeeder` + `UserFactory`) dans le projet ?
