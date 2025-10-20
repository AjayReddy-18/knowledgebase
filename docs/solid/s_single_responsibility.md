# S — Single Responsibility Principle (SRP)

## Introduction

The **Single Responsibility Principle (SRP)** is the first of the **SOLID** design principles proposed by Robert C. Martin (Uncle Bob).  
It states that:

> **A class should have only one reason to change.**

In simple terms — every class, module, or function should focus on doing **one thing** and doing it **well**.

---

## 1. Meaning and Intention

A *“reason to change”* usually means a *responsibility*.  
If a class handles multiple responsibilities — for example, both **data handling** and **UI rendering** — any change in either of those areas can cause unintended effects.

### 🧠 Core Idea

- Each module should focus on a **single concern**.  
- Reducing the number of reasons for change makes the system easier to maintain and extend.  
- SRP improves **clarity**, **testability**, and **reusability**.

---

## 2. Example — Without SRP

Consider this `Report` class:

```python
class Report:
    def __init__(self, data):
        self.data = data

    def generate_report(self):
        # Generates report data
        return f"Report data: {self.data}"

    def save_to_file(self, filename):
        # Handles file saving
        with open(filename, 'w') as f:
            f.write(self.generate_report())
        print("Report saved successfully!")
```

**What’s wrong?**

- This class does **two things**:
  1. Generates a report  
  2. Saves it to a file  

If file handling logic changes, we need to modify this same class — violating SRP.

---

## 3. Example — With SRP

Refactor it to separate responsibilities:

```python
class Report:
    def __init__(self, data):
        self.data = data

    def generate(self):
        return f"Report data: {self.data}"


class ReportSaver:
    def save_to_file(self, report: Report, filename):
        with open(filename, 'w') as f:
            f.write(report.generate())
        print("Report saved successfully!")
```

Now:
- `Report` is responsible for **data generation**
- `ReportSaver` is responsible for **persistence**

✅ Each class has **one reason to change**.

---

## 4. Why SRP Matters

| Benefit | Description |
|----------|--------------|
| **Maintainability** | Easier to locate and fix bugs in smaller, focused classes |
| **Reusability** | Independent components can be reused in other systems |
| **Testability** | Easier to unit-test smaller, single-purpose classes |
| **Scalability** | New features can be added without breaking existing logic |

---

## 5. When to Apply SRP

Use SRP when:
- You notice a class changing for **multiple reasons**
- Different parts of your system are affected by changes in **one large class**
- You want to **reduce coupling** between unrelated concerns

SRP is a **guideline**, not an absolute rule — sometimes minor overlap is acceptable if separation would overcomplicate the design.

---

## 6. Real-World Analogy

Think of SRP like a restaurant:

- The **chef** cooks.
- The **waiter** serves.
- The **cashier** handles billing.

If one person did all three jobs, it would quickly lead to confusion and inefficiency — the same happens in software without SRP.

---

## Summary

- SRP keeps your code **clean, modular, and adaptable**.  
- Each class should **do one thing** and **do it well**.  
- Following SRP reduces bugs and simplifies future maintenance.

---

*Last updated: October 2025*  
*Tags: solid, design-principles, srp, clean-code*
