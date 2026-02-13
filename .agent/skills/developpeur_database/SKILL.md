---
name: Alpine.js
description: Lightweight JavaScript framework for adding interactivity to Laravel applications using Alpine.js.
---

# Alpine.js Skill

Use Alpine.js for lightweight frontend interactivity in Laravel Blade templates.

## Principles
- **Declarative**: Use `x-data`, `x-init`, and `x-show` to manage state directly in HTML.
- **Minimalist**: Keep logic simple. If it gets complex, consider a dedicated component or a different tool.

## Common Directives
- `x-data`: Define a component's state.
- `x-on` (or `@`): Listen for browser events.
- `x-bind` (or `:`): Bind attributes to expressions.
- `x-model`: Two-way data binding.

## Integration with Laravel
- Ideal for modals, dropdowns, and simple toggleable UI elements.

---

---
name: developpeur_database
description: Responsable de la conception, de l'évolution et de la fiabilité de la base de données, ainsi que de la gestion des entités et des jeux de données pour l'application.
---

# Compétence : Administration de Base de Données

## 🎯 Mission Principale
**But** : Assurer la robustesse, la cohérence et la performance du schéma de données à l'aide des outils du framework (migrations, ORM, scripts d'initialisation).

---

## ⛔ Principes Essentiels
- ❌ Ne jamais réécrire une migration déjà appliquée → privilégier la création d'une nouvelle migration pour chaque modification.
- 🔐 Protéger les entités avec des propriétés de type whitelist (ex: `$fillable`).
- 🏷️ Suivre les conventions de nommage du framework (tables au pluriel, entités au singulier).

---

## ⚡ Tâches Clés

### Tâche 1 : Évolution du Schéma (Migration)
**Situation** : Modifier ou créer la structure de la base de données  
**Détail** : Voir [ressources/capacité_migration.md](ressources/capacité_migration.md)

**Procédure :**
1. Générer une migration avec la commande adaptée
2. Définir les méthodes d'évolution et de retour arrière
3. Appliquer la migration
4. Vérifier la réversibilité

**Critère de succès** : Migration testée et réversible

---

### Tâche 2 : Création d'Entité (Modèle)
**Situation** : Représenter une table sous forme d'entité manipulable  
**Détail** : Voir [ressources/capacité_modele_eloquent.md](ressources/capacité_modele_eloquent.md)

**Procédure :**
1. Générer le modèle
2. Définir les champs autorisés à l'écriture
3. Ajouter les conversions de types si besoin
4. Déclarer les relations entre entités
5. Tester les opérations de base (création, modification, suppression)

**Critère de succès** : Modèle opérationnel avec relations fonctionnelles

---

### Tâche 3 : Remplissage de la Base (Seeders)
**Situation** : Ajouter des données d'exemple ou initiales  
**Détail** : Voir [ressources/capacité_seeders.md](ressources/capacité_seeders.md)

**Procédure :**
1. Créer un script d'insertion de données
2. Préparer les sources de données (CSV, existant, etc.)
3. Lire et traiter les données
4. Insérer dans la base
5. Lancer le script d'initialisation

**Critère de succès** : Données insérées et vérifiées

---

## 🔄 Exemple de Processus
1. Génération d'une migration pour une nouvelle table
2. Création du modèle correspondant
3. Ajout de données de test
4. Vérification avec l'exécution complète du processus (migration + seed)

---

## 📐 Conseils Pratiques
- Toujours inclure les champs de suivi temporel si possible
- Privilégier la clarté du code
- Tester chaque étape avant validation finale
