# recipe-management

## Liste de fonctionnalités initiale

- Créer une recette
- Modifier une recette
- Supprimer une recette
- Voir une recette
- Rechercher une recette
- Filtrer les recettes par catégories
- Mettre une recette en favori
- Générer une liste à partir d'une recette
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
| Notification  | Nouvelle recette, partage de recettes                           |
| Favorite | Ajouter, Supprimer |


### Modules identifiés

- Recipe Module
- ShoppingList Module
- User Module
- Sharing Module
- Notification Module
- Favorite Module

## Étape 2 — Identifier les entités métier

- Recipe
- ShoppingList
- User
- Sharing
- Notification
- Favorite

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
      String<Unit> unit;
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
      
      
