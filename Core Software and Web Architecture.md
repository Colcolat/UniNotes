---
tags:
  - api
  - general-concepts
  - database
  - software-architecture
date: 2026-05-19
---

# Core Software and Web Architecture

Understanding the fundamental building blocks of modern web applications is essential for any architect.

## 1. The Client-Server Model
- **Frontend (Client):** The user interface (UI) and user experience (UX). Usually built with HTML/CSS/JS or frameworks like React, Angular, or **[[Architectural Patterns & .NET Ecosystem#Frontend & UI|Blazor]]**.
- **Backend (Server):** The business logic, data processing, and security. Languages like **[[Java - History and Ecosystem|Java]]** or C# (.NET) are common here.

## 2. Communication & Protocols
- **HTTP/HTTPS:** The foundation of data exchange on the web. HTTPS is the secure version using SSL/TLS.
- **REST (Representational State Transfer):** An architectural style for APIs using standard HTTP methods (GET, POST, PUT, DELETE).
- **JSON (JavaScript Object Notation):** The most common data format for APIs due to its lightweight and readable nature.
- **WebSockets:** Allows for real-time, two-way communication between client and server (e.g., chat apps).

## 3. APIs (Application Programming Interface)
An API is a "contract" that allows two systems to talk to each other.
- **Internal APIs:** Used within a company to connect different services.
- **Public APIs:** Provided by companies for external developers (e.g., Google Maps, Stripe, OpenAI).

## 4. Databases & Persistence
There are two main paradigms for storing data:

| Feature | Relational (SQL) | Non-Relational (NoSQL) |
| :--- | :--- | :--- |
| **Structure** | Strict tables, rows, columns. | Flexible (Documents, Key-Value, Graph). |
| **Scaling** | Vertical (Bigger server). | Horizontal (More servers). |
| **Best For** | Financial data, complex joins. | Large volumes, fast-changing data. |
| **Examples** | PostgreSQL, MySQL, SQL Server. | MongoDB, Redis, Cassandra. |

## 5. Web Infrastructure
- **Web Server:** Software that serves web content (e.g., Nginx, IIS, Apache).
- **Reverse Proxy:** A server that sits in front of web servers to handle load balancing, security, and caching (e.g., **[[Architectural Patterns & .NET Ecosystem#Essential Libraries (The "Architect's Toolkit")|YARP]]**).
- **Cloud Computing:** Renting infrastructure (servers, storage) from providers like AWS, Azure, or Google Cloud.
  - **IaaS:** Infrastructure as a Service (Virtual Machines).
  - **PaaS:** Platform as a Service (App Hosting).
  - **SaaS:** Software as a Service (e.g., Microsoft 365, Slack).

---
**Related Notes:**
- [[Software Architecture & The C4 Model]]
- [[Architectural Patterns & .NET Ecosystem]]
- [[Quality Attributes, Tactics & ADRs]]
- [[Java - History and Ecosystem]]