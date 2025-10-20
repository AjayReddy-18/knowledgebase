# Singleton Design Pattern - GoF Design Patterns

The **Singleton Pattern** is one of the **Creational Design Patterns** from the Gang of Four (GoF) catalog.

> **Definition:**  
> *Ensure a class has only one instance and provide a global point of access to it.*

The Singleton pattern is useful when exactly **one object is needed to coordinate actions across the system**.

---

## Key Points

- Only **one instance** of the class can exist.  
- Provides a **global access point** to that instance.  
- Often used for logging, configuration management, caching, thread pools, etc.  
- Can implement **lazy initialization** or **eager initialization**.

---

## Real-life Analogy

> Imagine a **President of a country**. There can be only **one president at a time**. Everyone in the country knows and accesses this single leader. Similarly, the Singleton pattern ensures only one instance of a class is used.

---

## Java Example - Lazy Initialization

```java
// Singleton class
public class Singleton {
    private static Singleton instance; // single instance

    // private constructor prevents instantiation from other classes
    private Singleton() {}

    // global access point
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton(); // lazy initialization
        }
        return instance;
    }

    public void showMessage() {
        System.out.println("Hello from Singleton!");
    }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        Singleton singleton1 = Singleton.getInstance();
        Singleton singleton2 = Singleton.getInstance();

        singleton1.showMessage();

        if (singleton1 == singleton2) {
            System.out.println("Both references point to the same instance.");
        }
    }
}
```

---

## Explanation

- **Private Constructor:** Prevents other classes from instantiating the Singleton class.  
- **Static Instance:** Holds the single instance of the class.  
- **Global Access Point (`getInstance()`):** Provides a way to get the single instance.  
- Lazy initialization ensures the instance is created only when it is needed.

---

## Benefits of Singleton Pattern

- Controlled access to the sole instance.  
- Reduces memory footprint since only one instance exists.  
- Can coordinate actions across the system.  
- Ensures consistency of shared resources.

---

## Variations

1. **Eager Initialization:** Instance is created at class loading time.  
2. **Thread-safe Singleton:** Ensures singleton works correctly in multithreaded environments (using `synchronized` or `volatile`).  
3. **Bill Pugh Singleton:** Uses static inner helper class for thread safety and lazy initialization.

---

## Summary

The Singleton pattern **ensures a class has only one instance** and **provides a global point of access**. It is widely used in scenarios where **a single shared resource or centralized management is required**.

