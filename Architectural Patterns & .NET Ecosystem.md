---
tags:
  - dotnet
  - software-architecture
  - patterns
date: 2026-05-19
---

# Architectural Patterns & .NET Ecosystem

Modern .NET development leverages a powerful suite of frameworks and libraries to implement diverse architectural patterns, from simple monoliths to complex distributed systems.

## 1. Common Architectural Patterns

| Pattern | Description | Best For |
| :--- | :--- | :--- |
| **Layered (N-Tier)** | Organizes code into horizontal layers (Presentation, Business, Data). | Simple CRUD apps, small teams. |
| **Clean / Hexagonal** | Inverts dependencies so the Domain Core is isolated from infrastructure. | Complex business logic, long-term maintainability. |
| **Microservices** | Decomposes a system into small, autonomous, independently deployable services. | Large-scale systems, multiple teams, high scalability. |
| **Event-Driven** | Services communicate asynchronously via events (e.g., RabbitMQ, Kafka). | Decoupled systems, high availability, responsiveness. |

> [!important] Dependency Inversion
> In **Clean Architecture**, the Domain layer defines interfaces (Ports), and the Infrastructure layer implements them (Adapters). This ensures your business logic doesn't depend on a specific database or framework.

---

## 2. The .NET Ecosystem Stack

The .NET ecosystem provides specialized tools for every part of the architecture:

### Backend & Data
- **ASP.NET Core:** The high-performance framework for building web APIs and services.
- **Entity Framework (EF) Core:** The primary Object-Relational Mapper (ORM) for data access.
- **Dapper:** A "Micro-ORM" used for high-performance read operations (often paired with CQRS).
- **MediatR:** Implements the Mediator pattern to decouple request senders from handlers.

### Frontend & UI
- **Blazor (Web):** Build interactive web UIs using C# instead of JavaScript.
  - *Blazor Server:* Runs logic on the server; updates UI via SignalR.
  - *Blazor WebAssembly:* Runs logic directly in the browser via WASM.
- **.NET MAUI (Mobile/Desktop):** A multi-platform UI framework for native iOS, Android, macOS, and Windows apps.
- **Blazor Hybrid:** Embeds Blazor web components inside a native MAUI app for maximum code reuse.

---

## 3. Communication Patterns

### Synchronous (Request/Response)
- **REST:** Standard HTTP-based communication using JSON.
- **gRPC:** High-performance, binary communication (Protocol Buffers) ideal for internal microservice calls.

### Asynchronous (Messaging)
- **MassTransit:** A powerful library that simplifies working with message brokers (RabbitMQ, Azure Service Bus).
- **Transactional Outbox:** A pattern to ensure data consistency by saving "events" to the database before publishing them to a broker.

---

## 4. Essential Libraries (The "Architect's Toolkit")
- **Serilog:** Structured logging for better observability.
- **FluentValidation:** Decouples validation logic from models.
- **Polly:** Implements resilience patterns like Retries and Circuit Breakers.
- **YARP (Yet Another Reverse Proxy):** A toolkit for building high-performance API Gateways.

---
**Related Notes:**
- [[Software Architecture & The C4 Model]]
- [[Quality Attributes, Tactics & ADRs]]
- [[Core Software and Web Architecture]]