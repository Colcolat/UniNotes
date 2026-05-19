---
tags:
  - database
  - sql
  - nosql
  - Backend
  - software-architecture
date: 2026-05-18
---
---

A **Database (DB)** is an organized collection of structured information, or data, typically stored electronically in a computer system. They are managed by a Database Management System (DBMS), which allows applications to safely store, retrieve, and update data.

## Core Concepts & Rules

To maintain data integrity and establish relationships, databases use specific identifiers and rules:

- **Constraint:** A strict rule applied to a column or table to limit the type of data that can be inserted. This ensures accuracy and reliability. 
	- *Examples:* `NOT NULL` (the field cannot be empty), `UNIQUE` (no duplicate values allowed).
- **Primary Key (PK):** A specific constraint that uniquely identifies each record (row) in a table. A table can only have one primary key, and its value must be unique and never null (e.g., a `UserID` or an `OrderNumber`).
- **Foreign Key (FK):** A column in one table that links to the Primary Key of another table. It acts as a bridge, creating a relationship between the two tables and ensuring referential integrity (e.g., an `OwnerID` in a `Cars` table pointing to the `Users` table).

## DDL vs. DML (SQL Sublanguages)

Within the SQL language used in relational databases, commands are divided into sublanguages based on their purpose:

> [!code] DDL (Data Definition Language)
> Responsible for **defining, modifying, or dropping the structure** of database objects (tables, views, indexes, schemas). These statements alter the container of the data, not the data itself.
> - **CREATE:** To build new databases, tables, or indexes.
> - **ALTER:** To modify the structure of an existing table (e.g., adding a new column).
> - **DROP:** To completely delete a table or database from the system.

> [!code] DML (Data Manipulation Language)
> Used to **manage and manipulate the actual data** that lives inside the structures created by the DDL. It allows you to interact directly with the information records.
> - **SELECT:** To query, filter, and retrieve data.
> - **INSERT:** To add new records or rows to a table.
> - **UPDATE:** To modify the values of existing records.
> - **DELETE:** To remove records or rows from a table.

## Database Types: Relational vs. Non-Relational

> [!abstract] Relational Databases (SQL)
> They organize data into strict tables with predefined columns and rows. They use Structured Query Language (SQL) and rely heavily on Primary and Foreign keys to link data across multiple tables.
> - **Best for:** Complex queries, strict data integrity (ACID compliance), and highly structured data like financial transactions or user accounts.
> - **Examples:** MySQL, PostgreSQL, Oracle Database, Microsoft SQL Server.

> [!abstract] Non-Relational Databases (NoSQL)
> They store data in flexible, non-tabular formats like JSON documents, key-value pairs, or graphs. They do not require a fixed schema, meaning each record can have different fields.
> - **Best for:** Unstructured data, rapid agile development, and handling massive volumes of data that change constantly.
> - **Examples:** MongoDB (Document-based), Redis (Key-Value), Cassandra (Wide-column).

## Exposing the Data: APIs

Databases rarely communicate directly with end-users or frontend interfaces due to security reasons. Instead, **APIs (Application Programming Interfaces)** act as the secure bridge. 

The frontend sends a request to the API, the API queries the database, and then the API sends the data back to the frontend (usually in JSON format).

> [!example] Real-World API Examples
> - **Stripe API:** Connects to secure financial databases to process user payments.
> - **Google Maps API:** Retrieves geographical data, coordinates, and routes from Google's spatial databases.
> - **OpenWeather API:** Pulls real-time meteorological data from massive weather databases.
> - **Spotify API:** Queries their NoSQL and relational databases to fetch your playlists, songs, and artist information.