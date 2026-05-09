# SOLID Principles

The **SOLID** principles are five design principles intended to make software designs more understandable, flexible, and maintainable.

## 1. Single Responsibility Principle (SRP)
> "A class should have one, and only one, reason to change."

Each module or class should have responsibility over a single part of the functionality provided by the software.

**Example (C#):**
```csharp
// BAD: Class does too much
public class Invoice {
    public void CalculateTotal() { /* ... */ }
    public void PrintInvoice() { /* ... */ } // Printing is a separate responsibility
    public void SaveToDatabase() { /* ... */ } // Persistence is a separate responsibility
}

// GOOD: Responsibilities separated
public class Invoice {
    public void CalculateTotal() { /* ... */ }
}
public class InvoicePrinter {
    public void Print(Invoice invoice) { /* ... */ }
}
public class InvoiceRepository {
    public void Save(Invoice invoice) { /* ... */ }
}
```

## 2. Open/Closed Principle (OCP)
> "Software entities should be open for extension, but closed for modification."

You should be able to extend a class's behavior without modifying it.

**Example (C#):**
```csharp
public abstract class Shape {
    public abstract double Area();
}

public class Rectangle : Shape {
    public double Width { get; set; }
    public double Height { get; set; }
    public override double Area() => Width * Height;
}

public class Circle : Shape {
    public double Radius { get; set; }
    public override double Area() => Math.PI * Radius * Radius;
}
```

## 3. Liskov Substitution Principle (LSP)
> "Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program."

Derived classes must be substitutable for their base classes.

## 4. Interface Segregation Principle (ISP)
> "Many client-specific interfaces are better than one general-purpose interface."

Clients should not be forced to depend upon interfaces that they do not use.

**Example (C#):**
```csharp
// BAD
public interface IWorker {
    void Work();
    void Eat();
}

// GOOD
public interface IWorkable {
    void Work();
}
public interface IEatable {
    void Eat();
}
```

## 5. Dependency Inversion Principle (DIP)
> "Depend upon abstractions, [not] concretions."

High-level modules should not depend on low-level modules. Both should depend on abstractions.

---
[Back to README](README.md)
