# Factory Method Pattern - GoF Design Patterns

The **Factory Method Pattern** is a **Creational Design Pattern** from the Gang of Four (GoF) catalog.

> **Definition:**  
> *Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.*

This pattern promotes **loose coupling** by eliminating the need to bind application-specific classes into the code.

---

## Key Points

- Provides a **method to create objects** without specifying the exact class.  
- Subclasses decide which class to instantiate.  
- Supports **Open/Closed Principle** because the code can introduce new products without changing existing code.  
- Useful when a class cannot anticipate the class of objects it needs to create.

---

## Real-life Analogy

> Imagine a **document editor application** that can create different types of documents, such as `WordDocument` or `PDFDocument`.
> The editor does not need to know the exact class; it just calls a **factory method**, and the appropriate document type is created by subclasses.

---

## Java Example

```java
// Product interface
interface Product {
    void showProductType();
}

// Concrete Products
class WordDocument implements Product {
    @Override
    public void showProductType() {
        System.out.println("This is a Word Document");
    }
}

class PDFDocument implements Product {
    @Override
    public void showProductType() {
        System.out.println("This is a PDF Document");
    }
}

// Creator abstract class
abstract class DocumentCreator {
    public abstract Product createDocument();

    public void showDocument() {
        Product doc = createDocument();
        doc.showProductType();
    }
}

// Concrete Creators
class WordDocumentCreator extends DocumentCreator {
    @Override
    public Product createDocument() {
        return new WordDocument();
    }
}

class PDFDocumentCreator extends DocumentCreator {
    @Override
    public Product createDocument() {
        return new PDFDocument();
    }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        DocumentCreator wordCreator = new WordDocumentCreator();
        DocumentCreator pdfCreator = new PDFDocumentCreator();

        wordCreator.showDocument();
        pdfCreator.showDocument();
    }
}
```

---

## Explanation

- **Product Interface:** Defines the common interface for products.  
- **Concrete Products:** Implement the product interface (`WordDocument` and `PDFDocument`).  
- **DocumentCreator Abstract Class:** Declares the factory method (`createDocument`) and provides a method to use the product.  
- **Concrete Creators:** Override the factory method to instantiate specific products.
- The client code (`Main`) uses the abstract creator without knowing the concrete product class, promoting loose coupling.

---

## Benefits of Factory Method Pattern

- Reduces tight coupling between client code and concrete classes.  
- Adheres to Open/Closed Principle; new product types can be added without modifying existing code.  
- Encapsulates object creation logic.  
- Supports code maintainability and flexibility.

---

## Summary

The Factory Method pattern **provides a way to create objects without specifying the exact class**, allowing subclasses to determine which objects to instantiate. It is widely used in frameworks and libraries to provide flexibility and extensibility.

