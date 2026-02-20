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

<!-- Parts 2–9 will be added in subsequent updates -->
