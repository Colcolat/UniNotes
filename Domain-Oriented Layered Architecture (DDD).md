---
tags:
  - software-architecture
  - architecture
  - Backend
date: 2026-05-14
---
In Software Engineering, Domain-Driven Design (DDD) promotes a layered architecture that isolates the domain logic (the core business rules) from the rest of the application. This ensures that the business logic is not polluted by infrastructure details like databases, UI, or web frameworks.

> [!info] The Golden Rule
> The **Domain Layer** is the heart of the software. It must not depend on any other layer. Instead, all other layers depend on it (directly or indirectly).

---
## The 4 Classic Layers

### 1. Presentation / User Interface Layer
Responsible for showing information to the user and interpreting user commands. It translates external requests into internal operations.
- **Examples:** REST Controllers in Spring Boot (Java) or ASP.NET Core (C#), graphical interfaces, or CLI views.
- **Rule:** It should only communicate with the Application layer, never directly with the database.

### 2. Application Layer
Coordinates the application's activity. It does **not** contain business logic. It simply orchestrates tasks, manages transactions, and delegates work to the domain objects.
- **Examples:** Application Services, Use Cases (e.g., `RegisterUserUseCase`, `ProcessPaymentService`).

### 3. Domain Layer
The most critical layer. It contains the fundamental business concepts, information about the business situation, and the core rules.
- **Examples:** Entities (e.g., `Customer`, `ShoppingCart`), Value Objects (e.g., `EmailAddress`, `Money`), Domain Events, and Repository Interfaces.
- **Rule:** It consists of pure code (Plain Old Java Objects / POCOs in C#) with zero dependencies on external libraries, frameworks, or databases.

### 4. Infrastructure Layer
Acts as a supporting library for all the other layers. It implements the interfaces defined in the Domain layer and provides communication with the outside world.
- **Examples:** Database implementations using Entity Framework Core (.NET) or Hibernate (Java), third-party API clients, file system access, and message brokers.

---
##  Dependency Flow
In a strict Domain-Oriented Architecture, the dependencies flow downwards or inwards:
`Presentation -> Application -> Domain <- Infrastructure`
*(Note: Infrastructure points towards the Domain through Dependency Inversion, meaning it implements the interfaces defined by the Domain).*