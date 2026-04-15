# recipe-management

## Liste de fonctionnalités initiale

- Créer une recette
- Modifier une recette
- Supprimer une recette
- Voir une recette
- Rechercher une recette
- Filtrer les recettes par catégories
- Mettre une recette en favori
- Générer une liste de course à partir d'une recette
- Voir la liste de course
- Supprimer la liste de course
- Ajouter des ingrédients
- Modifier des ingrédients
- Supprimer des ingrédients
- Voir des ingrédients
- Authentification utilisateur
- créer un compte
- Supprimer un compte
- se connecter
- se déconnecter
- Modifier son profil utilisateur
- Partage de recettes entre utilisateurs
- voir les recettes partagées
- Notifications de nouvelles recettes
- Notification de partage

## Étape 1 — Regrouper par domaines métier

|Module        | Fonctionnalités incluses                     |
|---------------|---------------------------------------------|
| Recipe        | Créer, modifier, supprimer, filtrer, voir, rechercher, filtrer par catégories |
| Ingredients   | Ajouter, modifier, supprimer, voir |
| ShoppingList  | Générer depuis recette, supprimer, voir            |
| User          | Authentification, créer un compte, se connecter, se déconnecter, modifier profil, supprimer compte |
| Sharing       | Partage recettes, voir les recettes partagées    |
| Notification  | Nouvelle recette, Notification de partage                           |
| Favorite | Ajouter, Supprimer |


### Modules identifiés

- Recipe Module
- ShoppingList Module
- User Module
- Sharing Module
- Notification Module
- Favorite Module
- Ingredient Module

## Étape 2 — Identifier les entités métier

- Recipe
- ShoppingList
- User
- Sharing
- Notification
- Favorite
- Ingredient

```
class Recipe {
      Long id;
      String title;
      String description;
      List<Ingredient> ingredient;
      Category category;
      User author;
      Date createdAt;
      Date updatedAt;
}

enum Category {
      APPETIZERS,
      ENTREES,
      DISHES,
      DESSERTS
}

class Ingredient {
      Long id;
      String name;
      Unit unit;
      String quantity;
}

enum Unit {
      G,
      L
}

class ShoppingList {
      Long id;
      List<Ingredient> items;
      User owner;
      Recipe recipe;
}

class User {
    Long id;
    String username;
    String email;
    String password;
    String firstName;
    String lastName;
    Date createdAt;
}

class Sharing {
    Long id;
    User sender;
    User receiver;
    Recipe recipe;
    String permission;
    Date sharedAt;
}

class Notification {
    Long id;
    String message;
    String type;
    Date createdAt;
    Boolean isRead;
    User recipient;
}

class Favorite {
    Long id;
    User user;
    ResourceType type_resource;
    Long resourceId;
    Date created_at
}

enum ResourceType {
    RECIPE
}
```

### Diagramme de classe

![Diagramme](./diagramme.png)
### Étape 3 — Dériver les composants techniques

1. Créer une recette
Fonctionnalité : créer une recette
Interface d’entrée
— recevoir la demande de création d’une recette
Logique métier
— vérifier le titre, la catégorie et les ingrédients
Persistance
— enregistrer la recette en base

2. Modifier une recette
Fonctionnalité : modifier une recette
Interface d’entrée
— recevoir la demande de modification d’une recette
Logique métier
— vérifier que la recette existe et valider les nouvelles données
Persistance
— mettre à jour la recette en base

3. Supprimer une recette
Fonctionnalité : supprimer une recette
Interface d’entrée
— recevoir la demande de suppression d’une recette
Logique métier
— vérifier que la recette existe et que la suppression est autorisée
Persistance
— supprimer la recette de la base

4. Voir une recette
Fonctionnalité : voir une recette
Interface d’entrée
— recevoir la demande d’affichage d’une recette
Logique métier
— vérifier que la recette demandée existe
Persistance
— récupérer la recette depuis la base

5. Rechercher une recette
Fonctionnalité : rechercher une recette
Interface d’entrée
— recevoir la demande de recherche de recette
Logique métier
— interpréter le mot-clé de recherche
Persistance
— récupérer les recettes correspondantes en base

6. Filtrer les recettes par catégorie
Fonctionnalité : filtrer les recettes par catégorie
Interface d’entrée
— recevoir la demande de filtrage par catégorie
Logique métier
— vérifier la catégorie sélectionnée
Persistance
— récupérer les recettes de cette catégorie en base

7. Générer une liste de course
Fonctionnalité : générer une liste de course
Interface d’entrée
— recevoir la demande de génération d’une liste
Logique métier
— récupérer les ingrédients de la recette et construire la liste
Persistance
— enregistrer la liste de course en base

8. Voir la liste de course
Fonctionnalité : voir la liste de course
Interface d’entrée
— recevoir la demande d’affichage de la liste
Logique métier
— vérifier que la liste existe et appartient à l’utilisateur
Persistance
— récupérer la liste depuis la base

9. Créer un compte
Fonctionnalité : créer un compte
Interface d’entrée
— recevoir les informations d’inscription
Logique métier
— vérifier la validité des données et l’unicité de l’email
Persistance
— enregistrer le nouvel utilisateur en base

10. Se connecter
Fonctionnalité : se connecter
Interface d’entrée
— recevoir les identifiants de connexion
Logique métier
— vérifier l’email et le mot de passe
Persistance
— récupérer les informations utilisateur en base

11. Modifier son profil
Fonctionnalité : modifier son profil
Interface d’entrée
— recevoir la demande de modification du profil
Logique métier
— vérifier la cohérence des nouvelles informations
Persistance
— mettre à jour le profil en base

12. Partager une recette
Fonctionnalité : partager une recette
Interface d’entrée
— recevoir la demande de partage d’une recette
Logique métier
— vérifier la recette, l’expéditeur et le destinataire
Persistance
— enregistrer le partage en base

13. Voir les recettes partagées
Fonctionnalité : voir les recettes partagées
Interface d’entrée
— recevoir la demande d’affichage des recettes partagées
Logique métier
— récupérer les partages liés à l’utilisateur
Persistance
— lire les partages depuis la base

14. Ajouter une recette en favori
Fonctionnalité : ajouter une recette en favori
Interface d’entrée
— recevoir la demande d’ajout en favori
Logique métier
— vérifier que la recette existe et n’est pas déjà en favori
Persistance
— enregistrer le favori en base

15. Notification de partage
Fonctionnalité : notification de partage
Interface d’entrée
— déclencher l’envoi d’une notification après un partage
Logique métier
— générer le message de notification
Persistance
— enregistrer la notification en base
