# Capacité : Définir et maintenir un Modèle Eloquent

🎯 Contexte
Le modèle Eloquent représente la couche d'accès aux données dans l'application. Il doit garantir intégrité, sécurité et simplicité d'utilisation pour les opérations CRUD et les relations entre entités.

📋 Pré-requis avant création
- Schéma de la table défini (migrations existantes ou planifiées)
- Liste des champs et types disponibles
- Contraintes (unicité, clés étrangères) et règles métiers connues
- Besoin en relations et chargement (eager/lazy)

🔧 Étapes pratiques

Étape 1 — Générer le modèle
- Commande :

```bash
php artisan make:model NomDuModele
# ou avec migration
php artisan make:model NomDuModele -m
```

Étape 2 — Protéger l'assignation de masse
- Définir les champs autorisés :

```php
protected $fillable = ['title','content','user_id'];
```

- Ou utiliser `$guarded = ['id']` si on préfère whitelist inverse.

Étape 3 — Types et conversions
- Utiliser `$casts` pour garantir les types :

```php
protected $casts = [
  'is_active' => 'boolean',
  'metadata' => 'array',
  'published_at' => 'datetime',
];
```

Étape 4 — Relations et méthodes utilitaires
- Déclarer `belongsTo`, `hasMany`, `belongsToMany`, etc.
- Ajouter méthodes d'accès (scopes, accessors, mutators) pour encapsuler la logique récurrente :

```php
public function scopePublished($query) {
  return $query->whereNotNull('published_at');
}

public function getFullNameAttribute() {
  return "$this->first_name $this->last_name";
}
```

Étape 5 — Factories et Seeders
- Créer une `Factory` pour faciliter les tests et le développement :

```bash
php artisan make:factory NomDuModeleFactory --model=NomDuModele
```

Étape 6 — Tests et validation
- Tester les méthodes majeures : création, mise à jour, relations, scopes et casts.
- Vérifier la protection mass-assignment via tests d'intégration.

⚠️ Points de vigilance

À faire systématiquement
- ✅ Restreindre `$fillable` ou définir `$guarded` correctement.
- ✅ Cacher les attributs sensibles avec `$hidden` (passwords, tokens).
- ✅ Utiliser `$visible` si nécessaire pour contrôler l'API exposée.
- ✅ Documenter les relations complexes et les attributs castés.

À éviter
- ❌ Mettre de la logique métier lourde directement dans le modèle (préférer Services ou Domain objects).
- ❌ Exposer des données sensibles par inadvertance (ne pas oublier `$hidden`).
- ❌ Utiliser `->toArray()` sans filtrer les champs dans les réponses publiques.

💡 Bonnes pratiques et optimisation
- Préférer les Scopes réutilisables plutôt que des requêtes dupliquées.
- Favoriser l'eager loading (`with()`) pour éviter le N+1.
- Garder les modèles simples : extraire validations/transformations complexes hors du modèle.
- Documenter les events model (`creating`, `updating`) si utilisés.

✅ Critères d'acceptation
- Le modèle gère les opérations CRUD attendues.
- Les relations sont correctes et testées.
- Les casts convertissent correctement les valeurs.
- La protection mass-assignment empêche l'écriture non autorisée.
- La factory permet de générer des jeux de données fiables pour les tests.

---

Souhaites‑tu que je génère un exemple concret (`User`, `Post`, etc.) et des tests correspondants ?
