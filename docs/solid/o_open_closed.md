# O — Open/Closed Principle (OCP)

## Introduction

The **Open/Closed Principle (OCP)** is the second principle in the **SOLID** design principles.  
It was first introduced by **Bertrand Meyer** and later popularized by **Robert C. Martin (Uncle Bob)**.

> **Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.**

In other words, we should be able to **add new functionality** to a system **without changing existing code**.

---

## 1. Meaning and Intention

- **Open for extension:** You can add new behavior when requirements change.  
- **Closed for modification:** You don’t need to alter existing, tested code.

This helps in writing code that’s **maintainable**, **scalable**, and **resilient to change**.

---

## 2. Example — Without OCP

Consider a simple example where we calculate area for shapes:

```java
class Rectangle {
    public double width;
    public double height;
}

class Circle {
    public double radius;
}

class AreaCalculator {
    public double calculateArea(Object shape) {
        if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.width * r.height;
        } else if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return Math.PI * c.radius * c.radius;
        }
        return 0;
    }
}
```

**Problem:**  
Whenever a new shape is added (like `Triangle`), we must modify `AreaCalculator` — violating OCP.

---

## 3. Example — With OCP

Refactor the code using **abstraction** and **polymorphism**:

```java
interface Shape {
    double area();
}

class Rectangle implements Shape {
    double width, height;
    Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    public double area() {
        return width * height;
    }
}

class Circle implements Shape {
    double radius;
    Circle(double radius) {
        this.radius = radius;
    }
    public double area() {
        return Math.PI * radius * radius;
    }
}

class AreaCalculator {
    public double calculateArea(Shape shape) {
        return shape.area();
    }
}
```

Now, adding a new shape (like `Triangle`) requires **no changes** to `AreaCalculator`.  
You simply **extend** the system by creating a new class implementing `Shape`.

✅ **Open for extension, closed for modification.**

---

## 4. Why OCP Matters

| Benefit | Description |
|----------|--------------|
| **Stability** | Reduces risk of breaking existing functionality |
| **Extensibility** | New behavior can be added easily |
| **Maintainability** | Code changes are localized to new modules |
| **Reusability** | Base abstractions can be reused across the system |

---

## 5. When to Apply OCP

Apply OCP when:
- You expect frequent changes or new features in a specific area.
- You can identify a clear abstraction or interface boundary.
- You want to **add behavior** without modifying core logic.

> Overusing OCP can make code unnecessarily complex — apply it where extensibility is truly valuable.

---

## 6. Real-World Analogy

Think of a **power outlet** — you can plug in new devices (extensions) without modifying the socket (core logic).  
The interface remains the same, but you gain new functionality by adding new devices.

---

## Summary

- OCP promotes **scalable and flexible design**.  
- Add new functionality via **extension**, not modification.  
- Use **interfaces** or **abstract classes** to enable extensibility.

---

*Last updated: October 2025*  
*Tags: solid, design-principles, ocp, clean-code*
