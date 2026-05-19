---
tags:
  - software-architecture
  - development
  - general-concepts
date: 2026-05-14
---

# Software Environments: Development vs. Production

In software engineering, code doesn't live in just one place. To ensure that an application works correctly without interrupting service to users, the software lifecycle is divided into different **environments**. The two main extremes are **Development** and **Production**.

> [!info] The Golden Rule
> Never test new code directly in Production. If something breaks in Development, only you notice. If it breaks in Production, users (or customers) suffer the consequences.

## Development Environment (Dev)
It is the local workspace where you write, test, and debug code. It's your machine, your terminal, and your editor.

- **Goal:** Experiment, build new features, and fix bugs quickly.
- **Code State:** Unstable, constantly changing.
- **Tools:** This is where you use an **IDE** (see [[Java - History and Ecosystem#Industry Adoption]]) to program.
- **Typical Configuration:** 
	- **[[Arquitectura Base de Software y Web#Bases de Datos|Local databases]]** (with test or dummy data).
	- Debugging tools enabled (detailed logs, explicit error messages).
	- For example, if you are setting up a web application with an MVC architecture in .NET or Java using [[Frameworks de programación y Spring|Spring Boot]], this is where you run your local server on `localhost` and compile changes in real time.

## Production Environment (Prod)
It is the "live" or real environment. It is the final server where the application is available to end users. 

- **Goal:** Stability, security, performance, and availability (24/7).
- **Code State:** Stable, tested, and optimized.
- **Typical Configuration:**
	- Real databases (with sensitive user data).
	- Debugging disabled to avoid consuming resources or exposing source code in errors.
	- Minified files, compiled code for maximum efficiency, and connection through real domains (HTTPS).

## Comparison Table

| Feature | Development (Dev) | Production (Prod) |
| :--- | :--- | :--- |
| **Users** | Only you (and your team) | End users / Customers |
| **Data** | Fake / Test data | Real / Sensitive |
| **Errors** | Welcome (to learn) | Critical (cause system downtime) |
| **Performance** | Secondary (debugging matters) | Absolute priority |

## The Bridge: Staging (Pre-production)
Often, between Development and Production, there is an environment called **Staging**. It is an exact replica of the Production server but hidden from the public. It serves for the final test before launching (*deploy*) the code to the real world.
