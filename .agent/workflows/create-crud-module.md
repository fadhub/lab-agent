---
description: Création d'un module CRUD complet (Migration → Modèle → Service → Contrôleur → Vues)
---

# Workflow: Création d'un module CRUD

Ce processus guide l'agent dans la génération d'un module complet pour une entité Laravel.

## Étapes

1. **Générer la Migration**
   - Créer une migration avec `php artisan make:migration create_[table]_table`.
   - Définir les colonnes (string, text, boolean, foreignId, etc.).

2. **Créer le Modèle**
   - Créer le modèle Eloquent dans `app/Models/`.
   - Définir `$fillable` et les relations.

3. **Créer le Service**
   - Créer une classe Service dans `app/Services/` pour gérer la logique métier (Store, Update, Delete).

4. **Créer le Contrôleur**
   - Créer un contrôleur de ressources avec `php artisan make:controller [Name]Controller --resource`.
   - Injecter le Service dans le constructeur.

5. **Définir les Routes**
   - Ajouter `Route::resource('[path]', [Name]Controller::class);` dans `routes/web.php`.

6. **Créer les Vues (Blade + Tailwind + Preline)**
   - `index.blade.php`: Table de données.
   - `create.blade.php`: Formulaire de création.
   - `edit.blade.php`: Formulaire de modification.
   - `show.blade.php`: Détails.

7. **Validation**
   - Créer des Form Requests pour la validation : `php artisan make:request Store[Name]Request`.
