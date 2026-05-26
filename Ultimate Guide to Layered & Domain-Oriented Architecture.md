---
tags:
  - software-architecture
  - Backend
  - ddd
  - mvc
  - dotnet
---

When scaling enterprise software, organizing code simply by functional type (e.g., putting all classes in one folder) creates tight coupling and code fragility. A **Domain-Oriented Layered Architecture** solves this by separating software into four distinct tiers, each representing a precise level of abstraction. 

Below is the exhaustive breakdown of the directory layout, the exact responsibility of each technical element, and the architectural philosophy governing their existence.

---

## Standard Enterprise Project Directory Layout

In a modern backend application (such as an ASP.NET Core solution or a Spring Boot modular system), the project structure maps directly to the architectural layers:

```

CatalogoSolucion.sln
│
├── 1. Catalogo.Domain/                # Core Business Layer (Zero dependencies)
│   ├── Models/                        # Domain Entities / Blueprints (e.g., Item.cs)
│   └── Interfaces/                    # Structural Contracts / Repositories (e.g., IItemRepository.cs)
│
├── 2. Catalogo.Application/           # Workflow & Orchestration Layer
│   ├── Services/                      # Use Cases / Application Engines (e.g., CatalogoService.cs)
│   └── DTOs/                          # Data Transfer Objects (e.g., ItemDto.cs)
│
├── 3. Catalogo.Infrastructure/        # Low-Level Technical Implementations
│   ├── Repositories/                  # Concrete Data Access (e.g., SqlItemRepository.cs)
│   └── Data/                          # Database Contexts / ORM Configurations (e.g., AppDbContext.cs)
│
└── 4. Catalogo.Presentation/          # UI / External Interaction Layer
    ├── Controllers/                   # Request Handlers / Routing (e.g., CatalogoController.cs)
    └── Views/                         # UI Layouts / Render Templates (e.g., Index.cshtml)
```


##  Granular Breakdown of Components & Layer Placement

### 1. The Domain Layer (`Catalogo.Domain`)
This is the absolute core of the software. It isolates the real-world business realities from any computer-science frameworks or deployment infrastructures.

#### 🔸 `Models/` (or `Entities/`) — e.g., `Item.cs`
* **What it is:** A domain blueprint representing a real-world business concept (such as a Video Game, an Invoice, or a User account).
* **Why it goes here:** It defines *what* the system handles fundamentally. It holds the core state properties (`Id`, `Nombre`, `Año`) and **Domain Invariants** (validation rules that must always be true, such as *"An item cannot have a negative price"*).
* **Architectural Rule:** It must consist entirely of Plain Old Objects (POCOs in C# / POJOs in Java). It must **never** reference database attributes, UI components, or external framework namespaces.

#### 🔸 `Interfaces/` — e.g., `IItemRepository.cs`
* **What it is:** An abstract structural contract declaring *what* data actions the business requires, without explaining *how* they are executed.
* **Why it goes here:** This is the execution of the **Dependency Inversion Principle (DIP)**. Instead of the Domain depending on a SQL database, the Domain declares an interface saying *"I need a mechanism to fetch all items"*. The infrastructure layer is forced to adapt to this contract. This encapsulates the domain from data changes.

---

### 2. The Application Layer (`Catalogo.Application`)
This layer represents the workflow execution engine. It handles operational orchestration but contains zero raw business evaluation formulas.

#### 🔸 `Services/` — e.g., `CatalogoService.cs`
* **What it is:** The handler of specific application use cases (e.g., `LoadCatalogWorkflow`, `ProcessPurchaseOrder`).
* **Why it goes here:** A service acts as the conductor of an orchestra. It coordinates data Retrieval, invokes the internal business logic on the Domain Model, updates states, and saves results back.
* **Component Mapping:** It receives requests, communicates with the interface (`IItemRepository`), and passes data up. It isolates the controller from the persistence tier completely.

---

### 3. The Infrastructure Layer (`Catalogo.Infrastructure`)
This layer handles the volatile, low-level technical machinery supporting the layers above it.

#### 🔸 `Repositories/` — e.g., `SqlItemRepository.cs` or `ItemRepositoryMemoria.cs`
* **What it is:** The concrete implementation of the interface defined inside the Domain Layer.
* **Why it goes here:** This component contains framework-specific code (such as Entity Framework Core, Hibernate, raw SQL queries, or in-memory arrays). It communicates directly with the physical storage engine to fulfill the data requirements dictated by the Domain.
* **Architectural Benefit:** If you change your data architecture from MySQL to MongoDB, you **only** modify this class. The Application and Domain layers remain 100% untouched.

---

### 4. The Presentation Layer (`Catalogo.Presentation`)
The interaction gateway exposing the application capabilities to external consumers or end-users.

#### 🔸 `Controllers/` — e.g., `CatalogoController.cs`
* **What it is:** An HTTP endpoint router that receives raw web requests and maps them to structural application commands.
* **Why it goes here:** It translates incoming network paradigms (HTTP verbs like GET/POST, JSON payloads, Query strings) into execution arguments. It hands the parameters to the `Application Service` and returns an appropriate response format (HTML View, RESTful JSON, or HTTP Status Codes).

#### 🔸 `Views/` — e.g., `Index.cshtml`
* **What it is:** The passive graphical user interface layout template.
* **Why it goes here:** It is strictly responsible for layout structure and rendering presentation data. It reads the specific model object passed by the Controller to generate the final markup text.

---

## Strict Architectural Rules & Communication Flows

To preserve structural integrity, component communication must comply with the strict down-and-inward rule:

```text
[ Presentation Layer ] ──> Calls ──> [ Application Layer ]
       │                                     │
       │ (Maps Data)                         │ (Orchestrates Use Cases)
       ▼                                     ▼
[ Infrastructure Layer ] ── Implements ──> [ Domain Layer ] (Absolute Center)