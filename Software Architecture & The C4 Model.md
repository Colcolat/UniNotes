---
tags:
  - software-architecture
  - c4-model
  - development
date: 2026-05-19
---

# Software Architecture & The C4 Model

**Software Architecture** represents the collection of significant design decisions that shape a system. These decisions are typically the "hard to change" parts that define the system's long-term viability, scalability, and maintainability.

## 1. Architectural Drivers
Architecture isn't decided in a vacuum. It is shaped by three primary drivers:

| Driver | Description | Examples |
| :--- | :--- | :--- |
| **Quality Attributes** | Non-functional requirements that define "how" the system works. | Scalability, Security, Availability, Portability. |
| **Constraints** | Non-negotiable limitations imposed by the business or environment. | Budget, Deadline, Tech Stack (e.g., "Must use Java"), Compliance. |
| **Principles** | Guiding rules for development teams. | "API First," "Cloud Native," "Mobile First," "Keep it Simple." |

> [!tip] Architecture vs. Design
> While **Architecture** focuses on high-level strategy (e.g., Microservices vs. Monolith), **Design** focuses on local implementation (e.g., Design Patterns like Factory or Strategy within a module).

---

## 2. The Role of the Modern Architect
In Agile environments, the architect acts as a bridge between business requirements and technical execution.
- **Decision Maker:** Chooses the architectural style and technology stack.
- **Quality Advocate:** Balances trade-offs between conflicting quality attributes (e.g., Performance vs. Security).
- **Technical Leader:** Participates in development, reviews code for architectural alignment, and mentors the team.
- **Communicator:** Translates complex technical structures for stakeholders.

---

## 3. Visualizing Architecture: The C4 Model
The C4 model provides a hierarchical way to visualize software architecture using four levels of abstraction. This prevents diagrams from becoming "cluttered" by tailoring the level of detail to the audience.

### C4 Levels Comparison

| Level | Name | Audience | Scope | Focus |
| :--- | :--- | :--- | :--- | :--- |
| **L1** | **System Context** | Everyone (Business & Tech) | The entire system | Relationships with users and external systems. |
| **L2** | **Container** | Developers & Ops | A single system | High-level technology choices (Apps, DBs, File Systems). |
| **L3** | **Component** | Developers & Architects | A single container | Internal building blocks (Packages, Services, Controllers). |
| **L4** | **Code** | Developers | A single component | Class diagrams, Entity Relationship Diagrams (ERDs). |

### Detailed Breakdown

#### Level 1: System Context
The highest level of abstraction. It treats your system as a "black box" and focuses on the value it provides.
- **Key Question:** Who uses the system and what external systems does it interact with?
- **Example:** A Banking System interacting with "Customers" and "Mainframe Banking System."

#### Level 2: Container
A "container" represents a runtime environment or a data store (not necessarily a Docker container).
- **Key Question:** What are the high-level technical building blocks?
- **Examples:** A React Web App, a Spring Boot API, a PostgreSQL Database, a Mobile App.

#### Level 3: Component
Breaks down a container into its constituent parts.
- **Key Question:** How is the code organized within a container?
- **Examples:** Authentication Service, Payment Gateway Interface, Email Controller.

#### Level 4: Code
The most granular level. This is often generated automatically by IDEs or modeling tools.
- **Key Question:** How is this component implemented?
- **Examples:** UML Class Diagrams, Database Schemas.

---
## 4. Best Practices for Architectural Diagrams
- **Title Every Diagram:** Clearly state the scope and level.
- **Use a Legend:** Never assume colors or shapes are self-explanatory.
- **Label Relationships:** Instead of just drawing a line, add a verb (e.g., "Sends email via," "Persists data to").
- **Specify Technology:** At Level 2 and below, explicitly name the technologies (e.g., "Redis" instead of "Cache").

---
**Related Notes:**
- [[Core Software and Web Architecture]]
- [[Domain-Oriented Layered Architecture (DDD)]]