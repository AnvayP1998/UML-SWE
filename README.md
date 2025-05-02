# PantryPal UML Class Diagram

Below is the class diagram for the PantryPal system, rendered via Mermaid.

```mermaid
classDiagram
  class User {
    - userId: String
    - username: String
    - email: String
    + login(): Boolean
    + logout(): void
  }
  class PantryItem {
    - itemId: String
    - name: String
    - quantity: Integer
    + addQuantity(n: Integer): void
    + removeQuantity(n: Integer): void
  }
  class Recipe {
    - recipeId: String
    - title: String
    - ingredients: List<String>
    + generateInstructions(): String
  }
  class ShoppingList {
    - listId: String
    - items: List<PantryItem>
    + addItem(item: PantryItem): void
    + removeItem(item: PantryItem): void
  }
  class RecommendationEngine {
    + recommendRecipes(pantry: List<PantryItem>): List<Recipe>
  }

  User "1" -- "*" PantryItem : owns
  User "1" -- "1" ShoppingList : manages
  ShoppingList "1" *-- "*" PantryItem
  Recipe "0..*" --> PantryItem : uses
  RecommendationEngine --> PantryItem : reads
  RecommendationEngine --> Recipe : outputs
