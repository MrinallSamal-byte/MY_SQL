# 📘 MySQL Tutorial Repository

> A complete, structured MySQL tutorial covering database fundamentals through advanced techniques — designed for absolute beginners.

## About

This repository contains a comprehensive, single-file MySQL tutorial ([TUTORIAL.md](TUTORIAL.md)) that takes you from zero database knowledge to building real-world applications. It features **37 topics** organized across **9 parts**, with **117 SQL examples**, **35 practice exercises**, and **4 complete projects** — all using a consistent **WHY / WHEN / HOW** teaching framework.

## Getting Started

### Prerequisites

- **MySQL 8.0+** installed locally, via Docker, or access to a remote MySQL server.
- A MySQL client: the `mysql` command-line tool, MySQL Workbench, DBeaver, or any SQL editor.

### Installation

Refer to **[Part 2: Installation & Setup](TUTORIAL.md#part-2-installation--setup)** in the tutorial for step-by-step instructions on installing MySQL on **Windows**, **macOS**, **Linux**, and **Docker**.

### How to Use This Tutorial

1. Open **[TUTORIAL.md](TUTORIAL.md)** and follow the topics in order.
2. Each topic uses the **WHY → WHEN → HOW** pattern: concept explanation, use cases, then hands-on implementation.
3. Run every SQL example in your own MySQL client to build muscle memory.
4. Complete the **✏️ Practice Exercises** at the end of each topic before moving on.

---

## Table of Contents

Below are the 9 parts and their key topics. Each link takes you directly to the corresponding section in [TUTORIAL.md](TUTORIAL.md).

### [Part 1: Basics](TUTORIAL.md#part-1-basics)

| # | Topic | Description |
|---|-------|-------------|
| 1 | [What Is a Database?](TUTORIAL.md#topic-1--what-is-a-database) | Databases vs. flat files, why databases matter |
| 2 | [Relational Databases Explained](TUTORIAL.md#topic-2--relational-databases-explained) | Tables, rows, columns, the relational model |
| 3 | [Keys in Databases](TUTORIAL.md#topic-3--keys-in-databases) | Primary, foreign, composite, candidate, and surrogate keys |
| 4 | [Introduction to SQL](TUTORIAL.md#topic-4--introduction-to-sql) | DDL, DML, DCL, TCL overview |
| 5 | [What Is MySQL?](TUTORIAL.md#topic-5--what-is-mysql) | MySQL in the ecosystem, storage engines, community vs. enterprise |

### [Part 2: Installation & Setup](TUTORIAL.md#part-2-installation--setup)

| # | Topic | Description |
|---|-------|-------------|
| 6 | [Installing MySQL](TUTORIAL.md#topic-6--installing-mysql) | Windows, macOS, Linux, Docker installation |
| 7 | [MySQL Clients & Tools](TUTORIAL.md#topic-7--mysql-clients--tools) | CLI, Workbench, DBeaver, phpMyAdmin |
| 8 | [Connecting to MySQL](TUTORIAL.md#topic-8--connecting-to-mysql) | CLI connections, connection strings, application connectors |

### [Part 3: SQL Fundamentals](TUTORIAL.md#part-3-sql-fundamentals)

| # | Topic | Description |
|---|-------|-------------|
| 9 | [CREATE and DROP Database/Table](TUTORIAL.md#topic-9--create-and-drop-databasetable) | Creating and removing databases and tables |
| 10 | [Data Types in MySQL](TUTORIAL.md#topic-10--data-types-in-mysql) | Numeric, string, date/time, and special types |
| 11 | [INSERT Data](TUTORIAL.md#topic-11--insert-data) | Single-row, multi-row, and INSERT…SELECT |
| 12 | [UPDATE Data](TUTORIAL.md#topic-12--update-data) | Updating rows with conditions and JOINs |
| 13 | [DELETE and TRUNCATE](TUTORIAL.md#topic-13--delete-and-truncate) | Removing data safely |
| 14 | [Basic SELECT Queries](TUTORIAL.md#topic-14--basic-select-queries) | WHERE, LIKE, IN, BETWEEN, DISTINCT, LIMIT |

### [Part 4: Data Modeling](TUTORIAL.md#part-4-data-modeling)

| # | Topic | Description |
|---|-------|-------------|
| 15 | [Normalization (1NF, 2NF, 3NF)](TUTORIAL.md#topic-15--normalization-1nf-2nf-3nf) | Eliminating redundancy, normal forms |
| 16 | [Foreign Keys and Relationships](TUTORIAL.md#topic-16--foreign-keys-and-relationships) | One-to-one, one-to-many, many-to-many |
| 17 | [Constraints](TUTORIAL.md#topic-17--constraints) | NOT NULL, UNIQUE, CHECK, DEFAULT |
| 18 | [Entity-Relationship (ER) Diagrams](TUTORIAL.md#topic-18--entity-relationship-er-diagrams) | Designing schemas visually |

### [Part 5: Querying Data](TUTORIAL.md#part-5-querying-data)

| # | Topic | Description |
|---|-------|-------------|
| 19 | [JOINs](TUTORIAL.md#topic-19--joins) | INNER, LEFT, RIGHT, FULL, CROSS, SELF joins |
| 20 | [Aggregate Functions](TUTORIAL.md#topic-20--aggregate-functions) | COUNT, SUM, AVG, MIN, MAX with GROUP BY |
| 21 | [Subqueries](TUTORIAL.md#topic-21--subqueries) | Scalar, row, correlated subqueries, EXISTS |
| 22 | [Window Functions](TUTORIAL.md#topic-22--window-functions) | ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD, running totals |
| 23 | [UNION, INTERSECT, EXCEPT](TUTORIAL.md#topic-23--union-intersect-except) | Combining result sets |
| 24 | [ORDER BY, GROUP BY, HAVING](TUTORIAL.md#topic-24--order-by-group-by-having) | Sorting, grouping, and filtering aggregates |

### [Part 6: Transactions & Security](TUTORIAL.md#part-6-transactions--security)

| # | Topic | Description |
|---|-------|-------------|
| 25 | [Transactions and ACID](TUTORIAL.md#topic-25--transactions-and-acid) | Atomicity, consistency, isolation, durability |
| 26 | [Isolation Levels](TUTORIAL.md#topic-26--isolation-levels) | READ UNCOMMITTED through SERIALIZABLE |
| 27 | [Users and Privileges](TUTORIAL.md#topic-27--users-and-privileges) | CREATE USER, GRANT, REVOKE, roles |
| 28 | [Backup and Restore](TUTORIAL.md#topic-28--backup-and-restore) | mysqldump, mysqlpump, point-in-time recovery |

### [Part 7: Performance Optimization](TUTORIAL.md#part-7-performance-optimization)

| # | Topic | Description |
|---|-------|-------------|
| 29 | [Indexes](TUTORIAL.md#topic-29--indexes) | B-Tree, composite, covering, full-text indexes |
| 30 | [EXPLAIN and Query Plans](TUTORIAL.md#topic-30--explain-and-query-plans) | Reading and interpreting EXPLAIN output |
| 31 | [Query Optimization Tips](TUTORIAL.md#topic-31--query-optimization-tips) | Avoiding common performance pitfalls |
| 32 | [Partitioning](TUTORIAL.md#topic-32--partitioning) | RANGE, LIST, HASH partitioning strategies |

### [Part 8: Advanced Features](TUTORIAL.md#part-8-advanced-features)

| # | Topic | Description |
|---|-------|-------------|
| 33 | [Stored Procedures and Functions](TUTORIAL.md#topic-33--stored-procedures-and-functions) | Creating reusable server-side logic |
| 34 | [Triggers](TUTORIAL.md#topic-34--triggers) | BEFORE/AFTER triggers for INSERT, UPDATE, DELETE |
| 35 | [Views](TUTORIAL.md#topic-35--views) | Virtual tables and updatable views |
| 36 | [JSON in MySQL](TUTORIAL.md#topic-36--json-in-mysql) | JSON columns, functions, and indexing |
| 37 | [Replication Basics](TUTORIAL.md#topic-37--replication-basics) | Source-replica setup, binary log replication |

### [Part 9: Real-World Projects & Comparisons](TUTORIAL.md#part-9-real-world-projects--comparisons)

| Section | Description |
|---------|-------------|
| [Project 1 — E-Commerce Database](TUTORIAL.md#project-1--e-commerce-database) | Complete schema with products, orders, customers, and queries |
| [Project 2 — College Management System](TUTORIAL.md#project-2--college-management-system) | Normalized schema with students, courses, enrollments |
| [Project 3 — Sales Analytics Dashboard](TUTORIAL.md#project-3--sales-analytics-dashboard) | Window functions, CTEs, running totals for analytics |
| [Project 4 — Traffic Logging System](TUTORIAL.md#project-4--traffic-logging-system) | Partitioning and optimization for high-volume logging |
| [Common Mistakes](TUTORIAL.md#common-mistakes) | Poor normalization, inefficient queries, security oversights |
| [MySQL vs Other Databases](TUTORIAL.md#mysql-vs-other-databases) | MySQL vs PostgreSQL vs SQLite vs MariaDB, relational vs NoSQL |
| [Quick Reference / Cheat Sheet](TUTORIAL.md#quick-reference--cheat-sheet) | One-page SQL syntax reference |
| [Further Reading & Resources](TUTORIAL.md#further-reading--resources) | Books, documentation, tools |
| [Glossary of Terms](TUTORIAL.md#glossary-of-terms) | Key database terminology |

---

## Tutorial Stats

| Metric | Count |
|--------|-------|
| Parts | 9 |
| Topics | 37 |
| SQL Examples | 117 |
| Practice Exercises | 35 |
| Complete Projects | 4 |
| Teaching Framework | WHY → WHEN → HOW |

## Contributing

Contributions are welcome! If you find errors, want to add examples, or improve explanations, feel free to open an issue or submit a pull request.

## License

This project is open source and available for educational use.
