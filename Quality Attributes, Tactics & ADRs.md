---
tags:
  - adr
  - architecture
  - quality
date: 2026-05-19
---

# Quality Attributes & ADRs

A system can be functionally correct but still fail if it's too slow, insecure, or hard to maintain. **Quality Attributes** (also known as "Non-Functional Requirements") determine *how well* the system operates.

## 1. Quality Attribute Categories

| Category | Attribute | Focus |
| :--- | :--- | :--- |
| **Runtime (Dynamic)** | **Performance** | Response time, throughput, resource utilization. |
| | **Availability** | System uptime and recovery from failure. |
| | **Scalability** | Ability to handle increased load (Vertical vs Horizontal). |
| | **Security** | Protecting data and ensuring authorized access. |
| **Development (Static)** | **Maintainability** | Ease of modifying or extending the system. |
| | **Testability** | Ease of verifying the system's correctness. |
| | **Modularity** | Separation of concerns and low coupling. |

---

## 2. Architectural Tactics
Tactics are specific, reusable design decisions that directly address a quality attribute.

### Performance & Scalability
- **Caching:** Store expensive results (DB queries, API calls) in memory (e.g., Redis).
- **Asynchronous Processing:** Use message queues (e.g., RabbitMQ) to handle long-running tasks without blocking the user.
- **Database Indexing:** Optimize query speeds at the cost of slower writes and disk space.

### Availability & Resilience
- **Redundancy:** Run multiple instances (replicas) of a service.
- **Circuit Breaker:** Stop calling a failing service to prevent "cascading failures" (e.g., using Polly).
- **Health Checks:** Automated probes to verify if a service is healthy.

### Security
- **Authentication:** Verifying *who* the user is (e.g., JWT, OAuth2).
- **Authorization:** Verifying *what* the user can do (e.g., Role-Based Access Control).
- **Encryption:** Protecting data "at rest" (database) and "in transit" (HTTPS).

---

## 3. Architecture Decision Records (ADR)
An ADR is a document that captures an important architectural decision made along with its context and consequences.

> [!tip] Why ADRs?
> We write ADRs for our "future selves" and teammates. They prevent the "Chesterton's Fence" problem—deleting code or changing architecture without understanding why it was put there in the first place.

### Standard ADR Template
1. **Title:** Short and descriptive (e.g., "ADR 05: Use PostgreSQL for main storage").
2. **Status:** Proposed, Accepted, Superseded, or Deprecated.
3. **Context:** What is the problem? Why are we making this decision now?
4. **Decision:** The chosen solution. Keep it clear and concise.
5. **Consequences:** What are the trade-offs? (e.g., "Better performance but higher license cost").

---
**Related Notes:**
- [[Software Architecture & The C4 Model]]
- [[Architectural Patterns & .NET Ecosystem]]
- [[Core Software and Web Architecture]]