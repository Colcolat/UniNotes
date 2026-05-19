---
tags:
  - api
  - general-concepts
  - database
  - software-architecture
date: 2026-05-14
---

# General Development Concepts

## Frontend vs Backend
-   **Backend:** It is the logical part of a program or service. Languages like **[[Java - History and Ecosystem|Java]]** are very common here, often using **[[Programming Frameworks and Spring|Spring]]**.
-   **Frontend:** It is the visual part provided to that program or service.

## APIs (Application Programming Interface)

An API is basically like a contract that allows two systems to communicate. They are created by companies so that others can use the service.

**Examples of widely used APIs:**
-   Google Maps API (maps in apps).
-   WhatsApp API (automated messaging).
-   Stripe (payments).
-   Twitter/X API (reading tweets).
-   Spotify API (getting music playlists).
-   OpenWeather (weather).
-   OpenAI API (using ChatGPT on other websites).

## Databases
There are two main paradigms:

> [!abstract] Relational (SQL) vs Non-Relational
> **Relational:** Organize data into tables with rows and columns. They are very strict and secure for financial data.
> *Examples:* MySQL, PostgreSQL, Oracle Database.
> 
> **Non-Relational:** Store data in flexible formats like JSON documents. They are better for large volumes of data that change quickly.
> *Examples:* MongoDB, Redis, Cassandra.

Databases are configured differently according to the **[[Software Environments|development or production environments]]**.

## Software Licenses
**GPL License (General Public License):** It is a free software license that grants users the right to use, study, share, and modify the software.
-   **Golden Rule:** Its main characteristic is that it is hereditary. If you modify your GPL software and distribute it, your version must also be free.
