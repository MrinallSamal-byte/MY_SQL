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

### [Part 4: Data Modeling](#part-4-data-modeling)
- [Topic 15 — Normalization (1NF, 2NF, 3NF)](#topic-15--normalization-1nf-2nf-3nf)
- [Topic 16 — Foreign Keys and Relationships](#topic-16--foreign-keys-and-relationships)
- [Topic 17 — Constraints](#topic-17--constraints)
- [Topic 18 — Entity-Relationship (ER) Diagrams](#topic-18--entity-relationship-er-diagrams)

### [Part 5: Querying Data](#part-5-querying-data)
- [Topic 19 — JOINs](#topic-19--joins)
- [Topic 20 — Aggregate Functions](#topic-20--aggregate-functions)
- [Topic 21 — Subqueries](#topic-21--subqueries)
- [Topic 22 — Window Functions](#topic-22--window-functions)
- [Topic 23 — UNION, INTERSECT, EXCEPT](#topic-23--union-intersect-except)
- [Topic 24 — ORDER BY, GROUP BY, HAVING](#topic-24--order-by-group-by-having)

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

## 🏁 Part 3 Summary

| Topic | Key Takeaway |
|---|---|
| **CREATE / DROP** | CREATE builds structures; DROP destroys them. Use IF EXISTS for safety. |
| **Data Types** | Choose the right type for efficiency and correctness. Use DECIMAL for money. |
| **INSERT** | Single, multi-row, IGNORE, and ON DUPLICATE KEY UPDATE for different needs. |
| **UPDATE** | Always use WHERE! Modifies existing rows in place. |
| **DELETE / TRUNCATE** | DELETE for selective removal; TRUNCATE for fast full-table wipe. |
| **SELECT** | The most-used statement. Master WHERE, ORDER BY, LIMIT, DISTINCT, and aliases. |

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

---

### 2️⃣ WHEN — When to Use Each JOIN Type

| JOIN Type | Use When |
|---|---|
| **INNER JOIN** | You only want rows that match in both tables |
| **LEFT JOIN** | You want all rows from the left table, even without matches |
| **RIGHT JOIN** | You want all rows from the right table, even without matches |
| **CROSS JOIN** | You want every combination of rows (Cartesian product) |
| **SELF JOIN** | A table references itself (e.g., employees and managers) |

---

### 3️⃣ HOW — JOIN Types Demonstrated

#### Setup data

```sql
CREATE DATABASE IF NOT EXISTS join_demo;
USE join_demo;

CREATE TABLE students (
    id   INT PRIMARY KEY,
    name VARCHAR(50)
);

CREATE TABLE grades (
    student_id INT,
    subject    VARCHAR(50),
    score      INT
);

INSERT INTO students VALUES (1, 'Alice'), (2, 'Bob'), (3, 'Charlie');
INSERT INTO grades VALUES
    (1, 'Math', 90), (1, 'Science', 85),
    (2, 'Math', 78),
    (4, 'History', 92);  -- student_id 4 doesn't exist in students
```

#### Example 38: INNER JOIN

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

```
INNER JOIN Diagram:
  Students     Grades
  ┌─────┐     ┌─────┐
  │     │█████│     │   █ = matched rows (returned)
  │     │█████│     │
  │  ○  │     │  ○  │   ○ = unmatched rows (excluded)
  └─────┘     └─────┘
```

#### Example 39: LEFT JOIN

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

Charlie appears with NULLs for grade columns — because LEFT JOIN keeps all left-table rows.

#### Example 40: RIGHT JOIN

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

#### Example 41: CROSS JOIN

```sql
-- Every combination of students and subjects
SELECT s.name, g.subject
FROM students s
CROSS JOIN (SELECT DISTINCT subject FROM grades) g;
```

**Result:** 3 students × 3 subjects = 9 rows (Cartesian product).

#### Example 42: SELF JOIN

```sql
-- Employees table where manager_id references another employee
CREATE TABLE employees_self (
    emp_id     INT PRIMARY KEY,
    emp_name   VARCHAR(50),
    manager_id INT
);

INSERT INTO employees_self VALUES
    (1, 'CEO',    NULL),
    (2, 'VP Eng', 1),
    (3, 'Dev',    2),
    (4, 'VP Sales', 1);

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
| Dev       | VP Eng  |
| VP Sales  | CEO     |

---

### ✏️ Practice Exercise 19

> **Difficulty:** ⭐⭐ Intermediate
>
> 1. Using the `students` and `grades` tables, write a LEFT JOIN that shows all students and their grades. Filter to show only students with no grades (hint: `WHERE g.subject IS NULL`).
> 2. Create `employees` and `departments` tables. Write an INNER JOIN to show employee names with department names.
> 3. Create a self-referencing `categories` table (parent_id → category_id) and query to show each category with its parent name.

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

## 🏁 Part 5 Summary

| Topic | Key Takeaway |
|---|---|
| **JOINs** | INNER (both match), LEFT (all left), RIGHT (all right), CROSS (all combos), SELF (table with itself). |
| **Aggregations** | COUNT, SUM, AVG, MIN, MAX + GROUP BY to summarize. HAVING filters groups. |
| **Subqueries** | Queries within queries. Scalar, table, correlated, and EXISTS forms. |
| **Window Functions** | ROW_NUMBER, RANK, LAG, LEAD, running totals — calculate across related rows without collapsing. |
| **Set Operations** | UNION (merge), INTERSECT (common), EXCEPT (difference). |
| **ORDER/GROUP/HAVING** | Sort, group, and filter groups — the backbone of reporting queries. |

> **Next up:** [Part 6: Transactions & Security](#part-6-transactions--security) — ACID properties, isolation levels, users, privileges, and backups.

---

<!-- Parts 6–9 will be added next -->
