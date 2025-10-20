# Interface Segregation Principle (ISP) - SOLID Principles

The **Interface Segregation Principle (ISP)** is the **“I”** in SOLID principles.

> **Definition:**  
> *“Clients should not be forced to depend on interfaces they do not use.”*

This principle encourages creating **small, client-specific interfaces** rather than large, general-purpose ones. It is similar to the Single Responsibility Principle but applies to interfaces. Following ISP helps reduce side effects and unnecessary code changes.

---

## Key Points

- Avoid “fat” interfaces; prefer multiple small, specific interfaces.  
- Clients should implement only the methods that are relevant to them.  
- Enhances modularity and reduces coupling between components.
- Makes code easier to maintain and extend.

---

## Real-life Analogy

> Imagine a restaurant serving multiple types of customers: vegetarians, non-vegetarians, and drink lovers.
> Instead of giving all customers the same menu, provide separate menus for each type. Vegetarians shouldn’t see non-vegetarian items, and vice versa.
> This reduces confusion and avoids forcing customers to deal with irrelevant options.

---

## Java Example

```java
import java.util.*;

// Interface for vegetarian menu
interface IVegetarianMenu {
    List<String> getVegetarianItems();
}

// Interface for non-vegetarian menu
interface INonVegetarianMenu {
    List<String> getNonVegetarianItems();
}

// Interface for drinks menu
interface IDrinkMenu {
    List<String> getDrinkItems();
}

// Class for vegetarian menu
class VegetarianMenu implements IVegetarianMenu {
    public List<String> getVegetarianItems() {
        return Arrays.asList("Vegetable Curry", "Paneer Tikka", "Salad");
    }
}

// Class for non-vegetarian menu
class NonVegetarianMenu implements INonVegetarianMenu {
    public List<String> getNonVegetarianItems() {
        return Arrays.asList("Chicken Curry", "Fish Fry", "Mutton Biryani");
    }
}

// Class for drinks menu
class DrinkMenu implements IDrinkMenu {
    public List<String> getDrinkItems() {
        return Arrays.asList("Water", "Soda", "Juice");
    }
}

// Menu display functions
class MenuDisplay {
    public static void displayVegetarianMenu(IVegetarianMenu menu) {
        System.out.println("Vegetarian Menu:");
        for (String item : menu.getVegetarianItems()) {
            System.out.println("- " + item);
        }
    }

    public static void displayNonVegetarianMenu(INonVegetarianMenu menu) {
        System.out.println("Non-Vegetarian Menu:");
        for (String item : menu.getNonVegetarianItems()) {
            System.out.println("- " + item);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        VegetarianMenu vegMenu = new VegetarianMenu();
        NonVegetarianMenu nonVegMenu = new NonVegetarianMenu();
        DrinkMenu drinkMenu = new DrinkMenu();

        MenuDisplay.displayVegetarianMenu(vegMenu);
        MenuDisplay.displayNonVegetarianMenu(nonVegMenu);
    }
}
```

---

## Explanation

- **IVegetarianMenu, INonVegetarianMenu, IDrinkMenu:** Small, focused interfaces for specific client needs.  
- **VegetarianMenu, NonVegetarianMenu, DrinkMenu:** Implement only the methods relevant to their category.  
- Avoids forcing clients to implement unrelated methods, following ISP.
- **MenuDisplay class:** Demonstrates using the interfaces without depending on unrelated items.

---

## Benefits of ISP

- Reduces coupling between modules.  
- Prevents clients from being forced to implement irrelevant methods.  
- Easier to maintain, extend, and refactor code.  
- Supports flexible and modular design, making software more robust.

---

## Summary

The Interface Segregation Principle promotes creating multiple **small and specific interfaces** instead of a single large one. Clients only implement what they need, improving clarity, modularity, and maintainability of the code.

