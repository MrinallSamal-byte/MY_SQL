# 📘 The Complete MySQL Tutorial

> **From Absolute Beginner to Confident Practitioner**
>
> A structured, hands-on guide covering database fundamentals through advanced techniques — all in one file.

---

## 📑 Table of Contents

### [Part 1: Basics](#part-1-basics)
- [Topic 1 — What Is a Database?](#topic-1--what-is-a-database)
- [Topic 2 — Relational Databases Explained](#topic-2--relational-databases-explained)
- [Topic 3 — Keys in Databases](#topic-3--keys-in-databases)
- [Topic 4 — Introduction to SQL](#topic-4--introduction-to-sql)
- [Topic 5 — What Is MySQL?](#topic-5--what-is-mysql)

### [Part 2: Installation & Setup](#part-2-installation--setup)
- [Topic 6 — Installing MySQL](#topic-6--installing-mysql)
- [Topic 7 — MySQL Clients & Tools](#topic-7--mysql-clients--tools)
- [Topic 8 — Connecting to MySQL](#topic-8--connecting-to-mysql)

### [Part 3: SQL Fundamentals](#part-3-sql-fundamentals)
- [Topic 9 — CREATE and DROP Database/Table](#topic-9--create-and-drop-databasetable)
- [Topic 10 — Data Types in MySQL](#topic-10--data-types-in-mysql)
- [Topic 11 — INSERT Data](#topic-11--insert-data)
- [Topic 12 — UPDATE Data](#topic-12--update-data)
- [Topic 13 — DELETE and TRUNCATE](#topic-13--delete-and-truncate)
- [Topic 14 — Basic SELECT Queries](#topic-14--basic-select-queries)
- [Topic 14A — String Functions](#topic-14a--string-functions)
- [Topic 14B — Date & Time Functions](#topic-14b--date--time-functions)
- [Topic 14C — Numeric Functions & Conditional Expressions](#topic-14c--numeric-functions--conditional-expressions)
- [Topic 14D — ALTER TABLE Operations](#topic-14d--alter-table-operations)
- [Topic 14E — Regular Expressions (REGEXP)](#topic-14e--regular-expressions-regexp)

### [Part 4: Data Modeling](#part-4-data-modeling)
- [Topic 15 — Normalization (1NF, 2NF, 3NF)](#topic-15--normalization-1nf-2nf-3nf)
- [Topic 16 — Foreign Keys and Relationships](#topic-16--foreign-keys-and-relationships)
- [Topic 17 — Constraints](#topic-17--constraints)
- [Topic 18 — Entity-Relationship (ER) Diagrams](#topic-18--entity-relationship-er-diagrams)

### [Part 5: Querying Data](#part-5-querying-data)
- [Topic 19 — JOINs (All 7 Types)](#topic-19--joins)
- [Topic 20 — Aggregate Functions](#topic-20--aggregate-functions)
- [Topic 21 — Subqueries](#topic-21--subqueries)
- [Topic 22 — Window Functions](#topic-22--window-functions)
- [Topic 23 — UNION, INTERSECT, EXCEPT](#topic-23--union-intersect-except)
- [Topic 24 — ORDER BY, GROUP BY, HAVING](#topic-24--order-by-group-by-having)
- [Topic 24A — Common Table Expressions (CTEs)](#topic-24a--common-table-expressions-ctes)

### [Part 6: Transactions & Security](#part-6-transactions--security)
- [Topic 25 — Transactions and ACID](#topic-25--transactions-and-acid)
- [Topic 26 — Isolation Levels](#topic-26--isolation-levels)
- [Topic 27 — Users and Privileges](#topic-27--users-and-privileges)
- [Topic 28 — Backup and Restore](#topic-28--backup-and-restore)

### [Part 7: Performance Optimization](#part-7-performance-optimization)
- [Topic 29 — Indexes](#topic-29--indexes)
- [Topic 30 — EXPLAIN and Query Plans](#topic-30--explain-and-query-plans)
- [Topic 31 — Query Optimization Tips](#topic-31--query-optimization-tips)
- [Topic 32 — Partitioning](#topic-32--partitioning)

### [Part 8: Advanced Features](#part-8-advanced-features)
- [Topic 33 — Stored Procedures and Functions](#topic-33--stored-procedures-and-functions)
- [Topic 34 — Triggers](#topic-34--triggers)
- [Topic 35 — Views](#topic-35--views)
- [Topic 36 — JSON in MySQL](#topic-36--json-in-mysql)
- [Topic 37 — Replication Basics](#topic-37--replication-basics)
- [Topic 37A — Storage Engines (InnoDB vs MyISAM)](#topic-37a--storage-engines-innodb-vs-myisam)
- [Topic 37B — Temporary Tables & Prepared Statements](#topic-37b--temporary-tables--prepared-statements)
- [Topic 37C — Character Sets & Collations](#topic-37c--character-sets--collations)
- [Topic 37D — User Variables, Session Variables & Cursors](#topic-37d--user-variables-session-variables--cursors)
- [Topic 37E — Events (Scheduled Tasks)](#topic-37e--events-scheduled-tasks)

### [Part 9: Real-World Projects & Comparisons](#part-9-real-world-projects--comparisons)
- [Project 1 — E-Commerce Database](#project-1--e-commerce-database)
- [Project 2 — College Management System](#project-2--college-management-system)
- [Project 3 — Sales Analytics Dashboard](#project-3--sales-analytics-dashboard)
- [Project 4 — Traffic Logging System](#project-4--traffic-logging-system)
- [Common Mistakes](#common-mistakes)
- [MySQL vs Other Databases](#mysql-vs-other-databases)
- [Quick Reference / Cheat Sheet](#quick-reference--cheat-sheet)
- [Further Reading & Resources](#further-reading--resources)
- [Glossary of Terms](#glossary-of-terms)

---

# Part 1: Basics

> **Goal:** Understand what databases are, how relational databases work, the role of keys, what SQL is, and why MySQL is one of the most popular database systems in the world.

---

## Topic 1 — What Is a Database?

### 🌍 Real-Life Analogy

Imagine a **filing cabinet** in an office. Each drawer holds folders for a different category (Employees, Invoices, Clients). Each folder contains neatly organized pages of information. A **database** is the digital equivalent of that filing cabinet — it stores, organizes, and lets you retrieve information quickly and reliably.

Without a filing cabinet, you'd have loose papers scattered across desks. Similarly, without a database, your application data would live in random text files with no reliable way to search, update, or protect it.

---

### 1️⃣ WHY — Why Do We Need Databases?

| Problem Without a Database | How a Database Solves It |
|---|---|
| Data is scattered across files | Centralized, structured storage |
| Searching is slow and error-prone | Indexed, instant lookups |
| Multiple users overwrite each other | Concurrency control and locking |
| No protection against crashes | Transaction safety and recovery |
| No access control | User permissions and authentication |
| Duplicate data everywhere | Normalization eliminates redundancy |

**Key reasons:**
- **Persistence** — Data survives application restarts and server reboots.
- **Integrity** — Rules (constraints) ensure data stays valid (e.g., an age can't be negative).
- **Performance** — Indexes and query optimizers make retrieval fast even with millions of rows.
- **Security** — Fine-grained user permissions control who can read or modify data.
- **Concurrency** — Hundreds of users can read and write simultaneously without corruption.

---

### 2️⃣ WHEN — When Should You Use a Database?

✅ **Use a database when:**
- Your app needs to store data that outlives a single session (user accounts, orders, posts).
- Multiple users or services access the same data at the same time.
- You need to search, filter, or aggregate data efficiently.
- Data integrity and consistency are critical (financial records, medical data).
- You need audit trails, backups, and disaster recovery.

❌ **A simple file might suffice when:**
- You have a small, read-only configuration (e.g., a `config.json`).
- Data is temporary and disposable (e.g., a cache file).
- There is only one user/process and the data set is tiny.

---

### 3️⃣ HOW — Databases vs. Flat Files

#### Example 1: Storing customer data in a flat CSV file

```
name,email,city
Alice,alice@example.com,New York
Bob,bob@example.com,London
Alice,alice@example.com,New York   ← duplicate! no way to prevent it
```

**Problems:**
- No duplicate prevention — the same row can appear many times.
- Searching requires scanning every line (slow for large files).
- No way to enforce rules like "email must be unique."
- If two programs write at the same time, data can be corrupted.

#### Example 2: Storing the same data in a MySQL database

```sql
-- Create a table with rules built in
CREATE TABLE customers (
    id    INT           AUTO_INCREMENT PRIMARY KEY,  -- unique ID for every row
    name  VARCHAR(100)  NOT NULL,                    -- name cannot be empty
    email VARCHAR(150)  NOT NULL UNIQUE,             -- email must be unique
    city  VARCHAR(100)
);

-- Insert data safely
INSERT INTO customers (name, email, city)
VALUES ('Alice', 'alice@example.com', 'New York');

INSERT INTO customers (name, email, city)
VALUES ('Bob', 'bob@example.com', 'London');
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `CREATE TABLE customers (` | Creates a new table named `customers`. |
| `id INT AUTO_INCREMENT PRIMARY KEY,` | Adds an integer column `id` that auto-increments and uniquely identifies each row. |
| `name VARCHAR(100) NOT NULL,` | Adds a `name` column (up to 100 characters) that cannot be left empty. |
| `email VARCHAR(150) NOT NULL UNIQUE,` | Adds an `email` column that must be unique across all rows. |
| `city VARCHAR(100)` | Adds an optional `city` column. |
| `INSERT INTO customers ...` | Adds a new row with the given values. |

If you try to insert a duplicate email:

```sql
INSERT INTO customers (name, email, city)
VALUES ('Alice Clone', 'alice@example.com', 'Boston');
-- ERROR 1062: Duplicate entry 'alice@example.com' for key 'email'
```

The database **rejects** the duplicate automatically — something a flat file can never do.

---

### ✏️ Practice Exercise 1

> **Difficulty:** ⭐ Beginner
>
> 1. Think of three real-world examples where a database is better than a file (e.g., a banking system). Write down why for each.
> 2. Think of two examples where a simple file is sufficient. Write down why.
> 3. Using the `customers` table above as a model, sketch out a table definition (columns, data types, constraints) for a `products` table that stores: product name, price, stock quantity, and a unique product code.

---

## Topic 2 — Relational Databases Explained

### 🌍 Real-Life Analogy

Think of a **spreadsheet workbook**. Each **sheet** (tab) holds a different kind of data — one for Employees, one for Departments, one for Salaries. Within each sheet, every **column** is a category of information (Name, Hire Date, Salary), and every **row** is one record (one employee).

A **relational database** works the same way, except:
- Sheets are called **tables**.
- Columns are called **fields** (or attributes).
- Rows are called **records** (or tuples).
- Tables can be **linked** (related) to each other through shared columns — that's where the word "relational" comes from.

---

### 1️⃣ WHY — Why Relational Databases?

The **relational model** was proposed by Edgar F. Codd in 1970. Its power lies in:

| Benefit | Explanation |
|---|---|
| **Structured Data** | Data lives in well-defined tables with fixed columns and data types. |
| **Relationships** | Tables can reference each other (e.g., an `orders` table points to a `customers` table). |
| **Data Integrity** | Constraints ensure only valid data is stored. |
| **Flexible Querying** | SQL lets you combine, filter, sort, and aggregate data from multiple tables in a single query. |
| **Standardized** | SQL is an industry standard — skills transfer across MySQL, PostgreSQL, SQL Server, Oracle, etc. |
| **ACID Compliance** | Transactions guarantee reliability (more on this in Part 6). |

---

### 2️⃣ WHEN — When to Choose a Relational Database?

✅ **Choose relational when:**
- Your data has a clear, predictable structure (columns are known in advance).
- Relationships between entities are important (customers → orders → products).
- You need strong consistency guarantees (banking, healthcare, e-commerce).
- You need complex queries: joins, aggregations, grouping, subqueries.

❌ **Consider NoSQL when:**
- Your data structure changes frequently (schema-less documents).
- You need extreme horizontal scalability with simple key-value lookups.
- You're storing large volumes of unstructured data (logs, sensor data, social feeds).

---

### 3️⃣ HOW — Tables, Rows, and Columns in Practice

#### Example 3: Creating two related tables

```sql
-- Table to store departments
CREATE TABLE departments (
    dept_id   INT         AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL UNIQUE
);

-- Table to store employees (linked to departments)
CREATE TABLE employees (
    emp_id    INT          AUTO_INCREMENT PRIMARY KEY,
    emp_name  VARCHAR(100) NOT NULL,
    hire_date DATE         NOT NULL,
    salary    DECIMAL(10,2) DEFAULT 0.00,
    dept_id   INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `CREATE TABLE departments (` | Defines a new table for departments. |
| `dept_id INT AUTO_INCREMENT PRIMARY KEY,` | Each department gets a unique auto-generated ID. |
| `dept_name VARCHAR(50) NOT NULL UNIQUE` | Department name is required and must be unique. |
| `CREATE TABLE employees (` | Defines a new table for employees. |
| `emp_id INT AUTO_INCREMENT PRIMARY KEY,` | Each employee gets a unique auto-generated ID. |
| `emp_name VARCHAR(100) NOT NULL,` | Employee name is required. |
| `hire_date DATE NOT NULL,` | Hire date is required (format: `YYYY-MM-DD`). |
| `salary DECIMAL(10,2) DEFAULT 0.00,` | Salary has up to 10 digits with 2 decimal places; defaults to 0. |
| `dept_id INT,` | References a department. |
| `FOREIGN KEY (dept_id) REFERENCES departments(dept_id)` | Enforces that `dept_id` must match an existing department. |

#### Example 4: Inserting and querying related data

```sql
-- Insert departments first (because employees reference them)
INSERT INTO departments (dept_name) VALUES ('Engineering');
INSERT INTO departments (dept_name) VALUES ('Marketing');

-- Insert employees
INSERT INTO employees (emp_name, hire_date, salary, dept_id)
VALUES ('Alice', '2023-01-15', 85000.00, 1);

INSERT INTO employees (emp_name, hire_date, salary, dept_id)
VALUES ('Bob', '2023-06-01', 72000.00, 2);

INSERT INTO employees (emp_name, hire_date, salary, dept_id)
VALUES ('Charlie', '2024-02-10', 90000.00, 1);

-- Query: list all employees with their department names
SELECT e.emp_name, e.salary, d.dept_name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;
```

**Expected output:**

| emp_name | salary   | dept_name   |
|----------|----------|-------------|
| Alice    | 85000.00 | Engineering |
| Bob      | 72000.00 | Marketing   |
| Charlie  | 90000.00 | Engineering |

**Key takeaway:** The `employees` table doesn't store the department name directly. It stores a `dept_id` that *points to* the `departments` table. This avoids repeating "Engineering" for every engineering employee and makes updates easy — rename the department once, and every employee reflects the change.

---

#### Visual: How Tables Relate

```
┌─────────────────────┐         ┌──────────────────────────────────────────┐
│    departments       │         │              employees                    │
├─────────────────────┤         ├──────────────────────────────────────────┤
│ dept_id (PK)        │◄────────│ dept_id (FK) → departments.dept_id       │
│ dept_name           │         │ emp_id  (PK)                             │
│                     │         │ emp_name                                 │
│                     │         │ hire_date                                │
│                     │         │ salary                                   │
└─────────────────────┘         └──────────────────────────────────────────┘
```

- **PK** = Primary Key (unique identifier for each row)
- **FK** = Foreign Key (a column that references another table's primary key)

---

### ✏️ Practice Exercise 2

> **Difficulty:** ⭐ Beginner
>
> 1. Using the `departments` and `employees` tables above, write an `INSERT` statement to add a new department called "Sales".
> 2. Write an `INSERT` statement to add an employee named "Diana" in the "Sales" department hired on 2024-09-01 with a salary of 68000.
> 3. Write a `SELECT` query to show only employees in the "Engineering" department with a salary greater than 80000.

---

## Topic 3 — Keys in Databases

### 🌍 Real-Life Analogy

Think of a **student ID card**. Every student at a university has a unique student number — no two students share the same one. That number is the **primary key**. Now imagine a class enrollment list that records each student's number next to the course they signed up for — that student number on the enrollment list is a **foreign key** pointing back to the student record.

---

### 1️⃣ WHY — Why Are Keys Important?

Keys are the backbone of relational databases. They serve three critical purposes:

| Purpose | Explanation |
|---|---|
| **Uniqueness** | A primary key guarantees every row can be identified individually — no duplicates. |
| **Relationships** | Foreign keys link tables together, enabling JOINs and relational queries. |
| **Integrity** | The database engine enforces key rules automatically — it rejects invalid data. |

Without keys:
- You can't reliably find a specific row.
- You can't link tables together.
- Duplicate and orphaned data accumulates.

---

### 2️⃣ WHEN — When to Use Each Key Type?

| Key Type | Use When… | Example |
|---|---|---|
| **Primary Key (PK)** | Every table needs one. Uniquely identifies each row. | `student_id` in a `students` table |
| **Foreign Key (FK)** | A column in one table needs to point to a row in another table. | `dept_id` in `employees` referencing `departments` |
| **Unique Key** | A column must have unique values but isn't the primary identifier. | `email` in a `users` table |
| **Composite Key** | A combination of two or more columns together form a unique identifier. | `(student_id, course_id)` in an `enrollments` table |

---

### 3️⃣ HOW — Key Types in Practice

#### Example 5: Primary Key

```sql
CREATE TABLE students (
    student_id INT AUTO_INCREMENT PRIMARY KEY,  -- unique ID, auto-generated
    full_name  VARCHAR(100) NOT NULL,
    email      VARCHAR(150) NOT NULL
);
```

- `student_id` is the **primary key**: every student gets a unique number.
- `AUTO_INCREMENT` means MySQL assigns the next available integer automatically.
- A table can have **only one** primary key.

#### Example 6: Foreign Key

```sql
CREATE TABLE courses (
    course_id   INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL
);

CREATE TABLE enrollments (
    enrollment_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id    INT NOT NULL,
    course_id     INT NOT NULL,
    enrolled_on   DATE DEFAULT (CURRENT_DATE),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id)  REFERENCES courses(course_id)
);
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `enrollment_id INT AUTO_INCREMENT PRIMARY KEY` | Each enrollment gets its own unique ID. |
| `student_id INT NOT NULL` | Records which student is enrolling. |
| `course_id INT NOT NULL` | Records which course they're enrolling in. |
| `enrolled_on DATE DEFAULT (CURRENT_DATE)` | Defaults to today's date if not specified. |
| `FOREIGN KEY (student_id) REFERENCES students(student_id)` | Ensures the student exists in the `students` table. |
| `FOREIGN KEY (course_id) REFERENCES courses(course_id)` | Ensures the course exists in the `courses` table. |

If you try to enroll a student that doesn't exist:

```sql
INSERT INTO enrollments (student_id, course_id)
VALUES (9999, 1);
-- ERROR 1452: Cannot add or update a child row:
-- a foreign key constraint fails
```

The database **automatically rejects** the invalid reference.

#### Example 7: Unique Key

```sql
CREATE TABLE users (
    user_id  INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,  -- no two users share a username
    email    VARCHAR(150) NOT NULL UNIQUE  -- no two users share an email
);
```

- Both `username` and `email` have **unique constraints**, but neither is the primary key.
- A table can have **many** unique keys but only **one** primary key.

#### Example 8: Composite Key

```sql
CREATE TABLE course_ratings (
    student_id INT NOT NULL,
    course_id  INT NOT NULL,
    rating     TINYINT CHECK (rating BETWEEN 1 AND 5),
    PRIMARY KEY (student_id, course_id),  -- composite PK: one rating per student per course
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id)  REFERENCES courses(course_id)
);
```

- The **composite primary key** `(student_id, course_id)` means a student can rate a course only once.
- Either column alone can repeat, but the **combination** must be unique.

```sql
-- This works: student 1 rates courses 1 and 2
INSERT INTO course_ratings VALUES (1, 1, 5);
INSERT INTO course_ratings VALUES (1, 2, 4);

-- This fails: student 1 already rated course 1
INSERT INTO course_ratings VALUES (1, 1, 3);
-- ERROR 1062: Duplicate entry '1-1' for key 'PRIMARY'
```

---

### Summary of Key Types

| Key | Allows NULLs? | Allows Duplicates? | How Many Per Table? |
|---|---|---|---|
| **Primary Key** | ❌ No | ❌ No | Exactly 1 |
| **Foreign Key** | ✅ Yes (if column is nullable) | ✅ Yes | Many |
| **Unique Key** | ✅ Yes (one NULL allowed) | ❌ No | Many |
| **Composite Key** | Depends on column defs | ❌ No (combo must be unique) | 1 (as PK) or many (as unique) |

---

### ✏️ Practice Exercise 3

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Create a `books` table with columns: `book_id` (PK), `isbn` (unique), `title`, `author`, `published_year`.
> 2. Create a `reviews` table with columns: `review_id` (PK), `book_id` (FK → books), `reviewer_name`, `rating` (1–5), `review_text`.
> 3. Create a `book_authors` junction table for a many-to-many relationship between books and authors. Use a composite primary key of `(book_id, author_id)`. (Hint: you'll need a separate `authors` table too.)
> 4. Write an INSERT statement that would **fail** due to a foreign key violation, and explain why.

---

## Topic 4 — Introduction to SQL

### 🌍 Real-Life Analogy

Imagine you walk into a library and say: *"Find me all mystery novels published after 2020, sorted by title."* The librarian understands your request and brings you the books.

**SQL (Structured Query Language)** is how you talk to a database. Instead of speaking English to a librarian, you write SQL statements to tell the database exactly what you want.

---

### 1️⃣ WHY — Why Learn SQL?

| Reason | Details |
|---|---|
| **Universal language** | SQL works across MySQL, PostgreSQL, SQL Server, Oracle, SQLite, and more. |
| **Declarative** | You describe *what* you want, not *how* to get it. The database figures out the best way. |
| **Powerful** | One SQL statement can filter, join, sort, group, and aggregate millions of rows. |
| **Career essential** | SQL is required for backend development, data analysis, data engineering, DevOps, and more. |
| **Standardized** | SQL is an ANSI/ISO standard (since 1986), so core syntax is the same everywhere. |

---

### 2️⃣ WHEN — When Do You Use SQL?

Every time you interact with a relational database, you use SQL:

| Action | SQL Category | Example |
|---|---|---|
| Create or modify tables | **DDL** (Data Definition Language) | `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE` |
| Insert, update, delete data | **DML** (Data Manipulation Language) | `INSERT`, `UPDATE`, `DELETE`, `SELECT` |
| Control user access | **DCL** (Data Control Language) | `GRANT`, `REVOKE` |
| Manage transactions | **TCL** (Transaction Control Language) | `START TRANSACTION`, `COMMIT`, `ROLLBACK` |

---

### 3️⃣ HOW — The Four Categories of SQL

#### 📦 DDL — Data Definition Language

DDL statements define the **structure** (schema) of your database. They create, modify, and remove database objects.

```sql
-- Create a new database
CREATE DATABASE school;

-- Switch to the database
USE school;

-- Create a table
CREATE TABLE teachers (
    teacher_id INT AUTO_INCREMENT PRIMARY KEY,
    name       VARCHAR(100) NOT NULL,
    subject    VARCHAR(50)
);

-- Add a column to an existing table
ALTER TABLE teachers ADD COLUMN hire_date DATE;

-- Remove the table entirely
DROP TABLE teachers;
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `CREATE DATABASE school;` | Creates a new database called `school`. |
| `USE school;` | Selects `school` as the active database for subsequent commands. |
| `CREATE TABLE teachers (...)` | Defines a `teachers` table with three columns. |
| `ALTER TABLE teachers ADD COLUMN hire_date DATE;` | Adds a new `hire_date` column to the existing `teachers` table. |
| `DROP TABLE teachers;` | Permanently deletes the `teachers` table and all its data. |

#### 📝 DML — Data Manipulation Language

DML statements work with the **data** inside tables.

```sql
-- INSERT: add new rows
INSERT INTO teachers (name, subject, hire_date)
VALUES ('Ms. Smith', 'Mathematics', '2022-08-20');

INSERT INTO teachers (name, subject, hire_date)
VALUES ('Mr. Johnson', 'Science', '2021-03-15');

-- SELECT: read data
SELECT name, subject FROM teachers;

-- UPDATE: modify existing rows
UPDATE teachers
SET subject = 'Physics'
WHERE name = 'Mr. Johnson';

-- DELETE: remove rows
DELETE FROM teachers
WHERE name = 'Ms. Smith';
```

**Key points:**
- `INSERT` adds new records.
- `SELECT` retrieves records (the most-used SQL statement).
- `UPDATE` changes existing records — **always use WHERE** or you'll update every row!
- `DELETE` removes records — **always use WHERE** or you'll delete everything!

#### 🔐 DCL — Data Control Language

DCL manages **who can do what** in the database.

```sql
-- Create a new user
CREATE USER 'readonly_user'@'localhost' IDENTIFIED BY 'SecurePass123!';

-- Grant read-only access to the school database
GRANT SELECT ON school.* TO 'readonly_user'@'localhost';

-- Remove access
REVOKE SELECT ON school.* FROM 'readonly_user'@'localhost';
```

| Line | What It Does |
|---|---|
| `CREATE USER ...` | Creates a new database user with a password. |
| `GRANT SELECT ON school.* ...` | Allows the user to run SELECT queries on all tables in `school`. |
| `REVOKE SELECT ON school.* ...` | Removes that permission. |

#### 🔄 TCL — Transaction Control Language

TCL manages **transactions** — groups of operations that must all succeed or all fail.

```sql
-- Start a transaction
START TRANSACTION;

-- Transfer $500 from account 1 to account 2
UPDATE accounts SET balance = balance - 500 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 500 WHERE account_id = 2;

-- If both succeeded, make it permanent
COMMIT;

-- If something went wrong, undo everything
-- ROLLBACK;
```

**Analogy:** A bank transfer. You wouldn't want the money to leave one account without arriving in the other. A transaction ensures both happen or neither happens.

---

### ✏️ Practice Exercise 4

> **Difficulty:** ⭐ Beginner
>
> Classify each of the following SQL statements into its category (DDL, DML, DCL, or TCL):
>
> 1. `DROP DATABASE test_db;`
> 2. `INSERT INTO orders (product, qty) VALUES ('Widget', 10);`
> 3. `GRANT ALL ON shop.* TO 'admin'@'%';`
> 4. `ROLLBACK;`
> 5. `ALTER TABLE products ADD COLUMN weight DECIMAL(5,2);`
> 6. `SELECT * FROM users WHERE active = 1;`
> 7. `REVOKE DELETE ON shop.orders FROM 'intern'@'localhost';`
> 8. `COMMIT;`
>
> **Answers:**
> 1. DDL  2. DML  3. DCL  4. TCL  5. DDL  6. DML  7. DCL  8. TCL

---

## Topic 5 — What Is MySQL?

### 🌍 Real-Life Analogy

If SQL is the **language** you speak, then MySQL is one of the **engines** that listens, understands, and executes what you say. Just like there are many brands of cars that all run on gasoline, there are many database engines (MySQL, PostgreSQL, SQL Server) that all understand SQL — but each has its own features, strengths, and quirks.

---

### 1️⃣ WHY — Why Choose MySQL?

MySQL is one of the most popular relational databases in the world. Here's why:

| Strength | Details |
|---|---|
| **Free and Open Source** | Community edition is free (GPL license). Enterprise edition available for paid support. |
| **Battle-Tested** | Powers Facebook, Twitter/X, Netflix, Airbnb, Uber, YouTube, and millions of websites. |
| **Fast** | Optimized for read-heavy workloads common in web applications. |
| **Cross-Platform** | Runs on Windows, macOS, Linux, Docker, cloud (AWS RDS, Google Cloud SQL, Azure). |
| **Huge Ecosystem** | Works with every major programming language: Python, Java, PHP, Node.js, Go, Ruby, C#. |
| **Large Community** | Decades of tutorials, Stack Overflow answers, and documentation. |
| **Replication & Clustering** | Built-in support for master-slave replication and high availability. |

---

### 2️⃣ WHEN — When to Use MySQL?

✅ **MySQL excels at:**
- **Web applications** — The "M" in the LAMP stack (Linux, Apache, MySQL, PHP).
- **Content management systems** — WordPress, Drupal, Joomla all use MySQL by default.
- **E-commerce platforms** — Magento, WooCommerce, Shopify (historically).
- **Read-heavy workloads** — Blogs, news sites, catalogs, search results.
- **Rapid prototyping** — Easy to install, easy to learn, fast to get started.

⚠️ **Consider alternatives when:**
- You need advanced analytical features (PostgreSQL has richer window functions and CTEs).
- You need a serverless embedded database (SQLite).
- You want a drop-in MySQL replacement with extra features (MariaDB).
- You need to store deeply nested, schema-less documents (MongoDB, a NoSQL option).

---

### 3️⃣ HOW — MySQL in the Ecosystem

#### MySQL Editions

| Edition | Cost | Use Case |
|---|---|---|
| **Community** | Free | Development, small-to-medium production |
| **Enterprise** | Paid | Large-scale production, advanced security, monitoring, backup |
| **Cluster (NDB)** | Paid | Distributed, high-availability deployments |

#### MySQL Architecture Overview

```
┌──────────────────────────────────────────────┐
│              Client Applications              │
│  (PHP, Python, Java, Node.js, MySQL CLI)     │
└──────────────────┬───────────────────────────┘
                   │  SQL Queries
                   ▼
┌──────────────────────────────────────────────┐
│            MySQL Server                       │
│  ┌────────────────────────────────────────┐  │
│  │  Connection Layer                      │  │
│  │  (Authentication, thread management)   │  │
│  ├────────────────────────────────────────┤  │
│  │  SQL Layer                             │  │
│  │  (Parser → Optimizer → Executor)       │  │
│  ├────────────────────────────────────────┤  │
│  │  Storage Engine Layer                  │  │
│  │  (InnoDB, MyISAM, Memory, etc.)       │  │
│  └────────────────────────────────────────┘  │
└──────────────────┬───────────────────────────┘
                   │
                   ▼
┌──────────────────────────────────────────────┐
│            Data Files on Disk                 │
│  (.ibd files, redo logs, undo logs)          │
└──────────────────────────────────────────────┘
```

**How a query flows:**
1. Client sends a SQL query (e.g., `SELECT * FROM users WHERE id = 5;`).
2. **Connection Layer** authenticates the client and manages the session.
3. **SQL Layer** parses the query, optimizes it (chooses the best execution plan), and executes it.
4. **Storage Engine** (usually InnoDB) reads/writes the actual data from/to disk.
5. Results are sent back to the client.

#### Example 9: Your first MySQL session

```sql
-- Check which version of MySQL is running
SELECT VERSION();
-- Example output: 8.0.36

-- Show all databases on the server
SHOW DATABASES;
-- Output:
-- +--------------------+
-- | Database           |
-- +--------------------+
-- | information_schema |
-- | mysql              |
-- | performance_schema |
-- | sys                |
-- +--------------------+

-- Create your first database
CREATE DATABASE my_first_db;

-- Switch to it
USE my_first_db;

-- Create a simple table
CREATE TABLE greetings (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    message VARCHAR(200) NOT NULL
);

-- Insert a row
INSERT INTO greetings (message) VALUES ('Hello, MySQL!');

-- Read it back
SELECT * FROM greetings;
-- Output:
-- +----+---------------+
-- | id | message       |
-- +----+---------------+
-- |  1 | Hello, MySQL! |
-- +----+---------------+
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `SELECT VERSION();` | Returns the MySQL server version — useful for compatibility checks. |
| `SHOW DATABASES;` | Lists all databases the current user can see. |
| `CREATE DATABASE my_first_db;` | Creates a new, empty database. |
| `USE my_first_db;` | Sets `my_first_db` as the active database for all subsequent queries. |
| `CREATE TABLE greetings (...)` | Creates a table with an auto-incrementing `id` and a `message` column. |
| `INSERT INTO greetings (message) VALUES ('Hello, MySQL!');` | Adds one row with the message "Hello, MySQL!". |
| `SELECT * FROM greetings;` | Retrieves all rows and all columns from the `greetings` table. |

---

#### Example 10: MySQL vs. Other Databases — Quick Comparison

| Feature | MySQL | PostgreSQL | SQLite | MariaDB |
|---|---|---|---|---|
| **License** | GPL (free) + Enterprise | PostgreSQL License (free) | Public Domain (free) | GPL (free) |
| **Best For** | Web apps, read-heavy | Analytics, complex queries | Embedded, mobile, testing | MySQL replacement |
| **ACID Compliant** | Yes (InnoDB) | Yes | Yes | Yes |
| **JSON Support** | Yes (since 5.7) | Yes (richer) | Yes (extension) | Yes |
| **Replication** | Built-in | Built-in | Not applicable | Built-in |
| **Stored Procedures** | Yes | Yes (PL/pgSQL) | No | Yes |
| **Full-Text Search** | Yes | Yes | Yes (FTS5) | Yes |
| **Ease of Setup** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Community Size** | Largest | Large | Large | Growing |
| **Default Storage** | InnoDB | Heap-based | B-tree file | InnoDB (Aria) |

> **Tip:** If you're unsure which database to use, MySQL is a safe default for most web applications. You can always migrate later as your needs evolve.

---

### ✏️ Practice Exercise 5

> **Difficulty:** ⭐ Beginner
>
> 1. What does "open source" mean in the context of MySQL? What license does the Community edition use?
> 2. Name three large companies or platforms that use MySQL.
> 3. What is the default storage engine in modern MySQL, and why is it preferred?
> 4. In 2–3 sentences, explain when you might choose PostgreSQL over MySQL.
> 5. Run `SELECT VERSION();` on your own MySQL instance (or a free online sandbox) and note the version number.

---

## 🏁 Part 1 Summary

| Topic | Key Takeaway |
|---|---|
| **Databases** | Organized digital storage with integrity, security, and performance — far superior to flat files. |
| **Relational Databases** | Data stored in tables linked by keys; queried with SQL. |
| **Keys** | Primary keys uniquely identify rows; foreign keys link tables; unique keys enforce distinctness; composite keys combine columns. |
| **SQL** | The universal language for relational databases, split into DDL, DML, DCL, and TCL. |
| **MySQL** | A free, fast, battle-tested relational database ideal for web applications. |

> **Next up:** [Part 2: Installation & Setup](#part-2-installation--setup) — We'll install MySQL on your machine, explore client tools, and run your first real queries.

---

# Part 2: Installation & Setup

> **Goal:** Get MySQL running on your machine, explore client tools, and make your first connection.

---

## Topic 6 — Installing MySQL

### 🌍 Real-Life Analogy

Installing MySQL is like setting up a new appliance in your kitchen. You pick the right model for your counter (operating system), plug it in (install), and turn it on (start the service). Once running, it's ready to take orders (SQL queries).

---

### 1️⃣ WHY — Why Install MySQL Locally?

- **Practice without limits** — No internet required, no shared server restrictions.
- **Full control** — Configure settings, create/drop databases freely.
- **Realistic experience** — Production environments run local or cloud MySQL instances.

---

### 2️⃣ WHEN — When Do You Need a Local Installation?

| Scenario | Recommendation |
|---|---|
| Learning SQL basics | Local install or online sandbox |
| Building a web app | Local MySQL + your app framework |
| Team development | Local for dev, shared staging/production server |
| Quick testing | SQLite or online sandbox may suffice |

---

### 3️⃣ HOW — Step-by-Step Installation

#### 🪟 Windows

```bash
# 1. Download MySQL Installer from https://dev.mysql.com/downloads/installer/
# 2. Run the installer, choose "Developer Default"
# 3. Follow the wizard — set a root password when prompted
# 4. Verify installation:
mysql --version
# Expected output: mysql  Ver 8.0.x for Win64 on x86_64
```

#### 🍎 macOS (Homebrew)

```bash
# 1. Install Homebrew if you haven't already
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Install MySQL
brew install mysql

# 3. Start the MySQL service
brew services start mysql

# 4. Secure the installation (set root password)
mysql_secure_installation

# 5. Verify
mysql --version
# Expected output: mysql  Ver 8.0.x for macos on arm64
```

#### 🐧 Linux (Ubuntu/Debian)

```bash
# 1. Update package lists
sudo apt update

# 2. Install MySQL server
sudo apt install mysql-server -y

# 3. Start and enable the service
sudo systemctl start mysql
sudo systemctl enable mysql

# 4. Secure the installation
sudo mysql_secure_installation

# 5. Verify
mysql --version
# Expected output: mysql  Ver 8.0.x for Linux on x86_64
```

#### 🐳 Docker (Any Platform)

```bash
# Pull and run MySQL in a container
docker run --name mysql-tutorial \
  -e MYSQL_ROOT_PASSWORD=MySecretPass123 \
  -p 3306:3306 \
  -d mysql:8.0

# Connect to it
docker exec -it mysql-tutorial mysql -uroot -pMySecretPass123
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `docker run --name mysql-tutorial` | Creates a new container named `mysql-tutorial`. |
| `-e MYSQL_ROOT_PASSWORD=MySecretPass123` | Sets the root password via an environment variable. |
| `-p 3306:3306` | Maps port 3306 on your machine to port 3306 in the container. |
| `-d mysql:8.0` | Runs MySQL 8.0 in detached (background) mode. |
| `docker exec -it mysql-tutorial mysql ...` | Opens an interactive MySQL shell inside the container. |

---

### ✏️ Practice Exercise 6

> **Difficulty:** ⭐ Beginner
>
> 1. Install MySQL on your computer using the method appropriate for your OS.
> 2. Run `mysql --version` and note the version number.
> 3. Start the MySQL service and confirm it's running (use `systemctl status mysql` on Linux, `brew services list` on macOS, or check Services on Windows).

---

## Topic 7 — MySQL Clients & Tools

### 🌍 Real-Life Analogy

MySQL Server is like a restaurant kitchen. The **clients and tools** are the different ways you can place your order — you can walk up to the counter (command line), use a tablet menu (GUI tool), or order through an app (programming language driver).

---

### 1️⃣ WHY — Why Do You Need Clients?

MySQL Server runs in the background. You need a **client** to send SQL queries and see results. Different clients suit different workflows.

---

### 2️⃣ WHEN — Choosing the Right Tool

| Tool | Best For | Type |
|---|---|---|
| **mysql CLI** | Quick queries, scripting, automation | Command line |
| **MySQL Workbench** | Visual schema design, complex queries, admin tasks | GUI (official) |
| **phpMyAdmin** | Web-based management (common on shared hosting) | Web GUI |
| **DBeaver** | Multi-database support, free, feature-rich | GUI (third-party) |
| **DataGrip** | Professional IDE for databases (JetBrains) | GUI (paid) |

---

### 3️⃣ HOW — Using the mysql Command-Line Client

#### Example 11: Basic CLI session

```sql
-- Connect to MySQL as root
-- (run this in your terminal, not inside MySQL)
-- mysql -u root -p

-- Once connected, you'll see the mysql> prompt

-- Show all databases
SHOW DATABASES;

-- Create a practice database
CREATE DATABASE practice;

-- Use it
USE practice;

-- Show current database
SELECT DATABASE();
-- Output: practice

-- Show tables (empty for now)
SHOW TABLES;
-- Output: Empty set
```

#### Example 12: Useful CLI commands

```sql
-- Show server status
STATUS;

-- Show all tables in current database
SHOW TABLES;

-- Describe a table's structure
DESCRIBE employees;
-- or
SHOW COLUMNS FROM employees;

-- Show the CREATE statement used to make a table
SHOW CREATE TABLE employees;

-- Clear the screen (in the CLI)
-- \! clear    (Linux/macOS)
-- \! cls      (Windows)

-- Exit MySQL CLI
EXIT;
-- or
QUIT;
```

---

### ✏️ Practice Exercise 7

> **Difficulty:** ⭐ Beginner
>
> 1. Open the `mysql` CLI and connect as root.
> 2. Run `SHOW DATABASES;` and list what you see.
> 3. Create a database called `exercise_db`, switch to it, then run `SELECT DATABASE();` to confirm.
> 4. (Optional) Download MySQL Workbench or DBeaver, connect to your local MySQL, and explore the interface.

---

## Topic 8 — Connecting to MySQL

### 🌍 Real-Life Analogy

Connecting to MySQL is like making a phone call: you need the **phone number** (host/port), you need to identify yourself (**username**), and you need to prove it's you (**password**). Once connected, you can start your conversation (run queries).

---

### 1️⃣ WHY — Why Understand Connections?

Every application that uses MySQL needs to establish a connection. Understanding connection parameters helps you:
- Debug "Access denied" and "Can't connect" errors.
- Configure remote access securely.
- Set up connection pools in your application.

---

### 2️⃣ WHEN — Connection Scenarios

| Scenario | Host | Port | Notes |
|---|---|---|---|
| Local development | `localhost` or `127.0.0.1` | `3306` | Default setup |
| Docker container | `127.0.0.1` | Mapped port | Use `-p` flag |
| Remote server | Server IP or hostname | `3306` | Firewall must allow it |
| Cloud (AWS RDS) | Endpoint URL | `3306` | Security group rules |

---

### 3️⃣ HOW — Making Connections

#### Example 13: Command-line connections

```bash
# Basic local connection
mysql -u root -p

# Specify host and port
mysql -u root -p -h 127.0.0.1 -P 3306

# Connect and immediately select a database
mysql -u root -p my_database

# Execute a single query without entering interactive mode
mysql -u root -p -e "SHOW DATABASES;"
```

| Flag | Meaning |
|---|---|
| `-u root` | Connect as user `root` |
| `-p` | Prompt for password |
| `-h 127.0.0.1` | Connect to host `127.0.0.1` |
| `-P 3306` | Use port `3306` |
| `-e "..."` | Execute a query and exit |

#### Example 14: First commands after connecting

```sql
-- Check your current user
SELECT CURRENT_USER();
-- Output: root@localhost

-- Check the server version
SELECT VERSION();
-- Output: 8.0.36

-- See all databases you have access to
SHOW DATABASES;

-- See system variables
SHOW VARIABLES LIKE 'max_connections';
-- Output: max_connections | 151

-- See running processes
SHOW PROCESSLIST;
```

#### Example 15: Connection strings in applications

```python
# Python (using mysql-connector-python)
import mysql.connector

connection = mysql.connector.connect(
    host="localhost",       # database server address
    port=3306,              # port number
    user="root",            # username
    password="MyPass123",   # password
    database="practice"     # default database
)

cursor = connection.cursor()
cursor.execute("SELECT VERSION()")
print(cursor.fetchone())    # ('8.0.36',)
connection.close()
```

```javascript
// Node.js (using mysql2)
const mysql = require('mysql2');

const connection = mysql.createConnection({
  host: 'localhost',
  port: 3306,
  user: 'root',
  password: 'MyPass123',
  database: 'practice'
});

connection.query('SELECT VERSION() AS version', (err, results) => {
  console.log(results[0].version);  // 8.0.36
});

connection.end();
```

---

### ✏️ Practice Exercise 8

> **Difficulty:** ⭐ Beginner
>
> 1. Connect to MySQL using the CLI with `mysql -u root -p`.
> 2. Run `SELECT CURRENT_USER();` and `SELECT VERSION();`.
> 3. Try connecting with a wrong password — what error message do you see?
> 4. Run `mysql -u root -p -e "SELECT 1+1 AS result;"` to execute a query non-interactively.

---

## 🏁 Part 2 Summary

| Topic | Key Takeaway |
|---|---|
| **Installing MySQL** | Available on all platforms; use `mysql_secure_installation` after install. |
| **Clients & Tools** | CLI for speed and scripting; Workbench/DBeaver for visual management. |
| **Connecting** | You need host, port, username, and password. Use `-u`, `-p`, `-h`, `-P` flags. |

> **Next up:** [Part 3: SQL Fundamentals](#part-3-sql-fundamentals) — Creating databases and tables, data types, and CRUD operations.

---

# Part 3: SQL Fundamentals

> **Goal:** Master the core SQL operations — creating structures, inserting data, modifying records, and querying results.

---

## Topic 9 — CREATE and DROP Database/Table

### 🌍 Real-Life Analogy

`CREATE` is like building a new filing cabinet (database) and adding labeled drawers (tables). `DROP` is like throwing the entire cabinet into a dumpster — everything inside is gone forever.

---

### 1️⃣ WHY — Why CREATE and DROP?

- **CREATE** establishes the structure where your data will live.
- **DROP** removes structures you no longer need, freeing resources.
- Understanding these is fundamental — you can't store data without tables.

---

### 2️⃣ WHEN — When to Use?

| Command | Use When |
|---|---|
| `CREATE DATABASE` | Starting a new project or application |
| `CREATE TABLE` | Defining a new entity (users, products, orders) |
| `DROP DATABASE` | Removing an entire project's data (use with extreme caution!) |
| `DROP TABLE` | Removing a table you no longer need |
| `IF EXISTS` / `IF NOT EXISTS` | Writing scripts that must be re-runnable without errors |

---

### 3️⃣ HOW — Syntax and Examples

#### Example 16: Creating and dropping databases

```sql
-- Create a database
CREATE DATABASE shop;

-- Create only if it doesn't already exist (avoids errors in scripts)
CREATE DATABASE IF NOT EXISTS shop;

-- Show all databases
SHOW DATABASES;

-- Switch to the database
USE shop;

-- Drop a database (CAUTION: destroys everything inside!)
DROP DATABASE IF EXISTS shop;
```

#### Example 17: Creating tables with various options

```sql
CREATE DATABASE IF NOT EXISTS shop;
USE shop;

-- Basic table creation
CREATE TABLE categories (
    category_id   INT AUTO_INCREMENT PRIMARY KEY,
    category_name VARCHAR(50) NOT NULL UNIQUE
);

-- Table with more constraints
CREATE TABLE products (
    product_id   INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    category_id  INT,
    price        DECIMAL(10,2) NOT NULL CHECK (price >= 0),
    stock        INT DEFAULT 0 CHECK (stock >= 0),
    created_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(category_id)
);

-- View the table structure
DESCRIBE products;

-- See the full CREATE statement
SHOW CREATE TABLE products;

-- Drop a table safely
DROP TABLE IF EXISTS products;
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `CREATE DATABASE IF NOT EXISTS shop;` | Creates `shop` database only if it doesn't exist — safe for scripts. |
| `CREATE TABLE categories (...)` | Defines a categories table with an auto-incrementing PK. |
| `category_name VARCHAR(50) NOT NULL UNIQUE` | Name is required and must be unique. |
| `price DECIMAL(10,2) NOT NULL CHECK (price >= 0)` | Price has 2 decimal places and cannot be negative. |
| `stock INT DEFAULT 0 CHECK (stock >= 0)` | Stock defaults to 0 and cannot be negative. |
| `created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP` | Automatically records when the row was created. |
| `FOREIGN KEY (category_id) REFERENCES categories(category_id)` | Links products to categories. |

---

### ✏️ Practice Exercise 9

> **Difficulty:** ⭐ Beginner
>
> 1. Create a database called `library`.
> 2. Inside it, create a table called `books` with columns: `book_id` (PK, auto-increment), `title` (required, max 200 chars), `author` (required, max 100 chars), `isbn` (unique, max 20 chars), `published_year` (integer), `price` (decimal, must be >= 0).
> 3. Run `DESCRIBE books;` to verify the structure.
> 4. Drop the table, then drop the database.

---

## Topic 10 — Data Types in MySQL

### 🌍 Real-Life Analogy

Data types are like different kinds of containers. You wouldn't store soup in a paper bag or documents in a fishbowl. Similarly, you store numbers in numeric columns, text in string columns, and dates in date columns. Choosing the right container (data type) ensures efficiency and correctness.

---

### 1️⃣ WHY — Why Do Data Types Matter?

| Reason | Explanation |
|---|---|
| **Storage efficiency** | `TINYINT` uses 1 byte; `BIGINT` uses 8. Choosing wisely saves disk space. |
| **Validation** | A `DATE` column rejects "hello" — only valid dates are accepted. |
| **Performance** | Numeric comparisons are faster than string comparisons. |
| **Correctness** | Arithmetic on numbers, date math on dates — the right type enables the right operations. |

---

### 2️⃣ WHEN — Choosing the Right Type

| Data | Recommended Type | Why |
|---|---|---|
| Age, quantity | `INT` or `SMALLINT` | Whole numbers, small range |
| Price, salary | `DECIMAL(10,2)` | Exact decimal precision (never use FLOAT for money!) |
| Short text (name) | `VARCHAR(100)` | Variable-length, efficient |
| Long text (article) | `TEXT` | Up to 65,535 characters |
| Yes/No flag | `BOOLEAN` (alias for `TINYINT(1)`) | Simple true/false |
| Date without time | `DATE` | `YYYY-MM-DD` |
| Date with time | `DATETIME` or `TIMESTAMP` | `YYYY-MM-DD HH:MM:SS` |
| Fixed set of values | `ENUM('small','medium','large')` | Restricts to defined options |
| Files, images | `BLOB` | Binary data (but usually store files on disk, not in DB) |

---

### 3️⃣ HOW — Data Types Reference

#### Example 18: Comprehensive data types demonstration

```sql
CREATE TABLE data_type_demo (
    -- Integer types
    tiny_col    TINYINT,          -- -128 to 127 (1 byte)
    small_col   SMALLINT,         -- -32,768 to 32,767 (2 bytes)
    medium_col  MEDIUMINT,        -- -8M to 8M (3 bytes)
    int_col     INT,              -- -2B to 2B (4 bytes)
    big_col     BIGINT,           -- very large (8 bytes)
    unsigned_col INT UNSIGNED,    -- 0 to ~4.2B

    -- Decimal types
    float_col   FLOAT,            -- approximate (avoid for money!)
    double_col  DOUBLE,           -- more precise approximate
    decimal_col DECIMAL(10,2),    -- exact: 10 digits total, 2 after decimal

    -- String types
    char_col    CHAR(10),         -- fixed-length: always 10 chars (padded)
    varchar_col VARCHAR(255),     -- variable-length: up to 255 chars
    text_col    TEXT,             -- up to 65,535 chars
    longtext_col LONGTEXT,       -- up to 4GB

    -- Date/Time types
    date_col     DATE,            -- 'YYYY-MM-DD'
    time_col     TIME,            -- 'HH:MM:SS'
    datetime_col DATETIME,        -- 'YYYY-MM-DD HH:MM:SS'
    timestamp_col TIMESTAMP,      -- like DATETIME but auto-converts to UTC
    year_col     YEAR,            -- 4-digit year

    -- Other types
    bool_col    BOOLEAN,          -- alias for TINYINT(1)
    enum_col    ENUM('S','M','L','XL'),  -- one value from a fixed list
    set_col     SET('read','write','admin'), -- one or more from a list
    json_col    JSON,             -- native JSON data
    blob_col    BLOB              -- binary data
);
```

#### Data Types Quick Reference Table

| Category | Type | Size | Range / Notes |
|---|---|---|---|
| **Integer** | `TINYINT` | 1 byte | -128 to 127 |
| | `SMALLINT` | 2 bytes | -32,768 to 32,767 |
| | `INT` | 4 bytes | -2.1B to 2.1B |
| | `BIGINT` | 8 bytes | ±9.2 quintillion |
| **Decimal** | `DECIMAL(M,D)` | Varies | Exact; M total digits, D after decimal |
| | `FLOAT` | 4 bytes | Approximate (avoid for money) |
| **String** | `CHAR(N)` | N bytes | Fixed-length; padded with spaces |
| | `VARCHAR(N)` | Up to N+1 | Variable-length; only uses what's needed |
| | `TEXT` | Up to 64KB | Large text blocks |
| **Date** | `DATE` | 3 bytes | `YYYY-MM-DD` |
| | `DATETIME` | 8 bytes | `YYYY-MM-DD HH:MM:SS` |
| | `TIMESTAMP` | 4 bytes | Like DATETIME; stored as UTC |
| **Other** | `BOOLEAN` | 1 byte | `TRUE` (1) or `FALSE` (0) |
| | `ENUM` | 1-2 bytes | One value from a list |
| | `JSON` | Varies | Native JSON document storage |

---

### ✏️ Practice Exercise 10

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Why should you use `DECIMAL(10,2)` instead of `FLOAT` for a `price` column?
> 2. What's the difference between `CHAR(10)` and `VARCHAR(10)`?
> 3. Create a table called `events` with: `event_id` (PK), `event_name` (varchar), `event_date` (date), `event_time` (time), `location` (varchar), `is_free` (boolean), `capacity` (int, unsigned), `ticket_price` (decimal).
> 4. What data type would you use to store a blog post body? Why?

---

## Topic 11 — INSERT Data

### 🌍 Real-Life Analogy

`INSERT` is like filling out a new row in a ledger or adding a new contact to your phone. You specify what goes in each field.

---

### 1️⃣ WHY — Why INSERT?

Without `INSERT`, your tables are empty. It's how data enters the database — from user registrations, to product catalogs, to sensor readings.

---

### 2️⃣ WHEN — When and How to Insert

| Method | Use When |
|---|---|
| Single-row INSERT | Adding one record at a time |
| Multi-row INSERT | Bulk-loading data (much faster than individual inserts) |
| INSERT IGNORE | Skipping rows that violate constraints (e.g., duplicates) |
| INSERT ... ON DUPLICATE KEY UPDATE | Upserting: insert if new, update if already exists |

---

### 3️⃣ HOW — INSERT Variations

#### Example 19: Single-row insert

```sql
CREATE TABLE IF NOT EXISTS customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(100) NOT NULL,
    email       VARCHAR(150) NOT NULL UNIQUE,
    city        VARCHAR(100)
);

-- Insert one row (specifying columns)
INSERT INTO customers (name, email, city)
VALUES ('Alice Johnson', 'alice@example.com', 'New York');

-- Insert one row (all columns in order — less safe, but works)
-- Note: skip auto_increment column by providing NULL
INSERT INTO customers
VALUES (NULL, 'Bob Smith', 'bob@example.com', 'London');
```

#### Example 20: Multi-row insert

```sql
-- Insert multiple rows at once (much faster than individual INSERTs)
INSERT INTO customers (name, email, city) VALUES
    ('Charlie Brown', 'charlie@example.com', 'Paris'),
    ('Diana Prince', 'diana@example.com', 'Athens'),
    ('Eve Davis', 'eve@example.com', 'Tokyo');
```

#### Example 21: INSERT IGNORE and ON DUPLICATE KEY UPDATE

```sql
-- INSERT IGNORE: silently skips if a UNIQUE constraint is violated
INSERT IGNORE INTO customers (name, email, city)
VALUES ('Alice Clone', 'alice@example.com', 'Boston');
-- No error — the row is simply not inserted because email already exists

-- ON DUPLICATE KEY UPDATE: update the existing row instead of failing
INSERT INTO customers (name, email, city)
VALUES ('Alice Johnson', 'alice@example.com', 'San Francisco')
ON DUPLICATE KEY UPDATE city = VALUES(city);
-- Alice's city is now updated to 'San Francisco'

-- Verify
SELECT * FROM customers WHERE email = 'alice@example.com';
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `INSERT IGNORE INTO ...` | Tries to insert; if a UNIQUE/PK violation occurs, silently skips the row. |
| `ON DUPLICATE KEY UPDATE city = VALUES(city)` | If the row already exists (duplicate key), updates the `city` column with the new value. |

---

### ✏️ Practice Exercise 11

> **Difficulty:** ⭐ Beginner
>
> 1. Using the `customers` table, insert 3 new customers in a single multi-row INSERT.
> 2. Try inserting a customer with a duplicate email using `INSERT IGNORE`. What happens?
> 3. Use `INSERT ... ON DUPLICATE KEY UPDATE` to change an existing customer's city.

---

## Topic 12 — UPDATE Data

### 🌍 Real-Life Analogy

`UPDATE` is like using an eraser and pencil on a ledger — you find the entry you want to change and modify it in place. The row stays; only specific values change.

---

### 1️⃣ WHY — Why UPDATE?

Data changes over time — customers move, prices adjust, statuses change. `UPDATE` lets you modify existing records without deleting and re-inserting them.

---

### 2️⃣ WHEN — When to Use UPDATE

| Scenario | Example |
|---|---|
| Changing a single field | Update a customer's email |
| Bulk updates | Increase all prices by 10% |
| Status changes | Mark an order as "shipped" |
| Conditional updates | Deactivate users who haven't logged in for a year |

---

### 3️⃣ HOW — UPDATE Syntax and Safety

#### Example 22: Basic UPDATE

```sql
-- Update a single column for a specific row
UPDATE customers
SET city = 'Chicago'
WHERE email = 'bob@example.com';

-- Update multiple columns at once
UPDATE customers
SET name = 'Robert Smith', city = 'Seattle'
WHERE customer_id = 2;
```

#### Example 23: Bulk and conditional UPDATE

```sql
-- Increase all product prices by 10%
UPDATE products
SET price = price * 1.10;

-- Conditional update: give a discount only to expensive products
UPDATE products
SET price = price * 0.90
WHERE price > 100.00;

-- Update with a LIMIT (useful for batch processing)
UPDATE customers
SET city = 'Unknown'
WHERE city IS NULL
LIMIT 100;
```

> ⚠️ **CRITICAL WARNING:** Always use a `WHERE` clause with `UPDATE`. Without it, **every row** in the table is modified!

```sql
-- DANGEROUS! This updates ALL customers!
UPDATE customers SET city = 'Nowhere';
-- Every single customer now has city = 'Nowhere'

-- SAFE: This updates only one customer
UPDATE customers SET city = 'Nowhere' WHERE customer_id = 5;
```

---

### ✏️ Practice Exercise 12

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Update Alice's city to "Boston" using her `customer_id`.
> 2. Write an UPDATE that changes all customers in "Tokyo" to "Osaka".
> 3. What happens if you run `UPDATE customers SET name = 'Test';` without a WHERE clause? (Don't actually run this on important data!)

---

## Topic 13 — DELETE and TRUNCATE

### 🌍 Real-Life Analogy

- `DELETE` is like carefully removing specific pages from a binder — you choose which ones go.
- `TRUNCATE` is like dumping the entire binder's contents into the shredder — all pages gone, but the empty binder (table structure) remains.
- `DROP` is like throwing out the entire binder — gone forever.

---

### 1️⃣ WHY — Why Remove Data?

Old records, test data, cancelled orders, expired sessions — databases need cleanup. Using the right removal command protects you from accidental data loss.

---

### 2️⃣ WHEN — Choosing the Right Command

| Command | What It Removes | Reversible? | Speed | Resets AUTO_INCREMENT? |
|---|---|---|---|---|
| `DELETE` | Specific rows (with WHERE) | Yes (in a transaction) | Slower (row-by-row) | No |
| `TRUNCATE` | All rows | No | Very fast | Yes |
| `DROP TABLE` | Entire table + data | No | Instant | N/A (table is gone) |

---

### 3️⃣ HOW — DELETE, TRUNCATE, DROP

#### Example 24: DELETE with WHERE

```sql
-- Delete a specific customer
DELETE FROM customers
WHERE customer_id = 5;

-- Delete all customers in a specific city
DELETE FROM customers
WHERE city = 'Unknown';

-- Delete with a limit
DELETE FROM customers
WHERE city = 'Old City'
LIMIT 10;
```

#### Example 25: TRUNCATE vs DELETE vs DROP

```sql
-- TRUNCATE: remove ALL rows (fast, cannot be rolled back)
TRUNCATE TABLE customers;
-- Table structure remains, auto_increment resets to 1

-- DELETE all rows (slower, CAN be rolled back in a transaction)
DELETE FROM customers;
-- Table structure remains, auto_increment does NOT reset

-- DROP: destroy the entire table
DROP TABLE customers;
-- Table is completely gone — structure and data
```

> ⚠️ **CRITICAL WARNING:** `DELETE` without `WHERE` deletes **every row**, just like `TRUNCATE`, but slower!

```sql
-- DANGEROUS! Deletes ALL rows!
DELETE FROM customers;

-- SAFE: Deletes only matching rows
DELETE FROM customers WHERE customer_id = 3;
```

---

### ✏️ Practice Exercise 13

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Insert 5 rows into a test table, then DELETE 2 specific rows using WHERE.
> 2. What's the difference between `DELETE FROM test_table;` and `TRUNCATE TABLE test_table;`?
> 3. If you run `TRUNCATE TABLE orders;` and the next INSERT gets `order_id = 1`, what does that tell you about AUTO_INCREMENT behavior?
> 4. Can you TRUNCATE a table that has foreign key references pointing to it? Try it and report what happens.

---

## Topic 14 — Basic SELECT Queries

### 🌍 Real-Life Analogy

`SELECT` is like asking a librarian a question: "Show me all mystery books published after 2020, sorted by title." You describe what you want, and the database fetches it.

---

### 1️⃣ WHY — Why SELECT?

`SELECT` is the **most-used SQL statement**. It's how you read data — whether displaying a user profile, generating a report, or feeding data to an application.

---

### 2️⃣ WHEN — When to Use SELECT Features

| Feature | Use When |
|---|---|
| `SELECT *` | Quick exploration (avoid in production!) |
| `SELECT col1, col2` | You know exactly which columns you need |
| `WHERE` | Filtering rows by conditions |
| `ORDER BY` | Sorting results |
| `LIMIT` | Pagination or getting top N results |
| `DISTINCT` | Removing duplicate values from results |
| `AS` (aliases) | Renaming columns for readability |

---

### 3️⃣ HOW — SELECT Essentials

#### Example 26: Setup data for SELECT examples

```sql
CREATE DATABASE IF NOT EXISTS store;
USE store;

CREATE TABLE products (
    product_id   INT AUTO_INCREMENT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    category     VARCHAR(50),
    price        DECIMAL(10,2) NOT NULL,
    stock        INT DEFAULT 0
);

INSERT INTO products (product_name, category, price, stock) VALUES
    ('Laptop',       'Electronics', 999.99, 50),
    ('Headphones',   'Electronics', 79.99,  200),
    ('Desk Chair',   'Furniture',   249.99, 30),
    ('Notebook',     'Stationery',  4.99,   500),
    ('Pen Pack',     'Stationery',  2.99,   1000),
    ('Monitor',      'Electronics', 349.99, 75),
    ('Standing Desk','Furniture',   599.99, 15),
    ('Mouse',        'Electronics', 29.99,  300),
    ('Bookshelf',    'Furniture',   189.99, 25),
    ('Tablet',       'Electronics', 449.99, 60);
```

#### Example 27: Basic SELECT queries

```sql
-- Select all columns and all rows
SELECT * FROM products;

-- Select specific columns only
SELECT product_name, price FROM products;

-- Alias columns for readability
SELECT product_name AS "Product", price AS "Price (USD)" FROM products;

-- Get distinct categories (unique values only)
SELECT DISTINCT category FROM products;
-- Output: Electronics, Furniture, Stationery
```

#### Example 28: Filtering with WHERE

```sql
-- Exact match
SELECT * FROM products WHERE category = 'Electronics';

-- Comparison operators
SELECT * FROM products WHERE price > 100;
SELECT * FROM products WHERE stock <= 50;

-- BETWEEN (inclusive range)
SELECT * FROM products WHERE price BETWEEN 50 AND 500;

-- IN (match any value in a list)
SELECT * FROM products WHERE category IN ('Furniture', 'Stationery');

-- LIKE (pattern matching)
SELECT * FROM products WHERE product_name LIKE 'M%';     -- starts with M
SELECT * FROM products WHERE product_name LIKE '%desk%';  -- contains 'desk' (case-insensitive)
SELECT * FROM products WHERE product_name LIKE '___';     -- exactly 3 characters

-- IS NULL / IS NOT NULL
SELECT * FROM products WHERE category IS NOT NULL;

-- Combining conditions with AND, OR, NOT
SELECT * FROM products
WHERE category = 'Electronics' AND price < 100;

SELECT * FROM products
WHERE category = 'Furniture' OR price > 500;

SELECT * FROM products
WHERE NOT category = 'Stationery';
```

#### Example 29: Sorting, limiting, and combining

```sql
-- Sort by price ascending (cheapest first)
SELECT * FROM products ORDER BY price ASC;

-- Sort by price descending (most expensive first)
SELECT * FROM products ORDER BY price DESC;

-- Sort by category, then by price within each category
SELECT * FROM products ORDER BY category ASC, price DESC;

-- Limit results (top 3 most expensive)
SELECT * FROM products ORDER BY price DESC LIMIT 3;

-- Pagination: skip first 3, get next 3 (page 2)
SELECT * FROM products ORDER BY price DESC LIMIT 3 OFFSET 3;

-- Combining everything
SELECT product_name AS "Product", price AS "Price"
FROM products
WHERE category = 'Electronics'
ORDER BY price DESC
LIMIT 5;
```

**Execution order of a SELECT statement:**

| Order | Clause | Purpose |
|---|---|---|
| 1 | `FROM` | Which table to query |
| 2 | `WHERE` | Filter rows |
| 3 | `GROUP BY` | Group rows (covered in Part 5) |
| 4 | `HAVING` | Filter groups (covered in Part 5) |
| 5 | `SELECT` | Choose columns |
| 6 | `ORDER BY` | Sort results |
| 7 | `LIMIT` | Restrict number of rows returned |

---

### ✏️ Practice Exercise 14

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> Using the `products` table above:
> 1. Select all electronics products sorted by price (cheapest first).
> 2. Find all products with stock less than 50.
> 3. Find products whose name contains "desk" (case-insensitive).
> 4. Select the 3 cheapest products (any category).
> 5. Select products priced between $10 and $300 that are NOT in the "Stationery" category.

---

## Topic 14A — String Functions

### 🌍 Real-Life Analogy

String functions are like a **word processor's find-and-replace, spell-check, and formatting tools** — they let you clean, transform, search, and combine text data stored in your database.

---

### 1️⃣ WHY — Why String Functions?

- Clean dirty data (extra spaces, inconsistent casing).
- Format output for reports and display.
- Search and extract parts of text.
- Combine columns into readable strings.

---

### 2️⃣ HOW — Essential String Functions

#### Example 30: String manipulation functions

```sql
-- CONCAT: combine strings
SELECT CONCAT('Hello', ' ', 'World') AS greeting;
-- Output: Hello World

-- CONCAT_WS: combine with a separator
SELECT CONCAT_WS(', ', 'Alice', 'Bob', 'Charlie') AS names;
-- Output: Alice, Bob, Charlie

-- UPPER / LOWER: change case
SELECT UPPER('hello world') AS upper_case, LOWER('HELLO WORLD') AS lower_case;
-- Output: HELLO WORLD | hello world

-- LENGTH: byte length | CHAR_LENGTH: character length
SELECT LENGTH('Hello') AS byte_len, CHAR_LENGTH('Hello') AS char_len;
-- Output: 5 | 5
-- For UTF-8: LENGTH('é') = 2 bytes, CHAR_LENGTH('é') = 1 character

-- SUBSTRING (or SUBSTR): extract part of a string
SELECT SUBSTRING('Hello World', 1, 5) AS first_five;
-- Output: Hello
SELECT SUBSTRING('Hello World', 7) AS from_seventh;
-- Output: World

-- LEFT / RIGHT: get characters from start/end
SELECT LEFT('Hello World', 5) AS left_five, RIGHT('Hello World', 5) AS right_five;
-- Output: Hello | World

-- TRIM / LTRIM / RTRIM: remove whitespace
SELECT TRIM('   Hello   ') AS trimmed;
-- Output: Hello
SELECT TRIM(LEADING '0' FROM '00042') AS no_leading_zeros;
-- Output: 42

-- REPLACE: substitute text
SELECT REPLACE('Hello World', 'World', 'MySQL') AS replaced;
-- Output: Hello MySQL

-- REVERSE: reverse a string
SELECT REVERSE('Hello') AS reversed;
-- Output: olleH

-- REPEAT: repeat a string N times
SELECT REPEAT('Ha', 3) AS laugh;
-- Output: HaHaHa

-- LPAD / RPAD: pad to a specified length
SELECT LPAD('42', 5, '0') AS padded_left, RPAD('Hi', 10, '.') AS padded_right;
-- Output: 00042 | Hi........

-- LOCATE / INSTR: find position of substring (1-based; 0 = not found)
SELECT LOCATE('World', 'Hello World') AS position;
-- Output: 7

-- FORMAT: format a number as a string with commas
SELECT FORMAT(1234567.891, 2) AS formatted;
-- Output: 1,234,567.89

-- INSERT (string): insert text into a string at a position
SELECT INSERT('Hello World', 6, 1, ' Beautiful') AS modified;
-- Output: Hello Beautiful World
```

#### Example 31: Practical string usage in queries

```sql
-- Clean and format customer names
SELECT
    customer_id,
    TRIM(UPPER(name)) AS clean_name,
    LOWER(email) AS clean_email,
    CONCAT(LEFT(name, 1), '. ', SUBSTRING_INDEX(email, '@', 1)) AS short_name
FROM customers;

-- Search for names containing a substring (case-insensitive)
SELECT * FROM customers WHERE LOWER(name) LIKE '%smith%';

-- Extract domain from email
SELECT name, SUBSTRING_INDEX(email, '@', -1) AS email_domain
FROM customers;

-- Generate initials from a full name
SELECT
    name,
    CONCAT(
        LEFT(name, 1),
        LEFT(SUBSTRING_INDEX(name, ' ', -1), 1)
    ) AS initials
FROM customers;
```

**Complete String Functions Reference:**

| Function | Purpose | Example | Result |
|---|---|---|---|
| `CONCAT(a, b, ...)` | Join strings | `CONCAT('a','b')` | `ab` |
| `CONCAT_WS(sep, a, b)` | Join with separator | `CONCAT_WS('-','2024','01')` | `2024-01` |
| `UPPER(s)` | Uppercase | `UPPER('hi')` | `HI` |
| `LOWER(s)` | Lowercase | `LOWER('HI')` | `hi` |
| `LENGTH(s)` | Byte length | `LENGTH('Hi')` | `2` |
| `CHAR_LENGTH(s)` | Character length | `CHAR_LENGTH('Hi')` | `2` |
| `SUBSTRING(s, pos, len)` | Extract part | `SUBSTRING('Hello',1,3)` | `Hel` |
| `LEFT(s, n)` / `RIGHT(s, n)` | First/last n chars | `LEFT('Hello',2)` | `He` |
| `TRIM(s)` | Remove whitespace | `TRIM(' Hi ')` | `Hi` |
| `REPLACE(s, from, to)` | Substitute text | `REPLACE('abc','b','x')` | `axc` |
| `REVERSE(s)` | Reverse string | `REVERSE('abc')` | `cba` |
| `LPAD(s, len, pad)` | Left-pad | `LPAD('5',3,'0')` | `005` |
| `LOCATE(sub, s)` | Find position | `LOCATE('l','Hello')` | `3` |
| `SUBSTRING_INDEX(s, d, n)` | Split by delimiter | `SUBSTRING_INDEX('a@b','@',1)` | `a` |
| `FORMAT(n, d)` | Number → formatted string | `FORMAT(1234.5,2)` | `1,234.50` |

---

### ✏️ Practice Exercise 14A

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Write a query that displays all product names in uppercase with their prices formatted with 2 decimal places.
> 2. Extract the first 3 characters of each product name as a product code.
> 3. For the `customers` table, extract the email domain (part after @) for each customer.
> 4. Clean a customer name by trimming whitespace and capitalizing the first letter of each word.

---

## Topic 14B — Date & Time Functions

### 🌍 Real-Life Analogy

Date functions are like a **calendar and clock toolkit** — they let you calculate ages, find deadlines, measure time differences, format dates for reports, and extract parts like year, month, or day.

---

### 1️⃣ WHY — Why Date Functions?

- Calculate ages, durations, and deadlines.
- Filter data by time ranges (this month's orders, last year's revenue).
- Format dates for different locales and reports.
- Schedule and track events.

---

### 2️⃣ HOW — Essential Date Functions

#### Example 32: Getting current date and time

```sql
-- Current date and time
SELECT NOW()      AS current_datetime;    -- 2026-02-21 14:30:00
SELECT CURDATE()  AS current_date;        -- 2026-02-21
SELECT CURTIME()  AS current_time;        -- 14:30:00
SELECT UNIX_TIMESTAMP() AS epoch_seconds; -- 1771686600
```

#### Example 33: Extracting parts of a date

```sql
SELECT
    NOW() AS full_datetime,
    YEAR(NOW())    AS yr,       -- 2026
    MONTH(NOW())   AS mo,       -- 2
    DAY(NOW())     AS dy,       -- 21
    HOUR(NOW())    AS hr,       -- 14
    MINUTE(NOW())  AS min,      -- 30
    SECOND(NOW())  AS sec,      -- 0
    DAYNAME(NOW()) AS day_name, -- Saturday
    MONTHNAME(NOW()) AS month_name, -- February
    DAYOFWEEK(NOW()) AS dow,    -- 7 (1=Sunday, 7=Saturday)
    DAYOFYEAR(NOW()) AS doy,    -- 52
    WEEK(NOW())    AS week_num, -- 8
    QUARTER(NOW()) AS qtr;      -- 1
```

#### Example 34: Date arithmetic

```sql
-- Add/subtract intervals
SELECT DATE_ADD('2026-02-21', INTERVAL 30 DAY) AS plus_30_days;     -- 2026-03-23
SELECT DATE_SUB('2026-02-21', INTERVAL 3 MONTH) AS minus_3_months;  -- 2025-11-21
SELECT DATE_ADD(NOW(), INTERVAL 2 HOUR) AS plus_2_hours;

-- Shorthand with + and -
SELECT '2026-02-21' + INTERVAL 1 YEAR AS next_year;    -- 2027-02-21

-- Difference between dates
SELECT DATEDIFF('2026-12-31', '2026-01-01') AS days_in_year;  -- 364
SELECT TIMESTAMPDIFF(MONTH, '2025-06-15', '2026-02-21') AS months_diff;  -- 8
SELECT TIMESTAMPDIFF(YEAR, '1990-05-15', CURDATE()) AS age;  -- calculates age

-- Last day of the month
SELECT LAST_DAY('2026-02-21') AS month_end; -- 2026-02-28

-- Find the next specific weekday
-- E.g., next Monday (weekday 0=Monday ... 6=Sunday in some systems)
```

#### Example 35: Formatting dates

```sql
-- DATE_FORMAT: custom formatting
SELECT DATE_FORMAT(NOW(), '%Y-%m-%d') AS iso_date;           -- 2026-02-21
SELECT DATE_FORMAT(NOW(), '%d/%m/%Y') AS european_date;      -- 21/02/2026
SELECT DATE_FORMAT(NOW(), '%M %d, %Y') AS pretty_date;       -- February 21, 2026
SELECT DATE_FORMAT(NOW(), '%h:%i %p') AS twelve_hour_time;   -- 02:30 PM
SELECT DATE_FORMAT(NOW(), '%W, %M %d, %Y') AS full_date;    -- Saturday, February 21, 2026

-- STR_TO_DATE: parse a string into a date
SELECT STR_TO_DATE('21-02-2026', '%d-%m-%Y') AS parsed_date; -- 2026-02-21
SELECT STR_TO_DATE('Feb 21, 2026', '%b %d, %Y') AS parsed;  -- 2026-02-21
```

**Common Date Format Specifiers:**

| Specifier | Meaning | Example |
|---|---|---|
| `%Y` | 4-digit year | 2026 |
| `%y` | 2-digit year | 26 |
| `%m` | Month (01-12) | 02 |
| `%M` | Month name | February |
| `%b` | Abbreviated month | Feb |
| `%d` | Day (01-31) | 21 |
| `%H` | Hour 24h (00-23) | 14 |
| `%h` | Hour 12h (01-12) | 02 |
| `%i` | Minutes (00-59) | 30 |
| `%s` | Seconds (00-59) | 00 |
| `%p` | AM/PM | PM |
| `%W` | Weekday name | Saturday |

#### Example 36: Date functions in real queries

```sql
-- Orders placed in the last 30 days
SELECT * FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 30 DAY);

-- Group orders by month
SELECT
    DATE_FORMAT(order_date, '%Y-%m') AS month,
    COUNT(*) AS order_count,
    SUM(total) AS revenue
FROM orders
GROUP BY DATE_FORMAT(order_date, '%Y-%m')
ORDER BY month;

-- Calculate customer age from date of birth
SELECT name, dob,
    TIMESTAMPDIFF(YEAR, dob, CURDATE()) AS age
FROM students
ORDER BY age DESC;

-- Find orders placed on weekdays only (Mon-Fri)
SELECT * FROM orders
WHERE DAYOFWEEK(order_date) BETWEEN 2 AND 6;
```

---

### ✏️ Practice Exercise 14B

> **Difficulty:** ⭐⭐ Beginner–Intermediate
>
> 1. Write a query that shows the current date, time, and timestamp.
> 2. Calculate how many days are left until the end of the current year.
> 3. Format a date column as "Month Day, Year" (e.g., "February 21, 2026").
> 4. Find all orders placed in the current month.
> 5. Calculate the average number of days between order date and today for all orders.

---

## Topic 14C — Numeric Functions & Conditional Expressions

### 🌍 Real-Life Analogy

Numeric functions are your **calculator** — rounding, absolute values, modulo. Conditional expressions are your **if-then logic** — like a traffic light deciding green or red based on conditions.

---

### 1️⃣ Numeric Functions

```sql
-- ROUND: round to N decimal places
SELECT ROUND(3.14159, 2) AS rounded;    -- 3.14
SELECT ROUND(3.5) AS rounded_int;       -- 4

-- CEIL / CEILING: round UP to nearest integer
SELECT CEIL(3.1) AS ceiling;            -- 4
SELECT CEIL(-3.1) AS neg_ceiling;       -- -3

-- FLOOR: round DOWN to nearest integer
SELECT FLOOR(3.9) AS floored;           -- 3
SELECT FLOOR(-3.9) AS neg_floor;        -- -4

-- ABS: absolute value
SELECT ABS(-42) AS absolute;            -- 42

-- MOD: remainder (modulo)
SELECT MOD(10, 3) AS remainder;         -- 1
SELECT 10 % 3 AS remainder_alt;         -- 1

-- POWER / POW: exponentiation
SELECT POWER(2, 10) AS two_to_ten;      -- 1024

-- SQRT: square root
SELECT SQRT(144) AS root;               -- 12

-- TRUNCATE: truncate to N decimals (no rounding)
SELECT TRUNCATE(3.14159, 2) AS truncated; -- 3.14 (not 3.14 rounded)

-- RAND: random number between 0 and 1
SELECT RAND() AS random_num;            -- 0.7324... (varies)
SELECT FLOOR(RAND() * 100) + 1 AS random_1_to_100;

-- SIGN: returns -1, 0, or 1
SELECT SIGN(-42) AS neg, SIGN(0) AS zero, SIGN(42) AS pos;
-- Output: -1 | 0 | 1

-- GREATEST / LEAST: max/min of a list of values
SELECT GREATEST(10, 20, 5, 15) AS max_val;  -- 20
SELECT LEAST(10, 20, 5, 15) AS min_val;     -- 5
```

---

### 2️⃣ Conditional Expressions (CASE, IF, IFNULL, COALESCE)

#### CASE Expression — The SQL "Switch Statement"

```sql
-- Simple CASE: match a value
SELECT
    product_name,
    price,
    CASE category
        WHEN 'Electronics' THEN 'Tech'
        WHEN 'Furniture'   THEN 'Home'
        WHEN 'Stationery'  THEN 'Office'
        ELSE 'Other'
    END AS department
FROM products;

-- Searched CASE: evaluate conditions (more flexible)
SELECT
    product_name,
    price,
    CASE
        WHEN price >= 500 THEN 'Premium'
        WHEN price >= 100 THEN 'Mid-Range'
        WHEN price >= 10  THEN 'Budget'
        ELSE 'Bargain'
    END AS price_tier
FROM products;

-- CASE in ORDER BY (custom sort order)
SELECT product_name, category FROM products
ORDER BY CASE category
    WHEN 'Electronics' THEN 1
    WHEN 'Furniture' THEN 2
    WHEN 'Stationery' THEN 3
    ELSE 4
END;

-- CASE with aggregations (pivot-style query)
SELECT
    category,
    COUNT(*) AS total,
    SUM(CASE WHEN price > 100 THEN 1 ELSE 0 END) AS expensive_count,
    SUM(CASE WHEN price <= 100 THEN 1 ELSE 0 END) AS affordable_count
FROM products
GROUP BY category;
```

#### IF Function

```sql
-- IF(condition, true_value, false_value)
SELECT
    product_name,
    stock,
    IF(stock > 0, 'In Stock', 'Out of Stock') AS availability
FROM products;

-- Nested IF (avoid — use CASE instead for readability)
SELECT
    product_name,
    IF(price > 500, 'Expensive', IF(price > 100, 'Moderate', 'Cheap')) AS tier
FROM products;
```

#### IFNULL and COALESCE — Handling NULLs

```sql
-- IFNULL: replace NULL with a default (2 arguments only)
SELECT
    product_name,
    IFNULL(category, 'Uncategorized') AS category
FROM products;

-- COALESCE: returns the FIRST non-NULL value (N arguments)
SELECT
    COALESCE(phone, email, 'No Contact Info') AS contact
FROM customers;

-- COALESCE is more flexible than IFNULL:
SELECT COALESCE(NULL, NULL, 'third', 'fourth') AS first_non_null;
-- Output: third

-- NULLIF: returns NULL if two values are equal (useful to avoid division by zero)
SELECT
    product_name,
    price / NULLIF(stock, 0) AS price_per_unit
FROM products;
-- If stock = 0, NULLIF returns NULL, preventing division-by-zero error
```

**Comparison Table:**

| Function | Arguments | Purpose | Example |
|---|---|---|---|
| `IF(cond, t, f)` | 3 | Ternary: if-then-else | `IF(x>0, 'pos', 'neg')` |
| `IFNULL(val, default)` | 2 | Replace NULL | `IFNULL(phone, 'N/A')` |
| `COALESCE(v1, v2, ...)` | N | First non-NULL | `COALESCE(a, b, c)` |
| `NULLIF(v1, v2)` | 2 | NULL if equal | `NULLIF(stock, 0)` |
| `CASE WHEN...` | N | Multi-branch logic | See examples above |

---

### ✏️ Practice Exercise 14C

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Write a CASE expression to classify products as 'High Stock' (stock > 100), 'Medium Stock' (50-100), or 'Low Stock' (< 50).
> 2. Use COALESCE to display a customer's phone number, falling back to email, then 'No contact'.
> 3. Use ROUND and FORMAT to display product prices as formatted currency.
> 4. Generate a random number between 1000 and 9999 using RAND, FLOOR, and arithmetic.
> 5. Use NULLIF to safely divide total_revenue by order_count without division-by-zero errors.

---

## Topic 14D — ALTER TABLE Operations

### 🌍 Real-Life Analogy

`ALTER TABLE` is like **remodeling a room** while people are still using it. You can add a new closet (column), remove a window (drop column), widen a doorway (modify column), or rename the room (rename table) — all without tearing down the building.

---

### 1️⃣ WHY — Why ALTER TABLE?

- Requirements change — new features need new columns.
- Performance tuning — add/remove indexes.
- Schema evolution — rename columns, change data types.
- Fix mistakes — correct constraints or defaults.

---

### 2️⃣ HOW — ALTER TABLE Operations

```sql
-- ADD a new column
ALTER TABLE products ADD COLUMN description TEXT AFTER product_name;
ALTER TABLE products ADD COLUMN weight DECIMAL(8,2) DEFAULT 0;

-- ADD multiple columns at once
ALTER TABLE products
    ADD COLUMN color VARCHAR(30) AFTER description,
    ADD COLUMN brand VARCHAR(50) AFTER color;

-- DROP a column
ALTER TABLE products DROP COLUMN weight;

-- MODIFY a column (change type, constraints, default)
ALTER TABLE products MODIFY COLUMN product_name VARCHAR(200) NOT NULL;
ALTER TABLE products MODIFY COLUMN stock INT DEFAULT 0 NOT NULL;

-- CHANGE a column (rename + modify)
ALTER TABLE products CHANGE COLUMN product_name name VARCHAR(200) NOT NULL;
-- CHANGE is like MODIFY but also lets you rename the column

-- RENAME a table
ALTER TABLE products RENAME TO inventory;
-- or
RENAME TABLE inventory TO products;

-- ADD a constraint
ALTER TABLE products ADD CONSTRAINT chk_price CHECK (price >= 0);
ALTER TABLE products ADD CONSTRAINT uq_name UNIQUE (product_name);

-- DROP a constraint
ALTER TABLE products DROP CHECK chk_price;
ALTER TABLE products DROP INDEX uq_name;

-- ADD a foreign key to an existing table
ALTER TABLE orders ADD CONSTRAINT fk_customer
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
    ON DELETE CASCADE ON UPDATE CASCADE;

-- DROP a foreign key
ALTER TABLE orders DROP FOREIGN KEY fk_customer;

-- ADD an index
ALTER TABLE products ADD INDEX idx_category (category);

-- DROP an index
ALTER TABLE products DROP INDEX idx_category;

-- Change AUTO_INCREMENT starting value
ALTER TABLE products AUTO_INCREMENT = 1000;

-- Change the table's storage engine
ALTER TABLE products ENGINE = InnoDB;

-- Change the default character set
ALTER TABLE products CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

#### ON DELETE and ON UPDATE actions for Foreign Keys

```sql
-- What happens when the referenced row is deleted/updated?
ALTER TABLE order_items ADD CONSTRAINT fk_order
    FOREIGN KEY (order_id) REFERENCES orders(order_id)
    ON DELETE CASCADE      -- delete order_items when order is deleted
    ON UPDATE CASCADE;     -- update order_id in items when order_id changes

-- Available actions:
-- CASCADE    → propagate the change
-- SET NULL   → set FK column to NULL
-- SET DEFAULT → set FK to its default value (rarely supported)
-- RESTRICT   → prevent the delete/update (default behavior)
-- NO ACTION  → same as RESTRICT in MySQL
```

> ⚠️ **Warning:** `ALTER TABLE` on large tables can be slow and lock the table. For production databases, consider using tools like `pt-online-schema-change` or `gh-ost` for zero-downtime migrations.

---

### ✏️ Practice Exercise 14D

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Add a `discount_pct` DECIMAL(5,2) column to the `products` table with a default of 0.
> 2. Modify the `product_name` column to allow up to 200 characters.
> 3. Add a UNIQUE constraint on the `email` column of `customers`.
> 4. Add a foreign key with ON DELETE CASCADE to a table of your choice.
> 5. Rename a table, then rename it back.

---

## Topic 14E — Regular Expressions (REGEXP)

### 🌍 Real-Life Analogy

If `LIKE` is a simple pattern matcher (wildcards only), `REGEXP` is a **powerful search engine** that understands complex patterns — like finding all phone numbers, emails, or specific word patterns in your data.

---

### 1️⃣ WHY — Why REGEXP?

- `LIKE` only supports `%` (any chars) and `_` (one char) — very limited.
- `REGEXP` supports character classes, alternation, quantifiers, anchors — much more powerful.
- Essential for data validation and complex pattern matching.

---

### 2️⃣ WHEN — LIKE vs REGEXP

| Task | LIKE | REGEXP |
|---|---|---|
| Starts with "A" | `LIKE 'A%'` | `REGEXP '^A'` |
| Ends with "ing" | `LIKE '%ing'` | `REGEXP 'ing$'` |
| Contains "phone" | `LIKE '%phone%'` | `REGEXP 'phone'` |
| Starts with vowel | Not easy | `REGEXP '^[AEIOU]'` |
| Contains a digit | Not possible | `REGEXP '[0-9]'` |
| Matches "color" or "colour" | Two conditions | `REGEXP 'colou?r'` |

---

### 3️⃣ HOW — REGEXP Syntax

```sql
-- Basic pattern matching
SELECT * FROM products WHERE product_name REGEXP 'phone';
-- Matches: Headphones, Smartphone, Phone Case (contains "phone")

-- ^ = starts with, $ = ends with
SELECT * FROM products WHERE product_name REGEXP '^M';
-- Matches: Monitor, Mouse (starts with M)

SELECT * FROM products WHERE product_name REGEXP 'k$';
-- Matches: Desk (ends with k)

-- [abc] = character class (any one of a, b, c)
SELECT * FROM customers WHERE name REGEXP '^[A-D]';
-- Matches names starting with A, B, C, or D

-- [0-9] = any digit
SELECT * FROM customers WHERE phone REGEXP '[0-9]{10}';
-- Matches phone numbers with exactly 10 digits

-- | = alternation (OR)
SELECT * FROM products WHERE category REGEXP 'Electronics|Furniture';
-- Matches Electronics or Furniture

-- . = any single character
SELECT * FROM products WHERE product_name REGEXP 'M..se';
-- Matches: Mouse (M + any 2 chars + se)

-- * = zero or more, + = one or more, ? = zero or one
SELECT * FROM customers WHERE name REGEXP 'Joh?n';
-- Matches: Jon, John (h is optional)

-- {n} = exactly n times, {n,m} = n to m times
SELECT * FROM customers WHERE email REGEXP '[a-z]{3,}@';
-- Matches: emails with 3+ lowercase letters before @

-- NOT REGEXP (negation)
SELECT * FROM products WHERE product_name NOT REGEXP '^[A-M]';
-- Products NOT starting with A through M

-- REGEXP_LIKE (MySQL 8.0+, same as REGEXP but function syntax)
SELECT * FROM products WHERE REGEXP_LIKE(product_name, '^[A-M]', 'i');
-- 'i' flag = case-insensitive

-- REGEXP_REPLACE (MySQL 8.0+)
SELECT REGEXP_REPLACE('Phone: 123-456-7890', '[^0-9]', '') AS digits_only;
-- Output: 1234567890

-- REGEXP_SUBSTR (MySQL 8.0+): extract matching substring
SELECT REGEXP_SUBSTR('Order #12345 confirmed', '[0-9]+') AS order_num;
-- Output: 12345

-- REGEXP_INSTR (MySQL 8.0+): position of match
SELECT REGEXP_INSTR('Hello World 123', '[0-9]') AS digit_position;
-- Output: 13
```

**REGEXP Quick Reference:**

| Pattern | Meaning | Example |
|---|---|---|
| `^` | Start of string | `^Hello` |
| `$` | End of string | `world$` |
| `.` | Any single character | `h.t` → hat, hit, hot |
| `*` | Zero or more of previous | `ab*c` → ac, abc, abbc |
| `+` | One or more of previous | `ab+c` → abc, abbc (not ac) |
| `?` | Zero or one of previous | `colou?r` → color, colour |
| `[abc]` | Any one of a, b, c | `[aeiou]` → any vowel |
| `[^abc]` | NOT a, b, or c | `[^0-9]` → non-digit |
| `[a-z]` | Range | `[A-Za-z]` → any letter |
| `{n}` | Exactly n times | `[0-9]{3}` → 3 digits |
| `{n,m}` | Between n and m times | `[a-z]{2,5}` |
| `\|` | OR | `cat\|dog` |
| `\\b` | Word boundary | `\\bword\\b` |

---

### ✏️ Practice Exercise 14E

> **Difficulty:** ⭐⭐⭐ Intermediate–Advanced
>
> 1. Find all products whose names start with a vowel.
> 2. Find customers whose email uses Gmail or Yahoo.
> 3. Use REGEXP_REPLACE to mask phone numbers (replace middle 4 digits with ****).
> 4. Find all products whose names contain exactly two words (one space).

---

## 🏁 Part 3 Summary

| Topic | Key Takeaway |
|---|---|
| **CREATE / DROP** | CREATE builds structures; DROP destroys them. Use IF EXISTS for safety. |
| **Data Types** | Choose the right type for efficiency and correctness. Use DECIMAL for money. |
| **INSERT** | Single, multi-row, IGNORE, and ON DUPLICATE KEY UPDATE for different needs. |
| **UPDATE** | Always use WHERE! Modifies existing rows in place. |
| **DELETE / TRUNCATE** | DELETE for selective removal; TRUNCATE for fast full-table wipe. |
| **SELECT** | The most-used statement. Master WHERE, ORDER BY, LIMIT, DISTINCT, and aliases. |
| **String Functions** | CONCAT, UPPER, LOWER, TRIM, REPLACE, SUBSTRING — text processing toolkit. |
| **Date Functions** | NOW, DATE_FORMAT, DATEDIFF, DATE_ADD — calendar and time toolkit. |
| **Numeric & Conditional** | ROUND, CEIL, FLOOR + CASE, IF, IFNULL, COALESCE for logic and math. |
| **ALTER TABLE** | Add/drop/modify columns, constraints, indexes on existing tables. |
| **REGEXP** | Powerful pattern matching beyond LIKE — character classes, quantifiers, anchors. |

> **Next up:** [Part 4: Data Modeling](#part-4-data-modeling) — Normalization, foreign keys, constraints, and ER diagrams.

---

# Part 4: Data Modeling

> **Goal:** Learn to design clean, efficient database schemas using normalization, foreign keys, constraints, and ER diagrams.

---

## Topic 15 — Normalization (1NF, 2NF, 3NF)

### 🌍 Real-Life Analogy

Imagine a single giant spreadsheet that stores everything: customer name, address, order date, product name, product price — all in one row. Now a customer changes their address. You'd have to update **every row** with their old address. That's tedious and error-prone. **Normalization** is the process of splitting that giant spreadsheet into smaller, focused tables linked by keys — so each piece of data lives in exactly one place.

---

### 1️⃣ WHY — Why Normalize?

| Problem (Unnormalized) | Solution (Normalized) |
|---|---|
| **Update anomaly** — Change address in 50 rows | Address stored once in `customers` table |
| **Insert anomaly** — Can't add a product without an order | Products have their own table |
| **Delete anomaly** — Deleting last order loses customer info | Customer data lives independently |
| **Wasted space** — Repeating "Electronics" 1000 times | Category stored once, referenced by ID |

---

### 2️⃣ WHEN — When to Normalize?

✅ **Always normalize** for transactional systems (OLTP): e-commerce, banking, user management.

⚠️ **Selective denormalization** is acceptable for:
- Reporting/analytics databases (OLAP) where read speed > write integrity.
- Caching layers where duplication is intentional and temporary.

---

### 3️⃣ HOW — The Three Normal Forms

#### ❌ Before: Unnormalized Table

```sql
-- BAD: Everything in one table
CREATE TABLE orders_unnormalized (
    order_id      INT,
    customer_name VARCHAR(100),
    customer_email VARCHAR(150),
    customer_city VARCHAR(100),
    product_name  VARCHAR(100),
    product_price DECIMAL(10,2),
    quantity      INT,
    order_date    DATE
);

INSERT INTO orders_unnormalized VALUES
(1, 'Alice', 'alice@example.com', 'NYC', 'Laptop',     999.99, 1, '2024-01-15'),
(2, 'Alice', 'alice@example.com', 'NYC', 'Mouse',       29.99, 2, '2024-01-15'),
(3, 'Bob',   'bob@example.com',   'LA',  'Headphones',  79.99, 1, '2024-01-16');
```

**Problems:** Alice's name and email appear twice. If she changes her email, we must update multiple rows.

#### ✅ 1NF — First Normal Form

**Rule:** Each cell contains a single value (no lists, no repeating groups), and each row is unique.

```sql
-- 1NF: Ensure atomic values and a primary key
-- The table above already has atomic values,
-- but let's add a proper primary key:
ALTER TABLE orders_unnormalized ADD PRIMARY KEY (order_id);
```

> **1NF is satisfied when:** Every column has a single value (not a comma-separated list), and every row is uniquely identifiable.

#### ✅ 2NF — Second Normal Form

**Rule:** Must be in 1NF + every non-key column depends on the **entire** primary key (not just part of it).

```sql
-- Split: customer info into its own table
CREATE TABLE customers_2nf (
    customer_id    INT AUTO_INCREMENT PRIMARY KEY,
    customer_name  VARCHAR(100) NOT NULL,
    customer_email VARCHAR(150) NOT NULL UNIQUE,
    customer_city  VARCHAR(100)
);

-- Products into their own table
CREATE TABLE products_2nf (
    product_id    INT AUTO_INCREMENT PRIMARY KEY,
    product_name  VARCHAR(100) NOT NULL,
    product_price DECIMAL(10,2) NOT NULL
);

-- Orders reference customers and products
CREATE TABLE orders_2nf (
    order_id    INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    product_id  INT NOT NULL,
    quantity    INT NOT NULL,
    order_date  DATE NOT NULL,
    FOREIGN KEY (customer_id) REFERENCES customers_2nf(customer_id),
    FOREIGN KEY (product_id)  REFERENCES products_2nf(product_id)
);
```

Now Alice's info is stored **once**. Changing her email means updating one row.

#### ✅ 3NF — Third Normal Form

**Rule:** Must be in 2NF + no transitive dependencies (non-key column shouldn't depend on another non-key column).

```sql
-- Example of a transitive dependency violation:
-- If we had: employees(emp_id, emp_name, dept_id, dept_name)
-- dept_name depends on dept_id, NOT on emp_id → transitive dependency!

-- Fix: move dept_name to its own table
CREATE TABLE departments_3nf (
    dept_id   INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE employees_3nf (
    emp_id   INT AUTO_INCREMENT PRIMARY KEY,
    emp_name VARCHAR(100) NOT NULL,
    dept_id  INT,
    FOREIGN KEY (dept_id) REFERENCES departments_3nf(dept_id)
);
```

#### Normalization Summary

| Form | Rule | Example Fix |
|---|---|---|
| **1NF** | Atomic values, unique rows | No comma-separated lists; add a PK |
| **2NF** | 1NF + no partial dependencies | Split customer/product data into separate tables |
| **3NF** | 2NF + no transitive dependencies | Move dept_name out of employees → departments table |

---

### ✏️ Practice Exercise 15

> **Difficulty:** ⭐⭐ Intermediate
>
> Given this unnormalized table:
> ```
> | order_id | customer | email           | products             | total |
> |----------|----------|-----------------|----------------------|-------|
> | 1        | Alice    | alice@mail.com  | Laptop, Mouse        | 1029  |
> | 2        | Bob      | bob@mail.com    | Headphones           | 79    |
> ```
> 1. Why does this violate 1NF? (Hint: look at the `products` column.)
> 2. Redesign this into 3NF with proper tables. Write the CREATE TABLE statements.
> 3. Insert sample data into your normalized tables.

---

## Topic 16 — Foreign Keys and Relationships

### 🌍 Real-Life Analogy

A foreign key is like a **reference on a form**. An order form has a "Customer #" field that must match an actual customer in the customer database. If you write a customer number that doesn't exist, the form is rejected.

---

### 1️⃣ WHY — Why Foreign Keys?

| Benefit | Explanation |
|---|---|
| **Referential integrity** | Prevents orphan records (orders without customers). |
| **Cascading actions** | Automatically delete or update related rows. |
| **Self-documenting** | The schema itself describes relationships. |
| **Query optimization** | JOINs on foreign key columns are optimized. |

---

### 2️⃣ WHEN — Relationship Types

| Relationship | Example | How to Implement |
|---|---|---|
| **One-to-One** | User ↔ Profile | FK with UNIQUE constraint |
| **One-to-Many** | Customer → Orders | FK in the "many" table |
| **Many-to-Many** | Students ↔ Courses | Junction (bridge) table |

---

### 3️⃣ HOW — Foreign Key Implementation

#### Example 30: One-to-Many relationship

```sql
CREATE DATABASE IF NOT EXISTS relationships_demo;
USE relationships_demo;

-- Parent table
CREATE TABLE authors (
    author_id INT AUTO_INCREMENT PRIMARY KEY,
    name      VARCHAR(100) NOT NULL
);

-- Child table (many books per author)
CREATE TABLE books (
    book_id   INT AUTO_INCREMENT PRIMARY KEY,
    title     VARCHAR(200) NOT NULL,
    author_id INT NOT NULL,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
        ON DELETE CASCADE       -- delete books when author is deleted
        ON UPDATE CASCADE       -- update FK when author_id changes
);

-- Insert data
INSERT INTO authors (name) VALUES ('J.K. Rowling'), ('George Orwell');
INSERT INTO books (title, author_id) VALUES
    ('Harry Potter', 1),
    ('Fantastic Beasts', 1),
    ('1984', 2),
    ('Animal Farm', 2);

-- This fails: author_id 99 doesn't exist
INSERT INTO books (title, author_id) VALUES ('Ghost Book', 99);
-- ERROR 1452: Cannot add or update a child row
```

#### Example 31: Many-to-Many with junction table

```sql
-- Students
CREATE TABLE students (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    name       VARCHAR(100) NOT NULL
);

-- Courses
CREATE TABLE courses (
    course_id   INT AUTO_INCREMENT PRIMARY KEY,
    course_name VARCHAR(100) NOT NULL
);

-- Junction table: student_courses
CREATE TABLE student_courses (
    student_id INT NOT NULL,
    course_id  INT NOT NULL,
    enrolled_on DATE DEFAULT (CURRENT_DATE),
    grade       CHAR(2),
    PRIMARY KEY (student_id, course_id),              -- composite PK
    FOREIGN KEY (student_id) REFERENCES students(student_id) ON DELETE CASCADE,
    FOREIGN KEY (course_id)  REFERENCES courses(course_id) ON DELETE CASCADE
);

-- Insert data
INSERT INTO students (name) VALUES ('Alice'), ('Bob'), ('Charlie');
INSERT INTO courses (course_name) VALUES ('Math'), ('Science'), ('History');

-- Enroll students in courses
INSERT INTO student_courses (student_id, course_id) VALUES
    (1, 1), (1, 2),    -- Alice → Math, Science
    (2, 1), (2, 3),    -- Bob → Math, History
    (3, 2);            -- Charlie → Science

-- Query: which courses is Alice taking?
SELECT s.name, c.course_name
FROM students s
JOIN student_courses sc ON s.student_id = sc.student_id
JOIN courses c ON sc.course_id = c.course_id
WHERE s.name = 'Alice';
```

**Expected output:**

| name  | course_name |
|-------|-------------|
| Alice | Math        |
| Alice | Science     |

#### Example 32: One-to-One relationship

```sql
CREATE TABLE users (
    user_id  INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE user_profiles (
    profile_id INT AUTO_INCREMENT PRIMARY KEY,
    user_id    INT NOT NULL UNIQUE,         -- UNIQUE ensures one-to-one
    bio        TEXT,
    avatar_url VARCHAR(255),
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE
);
```

The `UNIQUE` constraint on `user_id` in `user_profiles` ensures each user has **at most one** profile.

#### Cascade Actions Reference

| Action | On DELETE | On UPDATE |
|---|---|---|
| `CASCADE` | Delete child rows when parent is deleted | Update child FK when parent PK changes |
| `SET NULL` | Set child FK to NULL when parent is deleted | Set child FK to NULL when parent PK changes |
| `RESTRICT` (default) | Block deletion if children exist | Block update if children exist |
| `NO ACTION` | Same as RESTRICT in MySQL | Same as RESTRICT in MySQL |

---

### ✏️ Practice Exercise 16

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create a one-to-many relationship between `departments` and `employees` where deleting a department sets the employee's `dept_id` to NULL.
> 2. Create a many-to-many relationship between `movies` and `actors` using a `movie_cast` junction table.
> 3. Insert sample data and write a query to find all actors in a specific movie.
> 4. Test CASCADE: delete a movie and verify the junction table rows are also removed.

---

## Topic 17 — Constraints

### 🌍 Real-Life Analogy

Constraints are like **rules posted on a form**: "This field is required," "Enter a valid email," "Age must be 18+." They prevent invalid data from ever entering the database.

---

### 1️⃣ WHY — Why Constraints?

Constraints enforce **data integrity** at the database level. Even if your application has bugs, the database will reject bad data.

---

### 2️⃣ WHEN — Which Constraint to Use

| Constraint | Purpose | Example |
|---|---|---|
| `NOT NULL` | Column must have a value | Name cannot be empty |
| `UNIQUE` | No duplicate values in column | Email must be unique |
| `PRIMARY KEY` | Unique + Not Null identifier | user_id |
| `FOREIGN KEY` | Must reference existing row | dept_id → departments |
| `DEFAULT` | Automatic value if none provided | status defaults to 'active' |
| `CHECK` | Custom validation rule | age >= 18, price >= 0 |
| `AUTO_INCREMENT` | Auto-generate sequential integers | IDs |

---

### 3️⃣ HOW — Constraints in Practice

#### Example 33: All constraints demonstrated

```sql
CREATE TABLE employees_constrained (
    emp_id     INT AUTO_INCREMENT PRIMARY KEY,           -- PK + AUTO_INCREMENT
    emp_name   VARCHAR(100) NOT NULL,                    -- NOT NULL
    email      VARCHAR(150) NOT NULL UNIQUE,             -- NOT NULL + UNIQUE
    age        INT CHECK (age >= 18 AND age <= 120),     -- CHECK constraint
    salary     DECIMAL(10,2) DEFAULT 50000.00,           -- DEFAULT
    dept_id    INT,
    hire_date  DATE DEFAULT (CURRENT_DATE),              -- DEFAULT with function
    status     ENUM('active','inactive') DEFAULT 'active', -- ENUM + DEFAULT
    FOREIGN KEY (dept_id) REFERENCES departments_3nf(dept_id) -- FK
);
```

#### Example 34: Constraint violations

```sql
-- NOT NULL violation
INSERT INTO employees_constrained (emp_name, email) VALUES (NULL, 'test@test.com');
-- ERROR 1048: Column 'emp_name' cannot be null

-- UNIQUE violation
INSERT INTO employees_constrained (emp_name, email) VALUES ('Alice', 'alice@co.com');
INSERT INTO employees_constrained (emp_name, email) VALUES ('Alice2', 'alice@co.com');
-- ERROR 1062: Duplicate entry 'alice@co.com' for key 'email'

-- CHECK violation
INSERT INTO employees_constrained (emp_name, email, age) VALUES ('Kid', 'kid@co.com', 10);
-- ERROR 3819: Check constraint 'employees_constrained_chk_1' is violated

-- FOREIGN KEY violation
INSERT INTO employees_constrained (emp_name, email, dept_id) VALUES ('Bob', 'bob@co.com', 9999);
-- ERROR 1452: Cannot add or update a child row
```

#### Example 35: Adding and dropping constraints on existing tables

```sql
-- Add a UNIQUE constraint
ALTER TABLE employees_constrained ADD CONSTRAINT uq_emp_name UNIQUE (emp_name);

-- Add a CHECK constraint
ALTER TABLE employees_constrained ADD CONSTRAINT chk_salary CHECK (salary >= 0);

-- Drop a constraint
ALTER TABLE employees_constrained DROP CONSTRAINT uq_emp_name;

-- Add NOT NULL (by modifying the column)
ALTER TABLE employees_constrained MODIFY COLUMN age INT NOT NULL;
```

---

### ✏️ Practice Exercise 17

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create a `products` table with: NOT NULL on `name` and `price`, UNIQUE on `sku`, CHECK that `price > 0` and `stock >= 0`, DEFAULT stock of 0.
> 2. Try inserting a row that violates each constraint and observe the error messages.
> 3. Add a CHECK constraint to an existing table using ALTER TABLE.

---

## Topic 18 — Entity-Relationship (ER) Diagrams

### 🌍 Real-Life Analogy

An ER diagram is like a **blueprint** for a house. Before building, architects draw plans showing rooms (tables), doors connecting them (relationships), and room specifications (columns). ER diagrams do the same for databases.

---

### 1️⃣ WHY — Why ER Diagrams?

- **Visual communication** — Stakeholders and developers can understand the schema at a glance.
- **Design before coding** — Catch problems before writing SQL.
- **Documentation** — Living reference for the database structure.

---

### 2️⃣ WHEN — When to Create ER Diagrams

- Before starting any new database project.
- When onboarding new team members.
- When planning schema changes or new features.
- During code reviews involving database changes.

---

### 3️⃣ HOW — Reading and Creating ER Diagrams

#### ER Diagram Notation

```
┌───────────────┐          ┌───────────────┐
│   Entity A    │          │   Entity B    │
├───────────────┤          ├───────────────┤
│ PK column_a   │──── 1:N ──│ FK column_a   │
│    column_b   │          │ PK column_b   │
│    column_c   │          │    column_c   │
└───────────────┘          └───────────────┘

Symbols:
  PK = Primary Key    FK = Foreign Key
  1:1 = One-to-One    1:N = One-to-Many    M:N = Many-to-Many
```

#### Example 36: E-Commerce ER Diagram

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│   customers     │       │     orders      │       │  order_items    │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ PK customer_id  │──1:N──│ FK customer_id  │       │ PK item_id      │
│    name         │       │ PK order_id     │──1:N──│ FK order_id     │
│    email        │       │    order_date   │       │ FK product_id   │
│    city         │       │    total_amount │       │    quantity     │
└─────────────────┘       └─────────────────┘       │    unit_price   │
                                                     └────────┬────────┘
                                                              │
┌─────────────────┐       ┌─────────────────┐                │
│  categories     │       │    products     │                │
├─────────────────┤       ├─────────────────┤                │
│ PK category_id  │──1:N──│ FK category_id  │                │
│    name         │       │ PK product_id   │───────N:1──────┘
│                 │       │    name         │
│                 │       │    price        │
│                 │       │    stock        │
└─────────────────┘       └─────────────────┘
```

**How to read this:**
- One customer can place **many** orders (1:N).
- One order can have **many** order items (1:N).
- Each order item references **one** product (N:1).
- Each product belongs to **one** category (N:1).

#### Example 37: SQL implementation of the ER diagram

```sql
CREATE DATABASE IF NOT EXISTS ecommerce_er;
USE ecommerce_er;

CREATE TABLE categories (
    category_id INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE products (
    product_id  INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(100) NOT NULL,
    price       DECIMAL(10,2) NOT NULL CHECK (price >= 0),
    stock       INT DEFAULT 0,
    category_id INT,
    FOREIGN KEY (category_id) REFERENCES categories(category_id)
);

CREATE TABLE customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(100) NOT NULL,
    email       VARCHAR(150) NOT NULL UNIQUE,
    city        VARCHAR(100)
);

CREATE TABLE orders (
    order_id     INT AUTO_INCREMENT PRIMARY KEY,
    customer_id  INT NOT NULL,
    order_date   DATE DEFAULT (CURRENT_DATE),
    total_amount DECIMAL(12,2) DEFAULT 0,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_items (
    item_id    INT AUTO_INCREMENT PRIMARY KEY,
    order_id   INT NOT NULL,
    product_id INT NOT NULL,
    quantity   INT NOT NULL CHECK (quantity > 0),
    unit_price DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (order_id)   REFERENCES orders(order_id) ON DELETE CASCADE,
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
```

---

### ✏️ Practice Exercise 18

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Draw an ASCII ER diagram for a **blog system** with tables: `users`, `posts`, `comments`, `tags`, and a junction table `post_tags`.
> 2. Identify the relationship type for each connection (1:1, 1:N, or M:N).
> 3. Write the CREATE TABLE statements for your design.

---

## 🏁 Part 4 Summary

| Topic | Key Takeaway |
|---|---|
| **Normalization** | Split data into focused tables to avoid anomalies. 1NF → 2NF → 3NF. |
| **Foreign Keys** | Link tables and enforce referential integrity. Use CASCADE for automatic cleanup. |
| **Constraints** | NOT NULL, UNIQUE, CHECK, DEFAULT — enforce data rules at the DB level. |
| **ER Diagrams** | Visual blueprints for database design. Plan before you code. |

> **Next up:** [Part 5: Querying Data](#part-5-querying-data) — JOINs, aggregations, subqueries, and window functions.

---

# Part 5: Querying Data

> **Goal:** Master the art of retrieving and combining data from multiple tables using JOINs, aggregations, subqueries, window functions, and set operations.

---

## Topic 19 — JOINs

### 🌍 Real-Life Analogy

Imagine two spreadsheets: one lists **students** and another lists **grades**. To create a report card, you need to **combine** them — matching each student to their grades by student ID. That's exactly what a JOIN does.

---

### 1️⃣ WHY — Why JOINs?

- Normalization splits data across tables. JOINs bring it back together for queries.
- Avoids storing duplicate data (e.g., student name in every grade row).
- Enables complex reports spanning multiple entities.
- Every real-world application needs JOINs — they are the backbone of relational querying.

---

### 2️⃣ HOW MANY — The 7 Types of JOINs in MySQL

MySQL supports **7 types** of JOINs. Here is the complete list:

| # | JOIN Type | Description | MySQL Support |
|---|---|---|---|
| 1 | **INNER JOIN** | Only matching rows from both tables | ✅ Native |
| 2 | **LEFT (OUTER) JOIN** | All rows from left table + matching from right | ✅ Native |
| 3 | **RIGHT (OUTER) JOIN** | All rows from right table + matching from left | ✅ Native |
| 4 | **FULL (OUTER) JOIN** | All rows from both tables (matched + unmatched) | ⚠️ Emulated via UNION |
| 5 | **CROSS JOIN** | Every combination of rows (Cartesian product) | ✅ Native |
| 6 | **SELF JOIN** | A table joined with itself | ✅ Native (uses any JOIN type) |
| 7 | **NATURAL JOIN** | Auto-matches columns with the same name | ✅ Native (use cautiously) |

#### Visual Overview of All JOIN Types

```
   Table A       Table B         INNER JOIN         LEFT JOIN          RIGHT JOIN        FULL OUTER JOIN
  ┌───────┐     ┌───────┐      ┌───────┐          ┌───────┐          ┌───────┐          ┌───────┐
  │       │     │       │      │       │          │███████│          │       │          │███████│
  │   A   │     │   B   │      │  A∩B  │          │  A∩B  │          │  A∩B  │          │  A∪B  │
  │       │     │       │      │       │          │       │          │███████│          │███████│
  └───────┘     └───────┘      └───────┘          └───────┘          └───────┘          └───────┘
                                Only match         All A +            All B +            Everything
                                in both            match from B       match from A       from both

   CROSS JOIN      SELF JOIN        NATURAL JOIN
  ┌───────────┐   ┌───┐            ┌───────┐
  │ A × B     │   │ A │──┐         │  auto │
  │ (all      │   │   │  │ same    │ match │  (matches on
  │  combos)  │   │   │←─┘ table   │ cols  │   same-name columns)
  └───────────┘   └───┘            └───────┘
```

---

### 3️⃣ WHEN — When to Use Each JOIN Type

| JOIN Type | Use When | Real-World Example |
|---|---|---|
| **INNER JOIN** | You only want rows that match in both tables | Show orders with their customer names |
| **LEFT JOIN** | You want all rows from the left table, even without matches | List all customers, even those with no orders |
| **RIGHT JOIN** | You want all rows from the right table, even without matches | Show all departments, even those with no employees |
| **FULL OUTER JOIN** | You want unmatched rows from BOTH sides | Reconcile two lists (all students + all grades, matched or not) |
| **CROSS JOIN** | You want every combination of rows (Cartesian product) | Generate all size-color combinations for a product |
| **SELF JOIN** | A table references itself | Employees and their managers (same table) |
| **NATURAL JOIN** | Tables share an obvious column name and you want auto-matching | Quick prototyping (avoid in production — fragile!) |

#### How to Choose: Decision Flowchart

```
Do you need rows from BOTH tables even if no match?
├── YES → Do you need unmatched from BOTH sides?
│         ├── YES → FULL OUTER JOIN (emulated in MySQL)
│         └── NO  → Which side must keep all rows?
│                   ├── Left table  → LEFT JOIN
│                   └── Right table → RIGHT JOIN
├── NO  → Do you need ALL combinations?
│         ├── YES → CROSS JOIN
│         └── NO  → INNER JOIN
└── Is the table joining itself?
          └── YES → SELF JOIN (using LEFT/INNER JOIN)
```

---

### 4️⃣ HOW — All JOIN Types Demonstrated

#### Setup data

```sql
CREATE DATABASE IF NOT EXISTS join_demo;
USE join_demo;

CREATE TABLE students (
    id   INT PRIMARY KEY,
    name VARCHAR(50)
);

CREATE TABLE grades (
    grade_id   INT AUTO_INCREMENT PRIMARY KEY,
    student_id INT,
    subject    VARCHAR(50),
    score      INT
);

INSERT INTO students VALUES (1, 'Alice'), (2, 'Bob'), (3, 'Charlie');
INSERT INTO grades (student_id, subject, score) VALUES
    (1, 'Math', 90), (1, 'Science', 85),
    (2, 'Math', 78),
    (4, 'History', 92);  -- student_id 4 doesn't exist in students
```

**Data at a glance:**

| students |  | grades |  |  |
|---|---|---|---|---|
| id=1, Alice | | student_id=1, Math, 90 | student_id=1, Science, 85 | |
| id=2, Bob | | student_id=2, Math, 78 | | |
| id=3, Charlie ← no grades | | student_id=4, History, 92 ← no student | | |

---

#### Example 38: INNER JOIN — Only Matching Rows

```sql
-- Only returns rows where a match exists in BOTH tables
SELECT s.name, g.subject, g.score
FROM students s
INNER JOIN grades g ON s.id = g.student_id;
```

**Result:**

| name  | subject | score |
|-------|---------|-------|
| Alice | Math    | 90    |
| Alice | Science | 85    |
| Bob   | Math    | 78    |

Charlie (no grades) and student_id 4 (no student record) are **excluded**.

**When to use:** When you only care about records that exist in both tables. This is the most common JOIN type.

```
INNER JOIN Visualization:
  Students         Grades
  ┌──────────┐    ┌──────────┐
  │ Alice  ──────────── Math   │
  │ Alice  ──────────── Science│
  │ Bob    ──────────── Math   │
  │ Charlie ✗│    │✗ History  │  ✗ = excluded (no match)
  └──────────┘    └──────────┘
  Returns: 3 rows (only matched pairs)
```

> **Note:** `JOIN` and `INNER JOIN` are identical. The keyword `INNER` is optional but recommended for clarity.

---

#### Example 39: LEFT JOIN (LEFT OUTER JOIN) — All Left + Matching Right

```sql
-- All students, even if they have no grades
SELECT s.name, g.subject, g.score
FROM students s
LEFT JOIN grades g ON s.id = g.student_id;
```

**Result:**

| name    | subject | score |
|---------|---------|-------|
| Alice   | Math    | 90    |
| Alice   | Science | 85    |
| Bob     | Math    | 78    |
| Charlie | NULL    | NULL  |

Charlie appears with NULLs for grade columns — because LEFT JOIN keeps **all** left-table rows.

**When to use:** When you need all records from the "main" table, with optional data from the related table.

```
LEFT JOIN Visualization:
  Students (ALL)     Grades (matching only)
  ┌──────────┐      ┌──────────┐
  │ Alice  ──────────── Math    │
  │ Alice  ──────────── Science │
  │ Bob    ──────────── Math    │
  │ Charlie ──── NULL, NULL     │  ← kept with NULLs
  └──────────┘      │✗ History  │  ✗ = excluded (no student)
                     └──────────┘
  Returns: 4 rows
```

**Useful pattern — Finding unmatched rows (LEFT JOIN + IS NULL):**

```sql
-- Students who have NO grades at all
SELECT s.name
FROM students s
LEFT JOIN grades g ON s.id = g.student_id
WHERE g.student_id IS NULL;
-- Result: Charlie
```

> **Note:** `LEFT JOIN` and `LEFT OUTER JOIN` are identical. The keyword `OUTER` is optional.

---

#### Example 40: RIGHT JOIN (RIGHT OUTER JOIN) — All Right + Matching Left

```sql
-- All grades, even if the student doesn't exist
SELECT s.name, g.subject, g.score
FROM students s
RIGHT JOIN grades g ON s.id = g.student_id;
```

**Result:**

| name  | subject | score |
|-------|---------|-------|
| Alice | Math    | 90    |
| Alice | Science | 85    |
| Bob   | Math    | 78    |
| NULL  | History | 92    |

The History grade for non-existent student 4 appears with NULL for name.

**When to use:** When you need all records from the right table with optional data from the left. In practice, you can usually rewrite a RIGHT JOIN as a LEFT JOIN by swapping table order.

```
RIGHT JOIN Visualization:
  Students (matching)    Grades (ALL)
  ┌──────────┐          ┌──────────┐
  │ Alice  ──────────────── Math   │
  │ Alice  ──────────────── Science│
  │ Bob    ──────────────── Math   │
  │✗ Charlie│    NULL ──── History │  ← kept with NULLs
  └──────────┘          └──────────┘
  Returns: 4 rows
```

> **Tip:** Most developers prefer LEFT JOIN and reorder the tables instead of using RIGHT JOIN — it reads more naturally left-to-right.

---

#### Example 40b: FULL OUTER JOIN — All Rows From Both Tables

MySQL does **not** have a native `FULL OUTER JOIN` keyword, but you can emulate it with `UNION`:

```sql
-- Emulate FULL OUTER JOIN: all students + all grades, matched where possible
SELECT s.name, g.subject, g.score
FROM students s
LEFT JOIN grades g ON s.id = g.student_id

UNION

SELECT s.name, g.subject, g.score
FROM students s
RIGHT JOIN grades g ON s.id = g.student_id;
```

**Result:**

| name    | subject | score |
|---------|---------|-------|
| Alice   | Math    | 90    |
| Alice   | Science | 85    |
| Bob     | Math    | 78    |
| Charlie | NULL    | NULL  |
| NULL    | History | 92    |

Both Charlie (no grades) AND History for student_id 4 (no student) appear.

**When to use:** When you need a complete picture of BOTH tables. Common in data reconciliation tasks.

```
FULL OUTER JOIN Visualization:
  Students (ALL)        Grades (ALL)
  ┌──────────┐         ┌──────────┐
  │ Alice  ────────────── Math    │
  │ Alice  ────────────── Science │
  │ Bob    ────────────── Math    │
  │ Charlie ── NULL, NULL         │  ← left-only row
  └──────────┘   NULL ── History  │  ← right-only row
                        └──────────┘
  Returns: 5 rows (everything from both sides)
```

**How the emulation works:**
1. `LEFT JOIN` gets all students (including Charlie with NULLs)
2. `RIGHT JOIN` gets all grades (including History with NULLs)
3. `UNION` merges both results and removes duplicates

---

#### Example 41: CROSS JOIN — Cartesian Product (Every Combination)

```sql
-- Every combination of students and subjects
SELECT s.name, g.subject
FROM students s
CROSS JOIN (SELECT DISTINCT subject FROM grades) g
ORDER BY s.name, g.subject;
```

**Result:** 3 students × 3 subjects = **9 rows**

| name    | subject |
|---------|---------|
| Alice   | History |
| Alice   | Math    |
| Alice   | Science |
| Bob     | History |
| Bob     | Math    |
| Bob     | Science |
| Charlie | History |
| Charlie | Math    |
| Charlie | Science |

**When to use:** Generating all possible combinations. Useful for:
- Product configurations (all size × color × material combos)
- Calendar/time slot generation
- Test data generation

```
CROSS JOIN Visualization:
  Students    Subjects       Result
  ┌───────┐  ┌─────────┐    ┌─────────────────┐
  │ Alice │  │ Math    │    │ Alice × Math    │
  │ Bob   │ ×│ Science │ =  │ Alice × Science │
  │Charlie│  │ History │    │ Alice × History │
  └───────┘  └─────────┘    │ Bob   × Math    │
   3 rows     3 rows         │ Bob   × Science │
                              │ Bob   × History │
                              │ Charlie × Math  │
                              │ ...9 rows total │
                              └─────────────────┘
```

> ⚠️ **Warning:** CROSS JOIN can produce enormous results! 1000 rows × 1000 rows = 1,000,000 rows. Always use wisely.

**Real-world example — generating a sizes/colors matrix:**

```sql
CREATE TABLE sizes (size VARCHAR(5));
CREATE TABLE colors (color VARCHAR(20));

INSERT INTO sizes VALUES ('S'), ('M'), ('L'), ('XL');
INSERT INTO colors VALUES ('Red'), ('Blue'), ('Black');

-- Generate all product variants
SELECT s.size, c.color
FROM sizes s
CROSS JOIN colors c
ORDER BY s.size, c.color;
-- Returns: 4 × 3 = 12 rows
```

---

#### Example 42: SELF JOIN — A Table Joined With Itself

A SELF JOIN is not a separate syntax — it uses INNER JOIN or LEFT JOIN, but **both sides reference the same table** with different aliases.

```sql
-- Employees table where manager_id references another employee
CREATE TABLE employees_self (
    emp_id     INT PRIMARY KEY,
    emp_name   VARCHAR(50),
    manager_id INT
);

INSERT INTO employees_self VALUES
    (1, 'CEO',      NULL),
    (2, 'VP Eng',   1),
    (3, 'Dev Lead', 2),
    (4, 'Dev',      3),
    (5, 'VP Sales', 1),
    (6, 'Sales Rep', 5);

-- Self join: show each employee with their manager's name
SELECT e.emp_name AS employee, m.emp_name AS manager
FROM employees_self e
LEFT JOIN employees_self m ON e.manager_id = m.emp_id;
```

**Result:**

| employee  | manager |
|-----------|---------|
| CEO       | NULL    |
| VP Eng    | CEO     |
| Dev Lead  | VP Eng  |
| Dev       | Dev Lead|
| VP Sales  | CEO     |
| Sales Rep | VP Sales|

**When to use:**
- **Org charts** — Employees and their managers
- **Hierarchies** — Categories and subcategories (parent_id → category_id)
- **Comparisons** — Find pairs within the same table (e.g., students in the same city)

```
SELF JOIN Visualization:
  employees_self (AS e)    employees_self (AS m)
  ┌──────────────┐        ┌──────────────┐
  │ CEO (mgr:NULL)│───────│              │ ← NULL (no manager)
  │ VP Eng (mgr:1)│───────│ CEO (id:1)   │
  │ Dev Lead(mgr:2)│──────│ VP Eng (id:2)│
  │ Dev    (mgr:3)│───────│ Dev Lead(id:3)│
  └──────────────┘        └──────────────┘
  Same table, different aliases!
```

**More self-join examples:**

```sql
-- Find all pairs of students (e.g., for group projects)
-- Assumes a students table with id, name, city
SELECT a.name AS student_1, b.name AS student_2, a.city
FROM students a
INNER JOIN students b ON a.city = b.city AND a.id < b.id;
-- a.id < b.id prevents duplicate pairs (Alice-Bob vs Bob-Alice)

-- Find employees who earn more than their manager
SELECT e.emp_name AS employee, e.salary AS emp_salary,
       m.emp_name AS manager, m.salary AS mgr_salary
FROM employees e
INNER JOIN employees m ON e.manager_id = m.emp_id
WHERE e.salary > m.salary;
```

---

#### Example 42b: NATURAL JOIN — Auto-Match on Same-Name Columns

```sql
-- NATURAL JOIN automatically matches columns with the same name
-- If students has 'id' and grades has 'student_id', this WON'T work as expected
-- The columns must have the SAME NAME

-- Let's create tables where it works:
CREATE TABLE authors (
    author_id INT PRIMARY KEY,
    name      VARCHAR(50)
);

CREATE TABLE books (
    book_id   INT PRIMARY KEY,
    title     VARCHAR(100),
    author_id INT              -- same name as in authors table
);

INSERT INTO authors VALUES (1, 'Tolkien'), (2, 'Rowling');
INSERT INTO books VALUES (1, 'The Hobbit', 1), (2, 'Harry Potter', 2), (3, 'Unknown', 99);

-- NATURAL JOIN automatically matches on 'author_id'
SELECT * FROM authors NATURAL JOIN books;
-- Equivalent to: SELECT * FROM authors INNER JOIN books ON authors.author_id = books.author_id;
```

**Result:**

| author_id | name    | book_id | title        |
|-----------|---------|---------|--------------|
| 1         | Tolkien | 1       | The Hobbit   |
| 2         | Rowling | 2       | Harry Potter |

> ⚠️ **Warning — Why NATURAL JOIN is dangerous in production:**
> - Adding a new column with a coincidentally matching name silently changes the JOIN condition.
> - It's implicit — readers can't see what columns are being matched.
> - Use explicit `ON` or `USING` clauses instead for production code.

---

### 5️⃣ JOIN Syntax Variants: ON vs USING vs NATURAL

MySQL offers three ways to specify join conditions:

```sql
-- 1. ON clause (most flexible, recommended)
SELECT * FROM students s
INNER JOIN grades g ON s.id = g.student_id;

-- 2. USING clause (when both tables have the SAME column name)
-- USING eliminates the duplicate column from results
SELECT * FROM authors
INNER JOIN books USING (author_id);
-- Equivalent to: ON authors.author_id = books.author_id
-- But the result only shows author_id ONCE

-- 3. NATURAL JOIN (auto-matches all same-name columns — avoid in production)
SELECT * FROM authors NATURAL JOIN books;
```

**Comparison:**

| Feature | ON | USING | NATURAL |
|---|---|---|---|
| Column names must match | No | Yes | Yes |
| Explicit condition | ✅ | ✅ (column name only) | ❌ (auto) |
| Joins on different column names | ✅ | ❌ | ❌ |
| Multiple conditions | ✅ | ✅ (multiple columns) | ❌ |
| Production-safe | ✅ | ✅ | ❌ |
| **Recommended** | **Yes** | **Yes** | **No** |

```sql
-- USING with multiple columns
SELECT * FROM enrollments
INNER JOIN student_courses USING (student_id, course_id);
```

---

### 6️⃣ Multi-Table JOINs (3+ Tables)

Real-world queries frequently join 3, 4, or even more tables in a single query.

```sql
-- Example: Students → Enrollments → Courses → Professors
-- (4 tables joined together)

-- Setup
CREATE TABLE IF NOT EXISTS departments (
    dept_id   INT PRIMARY KEY,
    dept_name VARCHAR(50)
);
CREATE TABLE IF NOT EXISTS professors (
    prof_id INT PRIMARY KEY,
    name    VARCHAR(50),
    dept_id INT
);
CREATE TABLE IF NOT EXISTS courses (
    course_id   INT PRIMARY KEY,
    course_name VARCHAR(100),
    prof_id     INT
);
CREATE TABLE IF NOT EXISTS enrollments (
    enrollment_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id    INT,
    course_id     INT,
    grade         CHAR(2)
);

-- 4-table JOIN: Show student name, course, professor, and department
SELECT
    s.name       AS student,
    c.course_name AS course,
    p.name       AS professor,
    d.dept_name  AS department,
    e.grade
FROM students s
INNER JOIN enrollments e ON s.id = e.student_id       -- student ↔ enrollment
INNER JOIN courses c     ON e.course_id = c.course_id  -- enrollment ↔ course
INNER JOIN professors p  ON c.prof_id = p.prof_id      -- course ↔ professor
INNER JOIN departments d ON p.dept_id = d.dept_id      -- professor ↔ department
ORDER BY s.name, c.course_name;
```

**How multi-table JOINs work step by step:**

```
Step 1: students ⟕ enrollments    → result_1 (students with their enrollments)
Step 2: result_1 ⟕ courses        → result_2 (add course details)
Step 3: result_2 ⟕ professors     → result_3 (add professor details)
Step 4: result_3 ⟕ departments    → final   (add department details)
```

**Mixing JOIN types in multi-table queries:**

```sql
-- Left join to include students with NO enrollments,
-- but inner join for course → professor (every course must have a professor)
SELECT s.name AS student, c.course_name, p.name AS professor
FROM students s
LEFT JOIN enrollments e  ON s.id = e.student_id          -- keep all students
LEFT JOIN courses c      ON e.course_id = c.course_id    -- keep enrollment NULLs
INNER JOIN professors p  ON c.prof_id = p.prof_id        -- only where professor exists
ORDER BY s.name;
```

---

### 7️⃣ JOIN Performance Tips

| Tip | Why |
|---|---|
| **Always index JOIN columns** | JOINs on non-indexed columns cause full table scans |
| **Index foreign key columns** | FK columns are the most common JOIN conditions |
| **Use INNER JOIN when possible** | Narrower results = less work for MySQL |
| **Avoid CROSS JOIN on large tables** | 1M × 1M = 1 trillion rows! |
| **Put the smaller table first** | MySQL's optimizer usually handles this, but it helps readability |
| **Use EXPLAIN to verify** | Check that MySQL uses indexes for the JOIN |
| **JOIN vs Subquery** | JOINs are usually faster; use EXPLAIN to confirm |

```sql
-- Verify JOIN uses indexes
EXPLAIN SELECT s.name, g.subject
FROM students s
INNER JOIN grades g ON s.id = g.student_id;
-- Look for 'type: ref' or 'type: eq_ref' (good)
-- Avoid 'type: ALL' (full table scan — bad)
```

---

### 8️⃣ Common JOIN Mistakes & How to Fix Them

| Mistake | Problem | Fix |
|---|---|---|
| Missing ON clause | Becomes a CROSS JOIN (Cartesian product!) | Always specify ON or USING |
| Wrong JOIN column | Incorrect or meaningless results | Verify the relationship between tables |
| Forgetting NULL handling | LEFT JOIN NULLs cause wrong aggregations | Use COALESCE or filter NULLs |
| Using WHERE instead of ON | Changes LEFT/RIGHT JOIN into INNER JOIN | Put join conditions in ON, filters in WHERE |
| Not aliasing tables | Ambiguous column errors with same-name columns | Always alias tables in JOINs |

```sql
-- ❌ MISTAKE: WHERE on a LEFT JOIN effectively makes it INNER JOIN
SELECT s.name, g.subject
FROM students s
LEFT JOIN grades g ON s.id = g.student_id
WHERE g.subject = 'Math';
-- Charlie disappears! The WHERE filters out NULLs.

-- ✅ FIX: Put the condition in the ON clause to keep all left rows
SELECT s.name, g.subject
FROM students s
LEFT JOIN grades g ON s.id = g.student_id AND g.subject = 'Math';
-- Charlie appears with NULL (preserved by LEFT JOIN)
```

---

### 📊 Complete JOIN Comparison Summary

| JOIN Type | Left Unmatched | Right Unmatched | Matched Rows | NULL-Filled | Common Use |
|---|---|---|---|---|---|
| **INNER** | ❌ Excluded | ❌ Excluded | ✅ Returned | No | Default — most common |
| **LEFT** | ✅ Kept | ❌ Excluded | ✅ Returned | Right side → NULL | "All from main + optional related" |
| **RIGHT** | ❌ Excluded | ✅ Kept | ✅ Returned | Left side → NULL | Rarely used; rewrite as LEFT |
| **FULL OUTER** | ✅ Kept | ✅ Kept | ✅ Returned | Both sides → NULL | Data reconciliation |
| **CROSS** | N/A | N/A | All × All | No | Combinations, matrix generation |
| **SELF** | Depends on type | Depends on type | ✅ | Depends | Hierarchies, comparisons |
| **NATURAL** | ❌ (like INNER) | ❌ (like INNER) | ✅ | No | Prototyping only |

---

### ✏️ Practice Exercise 19

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Using the `students` and `grades` tables, write a LEFT JOIN that shows all students and their grades. Filter to show only students with no grades (hint: `WHERE g.student_id IS NULL`).
> 2. Write a FULL OUTER JOIN (using UNION) between `students` and `grades` — show all unmatched rows from both sides.
> 3. Create `employees` and `departments` tables. Write an INNER JOIN to show employee names with department names. Then rewrite it as a LEFT JOIN — what changes?
> 4. Create a self-referencing `categories` table (parent_id → category_id) and query to show each category with its parent name.
> 5. Write a CROSS JOIN to generate all combinations of sizes (S, M, L, XL) and colors (Red, Blue, Green).
> 6. Join 3 tables together: `orders → order_items → products` to show order details with product names.
> 7. Explain the difference between putting a filter in the `ON` clause vs the `WHERE` clause for a LEFT JOIN.

---

## Topic 20 — Aggregate Functions

### 🌍 Real-Life Analogy

Aggregate functions are like a **calculator for your data**. Instead of looking at individual rows, you zoom out: "How many orders?" (COUNT), "What's the total revenue?" (SUM), "What's the average score?" (AVG).

---

### 1️⃣ WHY — Why Aggregations?

- **Reporting** — Total sales, average ratings, maximum values.
- **Business intelligence** — KPIs, dashboards, summaries.
- **Data analysis** — Statistical measures across groups.

---

### 2️⃣ WHEN — When to Use Each Function

| Function | Returns | Example Use |
|---|---|---|
| `COUNT(*)` | Number of rows | How many orders? |
| `COUNT(col)` | Non-NULL values in column | How many customers have a phone number? |
| `SUM(col)` | Total | Total revenue |
| `AVG(col)` | Average | Average order value |
| `MIN(col)` | Smallest value | Lowest price |
| `MAX(col)` | Largest value | Highest score |

---

### 3️⃣ HOW — Aggregations with GROUP BY

#### Example 43: Basic aggregations

```sql
USE store;  -- using the products table from earlier

-- Count all products
SELECT COUNT(*) AS total_products FROM products;
-- Output: 10

-- Sum of all stock
SELECT SUM(stock) AS total_inventory FROM products;

-- Average price
SELECT AVG(price) AS avg_price FROM products;

-- Min and Max price
SELECT MIN(price) AS cheapest, MAX(price) AS most_expensive FROM products;
```

#### Example 44: GROUP BY — aggregate per category

```sql
-- Count products and average price per category
SELECT
    category,
    COUNT(*) AS num_products,
    ROUND(AVG(price), 2) AS avg_price,
    SUM(stock) AS total_stock
FROM products
GROUP BY category;
```

**Result:**

| category    | num_products | avg_price | total_stock |
|-------------|-------------|-----------|-------------|
| Electronics | 5           | 381.99    | 685         |
| Furniture   | 3           | 346.66    | 70          |
| Stationery  | 2           | 3.99      | 1500        |

#### Example 45: HAVING — filter groups

```sql
-- Only show categories with average price > 100
SELECT
    category,
    COUNT(*) AS num_products,
    ROUND(AVG(price), 2) AS avg_price
FROM products
GROUP BY category
HAVING AVG(price) > 100;
```

> **WHERE vs HAVING:**
> - `WHERE` filters **rows** before grouping.
> - `HAVING` filters **groups** after aggregation.

```sql
-- WHERE filters rows, then GROUP BY aggregates, then HAVING filters groups
SELECT category, AVG(price) AS avg_price
FROM products
WHERE stock > 20                  -- step 1: only rows where stock > 20
GROUP BY category                 -- step 2: group remaining rows
HAVING AVG(price) > 50;           -- step 3: only groups with avg_price > 50
```

---

### ✏️ Practice Exercise 20

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Find the total value of inventory (price × stock) for each category.
> 2. Find the category with the most products.
> 3. List categories that have more than 2 products using HAVING.
> 4. Find the average, min, and max price for electronics products only.

---

## Topic 21 — Subqueries

### 🌍 Real-Life Analogy

A subquery is like asking a **follow-up question**. "Find me all products that are more expensive than the average price." First, you calculate the average price (inner query), then you use that result to filter products (outer query).

---

### 1️⃣ WHY — Why Subqueries?

- Solve problems that require **two-step logic** in a single SQL statement.
- Create dynamic filters based on aggregated or computed values.
- Can sometimes replace JOINs for readability.

---

### 2️⃣ WHEN — Types of Subqueries

| Type | Returns | Example |
|---|---|---|
| **Scalar** | One value | `WHERE price > (SELECT AVG(price) FROM products)` |
| **Row** | One row | `WHERE (col1, col2) = (SELECT col1, col2 FROM ...)` |
| **Table** | Multiple rows | `WHERE id IN (SELECT id FROM ...)` |
| **Correlated** | References outer query | `WHERE price > (SELECT AVG(price) FROM products p2 WHERE p2.category = p1.category)` |

---

### 3️⃣ HOW — Subquery Examples

#### Example 46: Scalar subquery

```sql
-- Products priced above the overall average
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```

The inner query `SELECT AVG(price) FROM products` returns a single value (e.g., 293.69), which is then used in the WHERE clause.

#### Example 47: IN subquery

```sql
-- Products in categories that have more than 2 products
SELECT product_name, category, price
FROM products
WHERE category IN (
    SELECT category
    FROM products
    GROUP BY category
    HAVING COUNT(*) > 2
);
```

#### Example 48: Correlated subquery

```sql
-- Products that are the most expensive in their category
SELECT p1.product_name, p1.category, p1.price
FROM products p1
WHERE p1.price = (
    SELECT MAX(p2.price)
    FROM products p2
    WHERE p2.category = p1.category   -- references outer query
);
```

For each row in the outer query, the inner query recalculates `MAX(price)` for that row's category.

#### Example 49: EXISTS subquery

```sql
-- Customers who have placed at least one order
-- (assumes customers and orders tables exist)
SELECT c.name, c.email
FROM customers c
WHERE EXISTS (
    SELECT 1 FROM orders o WHERE o.customer_id = c.customer_id
);
```

`EXISTS` returns TRUE if the subquery returns **any** rows. It's often faster than `IN` for large datasets.

#### Example 50: Subquery in SELECT (computed column)

```sql
-- Show each product with the category's average price
SELECT
    product_name,
    price,
    category,
    (SELECT ROUND(AVG(price), 2) FROM products p2 WHERE p2.category = p1.category) AS category_avg
FROM products p1;
```

---

### ✏️ Practice Exercise 21

> **Difficulty:** ⭐⭐⭐ Intermediate–Advanced
>
> 1. Find products that cost more than double the cheapest product.
> 2. Find the product(s) with the highest price in each category using a correlated subquery.
> 3. Rewrite the correlated subquery from #2 using a JOIN instead.
> 4. Find categories where the total stock is above the average total stock across all categories.

---

## Topic 22 — Window Functions

### 🌍 Real-Life Analogy

Imagine a class ranking. Each student has their own score, but you also want to see their **rank** compared to everyone else — without collapsing the individual rows into a summary. Window functions calculate values **across a set of rows related to the current row** without grouping them.

---

### 1️⃣ WHY — Why Window Functions?

| Problem | Aggregate (GROUP BY) | Window Function |
|---|---|---|
| Show individual rows + summary | Can't — grouping collapses rows | ✅ Keeps all rows |
| Rank within groups | Requires complex subqueries | ✅ Built-in `RANK()` |
| Compare to previous/next row | Requires self-joins | ✅ `LAG()` / `LEAD()` |
| Running totals | Complex with variables | ✅ `SUM() OVER()` |

---

### 2️⃣ WHEN — Common Window Functions

| Function | Purpose |
|---|---|
| `ROW_NUMBER()` | Unique sequential number per row |
| `RANK()` | Rank with gaps (ties share rank, next rank skips) |
| `DENSE_RANK()` | Rank without gaps |
| `LAG(col, N)` | Value from N rows before |
| `LEAD(col, N)` | Value from N rows ahead |
| `SUM() OVER()` | Running total |
| `AVG() OVER()` | Moving average |
| `NTILE(N)` | Divide rows into N equal groups |

---

### 3️⃣ HOW — Window Function Syntax

```
function_name() OVER (
    [PARTITION BY column]   -- optional: groups rows
    [ORDER BY column]       -- optional: defines row ordering
    [ROWS frame_spec]       -- optional: defines the window frame
)
```

#### Example 51: ROW_NUMBER, RANK, DENSE_RANK

```sql
-- Rank products by price within each category
SELECT
    product_name,
    category,
    price,
    ROW_NUMBER() OVER (PARTITION BY category ORDER BY price DESC) AS row_num,
    RANK()       OVER (PARTITION BY category ORDER BY price DESC) AS rnk,
    DENSE_RANK() OVER (PARTITION BY category ORDER BY price DESC) AS dense_rnk
FROM products;
```

**Difference between RANK and DENSE_RANK:**
- Scores: 100, 90, 90, 80
- `RANK()`: 1, 2, 2, **4** (skips 3)
- `DENSE_RANK()`: 1, 2, 2, **3** (no gap)

#### Example 52: LAG and LEAD

```sql
-- Show each product with the previous and next product's price (ordered by price)
SELECT
    product_name,
    price,
    LAG(price, 1)  OVER (ORDER BY price) AS prev_price,
    LEAD(price, 1) OVER (ORDER BY price) AS next_price,
    price - LAG(price, 1) OVER (ORDER BY price) AS price_diff
FROM products;
```

#### Example 53: Running total with SUM OVER

```sql
-- Running total of product prices ordered by product_id
SELECT
    product_id,
    product_name,
    price,
    SUM(price) OVER (ORDER BY product_id) AS running_total
FROM products;
```

#### Example 54: NTILE — divide into groups

```sql
-- Divide products into 3 price tiers
SELECT
    product_name,
    price,
    NTILE(3) OVER (ORDER BY price) AS price_tier
FROM products;
```

---

### ✏️ Practice Exercise 22

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Rank products by price within each category using DENSE_RANK. Show only the top 2 in each category.
> 2. Calculate the running total of stock for all products ordered by product_id.
> 3. Use LAG to show the price difference between consecutive products (ordered by price).
> 4. Use NTILE(4) to divide products into quartiles by price.

---

## Topic 23 — UNION, INTERSECT, EXCEPT

### 🌍 Real-Life Analogy

You have two guest lists for two different parties. `UNION` merges them into one big list. `INTERSECT` finds people on **both** lists. `EXCEPT` finds people on the first list but **not** the second.

---

### 1️⃣ WHY — Why Set Operations?

- Combine results from **different queries** into a single result set.
- Compare two result sets to find commonalities or differences.

---

### 2️⃣ WHEN — When to Use

| Operation | Use Case |
|---|---|
| `UNION` | Merge results from two tables with the same structure |
| `UNION ALL` | Same as UNION but keeps duplicates (faster) |
| `INTERSECT` | Find rows common to both queries |
| `EXCEPT` | Find rows in the first query but not the second |

> ⚠️ MySQL 8.0.31+ supports INTERSECT and EXCEPT. Earlier versions require workarounds.

---

### 3️⃣ HOW — Set Operations

#### Example 55: UNION and UNION ALL

```sql
-- Two tables with similar structure
CREATE TABLE suppliers (
    id   INT PRIMARY KEY,
    name VARCHAR(100),
    city VARCHAR(50)
);

CREATE TABLE clients (
    id   INT PRIMARY KEY,
    name VARCHAR(100),
    city VARCHAR(50)
);

INSERT INTO suppliers VALUES (1, 'Acme Corp', 'NYC'), (2, 'Globex', 'LA');
INSERT INTO clients VALUES (1, 'Alice Inc', 'NYC'), (2, 'Acme Corp', 'NYC');

-- UNION: combine and remove duplicates
SELECT name, city FROM suppliers
UNION
SELECT name, city FROM clients;
-- Returns 3 rows (Acme Corp appears once)

-- UNION ALL: combine and keep duplicates (faster)
SELECT name, city FROM suppliers
UNION ALL
SELECT name, city FROM clients;
-- Returns 4 rows (Acme Corp appears twice)
```

#### Example 56: INTERSECT and EXCEPT

```sql
-- INTERSECT: rows in both results
SELECT name, city FROM suppliers
INTERSECT
SELECT name, city FROM clients;
-- Returns: Acme Corp, NYC (in both tables)

-- EXCEPT: rows in first but not second
SELECT name, city FROM suppliers
EXCEPT
SELECT name, city FROM clients;
-- Returns: Globex, LA (only in suppliers)
```

---

### ✏️ Practice Exercise 23

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create two tables: `online_customers` and `store_customers` with (id, name, email).
> 2. Use UNION to create a combined customer list.
> 3. Use INTERSECT to find customers who buy both online and in-store.
> 4. Use EXCEPT to find online-only customers.

---

## Topic 24 — ORDER BY, GROUP BY, HAVING

### 🌍 Real-Life Analogy

- `ORDER BY` is sorting your mail by date.
- `GROUP BY` is sorting mail into piles by sender.
- `HAVING` is removing piles with fewer than 3 letters.

---

### 1️⃣ WHY — Why These Clauses?

They transform raw data into organized, summarized information — the foundation of all reporting.

---

### 2️⃣ WHEN — Combining Them

Typical pattern: `SELECT` → `FROM` → `WHERE` → `GROUP BY` → `HAVING` → `ORDER BY` → `LIMIT`

---

### 3️⃣ HOW — Practical Combinations

#### Example 57: Combined query

```sql
-- Sales summary: top 3 categories by total revenue, only categories with > $500 revenue
SELECT
    category,
    COUNT(*) AS num_products,
    SUM(price * stock) AS total_value,
    ROUND(AVG(price), 2) AS avg_price
FROM products
WHERE stock > 0                         -- filter rows first
GROUP BY category                       -- group remaining rows
HAVING SUM(price * stock) > 500         -- filter groups
ORDER BY total_value DESC               -- sort results
LIMIT 3;                                -- take top 3
```

**Line-by-line explanation:**

| Line | Purpose |
|---|---|
| `WHERE stock > 0` | Only include products that are in stock (row-level filter). |
| `GROUP BY category` | Create one group per category. |
| `HAVING SUM(price * stock) > 500` | Keep only groups with total value > $500 (group-level filter). |
| `ORDER BY total_value DESC` | Sort by total value, highest first. |
| `LIMIT 3` | Show only top 3 results. |

#### Example 58: Multiple column ordering

```sql
-- Order by category (A-Z), then by price within each category (high to low)
SELECT product_name, category, price
FROM products
ORDER BY category ASC, price DESC;
```

---

### ✏️ Practice Exercise 24

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. List all categories sorted alphabetically, showing count of products in each.
> 2. Show the total stock value (price × stock) per category, ordered by total value descending.
> 3. Find categories where the average price is greater than $50, showing only the top 2.
> 4. Write a query that uses WHERE, GROUP BY, HAVING, ORDER BY, and LIMIT all together.

---

## Topic 24A — Common Table Expressions (CTEs)

### 🌍 Real-Life Analogy

A CTE is like writing a **draft paragraph** before using it in your essay. You define a temporary named result set at the top of your query, then reference it below — making complex queries much more readable and maintainable.

---

### 1️⃣ WHY — Why CTEs?

| Problem Without CTEs | Solution With CTEs |
|---|---|
| Deeply nested subqueries are hard to read | Named CTEs break queries into logical steps |
| Repeating the same subquery in multiple places | Define once in a CTE, reference many times |
| Recursive data (hierarchies, trees) impossible | Recursive CTEs handle parent-child traversals |
| No way to self-reference a subquery | Recursive CTEs reference themselves |

---

### 2️⃣ WHEN — When to Use CTEs

| Scenario | CTE Type |
|---|---|
| Breaking a complex query into readable steps | Non-recursive CTE |
| Reusing the same subquery result multiple times | Non-recursive CTE |
| Traversing hierarchies (org charts, category trees) | Recursive CTE |
| Generating sequences (numbers, dates) | Recursive CTE |
| Replacing complex subqueries for readability | Non-recursive CTE |

---

### 3️⃣ HOW — CTE Syntax and Examples

#### Basic CTE Syntax

```sql
WITH cte_name AS (
    -- CTE query (the "draft paragraph")
    SELECT ...
)
-- Main query that uses the CTE
SELECT * FROM cte_name;
```

#### Example 24A-1: Non-recursive CTE — simplify complex queries

```sql
-- Without CTE (nested subquery — harder to read):
SELECT name, total_spent
FROM (
    SELECT c.name, SUM(o.total) AS total_spent
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    WHERE o.status != 'cancelled'
    GROUP BY c.customer_id, c.name
) AS customer_spending
WHERE total_spent > 200;

-- With CTE (same result, much cleaner):
WITH customer_spending AS (
    SELECT c.name, SUM(o.total) AS total_spent
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    WHERE o.status != 'cancelled'
    GROUP BY c.customer_id, c.name
)
SELECT name, total_spent
FROM customer_spending
WHERE total_spent > 200
ORDER BY total_spent DESC;
```

#### Example 24A-2: Multiple CTEs — chain logic steps

```sql
-- Step 1: Calculate monthly revenue
-- Step 2: Calculate month-over-month growth
-- Step 3: Filter to growing months only

WITH monthly_revenue AS (
    SELECT
        DATE_FORMAT(order_date, '%Y-%m') AS month,
        SUM(total) AS revenue
    FROM orders
    WHERE status != 'cancelled'
    GROUP BY DATE_FORMAT(order_date, '%Y-%m')
),
revenue_with_growth AS (
    SELECT
        month,
        revenue,
        LAG(revenue) OVER (ORDER BY month) AS prev_revenue,
        ROUND(
            (revenue - LAG(revenue) OVER (ORDER BY month))
            / LAG(revenue) OVER (ORDER BY month) * 100, 1
        ) AS growth_pct
    FROM monthly_revenue
)
SELECT * FROM revenue_with_growth
WHERE growth_pct > 0
ORDER BY month;
```

#### Example 24A-3: CTE referenced multiple times

```sql
-- Calculate category stats, then use them in two different ways
WITH category_stats AS (
    SELECT
        category,
        COUNT(*) AS product_count,
        AVG(price) AS avg_price,
        SUM(stock) AS total_stock
    FROM products
    GROUP BY category
)
-- Use the CTE twice: once for the main query, once for a comparison
SELECT
    cs.category,
    cs.product_count,
    ROUND(cs.avg_price, 2) AS avg_price,
    cs.total_stock,
    ROUND(cs.avg_price / overall.global_avg * 100, 1) AS pct_of_global_avg
FROM category_stats cs
CROSS JOIN (
    SELECT AVG(avg_price) AS global_avg FROM category_stats
) AS overall
ORDER BY cs.avg_price DESC;
```

#### Example 24A-4: Recursive CTE — Org Chart / Hierarchy

```sql
-- Recursive CTEs traverse parent-child relationships!
-- Start from a root node and follow links to children

CREATE TABLE categories_tree (
    id        INT PRIMARY KEY,
    name      VARCHAR(50),
    parent_id INT
);

INSERT INTO categories_tree VALUES
    (1, 'All Products',  NULL),
    (2, 'Electronics',   1),
    (3, 'Computers',     2),
    (4, 'Laptops',       3),
    (5, 'Desktops',      3),
    (6, 'Phones',        2),
    (7, 'Clothing',      1),
    (8, 'Men',           7),
    (9, 'Women',         7);

-- Recursive CTE: show the full category hierarchy with depth
WITH RECURSIVE category_tree AS (
    -- Base case: start from root nodes (no parent)
    SELECT id, name, parent_id, 0 AS depth, CAST(name AS CHAR(500)) AS path
    FROM categories_tree
    WHERE parent_id IS NULL

    UNION ALL

    -- Recursive step: join children to their parents
    SELECT c.id, c.name, c.parent_id, ct.depth + 1,
           CONCAT(ct.path, ' → ', c.name)
    FROM categories_tree c
    INNER JOIN category_tree ct ON c.parent_id = ct.id
)
SELECT
    CONCAT(REPEAT('  ', depth), name) AS indented_name,
    depth,
    path
FROM category_tree
ORDER BY path;
```

**Result:**

| indented_name       | depth | path                                    |
|---------------------|-------|-----------------------------------------|
| All Products        | 0     | All Products                            |
|   Clothing          | 1     | All Products → Clothing                 |
|     Men             | 2     | All Products → Clothing → Men           |
|     Women           | 2     | All Products → Clothing → Women         |
|   Electronics       | 1     | All Products → Electronics              |
|     Computers       | 2     | All Products → Electronics → Computers  |
|       Desktops      | 3     | All Products → Electronics → Computers → Desktops |
|       Laptops       | 3     | All Products → Electronics → Computers → Laptops  |
|     Phones          | 2     | All Products → Electronics → Phones     |

#### Example 24A-5: Recursive CTE — Generate a Date Series

```sql
-- Generate all dates in January 2026 (no table needed!)
WITH RECURSIVE date_series AS (
    SELECT DATE('2026-01-01') AS dt
    UNION ALL
    SELECT DATE_ADD(dt, INTERVAL 1 DAY)
    FROM date_series
    WHERE dt < '2026-01-31'
)
SELECT dt AS date FROM date_series;
-- Returns 31 rows: 2026-01-01 through 2026-01-31

-- Practical use: find dates with NO orders (gaps in data)
WITH RECURSIVE date_series AS (
    SELECT DATE('2024-01-01') AS dt
    UNION ALL
    SELECT DATE_ADD(dt, INTERVAL 1 DAY)
    FROM date_series
    WHERE dt < '2024-03-31'
)
SELECT ds.dt AS missing_date
FROM date_series ds
LEFT JOIN orders o ON ds.dt = o.order_date
WHERE o.order_id IS NULL
ORDER BY ds.dt;
```

#### Example 24A-6: Recursive CTE — Employee Reporting Chain

```sql
-- Find all reports (direct and indirect) under a specific manager
WITH RECURSIVE reporting_chain AS (
    -- Base case: the manager themselves
    SELECT emp_id, emp_name, manager_id, 1 AS level
    FROM employees_self
    WHERE emp_id = 1  -- Start from CEO

    UNION ALL

    -- Recursive: find all employees who report to someone in the chain
    SELECT e.emp_id, e.emp_name, e.manager_id, rc.level + 1
    FROM employees_self e
    INNER JOIN reporting_chain rc ON e.manager_id = rc.emp_id
)
SELECT
    CONCAT(REPEAT('  ', level - 1), emp_name) AS org_chart,
    level
FROM reporting_chain
ORDER BY level, emp_name;
```

> ⚠️ **Warning:** Recursive CTEs need a termination condition! Without one, they run forever. MySQL has a default limit of 1000 recursions (`cte_max_recursion_depth`). You can increase it:
> ```sql
> SET SESSION cte_max_recursion_depth = 5000;
> ```

**CTE vs Subquery vs Temporary Table:**

| Feature | CTE | Subquery | Temporary Table |
|---|---|---|---|
| Readability | ✅ Best | ❌ Nested = hard | ✅ Good |
| Reusability in same query | ✅ Multiple references | ❌ Must repeat | ✅ Multiple queries |
| Recursive | ✅ Yes | ❌ No | ❌ No |
| Persists after query | ❌ No | ❌ No | ✅ Until session ends |
| Performance | Same as subquery | Same as CTE | May be faster (materialized) |

---

### ✏️ Practice Exercise 24A

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Rewrite a complex subquery you've written before as a CTE. Compare readability.
> 2. Write a CTE that calculates average order value per customer, then finds customers above the global average.
> 3. Create a recursive CTE to traverse the `categories_tree` table and show each category with its full path.
> 4. Use a recursive CTE to generate all dates in the current month.
> 5. Chain 3 CTEs together: monthly sales → running total → growth percentage.

---

## 🏁 Part 5 Summary

| Topic | Key Takeaway |
|---|---|
| **JOINs** | 7 types: INNER, LEFT, RIGHT, FULL OUTER (emulated), CROSS, SELF, NATURAL. Use ON/USING for conditions. |
| **Aggregations** | COUNT, SUM, AVG, MIN, MAX + GROUP BY to summarize. HAVING filters groups. |
| **Subqueries** | Queries within queries. Scalar, table, correlated, and EXISTS forms. |
| **Window Functions** | ROW_NUMBER, RANK, LAG, LEAD, running totals — calculate across related rows without collapsing. |
| **Set Operations** | UNION (merge), INTERSECT (common), EXCEPT (difference). |
| **ORDER/GROUP/HAVING** | Sort, group, and filter groups — the backbone of reporting queries. |
| **CTEs** | WITH clause for readable, reusable, and recursive query building. |

> **Next up:** [Part 6: Transactions & Security](#part-6-transactions--security) — ACID properties, isolation levels, users, privileges, and backups.

---

# Part 6: Transactions & Security

> **Goal:** Understand ACID transactions, isolation levels, user management, and backup strategies.

---

## Topic 25 — Transactions and ACID

### 🌍 Real-Life Analogy

A **bank transfer**: you move $500 from Account A to Account B. If the money leaves A but a power outage stops it from reaching B, you've lost $500. A **transaction** ensures that **both steps happen, or neither does**.

---

### 1️⃣ WHY — Why Transactions?

Transactions guarantee **ACID** properties:

| Property | Meaning | Example |
|---|---|---|
| **Atomicity** | All or nothing | Both debit and credit execute, or both are undone |
| **Consistency** | Data moves from one valid state to another | Total money in the system remains the same |
| **Isolation** | Concurrent transactions don't interfere | Two transfers happening simultaneously don't corrupt each other |
| **Durability** | Once committed, data survives crashes | Even if the server reboots, committed data is safe |

---

### 2️⃣ WHEN — When to Use Transactions

- Any operation involving **multiple related changes** (transfers, multi-table inserts).
- When you need a **rollback safety net** (import scripts, migrations).
- When concurrency matters (multiple users updating the same data).

---

### 3️⃣ HOW — Transaction Commands

#### Example 59: Basic transaction

```sql
CREATE TABLE accounts (
    account_id INT PRIMARY KEY,
    owner      VARCHAR(50),
    balance    DECIMAL(12,2) CHECK (balance >= 0)
);

INSERT INTO accounts VALUES (1, 'Alice', 1000.00), (2, 'Bob', 500.00);

-- Transfer $200 from Alice to Bob
START TRANSACTION;

UPDATE accounts SET balance = balance - 200 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 200 WHERE account_id = 2;

-- Verify before committing
SELECT * FROM accounts;
-- Alice: 800, Bob: 700

-- Make it permanent
COMMIT;
```

#### Example 60: ROLLBACK on error

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 2000 WHERE account_id = 1;
-- Alice only has 800! CHECK constraint or application logic detects this.

-- Something went wrong — undo everything
ROLLBACK;

-- Alice's balance is still 800 (unchanged)
SELECT balance FROM accounts WHERE account_id = 1;
```

#### Example 61: SAVEPOINT for partial rollback

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
SAVEPOINT after_debit;

UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;
-- Oops, wrong recipient! Roll back only to the savepoint
ROLLBACK TO SAVEPOINT after_debit;

-- Now credit the correct account
UPDATE accounts SET balance = balance + 100 WHERE account_id = 3;

COMMIT;
```

| Command | What It Does |
|---|---|
| `START TRANSACTION` | Begins a new transaction |
| `COMMIT` | Saves all changes permanently |
| `ROLLBACK` | Undoes all changes since START TRANSACTION |
| `SAVEPOINT name` | Creates a named checkpoint |
| `ROLLBACK TO SAVEPOINT name` | Undoes changes back to that checkpoint (not the whole transaction) |

---

### ✏️ Practice Exercise 25

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create an `accounts` table and insert 3 accounts.
> 2. Write a transaction that transfers money between two accounts. Verify balances before and after COMMIT.
> 3. Write a transaction that intentionally causes an error, and use ROLLBACK to undo the changes.
> 4. Use SAVEPOINT to partially rollback a multi-step transaction.

---

## Topic 26 — Isolation Levels

### 🌍 Real-Life Analogy

Imagine reading a shared document while someone else is editing it. Should you see their **unsaved changes**? Their **saved but uncommitted** changes? Only **final committed** changes? Isolation levels control how much of other transactions' work you can see.

---

### 1️⃣ WHY — Why Isolation Levels?

Different applications need different trade-offs between **data accuracy** and **performance**:
- Stricter isolation = more accurate but slower (more locking).
- Looser isolation = faster but may see incomplete data.

---

### 2️⃣ WHEN — Choosing an Isolation Level

| Level | Dirty Reads | Non-Repeatable Reads | Phantom Reads | Use When |
|---|---|---|---|---|
| **READ UNCOMMITTED** | ✅ Possible | ✅ Possible | ✅ Possible | Rough monitoring, never for production |
| **READ COMMITTED** | ❌ No | ✅ Possible | ✅ Possible | Most web apps, PostgreSQL default |
| **REPEATABLE READ** | ❌ No | ❌ No | ✅ Possible* | MySQL default, good balance |
| **SERIALIZABLE** | ❌ No | ❌ No | ❌ No | Financial systems, maximum safety |

> *MySQL's InnoDB uses gap locking to also prevent phantom reads at REPEATABLE READ.

---

### 3️⃣ HOW — Setting Isolation Levels

#### Example 62: Checking and setting isolation level

```sql
-- Check current isolation level
SELECT @@transaction_isolation;
-- Default: REPEATABLE-READ

-- Set for current session
SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED;

-- Set for next transaction only
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;

-- Set globally (requires privileges)
SET GLOBAL TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

#### Example 63: Dirty read demonstration

```sql
-- Session 1: Start transaction but don't commit
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
START TRANSACTION;
UPDATE accounts SET balance = 9999 WHERE account_id = 1;
-- Don't commit yet!

-- Session 2 (with READ UNCOMMITTED): Can see uncommitted data!
SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
SELECT balance FROM accounts WHERE account_id = 1;
-- Shows 9999 (dirty read!) — this value may be rolled back!

-- Session 1: ROLLBACK
ROLLBACK;
-- Session 2 just read data that never actually existed.
```

---

### ✏️ Practice Exercise 26

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Check your MySQL's default isolation level.
> 2. Explain the difference between a dirty read and a phantom read.
> 3. When would you choose SERIALIZABLE over REPEATABLE READ?
> 4. In your own words, explain why READ UNCOMMITTED is dangerous for production systems.

---

## Topic 27 — Users and Privileges

### 🌍 Real-Life Analogy

A building has different access levels: visitors can enter the lobby, employees can access offices, only the manager has keys to the vault. MySQL privileges work the same way — different users get different levels of access.

---

### 1️⃣ WHY — Why Manage Users?

- **Security** — Don't run everything as root! Limit access to reduce damage from compromises.
- **Accountability** — Track who did what.
- **Principle of least privilege** — Users should only have the permissions they need.

---

### 2️⃣ WHEN — When to Create Users

| Scenario | Permissions |
|---|---|
| Application backend | SELECT, INSERT, UPDATE, DELETE on specific databases |
| Read-only dashboard | SELECT only |
| DBA / Admin | ALL PRIVILEGES (sparingly) |
| Backup script | SELECT, LOCK TABLES, SHOW VIEW |

---

### 3️⃣ HOW — User Management

#### Example 64: Creating and managing users

```sql
-- Create a user
CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'Str0ngP@ss!';

-- Create a user that can connect from anywhere
CREATE USER 'remote_user'@'%' IDENTIFIED BY 'An0therP@ss!';

-- Grant specific permissions
GRANT SELECT, INSERT, UPDATE ON shop.* TO 'app_user'@'localhost';

-- Grant all permissions on a database
GRANT ALL PRIVILEGES ON shop.* TO 'app_user'@'localhost';

-- Grant read-only access
GRANT SELECT ON shop.* TO 'readonly_user'@'localhost';

-- Apply privilege changes
FLUSH PRIVILEGES;

-- Show grants for a user
SHOW GRANTS FOR 'app_user'@'localhost';

-- Revoke permissions
REVOKE INSERT, UPDATE ON shop.* FROM 'app_user'@'localhost';

-- Change a user's password
ALTER USER 'app_user'@'localhost' IDENTIFIED BY 'NewStr0ngP@ss!';

-- Delete a user
DROP USER 'remote_user'@'%';
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `CREATE USER 'app_user'@'localhost'` | Creates user who can only connect from the same machine |
| `IDENTIFIED BY 'Str0ngP@ss!'` | Sets the password |
| `'remote_user'@'%'` | `%` means the user can connect from any host |
| `GRANT SELECT, INSERT, UPDATE ON shop.*` | Allows read, insert, and update on all tables in `shop` |
| `FLUSH PRIVILEGES` | Reloads privilege tables (not always needed, but ensures changes take effect) |
| `REVOKE INSERT, UPDATE ...` | Removes specific permissions |

---

### ✏️ Practice Exercise 27

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create a user `report_user` that can only SELECT from the `store` database.
> 2. Create a user `admin_user` with ALL PRIVILEGES on all databases.
> 3. Show grants for both users.
> 4. Revoke all privileges from `admin_user` and then drop the user.

---

## Topic 28 — Backup and Restore

### 🌍 Real-Life Analogy

Backup is like making a **photocopy** of important documents. If the originals are lost in a fire, you have copies. No backup = no recovery.

---

### 1️⃣ WHY — Why Backup?

- **Hardware failure** — Disks die. Servers crash.
- **Human error** — Someone runs `DROP TABLE` by accident.
- **Security incidents** — Ransomware, data corruption.
- **Compliance** — Many regulations require data retention.

---

### 2️⃣ WHEN — Backup Strategies

| Strategy | Frequency | Tool | Use Case |
|---|---|---|---|
| **Full backup** | Daily or weekly | `mysqldump` | Small to medium databases |
| **Incremental** | Hourly | Binary logs | Large databases, point-in-time recovery |
| **Physical backup** | Daily | `mysqlbackup` or file copy | Very large databases |

---

### 3️⃣ HOW — Backup and Restore Commands

#### Example 65: mysqldump backup

```bash
# Backup a single database
mysqldump -u root -p shop > shop_backup.sql

# Backup specific tables
mysqldump -u root -p shop products customers > shop_tables_backup.sql

# Backup all databases
mysqldump -u root -p --all-databases > all_databases_backup.sql

# Backup with structure only (no data)
mysqldump -u root -p --no-data shop > shop_structure.sql

# Backup with data only (no structure)
mysqldump -u root -p --no-create-info shop > shop_data.sql
```

#### Example 66: Restoring from backup

```bash
# Restore a database
mysql -u root -p shop < shop_backup.sql

# Restore into a new database
mysql -u root -p -e "CREATE DATABASE shop_restored;"
mysql -u root -p shop_restored < shop_backup.sql

# Restore all databases
mysql -u root -p < all_databases_backup.sql
```

#### Example 67: Automated backup script

```bash
#!/bin/bash
# Simple daily backup script
DATE=$(date +%Y-%m-%d)
BACKUP_DIR="/var/backups/mysql"
DB_NAME="shop"

mkdir -p "$BACKUP_DIR"

mysqldump -u root -p"YourPassword" "$DB_NAME" | gzip > "$BACKUP_DIR/${DB_NAME}_${DATE}.sql.gz"

# Keep only last 30 days
find "$BACKUP_DIR" -name "*.sql.gz" -mtime +30 -delete

echo "Backup completed: ${DB_NAME}_${DATE}.sql.gz"
```

---

### ✏️ Practice Exercise 28

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Back up your `store` database using `mysqldump`.
> 2. Drop the database, then restore it from the backup.
> 3. Create a structure-only backup and a data-only backup. When might each be useful?
> 4. Write a simple backup script that compresses the output with gzip.

---

## 🏁 Part 6 Summary

| Topic | Key Takeaway |
|---|---|
| **Transactions** | START TRANSACTION → COMMIT/ROLLBACK. ACID ensures reliability. |
| **Isolation Levels** | Trade-off between accuracy and performance. REPEATABLE READ is MySQL's default. |
| **Users & Privileges** | Principle of least privilege. Never use root in applications. |
| **Backup & Restore** | `mysqldump` for logical backups. Automate and test restores regularly. |

> **Next up:** [Part 7: Performance Optimization](#part-7-performance-optimization) — Indexes, EXPLAIN, query tuning, and partitioning.

---

# Part 7: Performance Optimization

> **Goal:** Make your queries and database fast. Learn indexes, query plans, optimization techniques, and partitioning.

---

## Topic 29 — Indexes

### 🌍 Real-Life Analogy

Think of a **book index** at the back. Without it, finding "transactions" means reading every page. With an index, you look up "transactions → page 247" and go directly there. Database indexes work the same way — they create shortcuts to data, making searches much faster.

---

### 1️⃣ WHY — Why Indexes?

| Without Index | With Index |
|---|---|
| Full table scan (every row checked) | Direct lookup via B-Tree |
| Slow on large tables (millions of rows) | Near-instant even with billions |
| O(n) complexity | O(log n) complexity |

---

### 2️⃣ WHEN — When to Create Indexes

✅ **Index these:**
- Columns used in WHERE clauses frequently
- Columns used in JOIN conditions
- Columns used in ORDER BY / GROUP BY
- Foreign key columns

❌ **Don't over-index:**
- Columns rarely used in queries
- Tables with very few rows
- Columns with very low cardinality (e.g., boolean)
- Tables with heavy INSERT/UPDATE (indexes slow writes)

---

### 3️⃣ HOW — Index Types and Usage

#### Example 68: Creating indexes

```sql
USE store;

-- Single-column index
CREATE INDEX idx_product_name ON products(product_name);

-- Composite index (multi-column)
CREATE INDEX idx_cat_price ON products(category, price);

-- Unique index
CREATE UNIQUE INDEX idx_unique_email ON customers(email);

-- Show indexes on a table
SHOW INDEX FROM products;

-- Drop an index
DROP INDEX idx_product_name ON products;
```

#### Example 69: Index types

```sql
-- B-Tree index (default) — best for =, <, >, BETWEEN, LIKE 'prefix%'
CREATE INDEX idx_btree ON products(price);

-- FULLTEXT index — for text search
ALTER TABLE products ADD FULLTEXT INDEX idx_fulltext (product_name);
SELECT * FROM products WHERE MATCH(product_name) AGAINST('laptop');

-- Prefix index — for long VARCHAR columns
CREATE INDEX idx_prefix ON customers(email(20));
-- Only indexes the first 20 characters
```

#### Example 70: Composite index ordering matters

```sql
-- This composite index helps queries that filter by category, then price
CREATE INDEX idx_cat_price ON products(category, price);

-- ✅ Uses the index (leftmost columns match)
SELECT * FROM products WHERE category = 'Electronics';
SELECT * FROM products WHERE category = 'Electronics' AND price > 100;

-- ❌ Cannot use this index efficiently
SELECT * FROM products WHERE price > 100;
-- (price is the second column — the index requires category first)
```

> **Rule of thumb:** A composite index `(A, B, C)` supports queries filtering on `A`, `A+B`, or `A+B+C`, but NOT just `B` or `C` alone.

---

### ✏️ Practice Exercise 29

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Create an index on the `products.category` column. Run a SELECT with `WHERE category = 'Electronics'` before and after creating the index — use `EXPLAIN` to see the difference.
> 2. Create a composite index on `(category, price)`. Test which queries can use it.
> 3. What happens to INSERT performance when you add many indexes? Why?
> 4. When would you use a FULLTEXT index instead of a B-Tree index?

---

## Topic 30 — EXPLAIN and Query Plans

### 🌍 Real-Life Analogy

`EXPLAIN` is like asking a GPS to show you its planned route before you start driving. It shows you **how MySQL plans to execute your query** — which indexes it will use, how many rows it will scan, and where bottlenecks might be.

---

### 1️⃣ WHY — Why Use EXPLAIN?

- Identify **slow queries** before they become production problems.
- Verify that indexes are being used.
- Understand the cost of complex JOINs and subqueries.

---

### 2️⃣ WHEN — When to Use EXPLAIN

- Before deploying any query that runs on large tables.
- When a query is slower than expected.
- When adding or evaluating indexes.
- During code review of database queries.

---

### 3️⃣ HOW — Reading EXPLAIN Output

#### Example 71: Basic EXPLAIN

```sql
EXPLAIN SELECT * FROM products WHERE category = 'Electronics';
```

**Key columns in EXPLAIN output:**

| Column | What It Tells You |
|---|---|
| `type` | How MySQL accesses the table: `ALL` (full scan — bad), `ref` (index lookup — good), `const` (single row — best) |
| `possible_keys` | Indexes MySQL could use |
| `key` | Index MySQL actually chose |
| `rows` | Estimated number of rows to scan |
| `Extra` | Additional info: `Using where`, `Using index`, `Using filesort` |

#### Example 72: EXPLAIN comparison with and without index

```sql
-- Without index (full table scan)
DROP INDEX idx_cat_price ON products;
EXPLAIN SELECT * FROM products WHERE category = 'Electronics' AND price > 100;
-- type: ALL, rows: 10 (scans entire table)

-- With index
CREATE INDEX idx_cat_price ON products(category, price);
EXPLAIN SELECT * FROM products WHERE category = 'Electronics' AND price > 100;
-- type: range, key: idx_cat_price, rows: 3 (much fewer rows scanned)
```

#### Example 73: EXPLAIN FORMAT=JSON for detailed analysis

```sql
EXPLAIN FORMAT=JSON
SELECT p.product_name, c.category_name
FROM products p
JOIN categories c ON p.category_id = c.category_id
WHERE p.price > 100;
```

#### Common EXPLAIN type values (best to worst):

| type | Meaning | Speed |
|---|---|---|
| `system` | Single-row table | ⚡ Fastest |
| `const` | One matching row (PK/UNIQUE lookup) | ⚡ |
| `eq_ref` | One row per join (PK/UNIQUE) | ⚡ |
| `ref` | Multiple matching rows via index | ✅ Good |
| `range` | Index range scan (BETWEEN, <, >) | ✅ Good |
| `index` | Full index scan | ⚠️ OK |
| `ALL` | Full table scan | 🐌 Slow |

---

### ✏️ Practice Exercise 30 (bonus — see note below)

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Run `EXPLAIN` on a SELECT with no index and note the `type` and `rows`.
> 2. Create an index, re-run `EXPLAIN`, and compare.
> 3. Write a query with a JOIN and analyze its EXPLAIN output.
> 4. What does `Using filesort` in the Extra column mean? How can you avoid it?

---

## Topic 31 — Query Optimization Tips

### 1️⃣ WHY — Why Optimize?

A poorly written query on a large table can take minutes. An optimized one takes milliseconds. Optimization saves server resources, reduces costs, and improves user experience.

---

### 2️⃣ WHEN — Signs You Need Optimization

- Queries take more than a second.
- `EXPLAIN` shows `type: ALL` (full table scan).
- High CPU or disk usage on the database server.
- Application timeouts from slow database calls.

---

### 3️⃣ HOW — Optimization Techniques

#### Example 74: Common optimizations

```sql
-- ❌ BAD: SELECT * (fetches unnecessary columns)
SELECT * FROM products;

-- ✅ GOOD: Select only what you need
SELECT product_name, price FROM products;

-- ❌ BAD: Function on indexed column (prevents index use)
SELECT * FROM products WHERE YEAR(created_at) = 2024;

-- ✅ GOOD: Use range comparison (can use index)
SELECT * FROM products WHERE created_at >= '2024-01-01' AND created_at < '2025-01-01';

-- ❌ BAD: LIKE with leading wildcard (full scan)
SELECT * FROM products WHERE product_name LIKE '%phone%';

-- ✅ GOOD: LIKE with trailing wildcard (can use index)
SELECT * FROM products WHERE product_name LIKE 'phone%';

-- ❌ BAD: OR on different columns (hard to index)
SELECT * FROM products WHERE category = 'Electronics' OR price > 500;

-- ✅ GOOD: Use UNION for OR on different indexed columns
SELECT * FROM products WHERE category = 'Electronics'
UNION
SELECT * FROM products WHERE price > 500;
```

#### Example 75: Pagination optimization

```sql
-- ❌ SLOW for large offsets
SELECT * FROM products ORDER BY product_id LIMIT 10 OFFSET 100000;
-- MySQL must read and discard 100,000 rows!

-- ✅ FAST: Keyset pagination (seek method)
SELECT * FROM products
WHERE product_id > 100000
ORDER BY product_id
LIMIT 10;
-- Jumps directly to the right position using the index
```

---

## Topic 32 — Partitioning

### 🌍 Real-Life Analogy

Partitioning is like dividing a huge filing cabinet into labeled drawers (by year, by region). When you need "2024 records," you only open one drawer instead of searching the entire cabinet.

---

### 1️⃣ WHY — Why Partition?

- **Query performance** — Only scan relevant partitions (partition pruning).
- **Maintenance** — Drop old data by dropping a partition (instant vs. slow DELETE).
- **Manageability** — Backup/restore individual partitions.

---

### 2️⃣ WHEN — When to Partition

- Tables with millions/billions of rows.
- Queries frequently filter by the partition column (date, region, status).
- You need to regularly purge old data.

---

### 3️⃣ HOW — Partitioning Types

#### Example 76: RANGE partitioning (by date)

```sql
CREATE TABLE sales (
    sale_id   INT AUTO_INCREMENT,
    sale_date DATE NOT NULL,
    amount    DECIMAL(10,2),
    PRIMARY KEY (sale_id, sale_date)
) PARTITION BY RANGE (YEAR(sale_date)) (
    PARTITION p2022 VALUES LESS THAN (2023),
    PARTITION p2023 VALUES LESS THAN (2024),
    PARTITION p2024 VALUES LESS THAN (2025),
    PARTITION p_future VALUES LESS THAN MAXVALUE
);

-- Insert data (automatically goes to the right partition)
INSERT INTO sales (sale_date, amount) VALUES ('2023-06-15', 99.99);
INSERT INTO sales (sale_date, amount) VALUES ('2024-01-20', 149.99);

-- Query only scans the relevant partition
SELECT * FROM sales WHERE sale_date BETWEEN '2024-01-01' AND '2024-12-31';
-- MySQL only reads partition p2024 (partition pruning)

-- Drop old data instantly
ALTER TABLE sales DROP PARTITION p2022;
```

#### Example 77: LIST partitioning (by category)

```sql
CREATE TABLE orders_partitioned (
    order_id INT AUTO_INCREMENT,
    region   VARCHAR(20) NOT NULL,
    amount   DECIMAL(10,2),
    PRIMARY KEY (order_id, region)
) PARTITION BY LIST COLUMNS (region) (
    PARTITION p_americas VALUES IN ('US', 'Canada', 'Brazil'),
    PARTITION p_europe  VALUES IN ('UK', 'France', 'Germany'),
    PARTITION p_asia    VALUES IN ('Japan', 'India', 'China')
);
```

#### Example 78: HASH partitioning (even distribution)

```sql
CREATE TABLE sessions (
    session_id INT AUTO_INCREMENT,
    user_id    INT NOT NULL,
    data       TEXT,
    PRIMARY KEY (session_id, user_id)
) PARTITION BY HASH (user_id) PARTITIONS 4;
-- Distributes rows evenly across 4 partitions based on user_id
```

---

## 🏁 Part 7 Summary

| Topic | Key Takeaway |
|---|---|
| **Indexes** | B-Tree shortcuts for fast lookups. Index WHERE, JOIN, ORDER BY columns. Don't over-index. |
| **EXPLAIN** | Shows query execution plan. Look for `type`, `key`, and `rows`. Avoid `ALL`. |
| **Query Optimization** | Select only needed columns, avoid functions on indexed columns, use keyset pagination. |
| **Partitioning** | Split huge tables by range/list/hash. Enables partition pruning and fast data purging. |

> **Next up:** [Part 8: Advanced Features](#part-8-advanced-features) — Stored procedures, triggers, views, JSON, and replication.

---

# Part 8: Advanced Features

> **Goal:** Learn stored procedures, triggers, views, JSON handling, and replication basics.

---

## Topic 33 — Stored Procedures and Functions

### 🌍 Real-Life Analogy

A stored procedure is like a **recipe card** in a kitchen. Instead of giving instructions from scratch every time, the chef (database) reads the card and executes the steps. You call the recipe by name, optionally pass in ingredients (parameters), and get a dish (result).

---

### 1️⃣ WHY — Why Stored Procedures?

| Benefit | Explanation |
|---|---|
| **Reusability** | Write once, call many times |
| **Security** | Grant EXECUTE permission without exposing table details |
| **Performance** | Pre-parsed and cached; reduces network round-trips |
| **Encapsulation** | Complex logic lives in the database, not scattered in app code |

---

### 2️⃣ WHEN — When to Use

- Complex multi-step database operations.
- Business logic that must be enforced at the database level.
- Batch processing and scheduled tasks.
- When multiple applications share the same database.

---

### 3️⃣ HOW — Creating and Using Procedures

#### Example 79: Basic stored procedure

```sql
DELIMITER //

CREATE PROCEDURE GetAllProducts()
BEGIN
    SELECT product_name, price, category
    FROM products
    ORDER BY price DESC;
END //

DELIMITER ;

-- Call the procedure
CALL GetAllProducts();
```

**Line-by-line explanation:**

| Line | What It Does |
|---|---|
| `DELIMITER //` | Changes the statement delimiter from `;` to `//` so the procedure body can contain semicolons. |
| `CREATE PROCEDURE GetAllProducts()` | Defines a procedure named `GetAllProducts` with no parameters. |
| `BEGIN ... END` | Wraps the procedure body. |
| `DELIMITER ;` | Restores the normal delimiter. |
| `CALL GetAllProducts()` | Executes the procedure. |

#### Example 80: Procedure with IN, OUT, and INOUT parameters

```sql
DELIMITER //

CREATE PROCEDURE GetProductsByCategory(
    IN  p_category VARCHAR(50),        -- input parameter
    OUT p_count    INT                  -- output parameter
)
BEGIN
    SELECT * FROM products WHERE category = p_category;
    SELECT COUNT(*) INTO p_count FROM products WHERE category = p_category;
END //

DELIMITER ;

-- Call with parameters
CALL GetProductsByCategory('Electronics', @count);
SELECT @count AS electronics_count;
```

#### Example 81: Procedure with control flow

```sql
DELIMITER //

CREATE PROCEDURE ApplyDiscount(
    IN p_product_id INT,
    IN p_discount_pct DECIMAL(5,2)
)
BEGIN
    DECLARE v_current_price DECIMAL(10,2);
    DECLARE v_new_price DECIMAL(10,2);

    -- Get current price
    SELECT price INTO v_current_price
    FROM products WHERE product_id = p_product_id;

    -- Validate
    IF v_current_price IS NULL THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Product not found';
    ELSEIF p_discount_pct < 0 OR p_discount_pct > 100 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Discount must be between 0 and 100';
    ELSE
        SET v_new_price = v_current_price * (1 - p_discount_pct / 100);
        UPDATE products SET price = v_new_price WHERE product_id = p_product_id;
        SELECT CONCAT('Price updated: ', v_current_price, ' -> ', v_new_price) AS result;
    END IF;
END //

DELIMITER ;

-- Apply 15% discount to product 1
CALL ApplyDiscount(1, 15.00);
```

#### Example 82: Stored function (returns a value)

```sql
DELIMITER //

CREATE FUNCTION CalculateTax(p_amount DECIMAL(10,2))
RETURNS DECIMAL(10,2)
DETERMINISTIC
BEGIN
    RETURN p_amount * 0.08;  -- 8% tax
END //

DELIMITER ;

-- Use in a query
SELECT product_name, price, CalculateTax(price) AS tax,
       price + CalculateTax(price) AS total_with_tax
FROM products;
```

---

### ✏️ Practice Exercise 31 (bonus)

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Create a stored procedure that accepts a minimum price and returns all products above that price.
> 2. Create a stored function `FullName(first, last)` that returns a concatenated full name.
> 3. Create a procedure that transfers money between accounts (from Topic 25) with error handling.

---

## Topic 34 — Triggers

### 🌍 Real-Life Analogy

A trigger is like a **motion-sensor light**: when someone walks through the door (event happens), the light turns on automatically (action fires). Database triggers fire automatically when an INSERT, UPDATE, or DELETE happens.

---

### 1️⃣ WHY — Why Triggers?

- **Audit logging** — Automatically record who changed what and when.
- **Data validation** — Enforce complex rules beyond CHECK constraints.
- **Cascading updates** — Automatically update related data.
- **Consistency** — Logic runs regardless of which application touches the data.

---

### 2️⃣ WHEN — When to Use Triggers

| Timing | Event | Use Case |
|---|---|---|
| `BEFORE INSERT` | Before a row is added | Validate or modify data |
| `AFTER INSERT` | After a row is added | Log the change, update counters |
| `BEFORE UPDATE` | Before a row changes | Capture old values, validate |
| `AFTER UPDATE` | After a row changes | Audit log, sync related tables |
| `BEFORE DELETE` | Before a row is removed | Prevent deletion, archive |
| `AFTER DELETE` | After a row is removed | Update counters, cascade cleanup |

---

### 3️⃣ HOW — Creating Triggers

#### Example 83: Audit log trigger

```sql
-- Audit log table
CREATE TABLE product_audit (
    audit_id   INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    action     VARCHAR(10),
    old_price  DECIMAL(10,2),
    new_price  DECIMAL(10,2),
    changed_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    changed_by VARCHAR(100)
);

-- Trigger: log price changes
DELIMITER //
CREATE TRIGGER trg_product_price_update
AFTER UPDATE ON products
FOR EACH ROW
BEGIN
    IF OLD.price <> NEW.price THEN
        INSERT INTO product_audit (product_id, action, old_price, new_price, changed_by)
        VALUES (NEW.product_id, 'UPDATE', OLD.price, NEW.price, CURRENT_USER());
    END IF;
END //
DELIMITER ;

-- Test: update a product price
UPDATE products SET price = 899.99 WHERE product_id = 1;

-- Check the audit log
SELECT * FROM product_audit;
```

#### Example 84: Before insert trigger (validation)

```sql
DELIMITER //
CREATE TRIGGER trg_validate_stock
BEFORE INSERT ON products
FOR EACH ROW
BEGIN
    IF NEW.stock < 0 THEN
        SIGNAL SQLSTATE '45000'
        SET MESSAGE_TEXT = 'Stock cannot be negative';
    END IF;
    IF NEW.price < 0 THEN
        SET NEW.price = 0;  -- auto-correct negative prices to 0
    END IF;
END //
DELIMITER ;
```

#### Example 85: After delete trigger

```sql
-- Log deleted products
CREATE TABLE deleted_products_log (
    log_id      INT AUTO_INCREMENT PRIMARY KEY,
    product_id  INT,
    product_name VARCHAR(100),
    deleted_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

DELIMITER //
CREATE TRIGGER trg_log_deleted_product
AFTER DELETE ON products
FOR EACH ROW
BEGIN
    INSERT INTO deleted_products_log (product_id, product_name)
    VALUES (OLD.product_id, OLD.product_name);
END //
DELIMITER ;
```

---

### ✏️ Practice Exercise 32 (bonus)

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Create an audit trigger on the `customers` table that logs all UPDATE operations.
> 2. Create a BEFORE INSERT trigger that sets a default value for a column if NULL is provided.
> 3. List all triggers in your database using `SHOW TRIGGERS;`.

---

## Topic 35 — Views

### 🌍 Real-Life Analogy

A view is like a **saved search** or a **window** into your data. It doesn't copy data — it's a named query that you can treat like a table. Change the underlying data, and the view reflects it immediately.

---

### 1️⃣ WHY — Why Views?

| Benefit | Explanation |
|---|---|
| **Simplification** | Hide complex JOINs behind a simple name |
| **Security** | Expose only certain columns/rows to certain users |
| **Consistency** | Everyone uses the same query definition |
| **Abstraction** | Change underlying tables without changing application queries |

---

### 2️⃣ WHEN — When to Create Views

- Complex reports that are run frequently.
- Providing read-only access to sensitive tables.
- Simplifying queries for application developers.
- Creating a stable API over a changing schema.

---

### 3️⃣ HOW — Creating and Using Views

#### Example 86: Basic view

```sql
-- View: expensive products (price > 200)
CREATE VIEW expensive_products AS
SELECT product_name, category, price, stock
FROM products
WHERE price > 200
ORDER BY price DESC;

-- Use it like a table
SELECT * FROM expensive_products;

-- Filter the view further
SELECT * FROM expensive_products WHERE category = 'Electronics';
```

#### Example 87: View with JOINs

```sql
-- View: order summary (joins multiple tables)
CREATE VIEW order_summary AS
SELECT
    o.order_id,
    c.name AS customer_name,
    o.order_date,
    SUM(oi.quantity * oi.unit_price) AS total_amount
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
GROUP BY o.order_id, c.name, o.order_date;

-- Simple queries against the complex view
SELECT * FROM order_summary WHERE total_amount > 500;
```

#### Example 88: Updatable view and WITH CHECK OPTION

```sql
-- Updatable view (simple enough for INSERT/UPDATE)
CREATE VIEW active_customers AS
SELECT customer_id, name, email, city
FROM customers
WHERE city IS NOT NULL
WITH CHECK OPTION;

-- This works (city is not null)
UPDATE active_customers SET city = 'Denver' WHERE customer_id = 1;

-- This fails (would violate the view's WHERE condition)
UPDATE active_customers SET city = NULL WHERE customer_id = 1;
-- ERROR: CHECK OPTION failed

-- Drop a view
DROP VIEW IF EXISTS expensive_products;
```

---

### ✏️ Practice Exercise 33 (bonus)

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Create a view called `product_summary` that shows product name, category, price, and stock for products in stock (stock > 0).
> 2. Create a view with a JOIN between `employees` and `departments`.
> 3. Try updating data through a simple view. Does it work?

---

## Topic 36 — JSON in MySQL

### 🌍 Real-Life Analogy

JSON is like a **flexible notebook** inside your structured filing cabinet. Most data fits neatly into columns, but sometimes you need to store semi-structured data (user preferences, API responses, configuration) — JSON gives you that flexibility within a relational database.

---

### 1️⃣ WHY — Why JSON in MySQL?

- Store **semi-structured data** without creating extra columns for every attribute.
- Work with API data that arrives as JSON.
- Combine relational structure with document-style flexibility.

---

### 2️⃣ WHEN — When to Use JSON

✅ **Good uses:** User settings, metadata, API responses, optional attributes that vary per row.

❌ **Avoid when:** Data has a consistent structure — use regular columns for better performance.

---

### 3️⃣ HOW — JSON Operations

#### Example 89: Storing and querying JSON

```sql
CREATE TABLE user_settings (
    user_id  INT PRIMARY KEY,
    name     VARCHAR(100) NOT NULL,
    settings JSON
);

INSERT INTO user_settings VALUES
(1, 'Alice', '{"theme": "dark", "language": "en", "notifications": {"email": true, "sms": false}}'),
(2, 'Bob',   '{"theme": "light", "language": "fr", "notifications": {"email": false, "sms": true}}');

-- Extract a JSON value with ->> (returns text)
SELECT name, settings->>'$.theme' AS theme
FROM user_settings;

-- Extract nested value
SELECT name, settings->>'$.notifications.email' AS email_notifications
FROM user_settings;

-- Filter by JSON value
SELECT * FROM user_settings
WHERE settings->>'$.theme' = 'dark';
```

#### Example 90: JSON functions

```sql
-- JSON_EXTRACT (same as -> operator)
SELECT JSON_EXTRACT(settings, '$.language') FROM user_settings WHERE user_id = 1;
-- Output: "en" (with quotes)

-- JSON_UNQUOTE + JSON_EXTRACT (same as ->>)
SELECT JSON_UNQUOTE(JSON_EXTRACT(settings, '$.language')) FROM user_settings WHERE user_id = 1;
-- Output: en (without quotes)

-- JSON_SET: update a JSON value
UPDATE user_settings
SET settings = JSON_SET(settings, '$.theme', 'blue')
WHERE user_id = 1;

-- JSON_INSERT: add a new key (only if it doesn't exist)
UPDATE user_settings
SET settings = JSON_INSERT(settings, '$.font_size', 14)
WHERE user_id = 1;

-- JSON_REMOVE: remove a key
UPDATE user_settings
SET settings = JSON_REMOVE(settings, '$.notifications.sms')
WHERE user_id = 2;

-- JSON_ARRAYAGG: aggregate values into a JSON array
SELECT JSON_ARRAYAGG(name) AS all_users FROM user_settings;
-- Output: ["Alice", "Bob"]

-- JSON_OBJECTAGG: aggregate key-value pairs into a JSON object
SELECT JSON_OBJECTAGG(name, settings->>'$.theme') AS user_themes FROM user_settings;
-- Output: {"Alice": "blue", "Bob": "light"}
```

---

### ✏️ Practice Exercise 34 (bonus)

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Create a `products_extended` table with a JSON `attributes` column. Insert products with different attributes (color, weight, dimensions).
> 2. Query products where the JSON attribute `color` equals "red".
> 3. Use JSON_SET to update an attribute and JSON_REMOVE to delete one.

---

## Topic 37 — Replication Basics

### 🌍 Real-Life Analogy

Replication is like having a **backup singer** who mirrors everything the lead singer does in real-time. If the lead singer loses their voice (primary server fails), the backup can take over. It also lets multiple backup singers handle audience requests (read queries) to lighten the lead's load.

---

### 1️⃣ WHY — Why Replication?

| Benefit | Explanation |
|---|---|
| **High availability** | If the primary goes down, a replica can take over |
| **Read scaling** | Distribute read queries across replicas |
| **Backup without downtime** | Back up from a replica, not the busy primary |
| **Geographic distribution** | Place replicas close to users in different regions |

---

### 2️⃣ WHEN — When to Use Replication

- Applications with high read-to-write ratios (blogs, e-commerce catalogs).
- When zero-downtime deployments are required.
- For disaster recovery across data centers.

---

### 3️⃣ HOW — Replication Architecture

#### How It Works

```
┌──────────────┐    Binary Log     ┌──────────────┐
│   Primary    │ ────────────────> │   Replica    │
│  (Source)    │    (writes)       │  (Read-only) │
│              │                   │              │
│ Handles all  │                   │ Handles read │
│ writes       │                   │ queries      │
└──────────────┘                   └──────────────┘
```

1. **Primary** records all changes in the **binary log** (binlog).
2. **Replica** reads the binlog and replays the changes.
3. Applications send writes to the primary and reads to replicas.

#### Example 91: Configuring replication (primary side)

```sql
-- On the PRIMARY server:
-- 1. Enable binary logging in my.cnf:
-- [mysqld]
-- server-id = 1
-- log-bin = mysql-bin
-- binlog-format = ROW

-- 2. Create a replication user
CREATE USER 'repl_user'@'%' IDENTIFIED BY 'ReplP@ss123';
GRANT REPLICATION SLAVE ON *.* TO 'repl_user'@'%';
FLUSH PRIVILEGES;

-- 3. Get the current binlog position
SHOW MASTER STATUS;
-- Note the File and Position values
```

#### Example 92: Configuring replication (replica side)

```sql
-- On the REPLICA server:
-- 1. Configure in my.cnf:
-- [mysqld]
-- server-id = 2
-- relay-log = mysql-relay-bin
-- read-only = ON

-- 2. Point to the primary
CHANGE REPLICATION SOURCE TO
    SOURCE_HOST = '192.168.1.100',
    SOURCE_USER = 'repl_user',
    SOURCE_PASSWORD = 'ReplP@ss123',
    SOURCE_LOG_FILE = 'mysql-bin.000001',
    SOURCE_LOG_POS = 154;

-- 3. Start replication
START REPLICA;

-- 4. Check status
SHOW REPLICA STATUS\G
-- Look for: Replica_IO_Running: Yes, Replica_SQL_Running: Yes
```

---

### ✏️ Practice Exercise 35 (bonus)

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Explain the difference between synchronous and asynchronous replication.
> 2. What happens if the primary server goes down? How do you promote a replica?
> 3. When would you use MySQL Group Replication instead of traditional replication?

---

---

## Topic 37A — Storage Engines (InnoDB vs MyISAM)

### 🌍 Real-Life Analogy

A storage engine is like the **filing system** inside the cabinet. You might use fireproof folders for important documents (InnoDB — safe, transactional) or lightweight paper folders for quick-access reference sheets (MyISAM — fast reads). The cabinet (MySQL server) stays the same, but how files are stored and accessed changes.

---

### 1️⃣ WHY — Why Do Storage Engines Matter?

MySQL is unique among databases — it supports **pluggable storage engines**. The engine determines how data is physically stored, indexed, locked, and recovered. Choosing the right engine affects performance, reliability, and features.

---

### 2️⃣ WHEN — Comparison Table

| Feature | InnoDB (Default) | MyISAM | MEMORY | ARCHIVE |
|---|---|---|---|---|
| **Transactions** | ✅ Yes (ACID) | ❌ No | ❌ No | ❌ No |
| **Foreign Keys** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **Row-level Locking** | ✅ Yes | ❌ Table-level | ✅ Yes | ❌ No |
| **Crash Recovery** | ✅ Automatic | ❌ Manual repair | N/A (RAM) | ✅ Yes |
| **Full-text Index** | ✅ Yes (5.6+) | ✅ Yes | ❌ No | ❌ No |
| **Data Caching** | ✅ Buffer pool | ❌ OS cache only | ✅ In RAM | ❌ No |
| **Compression** | ✅ Yes | ✅ Yes | ❌ No | ✅ Yes (high) |
| **Best For** | General purpose, OLTP | Read-heavy, legacy | Temp data, caching | Archival, logs |
| **COUNT(*) Speed** | Slower (counts rows) | ⚡ Instant (stored) | Fast | Slow |

---

### 3️⃣ HOW — Working with Storage Engines

```sql
-- Check current default engine
SHOW VARIABLES LIKE 'default_storage_engine';
-- Output: InnoDB

-- See all available engines
SHOW ENGINES;

-- Check which engine a table uses
SHOW TABLE STATUS LIKE 'products';
-- Look at the Engine column

-- Create a table with a specific engine
CREATE TABLE fast_cache (
    id INT PRIMARY KEY,
    data VARCHAR(255)
) ENGINE = MEMORY;

CREATE TABLE log_archive (
    id INT AUTO_INCREMENT PRIMARY KEY,
    message TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) ENGINE = ARCHIVE;

-- Change an existing table's engine (rewrites entire table!)
ALTER TABLE old_table ENGINE = InnoDB;

-- Create a MyISAM table (rare in modern MySQL)
CREATE TABLE legacy_table (
    id INT PRIMARY KEY,
    name VARCHAR(100)
) ENGINE = MyISAM;
```

#### When to Choose Which Engine

| Scenario | Engine | Why |
|---|---|---|
| Any new project | **InnoDB** | Transactions, FK, crash recovery — no reason not to |
| Legacy system that uses MyISAM | **InnoDB** (migrate!) | MyISAM lacks transactions and crash safety |
| Temporary lookup tables | **MEMORY** | Lightning-fast but data lost on restart |
| Write-once log archival | **ARCHIVE** | Excellent compression, append-only |
| Full-text search on older MySQL | **MyISAM** | Historically better FTS (InnoDB caught up in 5.6+) |

> **Best Practice:** Use **InnoDB** for everything unless you have a very specific reason not to. It's been the default since MySQL 5.5 for good reason.

---

## Topic 37B — Temporary Tables & Prepared Statements

### Temporary Tables

Temporary tables exist only for the duration of your session. They are invisible to other connections and are automatically dropped when the session ends.

```sql
-- Create a temporary table
CREATE TEMPORARY TABLE temp_high_value_products AS
SELECT product_id, product_name, price, stock, price * stock AS inventory_value
FROM products
WHERE price * stock > 1000;

-- Use it like any regular table
SELECT * FROM temp_high_value_products ORDER BY inventory_value DESC;

-- Join temporary tables with regular tables
SELECT t.product_name, t.inventory_value, c.category_name
FROM temp_high_value_products t
JOIN categories c ON t.category_id = c.category_id;

-- Temporary tables are session-specific:
-- Session 1 can have a temp_orders table
-- Session 2 can have a DIFFERENT temp_orders table
-- They don't interfere with each other

-- Explicitly drop when done (optional — auto-dropped on disconnect)
DROP TEMPORARY TABLE IF EXISTS temp_high_value_products;
```

**When to use temporary tables:**
- Break complex queries into manageable steps.
- Store intermediate results for multi-step reports.
- Avoid repeating expensive subqueries.
- Import/transform data before loading into permanent tables.

**Temporary Table vs CTE vs Subquery:**

| Feature | Temporary Table | CTE | Subquery |
|---|---|---|---|
| Scope | Entire session | Single query | Single query |
| Reusable | ✅ Across queries | ✅ Within query | ❌ Must repeat |
| Indexed | ✅ Can add indexes | ❌ No | ❌ No |
| Materialized | ✅ Always | ❌ MySQL may not | ❌ No |
| Recursive | ❌ No | ✅ Yes | ❌ No |

---

### Prepared Statements

Prepared statements are **pre-compiled SQL templates** with placeholders. They prevent **SQL injection** and improve performance for repeated queries.

```sql
-- 1. PREPARE: create a template with ? placeholders
PREPARE stmt_find_product FROM
    'SELECT product_name, price FROM products WHERE category = ? AND price > ?';

-- 2. SET variables and EXECUTE
SET @cat = 'Electronics';
SET @min_price = 100;
EXECUTE stmt_find_product USING @cat, @min_price;

-- 3. Execute again with different values (reuses the compiled plan)
SET @cat = 'Furniture';
SET @min_price = 200;
EXECUTE stmt_find_product USING @cat, @min_price;

-- 4. DEALLOCATE when done
DEALLOCATE PREPARE stmt_find_product;

-- Prepared INSERT
PREPARE stmt_insert FROM
    'INSERT INTO customers (name, email, city) VALUES (?, ?, ?)';

SET @name = 'Frank Wilson';
SET @email = 'frank@example.com';
SET @city = 'Denver';
EXECUTE stmt_insert USING @name, @email, @city;

DEALLOCATE PREPARE stmt_insert;
```

**Why Prepared Statements Prevent SQL Injection:**

```sql
-- Without prepared statement (DANGEROUS in application code):
-- query = "SELECT * FROM users WHERE name = '" + user_input + "'"
-- If user_input = "'; DROP TABLE users; --"
-- Result: SELECT * FROM users WHERE name = ''; DROP TABLE users; --'

-- With prepared statement (SAFE):
-- The database treats the ? parameter as a VALUE, never as SQL code
-- Even if user_input = "'; DROP TABLE users; --"
-- It searches for a user literally named "'; DROP TABLE users; --"
-- The SQL structure is FIXED and cannot be altered by input

PREPARE safe_query FROM 'SELECT * FROM users WHERE name = ?';
SET @input = "'; DROP TABLE users; --";
EXECUTE safe_query USING @input;
-- Safely searches for that exact string — no injection!
DEALLOCATE PREPARE safe_query;
```

**Application-level prepared statements (recommended):**

```python
# Python (mysql-connector-python)
cursor = connection.cursor(prepared=True)
cursor.execute("SELECT * FROM products WHERE category = %s AND price > %s",
               ('Electronics', 100))
results = cursor.fetchall()
```

```javascript
// Node.js (mysql2)
const [rows] = await connection.execute(
    'SELECT * FROM products WHERE category = ? AND price > ?',
    ['Electronics', 100]
);
```

---

## Topic 37C — Character Sets & Collations

### 🌍 Real-Life Analogy

A **character set** defines which symbols can be stored (English letters only? Chinese characters? Emojis?). A **collation** defines how those symbols are compared and sorted (case-sensitive? accent-sensitive?).

---

### 1️⃣ WHY — Why Character Sets Matter?

- **utf8mb4** supports ALL Unicode characters including emojis (👍, 🎉).
- MySQL's older `utf8` (alias for `utf8mb3`) only handles characters up to 3 bytes — it **cannot** store emojis or some Asian characters!
- Wrong character set = garbled text (mojibake), broken searches, or data loss.

---

### 2️⃣ HOW — Managing Character Sets

```sql
-- Check server defaults
SHOW VARIABLES LIKE 'character_set_server';   -- utf8mb4 (ideally)
SHOW VARIABLES LIKE 'collation_server';       -- utf8mb4_0900_ai_ci (ideally)

-- Check database character set
SELECT DEFAULT_CHARACTER_SET_NAME, DEFAULT_COLLATION_NAME
FROM INFORMATION_SCHEMA.SCHEMATA WHERE SCHEMA_NAME = 'shop';

-- Create database with explicit character set
CREATE DATABASE my_app
    CHARACTER SET utf8mb4
    COLLATE utf8mb4_unicode_ci;

-- Change existing database
ALTER DATABASE my_app
    CHARACTER SET utf8mb4
    COLLATE utf8mb4_unicode_ci;

-- Create table with specific character set
CREATE TABLE messages (
    id      INT AUTO_INCREMENT PRIMARY KEY,
    content TEXT CHARACTER SET utf8mb4
) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Convert existing table
ALTER TABLE messages CONVERT TO CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Check column character set
SHOW FULL COLUMNS FROM messages;
```

**Common Collations and Their Behavior:**

| Collation | Case-Sensitive | Accent-Sensitive | Example: 'a' = 'A'? | 'é' = 'e'? |
|---|---|---|---|---|
| `utf8mb4_0900_ai_ci` | No (ci) | No (ai) | Yes | Yes |
| `utf8mb4_0900_as_cs` | Yes (cs) | Yes (as) | No | No |
| `utf8mb4_unicode_ci` | No (ci) | No | Yes | Yes |
| `utf8mb4_bin` | Yes (binary) | Yes | No | No |
| `utf8mb4_general_ci` | No | No | Yes | Yes |

> - `ci` = case-insensitive, `cs` = case-sensitive
> - `ai` = accent-insensitive, `as` = accent-sensitive

```sql
-- Collation affects comparisons and sorting:
SELECT 'café' = 'cafe';  -- 1 (true) with utf8mb4_unicode_ci
SELECT 'café' = 'cafe';  -- 0 (false) with utf8mb4_bin

-- Force a specific collation in a query
SELECT * FROM customers
WHERE name COLLATE utf8mb4_bin = 'Alice';  -- case-sensitive search
```

> **Best Practice:** Always use `utf8mb4` with `utf8mb4_unicode_ci` or `utf8mb4_0900_ai_ci` (MySQL 8.0 default). Never use the old `utf8` (which is actually `utf8mb3`).

---

## Topic 37D — User Variables, Session Variables & Cursors

### User-Defined Variables (@variables)

```sql
-- Set a variable
SET @min_price = 100;
SET @greeting = 'Hello, World!';
SET @today = CURDATE();

-- Use in queries
SELECT * FROM products WHERE price > @min_price;

-- Set from a query result
SELECT @max_price := MAX(price) FROM products;
SELECT @max_price;  -- Shows the max price

-- Variables persist for the entire session
-- Different sessions have independent @variables

-- Variables in UPDATE statements
SET @row_number = 0;
SELECT @row_number := @row_number + 1 AS row_num, product_name, price
FROM products
ORDER BY price DESC;
```

### Session and Global Variables

```sql
-- View a system variable
SELECT @@max_connections;          -- global
SELECT @@session.wait_timeout;     -- session

-- Set for current session only
SET SESSION wait_timeout = 28800;
SET SESSION group_concat_max_len = 1000000;

-- Set globally (requires SUPER privilege, affects new sessions)
SET GLOBAL max_connections = 200;

-- Common session variables you might tune:
SHOW VARIABLES LIKE 'wait_timeout';         -- idle connection timeout
SHOW VARIABLES LIKE 'max_allowed_packet';   -- max query/data size
SHOW VARIABLES LIKE 'group_concat_max_len'; -- GROUP_CONCAT limit
SHOW VARIABLES LIKE 'sql_mode';             -- SQL strictness settings
```

### Cursors (Row-by-Row Processing in Stored Procedures)

Cursors let you iterate over query results **one row at a time** inside a stored procedure — like a `for` loop.

```sql
DELIMITER //

CREATE PROCEDURE ApplyBulkDiscount()
BEGIN
    -- Declare variables
    DECLARE v_product_id INT;
    DECLARE v_price DECIMAL(10,2);
    DECLARE v_done BOOLEAN DEFAULT FALSE;

    -- Declare cursor
    DECLARE product_cursor CURSOR FOR
        SELECT product_id, price FROM products WHERE stock > 100;

    -- Declare handler for end of cursor
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET v_done = TRUE;

    -- Open cursor
    OPEN product_cursor;

    -- Loop through rows
    read_loop: LOOP
        FETCH product_cursor INTO v_product_id, v_price;
        IF v_done THEN
            LEAVE read_loop;
        END IF;

        -- Apply 5% discount to high-stock products
        UPDATE products
        SET price = v_price * 0.95
        WHERE product_id = v_product_id;
    END LOOP;

    -- Close cursor
    CLOSE product_cursor;

    SELECT 'Bulk discount applied!' AS result;
END //

DELIMITER ;

CALL ApplyBulkDiscount();
```

> ⚠️ **Warning:** Cursors are slow (row-by-row). Prefer set-based operations (UPDATE with WHERE) whenever possible. Use cursors only when row-by-row logic is unavoidable.

---

## Topic 37E — Events (Scheduled Tasks)

### 🌍 Real-Life Analogy

MySQL Events are like **cron jobs** built into the database. They run SQL statements on a schedule — hourly, daily, weekly — without needing external scripts.

---

### 1️⃣ WHY — Why Events?

- Automate maintenance: purge old logs, update statistics, archive data.
- No need for external cron/scheduler.
- Runs inside MySQL with full SQL power.

---

### 2️⃣ HOW — Creating and Managing Events

```sql
-- First, ensure the event scheduler is ON
SET GLOBAL event_scheduler = ON;
SHOW VARIABLES LIKE 'event_scheduler';

-- One-time event (runs once, then auto-drops)
CREATE EVENT one_time_cleanup
ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 HOUR
DO
    DELETE FROM access_logs WHERE request_time < DATE_SUB(NOW(), INTERVAL 90 DAY);

-- Recurring event (runs every day at midnight)
CREATE EVENT daily_log_cleanup
ON SCHEDULE EVERY 1 DAY
STARTS '2026-02-22 00:00:00'
DO
    DELETE FROM access_logs WHERE request_time < DATE_SUB(NOW(), INTERVAL 90 DAY);

-- Recurring event with ENDS
CREATE EVENT weekly_stats_update
ON SCHEDULE EVERY 1 WEEK
STARTS '2026-02-23 02:00:00'
ENDS '2027-02-23 02:00:00'
DO
BEGIN
    TRUNCATE TABLE weekly_stats;
    INSERT INTO weekly_stats (category, revenue)
    SELECT category, SUM(amount) FROM sales
    WHERE sale_date >= DATE_SUB(CURDATE(), INTERVAL 7 DAY)
    GROUP BY category;
END;

-- Multi-statement event (requires BEGIN...END and DELIMITER)
DELIMITER //
CREATE EVENT monthly_archive
ON SCHEDULE EVERY 1 MONTH
DO
BEGIN
    -- Move old orders to archive
    INSERT INTO orders_archive SELECT * FROM orders
    WHERE order_date < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);

    -- Delete archived orders
    DELETE FROM orders
    WHERE order_date < DATE_SUB(CURDATE(), INTERVAL 1 YEAR);
END //
DELIMITER ;

-- View all events
SHOW EVENTS;

-- View event details
SHOW CREATE EVENT daily_log_cleanup;

-- Disable an event (keep but don't run)
ALTER EVENT daily_log_cleanup DISABLE;

-- Re-enable
ALTER EVENT daily_log_cleanup ENABLE;

-- Drop an event
DROP EVENT IF EXISTS one_time_cleanup;
```

---

### ✏️ Practice Exercise 37A–37E

> **Difficulty:** ⭐⭐⭐ Advanced
>
> 1. Check what storage engine your tables use. Convert a MyISAM table to InnoDB.
> 2. Create a temporary table with aggregated sales data, then join it with the main products table.
> 3. Write a prepared statement that searches for products by category and minimum price.
> 4. Check your database's character set. If it's not utf8mb4, convert it.
> 5. Write a stored procedure with a cursor that iterates over products and logs each one.
> 6. Create an event that runs daily to delete logs older than 30 days.

---

## 🏁 Part 8 Summary

| Topic | Key Takeaway |
|---|---|
| **Stored Procedures** | Reusable, parameterized SQL programs. DELIMITER, IN/OUT, IF/ELSE, SIGNAL. |
| **Triggers** | Automatic actions on INSERT/UPDATE/DELETE. Great for auditing and validation. |
| **Views** | Named queries that act like virtual tables. Simplify, secure, and abstract. |
| **JSON** | Native JSON type for semi-structured data. Use ->>, JSON_SET, JSON_EXTRACT. |
| **Replication** | Primary-replica for read scaling, high availability, and backups. |
| **Storage Engines** | InnoDB (default, ACID) vs MyISAM (fast reads). Choose based on requirements. |
| **Temp Tables & Prepared Stmts** | Temporary tables for intermediate results. Prepared statements prevent SQL injection. |
| **Character Sets** | Use utf8mb4 for full Unicode support. Collations control sort/compare rules. |
| **Variables & Cursors** | User @vars, session vars, row-by-row cursor processing in stored procedures. |
| **Events** | Scheduled tasks that run automatically (like cron jobs inside MySQL). |

> **Next up:** [Part 9: Real-World Projects & Comparisons](#part-9-real-world-projects--comparisons)

---

# Part 9: Real-World Projects & Comparisons

> **Goal:** Apply everything you've learned to complete projects. Avoid common mistakes. Understand how MySQL compares to other databases.

---

## Project 1 — E-Commerce Database

### Schema Design

```
┌────────────────┐      ┌────────────────┐      ┌────────────────┐
│   categories   │      │    products     │      │    reviews     │
├────────────────┤      ├────────────────┤      ├────────────────┤
│ PK category_id │─1:N─│ FK category_id │      │ PK review_id   │
│    name        │      │ PK product_id  │─1:N─│ FK product_id  │
└────────────────┘      │    name        │      │ FK customer_id │
                        │    price       │      │    rating      │
                        │    stock       │      │    comment     │
                        └───────┬────────┘      └────────────────┘
                                │
┌────────────────┐      ┌───────┴────────┐      ┌────────────────┐
│   customers    │      │  order_items   │      │    orders      │
├────────────────┤      ├────────────────┤      ├────────────────┤
│ PK customer_id │      │ PK item_id     │      │ PK order_id    │
│    name        │      │ FK order_id    │──N:1─│ FK customer_id │
│    email       │      │ FK product_id  │      │    order_date  │
│    city        │      │    quantity    │      │    status      │
│    joined_on   │      │    unit_price  │      │    total       │
└────────────────┘      └────────────────┘      └────────────────┘
```

### Full Schema SQL

```sql
CREATE DATABASE IF NOT EXISTS ecommerce;
USE ecommerce;

CREATE TABLE categories (
    category_id INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(50) NOT NULL UNIQUE,
    description TEXT
);

CREATE TABLE products (
    product_id  INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(150) NOT NULL,
    description TEXT,
    price       DECIMAL(10,2) NOT NULL CHECK (price >= 0),
    stock       INT DEFAULT 0 CHECK (stock >= 0),
    category_id INT,
    created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(category_id)
);

CREATE TABLE customers (
    customer_id INT AUTO_INCREMENT PRIMARY KEY,
    name        VARCHAR(100) NOT NULL,
    email       VARCHAR(150) NOT NULL UNIQUE,
    city        VARCHAR(100),
    joined_on   DATE DEFAULT (CURRENT_DATE)
);

CREATE TABLE orders (
    order_id    INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT NOT NULL,
    order_date  DATE DEFAULT (CURRENT_DATE),
    status      ENUM('pending','shipped','delivered','cancelled') DEFAULT 'pending',
    total       DECIMAL(12,2) DEFAULT 0,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

CREATE TABLE order_items (
    item_id    INT AUTO_INCREMENT PRIMARY KEY,
    order_id   INT NOT NULL,
    product_id INT NOT NULL,
    quantity   INT NOT NULL CHECK (quantity > 0),
    unit_price DECIMAL(10,2) NOT NULL,
    FOREIGN KEY (order_id)   REFERENCES orders(order_id) ON DELETE CASCADE,
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

CREATE TABLE reviews (
    review_id   INT AUTO_INCREMENT PRIMARY KEY,
    product_id  INT NOT NULL,
    customer_id INT NOT NULL,
    rating      TINYINT NOT NULL CHECK (rating BETWEEN 1 AND 5),
    comment     TEXT,
    created_at  TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id)  REFERENCES products(product_id),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id),
    UNIQUE KEY uq_review (product_id, customer_id)  -- one review per product per customer
);
```

### Sample Data

```sql
INSERT INTO categories (name) VALUES ('Electronics'), ('Clothing'), ('Books'), ('Home & Garden');

INSERT INTO products (name, price, stock, category_id) VALUES
    ('Wireless Headphones', 79.99,  150, 1),
    ('USB-C Cable',         12.99,  500, 1),
    ('Running Shoes',       119.99, 75,  2),
    ('Cotton T-Shirt',      24.99,  200, 2),
    ('SQL Cookbook',         39.99,  60,  3),
    ('Garden Hose',         34.99,  90,  4),
    ('Smart Watch',         249.99, 40,  1),
    ('Winter Jacket',       189.99, 30,  2),
    ('Plant Pot Set',       19.99,  120, 4),
    ('Laptop Stand',        59.99,  80,  1);

INSERT INTO customers (name, email, city) VALUES
    ('Alice Johnson',  'alice@example.com',   'New York'),
    ('Bob Smith',      'bob@example.com',     'London'),
    ('Charlie Brown',  'charlie@example.com', 'Paris'),
    ('Diana Prince',   'diana@example.com',   'Tokyo'),
    ('Eve Davis',      'eve@example.com',     'Sydney');

INSERT INTO orders (customer_id, order_date, status) VALUES
    (1, '2024-01-15', 'delivered'),
    (1, '2024-03-20', 'delivered'),
    (2, '2024-02-10', 'shipped'),
    (3, '2024-04-05', 'pending'),
    (4, '2024-01-28', 'delivered'),
    (5, '2024-03-12', 'cancelled');

INSERT INTO order_items (order_id, product_id, quantity, unit_price) VALUES
    (1, 1, 1, 79.99), (1, 2, 2, 12.99),   -- Order 1: headphones + 2 cables
    (2, 7, 1, 249.99),                      -- Order 2: smart watch
    (3, 3, 1, 119.99), (3, 5, 1, 39.99),   -- Order 3: shoes + book
    (4, 4, 3, 24.99),                       -- Order 4: 3 t-shirts
    (5, 6, 2, 34.99), (5, 9, 1, 19.99);    -- Order 5: 2 hoses + plant pots

-- Update order totals
UPDATE orders o SET total = (
    SELECT SUM(quantity * unit_price) FROM order_items oi WHERE oi.order_id = o.order_id
);

INSERT INTO reviews (product_id, customer_id, rating, comment) VALUES
    (1, 1, 5, 'Amazing sound quality!'),
    (1, 2, 4, 'Good but a bit heavy'),
    (7, 1, 5, 'Love this watch'),
    (3, 3, 3, 'Decent but expected more'),
    (5, 4, 5, 'Great reference book');
```

### E-Commerce Queries

```sql
-- Q1: Top 5 best-selling products by quantity
SELECT p.name, SUM(oi.quantity) AS total_sold
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
GROUP BY p.product_id, p.name
ORDER BY total_sold DESC
LIMIT 5;

-- Q2: Revenue per category
SELECT c.name AS category, SUM(oi.quantity * oi.unit_price) AS revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
JOIN categories c ON p.category_id = c.category_id
GROUP BY c.category_id, c.name
ORDER BY revenue DESC;

-- Q3: Customers who spent the most
SELECT cu.name, SUM(o.total) AS total_spent
FROM customers cu
JOIN orders o ON cu.customer_id = o.customer_id
WHERE o.status != 'cancelled'
GROUP BY cu.customer_id, cu.name
ORDER BY total_spent DESC;

-- Q4: Products with average rating below 4
SELECT p.name, ROUND(AVG(r.rating), 1) AS avg_rating, COUNT(r.review_id) AS num_reviews
FROM products p
LEFT JOIN reviews r ON p.product_id = r.product_id
GROUP BY p.product_id, p.name
HAVING AVG(r.rating) < 4 OR AVG(r.rating) IS NULL
ORDER BY avg_rating;

-- Q5: Monthly order count and revenue (time series)
SELECT
    DATE_FORMAT(order_date, '%Y-%m') AS month,
    COUNT(*) AS num_orders,
    SUM(total) AS revenue
FROM orders
WHERE status != 'cancelled'
GROUP BY DATE_FORMAT(order_date, '%Y-%m')
ORDER BY month;

-- Q6: Customers who have NOT placed any orders
SELECT cu.name, cu.email
FROM customers cu
LEFT JOIN orders o ON cu.customer_id = o.customer_id
WHERE o.order_id IS NULL;

-- Q7: Products never ordered
SELECT p.name, p.stock
FROM products p
WHERE p.product_id NOT IN (SELECT DISTINCT product_id FROM order_items);

-- Q8: Running total of revenue by order date
SELECT
    order_date,
    total,
    SUM(total) OVER (ORDER BY order_date) AS running_revenue
FROM orders
WHERE status != 'cancelled';

-- Q9: Rank customers by total spending
SELECT
    cu.name,
    SUM(o.total) AS total_spent,
    RANK() OVER (ORDER BY SUM(o.total) DESC) AS spending_rank
FROM customers cu
JOIN orders o ON cu.customer_id = o.customer_id
WHERE o.status != 'cancelled'
GROUP BY cu.customer_id, cu.name;

-- Q10: Products with stock below reorder threshold
SELECT name, stock, price,
    CASE
        WHEN stock = 0 THEN 'OUT OF STOCK'
        WHEN stock < 50 THEN 'LOW STOCK'
        ELSE 'IN STOCK'
    END AS stock_status
FROM products
ORDER BY stock ASC;
```

---

## Project 2 — College Management System

### Normalization Walkthrough

Starting from an unnormalized view:
```
Student: Alice | Courses: Math (Prof. Smith), Science (Prof. Jones) | GPA: 3.8
```

**Normalized into 3NF:**

```sql
CREATE DATABASE IF NOT EXISTS college;
USE college;

CREATE TABLE departments (
    dept_id   INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL UNIQUE
);

CREATE TABLE professors (
    prof_id   INT AUTO_INCREMENT PRIMARY KEY,
    name      VARCHAR(100) NOT NULL,
    email     VARCHAR(150) UNIQUE,
    dept_id   INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

CREATE TABLE courses (
    course_id   INT AUTO_INCREMENT PRIMARY KEY,
    course_code VARCHAR(10) NOT NULL UNIQUE,
    course_name VARCHAR(100) NOT NULL,
    credits     INT NOT NULL CHECK (credits > 0 AND credits <= 6),
    prof_id     INT,
    dept_id     INT,
    FOREIGN KEY (prof_id) REFERENCES professors(prof_id),
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

CREATE TABLE students (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    name       VARCHAR(100) NOT NULL,
    email      VARCHAR(150) NOT NULL UNIQUE,
    dob        DATE,
    dept_id    INT,
    enrolled_year INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

CREATE TABLE enrollments (
    enrollment_id INT AUTO_INCREMENT PRIMARY KEY,
    student_id    INT NOT NULL,
    course_id     INT NOT NULL,
    semester      VARCHAR(20) NOT NULL,
    grade         CHAR(2),
    FOREIGN KEY (student_id) REFERENCES students(student_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id),
    UNIQUE KEY uq_enrollment (student_id, course_id, semester)
);

-- Sample data
INSERT INTO departments (dept_name) VALUES ('Computer Science'), ('Mathematics'), ('Physics');

INSERT INTO professors (name, email, dept_id) VALUES
    ('Prof. Smith', 'smith@college.edu', 1),
    ('Prof. Jones', 'jones@college.edu', 2),
    ('Prof. Lee',   'lee@college.edu',   3);

INSERT INTO courses (course_code, course_name, credits, prof_id, dept_id) VALUES
    ('CS101', 'Intro to Programming', 3, 1, 1),
    ('CS201', 'Data Structures',      4, 1, 1),
    ('MA101', 'Calculus I',           3, 2, 2),
    ('PH101', 'Physics I',           4, 3, 3);

INSERT INTO students (name, email, dob, dept_id, enrolled_year) VALUES
    ('Alice', 'alice@student.edu', '2002-05-15', 1, 2020),
    ('Bob',   'bob@student.edu',   '2001-11-20', 1, 2020),
    ('Carol', 'carol@student.edu', '2003-01-10', 2, 2021),
    ('Dave',  'dave@student.edu',  '2002-08-25', 3, 2021);

INSERT INTO enrollments (student_id, course_id, semester, grade) VALUES
    (1, 1, 'Fall 2024', 'A'),  (1, 3, 'Fall 2024', 'B+'),
    (2, 1, 'Fall 2024', 'B'),  (2, 2, 'Fall 2024', 'A-'),
    (3, 3, 'Fall 2024', 'A'),  (3, 4, 'Fall 2024', 'B'),
    (4, 4, 'Fall 2024', 'A-');
```

### College Queries

```sql
-- Q1: Students and their courses with professor names
SELECT s.name AS student, c.course_name, p.name AS professor, e.grade
FROM enrollments e
JOIN students s ON e.student_id = s.student_id
JOIN courses c ON e.course_id = c.course_id
JOIN professors p ON c.prof_id = p.prof_id
ORDER BY s.name;

-- Q2: Course enrollment counts
SELECT c.course_code, c.course_name, COUNT(e.student_id) AS enrolled_students
FROM courses c
LEFT JOIN enrollments e ON c.course_id = e.course_id
GROUP BY c.course_id, c.course_code, c.course_name
ORDER BY enrolled_students DESC;

-- Q3: Students in the Computer Science department
SELECT s.name, s.email, s.enrolled_year
FROM students s
JOIN departments d ON s.dept_id = d.dept_id
WHERE d.dept_name = 'Computer Science';

-- Q4: Professor workload (courses taught)
SELECT p.name, COUNT(c.course_id) AS courses_taught, SUM(c.credits) AS total_credits
FROM professors p
LEFT JOIN courses c ON p.prof_id = c.prof_id
GROUP BY p.prof_id, p.name;

-- Q5: Students enrolled in more than 1 course
SELECT s.name, COUNT(e.course_id) AS num_courses
FROM students s
JOIN enrollments e ON s.student_id = e.student_id
GROUP BY s.student_id, s.name
HAVING COUNT(e.course_id) > 1;

-- Q6: Courses with no enrollments
SELECT c.course_code, c.course_name
FROM courses c
LEFT JOIN enrollments e ON c.course_id = e.course_id
WHERE e.enrollment_id IS NULL;

-- Q7: Department-wise student count
SELECT d.dept_name, COUNT(s.student_id) AS num_students
FROM departments d
LEFT JOIN students s ON d.dept_id = s.dept_id
GROUP BY d.dept_id, d.dept_name;

-- Q8: Grade distribution across all courses
SELECT grade, COUNT(*) AS count
FROM enrollments
WHERE grade IS NOT NULL
GROUP BY grade
ORDER BY count DESC;
```

---

## Project 3 — Sales Analytics Dashboard

### Schema with Window Functions and CTEs

```sql
CREATE DATABASE IF NOT EXISTS sales_analytics;
USE sales_analytics;

CREATE TABLE sales_reps (
    rep_id INT AUTO_INCREMENT PRIMARY KEY,
    name   VARCHAR(100) NOT NULL,
    region VARCHAR(50)
);

CREATE TABLE sales (
    sale_id   INT AUTO_INCREMENT PRIMARY KEY,
    rep_id    INT NOT NULL,
    sale_date DATE NOT NULL,
    amount    DECIMAL(12,2) NOT NULL CHECK (amount > 0),
    product   VARCHAR(100),
    FOREIGN KEY (rep_id) REFERENCES sales_reps(rep_id)
);

INSERT INTO sales_reps (name, region) VALUES
    ('Alice', 'North'), ('Bob', 'South'), ('Carol', 'North'),
    ('Dave', 'East'), ('Eve', 'South');

INSERT INTO sales (rep_id, sale_date, amount, product) VALUES
    (1, '2024-01-05', 5000, 'Enterprise Plan'),
    (1, '2024-01-20', 3000, 'Pro Plan'),
    (1, '2024-02-15', 7000, 'Enterprise Plan'),
    (2, '2024-01-10', 4000, 'Pro Plan'),
    (2, '2024-02-08', 6000, 'Enterprise Plan'),
    (2, '2024-03-12', 2000, 'Basic Plan'),
    (3, '2024-01-25', 8000, 'Enterprise Plan'),
    (3, '2024-02-28', 3500, 'Pro Plan'),
    (4, '2024-01-18', 4500, 'Pro Plan'),
    (4, '2024-03-01', 5500, 'Enterprise Plan'),
    (5, '2024-02-05', 2500, 'Basic Plan'),
    (5, '2024-03-20', 9000, 'Enterprise Plan');
```

### Analytics Queries

```sql
-- Q1: Monthly revenue with month-over-month growth
WITH monthly AS (
    SELECT
        DATE_FORMAT(sale_date, '%Y-%m') AS month,
        SUM(amount) AS revenue
    FROM sales
    GROUP BY DATE_FORMAT(sale_date, '%Y-%m')
)
SELECT
    month,
    revenue,
    LAG(revenue) OVER (ORDER BY month) AS prev_month,
    ROUND(
        (revenue - LAG(revenue) OVER (ORDER BY month))
        / LAG(revenue) OVER (ORDER BY month) * 100, 1
    ) AS growth_pct
FROM monthly;

-- Q2: Rank sales reps by total revenue
SELECT
    sr.name,
    sr.region,
    SUM(s.amount) AS total_revenue,
    RANK() OVER (ORDER BY SUM(s.amount) DESC) AS overall_rank,
    RANK() OVER (PARTITION BY sr.region ORDER BY SUM(s.amount) DESC) AS region_rank
FROM sales_reps sr
JOIN sales s ON sr.rep_id = s.rep_id
GROUP BY sr.rep_id, sr.name, sr.region;

-- Q3: Running total per sales rep
SELECT
    sr.name,
    s.sale_date,
    s.amount,
    SUM(s.amount) OVER (PARTITION BY sr.rep_id ORDER BY s.sale_date) AS running_total
FROM sales s
JOIN sales_reps sr ON s.rep_id = sr.rep_id
ORDER BY sr.name, s.sale_date;

-- Q4: Top product by revenue
SELECT product, SUM(amount) AS total_revenue, COUNT(*) AS num_sales
FROM sales
GROUP BY product
ORDER BY total_revenue DESC;

-- Q5: Regional performance comparison
SELECT
    sr.region,
    COUNT(s.sale_id) AS num_sales,
    SUM(s.amount) AS total_revenue,
    ROUND(AVG(s.amount), 2) AS avg_sale
FROM sales_reps sr
JOIN sales s ON sr.rep_id = s.rep_id
GROUP BY sr.region
ORDER BY total_revenue DESC;

-- Q6: Sales reps who exceeded their region's average
WITH region_avg AS (
    SELECT sr.region, AVG(s.amount) AS avg_amount
    FROM sales_reps sr
    JOIN sales s ON sr.rep_id = s.rep_id
    GROUP BY sr.region
)
SELECT sr.name, sr.region, s.amount, ra.avg_amount
FROM sales s
JOIN sales_reps sr ON s.rep_id = sr.rep_id
JOIN region_avg ra ON sr.region = ra.region
WHERE s.amount > ra.avg_amount;
```

---

## Project 4 — Traffic Logging System

### Optimized Schema with Indexes and Partitioning

```sql
CREATE DATABASE IF NOT EXISTS traffic_logs;
USE traffic_logs;

CREATE TABLE access_logs (
    log_id      BIGINT AUTO_INCREMENT,
    request_time DATETIME NOT NULL,
    ip_address  VARCHAR(45) NOT NULL,
    method      ENUM('GET','POST','PUT','DELETE','PATCH') NOT NULL,
    url_path    VARCHAR(500) NOT NULL,
    status_code SMALLINT NOT NULL,
    response_ms INT,
    user_agent  VARCHAR(500),
    PRIMARY KEY (log_id, request_time)
) PARTITION BY RANGE (YEAR(request_time)) (
    PARTITION p2023 VALUES LESS THAN (2024),
    PARTITION p2024 VALUES LESS THAN (2025),
    PARTITION p2025 VALUES LESS THAN (2026),
    PARTITION p_future VALUES LESS THAN MAXVALUE
);

-- Indexes for common query patterns
CREATE INDEX idx_ip ON access_logs(ip_address);
CREATE INDEX idx_status ON access_logs(status_code);
CREATE INDEX idx_time_status ON access_logs(request_time, status_code);

-- Sample data
INSERT INTO access_logs (request_time, ip_address, method, url_path, status_code, response_ms) VALUES
    ('2024-01-15 10:30:00', '192.168.1.1',  'GET',  '/api/products',     200, 45),
    ('2024-01-15 10:30:05', '192.168.1.2',  'POST', '/api/orders',       201, 120),
    ('2024-01-15 10:30:10', '192.168.1.1',  'GET',  '/api/products/5',   200, 30),
    ('2024-01-15 10:31:00', '10.0.0.5',     'GET',  '/api/users',        403, 15),
    ('2024-01-15 10:31:30', '192.168.1.3',  'DELETE','/api/products/99', 404, 10),
    ('2024-01-15 10:32:00', '192.168.1.1',  'GET',  '/api/products',     200, 50),
    ('2024-01-15 10:33:00', '10.0.0.5',     'POST', '/api/login',        401, 200),
    ('2024-01-15 10:34:00', '10.0.0.5',     'POST', '/api/login',        401, 180);
```

### Traffic Analysis Queries

```sql
-- Q1: Requests per status code
SELECT status_code, COUNT(*) AS count
FROM access_logs
GROUP BY status_code
ORDER BY count DESC;

-- Q2: Suspicious IPs (many 4xx errors)
SELECT ip_address, COUNT(*) AS error_count
FROM access_logs
WHERE status_code BETWEEN 400 AND 499
GROUP BY ip_address
HAVING COUNT(*) >= 3
ORDER BY error_count DESC;

-- Q3: Average response time by endpoint
SELECT url_path, ROUND(AVG(response_ms), 1) AS avg_ms, COUNT(*) AS hits
FROM access_logs
GROUP BY url_path
ORDER BY avg_ms DESC;

-- Q4: EXPLAIN analysis (verify index usage)
EXPLAIN SELECT * FROM access_logs
WHERE request_time BETWEEN '2024-01-15 10:30:00' AND '2024-01-15 10:35:00'
AND status_code = 200;

-- Q5: Hourly traffic pattern
SELECT
    HOUR(request_time) AS hour,
    COUNT(*) AS requests,
    ROUND(AVG(response_ms), 1) AS avg_response_ms
FROM access_logs
GROUP BY HOUR(request_time)
ORDER BY hour;

-- Q6: Purge old logs (fast with partitions)
-- ALTER TABLE access_logs DROP PARTITION p2023;
```

---

## Common Mistakes

Avoid these 15 common mistakes that trip up beginners and even experienced developers:

| # | Mistake | Problem | Fix |
|---|---|---|---|
| 1 | **Poor normalization** | Duplicate data, update anomalies | Normalize to 3NF for transactional systems |
| 2 | **Missing indexes** | Slow queries, full table scans | Add indexes on WHERE, JOIN, ORDER BY columns |
| 3 | **Using SELECT \*** | Wastes bandwidth, hides schema changes | Select only needed columns |
| 4 | **No WHERE on UPDATE/DELETE** | Accidentally modifies/deletes all rows | Always include WHERE; test with SELECT first |
| 5 | **Ignoring EXPLAIN** | Deploying slow queries unknowingly | Run EXPLAIN before deploying any query on large tables |
| 6 | **N+1 query problem** | 100 queries instead of 1 JOIN | Use JOINs or batch queries |
| 7 | **Wrong data types** | Using VARCHAR for dates, FLOAT for money | DATE for dates, DECIMAL for money |
| 8 | **Not using transactions** | Partial updates on failure | Wrap related changes in START TRANSACTION ... COMMIT |
| 9 | **SQL injection** | Hackers can read/destroy your database | Use parameterized queries (prepared statements) |
| 10 | **No backups** | Data loss from hardware failure or human error | Automate daily backups; test restores |
| 11 | **Over-indexing** | Slow INSERT/UPDATE, wasted disk space | Only index columns used in queries |
| 12 | **Ignoring character sets** | Garbled text, emoji issues | Use `utf8mb4` (MySQL's true UTF-8) |
| 13 | **Not using prepared statements** | SQL injection risk + less caching | Always use prepared statements in application code |
| 14 | **Storing passwords in plaintext** | Security breach exposes all passwords | Hash with bcrypt/argon2 in your application before storing |
| 15 | **No foreign keys** | Orphaned records, broken data integrity | Define FKs for all relationships |

### Example: SQL Injection (Mistake #9)

```sql
-- ❌ DANGEROUS: String concatenation in application code
-- query = "SELECT * FROM users WHERE username = '" + user_input + "'"
-- If user_input = "'; DROP TABLE users; --"
-- The query becomes:
-- SELECT * FROM users WHERE username = ''; DROP TABLE users; --'
-- YOUR TABLE IS NOW DELETED!

-- ✅ SAFE: Use prepared statements
-- Python example:
-- cursor.execute("SELECT * FROM users WHERE username = %s", (user_input,))
-- The database treats user_input as a value, not as SQL code.
```

---

## MySQL vs Other Databases

### Feature Comparison Table

| Feature | MySQL | PostgreSQL | SQLite | MariaDB |
|---|---|---|---|---|
| **Type** | Client-server RDBMS | Client-server RDBMS | Embedded RDBMS | Client-server RDBMS |
| **License** | GPL + commercial | PostgreSQL (MIT-like) | Public domain | GPL |
| **Best For** | Web apps, read-heavy | Analytics, complex queries | Mobile, embedded, testing | MySQL drop-in replacement |
| **ACID** | Yes (InnoDB) | Yes | Yes | Yes |
| **JSON** | Yes (since 5.7) | Yes (richer JSONB) | Yes (extension) | Yes |
| **Window Functions** | Yes (since 8.0) | Yes (more advanced) | Yes (since 3.25) | Yes |
| **CTEs** | Yes (since 8.0) | Yes | Yes | Yes (since 10.2) |
| **Stored Procedures** | Yes | Yes (PL/pgSQL) | No | Yes |
| **Full-Text Search** | Yes | Yes (better) | Yes (FTS5) | Yes |
| **Replication** | Built-in async | Built-in logical + streaming | N/A | Built-in |
| **Partitioning** | Yes | Yes (declarative) | N/A | Yes |
| **Max DB Size** | 256 TB | Unlimited | 281 TB | 256 TB |
| **Ease of Setup** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Community** | Largest | Large | Large | Growing |

### When to Choose Which

| Scenario | Recommended |
|---|---|
| Building a web app (PHP, Node.js, Python) | **MySQL** — mature ecosystem, hosting everywhere |
| Complex analytics, GIS data, strict SQL compliance | **PostgreSQL** — richer feature set |
| Mobile app, desktop app, testing, prototyping | **SQLite** — zero config, single file |
| MySQL user wanting more features, open-source guarantee | **MariaDB** — binary compatible with MySQL |
| Schema-less data, extreme horizontal scale | **MongoDB** (NoSQL) |
| Key-value caching | **Redis** (NoSQL) |

### Relational vs NoSQL

| Aspect | Relational (MySQL) | NoSQL (MongoDB, Redis) |
|---|---|---|
| **Schema** | Fixed (tables, columns, types) | Flexible (documents, key-value) |
| **Relationships** | Strong (foreign keys, JOINs) | Weak (embedded or manual) |
| **Consistency** | Strong (ACID) | Eventual (BASE model, typically) |
| **Query Language** | SQL (standardized) | Varies per database |
| **Scaling** | Vertical + read replicas | Horizontal (sharding) |
| **Best For** | Structured data, complex queries | Unstructured data, simple lookups |

### Scalability Considerations

| Scale Challenge | MySQL Solution |
|---|---|
| Read-heavy load | Read replicas |
| Write-heavy load | Partitioning, connection pooling |
| Global distribution | Multi-region replicas |
| Very large datasets | Sharding (application-level or ProxySQL) |
| High availability | MySQL Group Replication, InnoDB Cluster |

---

## Quick Reference / Cheat Sheet

### DDL Commands

```sql
CREATE DATABASE dbname;
DROP DATABASE IF EXISTS dbname;
USE dbname;

CREATE TABLE tablename (col1 TYPE, col2 TYPE, ...);
ALTER TABLE tablename ADD COLUMN col TYPE;
ALTER TABLE tablename DROP COLUMN col;
ALTER TABLE tablename MODIFY COLUMN col NEWTYPE;
DROP TABLE IF EXISTS tablename;
TRUNCATE TABLE tablename;
```

### DML Commands

```sql
INSERT INTO table (col1, col2) VALUES (val1, val2);
INSERT INTO table (col1, col2) VALUES (v1, v2), (v3, v4);  -- multi-row
INSERT IGNORE INTO table ...;                                -- skip duplicates
INSERT INTO table ... ON DUPLICATE KEY UPDATE col = val;     -- upsert

SELECT col1, col2 FROM table WHERE condition ORDER BY col LIMIT n;
SELECT DISTINCT col FROM table;

UPDATE table SET col = val WHERE condition;
DELETE FROM table WHERE condition;
```

### JOIN Types

```sql
-- INNER JOIN (matching rows only)
SELECT * FROM A INNER JOIN B ON A.id = B.a_id;

-- LEFT JOIN (all from A, matching from B)
SELECT * FROM A LEFT JOIN B ON A.id = B.a_id;

-- RIGHT JOIN (all from B, matching from A)
SELECT * FROM A RIGHT JOIN B ON A.id = B.a_id;

-- CROSS JOIN (Cartesian product)
SELECT * FROM A CROSS JOIN B;

-- SELF JOIN
SELECT * FROM A a1 JOIN A a2 ON a1.parent_id = a2.id;
```

### Aggregate Functions

```sql
SELECT COUNT(*), SUM(col), AVG(col), MIN(col), MAX(col)
FROM table
GROUP BY category
HAVING COUNT(*) > 5;
```

### Window Functions

```sql
ROW_NUMBER() OVER (PARTITION BY col ORDER BY col2)
RANK()       OVER (ORDER BY col DESC)
DENSE_RANK() OVER (ORDER BY col DESC)
LAG(col, 1)  OVER (ORDER BY col)
LEAD(col, 1) OVER (ORDER BY col)
SUM(col)     OVER (ORDER BY col)    -- running total
```

### Transactions

```sql
START TRANSACTION;
-- ... SQL statements ...
SAVEPOINT sp1;
-- ... more SQL ...
ROLLBACK TO SAVEPOINT sp1;   -- partial undo
COMMIT;                       -- make permanent
-- or ROLLBACK;               -- undo everything
```

### User Management

```sql
CREATE USER 'user'@'host' IDENTIFIED BY 'password';
GRANT SELECT, INSERT ON db.* TO 'user'@'host';
REVOKE INSERT ON db.* FROM 'user'@'host';
SHOW GRANTS FOR 'user'@'host';
DROP USER 'user'@'host';
```

### Common Functions

```sql
-- String
CONCAT('a', 'b')           -- 'ab'
UPPER('hello')              -- 'HELLO'
LOWER('HELLO')              -- 'hello'
SUBSTRING('hello', 1, 3)   -- 'hel'
LENGTH('hello')             -- 5
TRIM('  hi  ')              -- 'hi'
REPLACE('abc', 'b', 'x')   -- 'axc'

-- Numeric
ROUND(3.14159, 2)           -- 3.14
CEIL(3.2)                   -- 4
FLOOR(3.9)                  -- 3
ABS(-5)                     -- 5
MOD(10, 3)                  -- 1

-- Date
NOW()                       -- current datetime
CURDATE()                   -- current date
DATE_FORMAT(d, '%Y-%m-%d')  -- format date
DATEDIFF(d1, d2)            -- days between
DATE_ADD(d, INTERVAL 7 DAY) -- add 7 days
YEAR(d), MONTH(d), DAY(d)   -- extract parts

-- Conditional
IF(condition, true_val, false_val)
IFNULL(col, default_val)
COALESCE(v1, v2, v3)        -- first non-NULL
CASE WHEN cond THEN val ELSE other END
```

### Data Types Quick Reference

| Type | Size | Use For |
|---|---|---|
| `TINYINT` | 1 byte | Small integers (0-255 unsigned) |
| `INT` | 4 bytes | Standard integers |
| `BIGINT` | 8 bytes | Large integers |
| `DECIMAL(M,D)` | Variable | Exact decimals (money!) |
| `VARCHAR(N)` | Up to N+1 | Variable-length strings |
| `TEXT` | Up to 64KB | Long text |
| `DATE` | 3 bytes | Dates (YYYY-MM-DD) |
| `DATETIME` | 8 bytes | Date + time |
| `TIMESTAMP` | 4 bytes | Date + time (UTC) |
| `BOOLEAN` | 1 byte | True/false |
| `JSON` | Variable | JSON documents |
| `ENUM(...)` | 1-2 bytes | One from a fixed list |

---

## Further Reading & Resources

### Official Documentation
- [MySQL 8.0 Reference Manual](https://dev.mysql.com/doc/refman/8.0/en/)
- [MySQL Tutorial (Official)](https://dev.mysql.com/doc/refman/8.0/en/tutorial.html)

### Free Learning Platforms
- **SQLZoo** — Interactive SQL exercises
- **LeetCode (Database section)** — SQL problems for interviews
- **HackerRank (SQL domain)** — Progressive SQL challenges
- **Mode Analytics SQL Tutorial** — Free interactive course
- **W3Schools SQL Tutorial** — Quick reference and examples

### Books
- *"Learning MySQL"* by Seyed Tahaghoghi and Hugh Williams (O'Reilly)
- *"High Performance MySQL"* by Baron Schwartz et al. (O'Reilly)
- *"SQL Cookbook"* by Anthony Molinaro (O'Reilly)
- *"Database Design for Mere Mortals"* by Michael Hernandez

### Tools
- **MySQL Workbench** — Official GUI (free)
- **DBeaver** — Universal database GUI (free)
- **phpMyAdmin** — Web-based MySQL admin
- **DataGrip** — JetBrains database IDE (paid)
- **Percona Toolkit** — CLI tools for MySQL administration

---

## Glossary of Terms

| Term | Definition |
|---|---|
| **ACID** | Atomicity, Consistency, Isolation, Durability — properties that guarantee reliable transactions |
| **Aggregate Function** | Function that operates on a set of rows and returns a single value (COUNT, SUM, AVG) |
| **ALTER TABLE** | DDL command to modify an existing table's structure (add/drop columns, indexes, constraints) |
| **AUTO_INCREMENT** | Column attribute that automatically generates a unique integer for each new row |
| **B-Tree** | Balanced tree data structure used by most MySQL indexes for efficient lookups |
| **Binary Log (binlog)** | Log of all changes made to the database, used for replication and point-in-time recovery |
| **Cardinality** | The number of distinct values in a column; high cardinality = good index candidate |
| **CASE Expression** | SQL conditional logic — evaluates conditions and returns values (like if/switch in code) |
| **Character Set** | Defines which characters can be stored (e.g., utf8mb4 supports all Unicode including emojis) |
| **COALESCE** | Function that returns the first non-NULL value from a list of arguments |
| **Collation** | Rules for how characters are compared and sorted (case-sensitive, accent-sensitive, etc.) |
| **Composite Key** | A primary or unique key consisting of two or more columns |
| **Constraint** | A rule enforced on data in a table (NOT NULL, UNIQUE, CHECK, FOREIGN KEY) |
| **Correlated Subquery** | A subquery that references columns from the outer query |
| **CROSS JOIN** | Returns the Cartesian product of two tables (every row × every row) |
| **CTE** | Common Table Expression — a named temporary result set defined with `WITH` |
| **Cursor** | A database object that enables row-by-row processing of query results in stored procedures |
| **DDL** | Data Definition Language — SQL commands that define database structure (CREATE, ALTER, DROP) |
| **DML** | Data Manipulation Language — SQL commands that manipulate data (SELECT, INSERT, UPDATE, DELETE) |
| **DCL** | Data Control Language — SQL commands for access control (GRANT, REVOKE) |
| **Deadlock** | When two transactions block each other, waiting for resources the other holds |
| **Denormalization** | Intentionally adding redundancy for read performance (opposite of normalization) |
| **ER Diagram** | Entity-Relationship Diagram — visual representation of database tables and their relationships |
| **Event** | A scheduled task in MySQL that runs SQL automatically at specified intervals |
| **Foreign Key** | A column that references the primary key of another table, enforcing referential integrity |
| **FULL OUTER JOIN** | Returns all rows from both tables, matched where possible, NULLs where not (emulated in MySQL via UNION) |
| **Full Table Scan** | Reading every row in a table; slow for large tables. Indicated by `type: ALL` in EXPLAIN |
| **INNER JOIN** | Returns only rows that have matching values in both joined tables |
| **InnoDB** | MySQL's default storage engine; supports transactions, foreign keys, and row-level locking |
| **Isolation Level** | Controls how much of other transactions' uncommitted work a transaction can see |
| **JOIN** | Combining rows from two or more tables based on a related column |
| **Junction Table** | A table that implements a many-to-many relationship between two other tables |
| **LEFT JOIN** | Returns all rows from the left table and matched rows from the right (NULLs for non-matches) |
| **MyISAM** | Older MySQL storage engine; fast reads but no transactions, foreign keys, or crash recovery |
| **NATURAL JOIN** | Automatically joins tables on columns with the same name (fragile — avoid in production) |
| **Normalization** | Process of organizing data to reduce redundancy (1NF, 2NF, 3NF) |
| **Partition** | Dividing a table into smaller physical segments for performance and management |
| **Partition Pruning** | MySQL's ability to skip irrelevant partitions during a query |
| **Prepared Statement** | Pre-compiled SQL with placeholders; prevents SQL injection and improves repeated execution |
| **Primary Key** | A column (or combo) that uniquely identifies each row; NOT NULL and UNIQUE |
| **Query Plan** | The strategy MySQL chooses to execute a query (viewable via EXPLAIN) |
| **Recursive CTE** | A CTE that references itself to traverse hierarchies or generate sequences |
| **REGEXP** | Regular expression pattern matching in MySQL — more powerful than LIKE |
| **Replica** | A copy of the primary database that stays in sync; used for read scaling and availability |
| **RIGHT JOIN** | Returns all rows from the right table and matched rows from the left (NULLs for non-matches) |
| **Schema** | The structure of a database: its tables, columns, types, constraints, and relationships |
| **SELF JOIN** | A join where a table is joined with itself using different aliases |
| **Storage Engine** | The component that handles how data is stored, retrieved, and indexed (InnoDB, MyISAM, MEMORY) |
| **Stored Procedure** | A saved set of SQL statements that can be called by name with parameters |
| **Subquery** | A query nested inside another query |
| **TCL** | Transaction Control Language — SQL commands for transactions (COMMIT, ROLLBACK, SAVEPOINT) |
| **Temporary Table** | A table that exists only for the current session and is automatically dropped on disconnect |
| **Trigger** | A stored program that fires automatically in response to INSERT, UPDATE, or DELETE |
| **utf8mb4** | MySQL's true UTF-8 encoding supporting all Unicode characters including emojis (use instead of utf8) |
| **View** | A named query stored in the database that acts like a virtual table |
| **Window Function** | A function that performs a calculation across related rows without collapsing them |

---

> 🎓 **Congratulations!** You've completed the MySQL tutorial. You now have the knowledge to design databases, write efficient queries, secure your data, and build real-world applications. Keep practicing, and refer back to this guide whenever you need a refresher.
>
> *Happy querying!* 🐬
