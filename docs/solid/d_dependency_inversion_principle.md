# Dependency Inversion Principle (DIP) - SOLID Principles

The **Dependency Inversion Principle (DIP)** is the **“D”** in SOLID principles.

> **Definition:**  
> *“High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.”*

This principle emphasizes **relying on abstractions (interfaces or abstract classes)** rather than concrete implementations. It allows high-level code to remain flexible and decoupled from specific implementations.

---

## Key Points

- High-level modules should not depend on low-level modules directly.  
- Both high-level and low-level modules should depend on abstractions.  
- Abstractions should be stable and independent of implementation details.  
- Encourages decoupled, flexible, and maintainable code.

---

## Real-life Analogy

> In a software team, developers rely on an abstract version control system (like Git) rather than the specific implementation details. They can work with Git, Mercurial, or any version control system without changing how they write code.

---

## Java Example

```java
// Interface for version control system
interface IVersionControl {
    void commit(String message);
    void push();
    void pull();
}

// Git version control implementation
class GitVersionControl implements IVersionControl {
    @Override
    public void commit(String message) {
        System.out.println("Committing changes to Git with message: " + message);
    }

    @Override
    public void push() {
        System.out.println("Pushing changes to remote Git repository.");
    }

    @Override
    public void pull() {
        System.out.println("Pulling changes from remote Git repository.");
    }
}

// Development team class that relies on IVersionControl abstraction
class DevelopmentTeam {
    private IVersionControl versionControl;

    public DevelopmentTeam(IVersionControl vc) {
        this.versionControl = vc;
    }

    public void makeCommit(String message) {
        versionControl.commit(message);
    }

    public void performPush() {
        versionControl.push();
    }

    public void performPull() {
        versionControl.pull();
    }
}

public class Main {
    public static void main(String[] args) {
        GitVersionControl git = new GitVersionControl();
        DevelopmentTeam team = new DevelopmentTeam(git);

        team.makeCommit("Initial commit");
        team.performPush();
        team.performPull();
    }
}
```

---

## Explanation

- **IVersionControl Interface:** Defines operations like `commit`, `push`, and `pull`. High-level code depends on this abstraction.  
- **GitVersionControl Class:** Implements the interface, providing specific functionality for Git.  
- **DevelopmentTeam Class:** Uses `IVersionControl` instead of a concrete class, enabling flexibility to switch version control systems without modifying the team class.
- DIP ensures high-level modules are decoupled from low-level modules.

---

## Benefits of DIP

- Promotes loose coupling between high-level and low-level modules.  
- Makes the system more flexible and easier to extend.  
- Encourages coding to abstractions rather than concrete implementations.  
- Reduces ripple effects of changes in low-level modules.

---

## Summary

The Dependency Inversion Principle ensures **high-level modules depend on abstractions, not concrete implementations**, making software more maintainable, flexible, and resilient to change. Adhering to DIP helps decouple code and promotes reusable, modular design.