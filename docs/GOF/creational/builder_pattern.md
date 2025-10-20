# Builder Design Pattern - GoF Design Patterns

The **Builder Pattern** is a **Creational Design Pattern** from the Gang of Four (GoF) catalog.

> **Definition:**  
> *Separate the construction of a complex object from its representation, allowing the same construction process to create different representations.*

The Builder pattern is used when creating complex objects step by step and allows the creation process to be **independent of the parts that make up the object**.

---

## Key Points

- Separates **construction** from **representation**.  
- Provides a step-by-step approach to build a complex object.  
- Useful for objects with many optional or mandatory attributes.  
- Promotes **fluent interfaces** for better readability.

---

## Real-life Analogy

> Imagine building a **custom computer**. You can select different CPU, RAM, storage, GPU, and other components. The **builder** guides you through a step-by-step process, and at the end, you get a complete computer. Different selections lead to different representations of the final product.

---

## Java Example

```java
// Product class
class Computer {
    private String CPU;
    private String RAM;
    private String storage;
    private boolean graphicsCard;

    // setters for each part
    public void setCPU(String CPU) { this.CPU = CPU; }
    public void setRAM(String RAM) { this.RAM = RAM; }
    public void setStorage(String storage) { this.storage = storage; }
    public void setGraphicsCard(boolean graphicsCard) { this.graphicsCard = graphicsCard; }

    @Override
    public String toString() {
        return "Computer [CPU=" + CPU + ", RAM=" + RAM + ", Storage=" + storage + ", GraphicsCard=" + graphicsCard + "]";
    }
}

// Builder interface
interface ComputerBuilder {
    void buildCPU();
    void buildRAM();
    void buildStorage();
    void buildGraphicsCard();
    Computer getComputer();
}

// Concrete Builder
class GamingComputerBuilder implements ComputerBuilder {
    private Computer computer = new Computer();

    @Override
    public void buildCPU() { computer.setCPU("Intel i9"); }

    @Override
    public void buildRAM() { computer.setRAM("32GB"); }

    @Override
    public void buildStorage() { computer.setStorage("1TB SSD"); }

    @Override
    public void buildGraphicsCard() { computer.setGraphicsCard(true); }

    @Override
    public Computer getComputer() { return computer; }
}

// Director class
class ComputerDirector {
    private ComputerBuilder builder;

    public ComputerDirector(ComputerBuilder builder) {
        this.builder = builder;
    }

    public Computer constructComputer() {
        builder.buildCPU();
        builder.buildRAM();
        builder.buildStorage();
        builder.buildGraphicsCard();
        return builder.getComputer();
    }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        ComputerBuilder builder = new GamingComputerBuilder();
        ComputerDirector director = new ComputerDirector(builder);
        Computer computer = director.constructComputer();

        System.out.println(computer);
    }
}
```

---

## Explanation

- **Computer Class (Product):** Represents the complex object to be built.  
- **ComputerBuilder Interface:** Declares steps to build the product.  
- **GamingComputerBuilder (Concrete Builder):** Implements the steps for building a specific computer.  
- **ComputerDirector:** Controls the construction process and returns the final product.  
- This separation of construction and representation allows different builders to create different types of computers using the same process.

---

## Benefits of Builder Pattern

- Constructs complex objects step by step.  
- Promotes code readability and maintainability.  
- Supports creating different representations of the same product.  
- Avoids constructor telescoping (many constructors with different parameters).

---

## Summary

The Builder pattern **separates object construction from its representation**, providing a flexible way to create complex objects. It is widely used for building objects with multiple optional attributes or configurations.

