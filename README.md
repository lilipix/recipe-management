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
| Recipe        | Créer, modifier, supprimer, filtrer, voir, rechercher, favoris, filtrer par catégories |
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
      List<String> ingredients;
      Category category;
      User author;
}

enum Category {
      APPETIZERS,
      ENTREES,
      DISHES,
      DESSERTS
  }

class ShoppingList {
      Long id;
      List<String> items;
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
    Recipe recipe;
    User user;
}
```
      
      
