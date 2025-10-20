# Liskov Substitution Principle (LSP) - SOLID Principles

The **Liskov Substitution Principle (LSP)** is the **“L”** in SOLID principles.

> **Definition:**  
> *“Derived classes must be substitutable for their base classes without affecting the correctness of the program.”*  
> — Barbara Liskov, 1987

This principle ensures that a subclass can stand in for its parent class and that the program behaves as expected. Violating LSP can lead to unexpected behavior, bugs, or code that is difficult to maintain.

---

## Key Points

- Subtypes must be substitutable for their base types.
- Derived classes should extend functionality, not change expected behavior.
- Method signatures in derived classes should respect the base class contract.
- Avoid overriding methods in a way that breaks existing behavior.

---

## Real-life Analogy

> Think of a rectangle and a square. A rectangle can have any width and height, while a square has equal width and height.  
> If a square is used where a rectangle is expected, changing only the width or height may break the expected behavior, violating LSP.

---

## Java Example

```java
// Base class for shapes
class Rectangle {
    protected double width;
    protected double height;

    public Rectangle(double w, double h) {
        this.width = w;
        this.height = h;
    }

    public double area() {
        return width * height;
    }

    public double getWidth() { return width; }
    public double getHeight() { return height; }

    public void setWidth(double w) { this.width = w; }
    public void setHeight(double h) { this.height = h; }
}

// Derived class for squares
class Square extends Rectangle {
    public Square(double size) {
        super(size, size);
    }

    @Override
    public void setWidth(double w) {
        this.width = this.height = w; // Ensures both sides remain equal
    }

    @Override
    public void setHeight(double h) {
        this.width = this.height = h; // Ensures both sides remain equal
    }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        Rectangle rect = new Rectangle(5, 10);
        System.out.println("Rectangle area: " + rect.area());

        Rectangle square = new Square(5);
        square.setWidth(10);
        System.out.println("Square area: " + square.area()); // Behaves differently than Rectangle
    }
}
```

---

## Explanation

- **Rectangle Class:** Base class with width and height properties and methods to get/set dimensions.  
- **Square Class:** Subclass of Rectangle that overrides setters to maintain equal width and height.  
- **LSP Violation:** If code expects a `Rectangle`, using a `Square` may produce unexpected results when only width or height is changed.  
- **Correct LSP Usage:** Ensure that subclasses preserve expected behavior and do not break contracts defined by the base class.

---

## Benefits of LSP

- Ensures class hierarchies remain predictable and maintainable.  
- Reduces bugs caused by unexpected behavior in subclasses.  
- Supports polymorphism and safe code reuse.  
- Improves design quality by keeping subclass behavior consistent with the parent class.

---

## Summary

The Liskov Substitution Principle is about **ensuring that objects of a subclass can replace objects of the parent class without introducing errors or changing expected behavior**. Adhering to LSP helps maintain the integrity of your class hierarchies and makes your code more robust, reusable, and easier to maintain.