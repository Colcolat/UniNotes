---
tags:
  - #solid-principles
  - #domain-driven-design
  - #object-oriented-programming
---

# SOLID Principles & Domain Boundaries


**SOLID** is an acronym for 5 object-oriented design principles formulated by Robert C. Martin to make code more maintainable, testable, and extensible.

## The 5 Principles 
1. **S - Single Responsibility Principle (SRP):** A class should have one, and only one, reason to change. If a class handles data generation, saving files, and sending emails, it violates SRP.
2. **O - Open/Closed Principle (OCP):** Software entities should be open for extension, but closed for modification. You should be able to add new functionality without touching existing, working code (e.g., using Abstract classes or Interfaces instead of huge `switch` statements).
3. **L - Liskov Substitution Principle (LSP):** A subclass must be usable anywhere its parent class is used, without unexpected behavior. Inheritance is a behavioral contract; if a subclass implements a method just to `throw new NotImplementedException()`, it violates LSP.
4. **I - Interface Segregation Principle (ISP):** Clients should not be forced to depend on interfaces they do not use. It's better to have multiple small, specific interfaces (e.g., `IPrinter`, `IScanner`) than one "fat" interface (`IOfficeDevice`).
5. **D - Dependency Inversion Principle (DIP):** High-level modules should not depend on low-level modules; both should depend on abstractions (interfaces). Avoid instantiating concrete classes directly inside your business logic (`new Database()`).

---

## Bounded Contexts
As systems grow, decomposing them by business domain becomes crucial.

A **Bounded Context** is an explicit conceptual boundary where a domain model has a highly specific and consistent meaning.

> [!example] The "Item" Problem
> If your application has Catalog, Reviews, and User sections, the concept of an "Item" (Video Game) means something different in each:
> - **Catalog Context:** Cares about Name, Genre, Year, Cover Art.
> - **Reviews Context:** Only cares about the Game ID and Name to attach a rating.
> - **Users Context:** Only cares if the Game ID is in a "Favorites" list.
> 
> Trying to build a single `Item` class to satisfy all three contexts leads to a bloated, messy architecture. Identify your bounded contexts and let each have its own specific model.