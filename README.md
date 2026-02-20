# MySQL: A Complete Guide from Zero to Hero 🚀

> **Who is this for?** Complete beginners who have never touched a database, all the way to intermediate users who want to deepen their knowledge. Every concept is explained with *why* it matters, clear examples, and practice questions.

---

## Table of Contents

1. [What is a Database? What is MySQL?](#1-what-is-a-database-what-is-mysql)
2. [Installing MySQL](#2-installing-mysql)
3. [Connecting to MySQL](#3-connecting-to-mysql)
4. [Databases: Create, List, Select, Drop](#4-databases-create-list-select-drop)
5. [Tables and Data Types](#5-tables-and-data-types)
6. [Inserting Data (INSERT)](#6-inserting-data-insert)
7. [Reading Data (SELECT)](#7-reading-data-select)
8. [Filtering Data (WHERE)](#8-filtering-data-where)
9. [Updating Data (UPDATE)](#9-updating-data-update)
10. [Deleting Data (DELETE)](#10-deleting-data-delete)
11. [Sorting Results (ORDER BY)](#11-sorting-results-order-by)
12. [Limiting Results (LIMIT & OFFSET)](#12-limiting-results-limit--offset)
13. [Aggregate Functions](#13-aggregate-functions)
14. [Grouping Data (GROUP BY & HAVING)](#14-grouping-data-group-by--having)
15. [Joining Tables (JOINs)](#15-joining-tables-joins)
16. [Subqueries](#16-subqueries)
17. [Indexes](#17-indexes)
18. [Views](#18-views)
19. [Stored Procedures](#19-stored-procedures)
20. [User-Defined Functions](#20-user-defined-functions)
21. [Triggers](#21-triggers)
22. [Transactions](#22-transactions)
23. [User Management & Security](#23-user-management--security)
24. [Backup and Restore](#24-backup-and-restore)
25. [Performance Optimization](#25-performance-optimization)
26. [Advanced Topics: CTEs, Window Functions & JSON](#26-advanced-topics-ctes-window-functions--json)
27. [Final Practice Project](#27-final-practice-project)

---

## 1. What is a Database? What is MySQL?

### What is Data?
Data is simply information. Your name, your age, the price of a product — these are all pieces of data.

### What is a Database?
A **database** is an organized collection of data stored so that it can be easily accessed, managed, and updated.

> **Why do we need databases?**  
> Imagine you run an online store with 10,000 products and 50,000 customers. Storing all of this in text files or spreadsheets would be a nightmare — searching would be slow, updating would risk data loss, and two people editing the same file at the same time could corrupt it. A database solves all of these problems.

### What is a Relational Database?
A **relational database** stores data in **tables** (like spreadsheets), and tables can relate to each other. For example, a `customers` table and an `orders` table can be linked so you know which customer placed which order.

### What is MySQL?
**MySQL** is one of the most popular open-source **Relational Database Management Systems (RDBMS)**. It uses **SQL (Structured Query Language)** to interact with data.

> **Why MySQL?**  
> - Free and open-source  
> - Extremely fast and reliable  
> - Used by companies like Facebook, Twitter, YouTube, and Airbnb  
> - Huge community and documentation  
> - Works on Windows, macOS, and Linux  

### SQL vs MySQL
| SQL | MySQL |
|-----|-------|
| A *language* for querying databases | A *software* that uses SQL |
| Not a product you install | A product you download and run |
| Standard across databases | Has some MySQL-specific extensions |

### Key Terms
| Term | Meaning |
|------|---------|
| **Database** | A container for tables |
| **Table** | Rows and columns of data (like a spreadsheet) |
| **Row / Record** | A single entry in a table |
| **Column / Field** | A category of data (e.g., "name", "age") |
| **Primary Key** | A unique identifier for each row |
| **Query** | A question or command you send to the database |

---

### 📝 Practice Questions — Chapter 1

1. In your own words, what is a database?
2. What does RDBMS stand for?
3. What language does MySQL use?
4. Name three real-world examples where a database would be useful.
5. What is the difference between a row and a column?

---

## 2. Installing MySQL

### Option A — MySQL Community Server (Recommended for learning)
1. Go to [https://dev.mysql.com/downloads/mysql/](https://dev.mysql.com/downloads/mysql/)
2. Download **MySQL Community Server** for your operating system
3. Run the installer and follow the on-screen steps
4. Set a **root password** — remember it!
5. Complete the installation

### Option B — XAMPP (Easiest for beginners)
XAMPP bundles MySQL, Apache, and PHP together. Great if you are also learning web development.
1. Download from [https://www.apachefriends.org/](https://www.apachefriends.org/)
2. Install and start the MySQL module from the XAMPP control panel

### Option C — Docker (For developers)
```bash
docker run --name mysql-learning -e MYSQL_ROOT_PASSWORD=mypassword -p 3306:3306 -d mysql:8
```

### Verifying the Installation
Open a terminal and type:
```bash
mysql --version
```
You should see something like: `mysql  Ver 8.0.33`

---

## 3. Connecting to MySQL

### Using the Command Line
```bash
mysql -u root -p
```
- `-u root` means "connect as the user named *root*"
- `-p` means "prompt me for my password"

After entering your password, you will see:
```
Welcome to the MySQL monitor. Commands end with ; or \g.
mysql>
```

> **Why the semicolon?**  
> Every SQL statement must end with a semicolon (`;`). This tells MySQL "the statement is complete, execute it now." Without it, MySQL keeps waiting for more input.

### Using MySQL Workbench (GUI)
MySQL Workbench is a free graphical tool that makes it easy to write queries and see results visually. Download it from [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/).

### Useful MySQL Shell Commands
| Command | What it does |
|---------|-------------|
| `SHOW DATABASES;` | List all databases |
| `USE database_name;` | Select a database |
| `SHOW TABLES;` | List tables in the current database |
| `DESCRIBE table_name;` | Show table structure |
| `exit` or `quit` | Leave the MySQL shell |

---

## 4. Databases: Create, List, Select, Drop

### Creating a Database

```sql
CREATE DATABASE school;
```

> **Why organize data into separate databases?**  
> Just like you keep work files and personal files in separate folders, you keep data for different applications in different databases. This prevents data from different projects mixing together and keeps things organized.

### Listing Databases

```sql
SHOW DATABASES;
```

Output example:
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| school             |
| sys                |
+--------------------+
```

### Selecting a Database

Before you can work with tables, you must tell MySQL *which* database to use:

```sql
USE school;
```

### Dropping (Deleting) a Database

```sql
DROP DATABASE school;
```

> ⚠️ **Warning:** `DROP DATABASE` permanently deletes the database and **all its data**. There is no undo. Always double-check before running this command.

### IF EXISTS / IF NOT EXISTS

```sql
-- Safe creation: won't error if database already exists
CREATE DATABASE IF NOT EXISTS school;

-- Safe deletion: won't error if database doesn't exist
DROP DATABASE IF EXISTS school;
```

> **Why use IF EXISTS / IF NOT EXISTS?**  
> When writing scripts that run automatically (e.g., in deployment pipelines), you don't want the script to crash because a database already exists or doesn't exist. These keywords make scripts more robust.

---

### 📝 Practice Questions — Chapter 4

1. Write the SQL to create a database called `library`.
2. How do you switch to the `library` database?
3. What command lists all databases?
4. What happens when you run `DROP DATABASE library`?
5. Rewrite `CREATE DATABASE library;` so it does not produce an error if `library` already exists.

---

## 5. Tables and Data Types

### What is a Table?
A table is like a spreadsheet with rows and columns. Each column has a **name** and a **data type** that defines what kind of data it can hold.

### Common MySQL Data Types

#### Numeric Types
| Type | Range | Use Case |
|------|-------|----------|
| `TINYINT` | -128 to 127 | Age, small counts |
| `SMALLINT` | -32,768 to 32,767 | Small numbers |
| `INT` | -2.1 billion to 2.1 billion | General integers |
| `BIGINT` | Very large integers | User IDs in large apps |
| `DECIMAL(p, s)` | Exact decimal | Money, prices |
| `FLOAT` / `DOUBLE` | Approximate decimal | Scientific calculations |

#### String Types
| Type | Max Size | Use Case |
|------|---------|----------|
| `CHAR(n)` | 255 chars (fixed) | Country codes, postal codes |
| `VARCHAR(n)` | 65,535 chars (variable) | Names, email addresses |
| `TEXT` | 65,535 chars | Blog posts, descriptions |
| `MEDIUMTEXT` | ~16 million chars | Large articles |
| `LONGTEXT` | ~4 billion chars | Very large content |

> **Why use VARCHAR instead of CHAR for names?**  
> `CHAR(50)` always uses exactly 50 bytes of storage, even if the name is only 4 characters. `VARCHAR(50)` only uses the space that's actually needed. For variable-length data like names, `VARCHAR` is more storage-efficient.

#### Date and Time Types
| Type | Format | Example |
|------|--------|---------|
| `DATE` | YYYY-MM-DD | `2024-01-15` |
| `TIME` | HH:MM:SS | `14:30:00` |
| `DATETIME` | YYYY-MM-DD HH:MM:SS | `2024-01-15 14:30:00` |
| `TIMESTAMP` | YYYY-MM-DD HH:MM:SS | Auto-updates to current time |
| `YEAR` | YYYY | `2024` |

#### Other Types
| Type | Use Case |
|------|---------|
| `BOOLEAN` (alias for TINYINT(1)) | True/false values |
| `ENUM('val1','val2',...)` | A fixed set of allowed values |
| `JSON` | JSON documents |

### Creating a Table

```sql
USE school;

CREATE TABLE students (
    student_id   INT           AUTO_INCREMENT PRIMARY KEY,
    first_name   VARCHAR(50)   NOT NULL,
    last_name    VARCHAR(50)   NOT NULL,
    email        VARCHAR(100)  UNIQUE NOT NULL,
    date_of_birth DATE,
    grade        TINYINT       DEFAULT 1,
    created_at   TIMESTAMP     DEFAULT CURRENT_TIMESTAMP
);
```

Let's break down each column constraint:

| Constraint | Meaning |
|-----------|---------|
| `AUTO_INCREMENT` | MySQL automatically assigns the next number (1, 2, 3…) |
| `PRIMARY KEY` | Uniquely identifies each row; cannot be NULL |
| `NOT NULL` | The field must have a value; it cannot be empty |
| `UNIQUE` | No two rows can have the same value in this column |
| `DEFAULT value` | If no value is provided, use this default |

> **Why do we need a PRIMARY KEY?**  
> Think of a primary key like a passport number. Even if two people have the same name, their passport numbers are different. A primary key gives each row a unique, reliable identifier that you can use to find, update, or delete it precisely.

### Viewing a Table's Structure

```sql
DESCRIBE students;
-- or
SHOW COLUMNS FROM students;
```

### Modifying a Table (ALTER TABLE)

```sql
-- Add a new column
ALTER TABLE students ADD COLUMN phone_number VARCHAR(15);

-- Remove a column
ALTER TABLE students DROP COLUMN phone_number;

-- Rename a column
ALTER TABLE students RENAME COLUMN grade TO current_grade;

-- Change the data type of a column
ALTER TABLE students MODIFY COLUMN email VARCHAR(150);

-- Rename the table
ALTER TABLE students RENAME TO school_students;
```

> **Why ALTER instead of DROP and recreate?**  
> If the table already has data, dropping and recreating it would delete all that data. `ALTER TABLE` lets you change the structure while keeping existing rows.

### Dropping a Table

```sql
DROP TABLE IF EXISTS students;
```

---

### 📝 Practice Questions — Chapter 5

1. What data type would you use for a product price (e.g., 19.99)?
2. What is the difference between `CHAR(10)` and `VARCHAR(10)`?
3. Write the SQL to create a `books` table with columns: `book_id` (auto-increment primary key), `title` (up to 200 chars, required), `author` (up to 100 chars), `price` (decimal with 2 decimal places), `published_date` (date).
4. How do you add a column `isbn VARCHAR(20)` to the `books` table?
5. What does `NOT NULL` mean on a column?
6. What constraint would you use to ensure no two books have the same ISBN?

---

## 6. Inserting Data (INSERT)

### Basic INSERT

```sql
INSERT INTO students (first_name, last_name, email, date_of_birth, grade)
VALUES ('Alice', 'Johnson', 'alice@example.com', '2005-03-15', 10);
```

> **Why specify column names?**  
> If you list the column names explicitly, your INSERT works even if someone later adds new columns to the table. If you omit the column names, MySQL assumes you are providing a value for *every* column in the exact order they were defined — which breaks if the table structure changes.

### Inserting Multiple Rows at Once

```sql
INSERT INTO students (first_name, last_name, email, date_of_birth, grade)
VALUES
    ('Bob',   'Smith',   'bob@example.com',   '2004-07-22', 11),
    ('Carol', 'Davis',   'carol@example.com', '2005-11-08', 10),
    ('David', 'Wilson',  'david@example.com', '2003-01-30', 12),
    ('Emma',  'Martinez','emma@example.com',  '2006-05-19', 9);
```

> **Why insert multiple rows at once?**  
> Inserting 1000 rows one by one means 1000 round trips to the database. Inserting them all in one statement is far faster because the database can optimize the operation.

### INSERT with DEFAULT Values

```sql
-- grade will use its default value (1), created_at will use CURRENT_TIMESTAMP
INSERT INTO students (first_name, last_name, email)
VALUES ('Frank', 'Brown', 'frank@example.com');
```

### INSERT ... ON DUPLICATE KEY UPDATE

```sql
INSERT INTO students (student_id, first_name, last_name, email)
VALUES (1, 'Alice', 'Johnson', 'alice.new@example.com')
ON DUPLICATE KEY UPDATE email = 'alice.new@example.com';
```

> **Why use ON DUPLICATE KEY UPDATE?**  
> This is called an "upsert" — insert if the row doesn't exist, update if it does. It's very useful for syncing data without having to check first whether a row exists.

---

### 📝 Practice Questions — Chapter 6

1. Insert a book into the `books` table (from Chapter 5) with title "Clean Code", author "Robert C. Martin", price 34.99, and published_date 2008-08-01.
2. Insert three books in a single INSERT statement.
3. What happens if you try to insert a student with an email that already exists (and the email column has a UNIQUE constraint)?
4. Why is it good practice to list column names in an INSERT statement?

---

## 7. Reading Data (SELECT)

### Basic SELECT

```sql
-- Get all columns and all rows
SELECT * FROM students;

-- Get specific columns
SELECT first_name, last_name, email FROM students;
```

> **Why avoid SELECT * in production code?**  
> `SELECT *` retrieves every column, even ones your application doesn't need. This wastes network bandwidth and memory. Listing specific columns also documents what data you actually depend on, making code easier to maintain.

### Aliases (AS)

```sql
SELECT 
    first_name AS 'First Name',
    last_name  AS 'Last Name',
    email      AS 'Email Address'
FROM students;
```

### Expressions in SELECT

```sql
SELECT 
    first_name,
    last_name,
    CONCAT(first_name, ' ', last_name) AS full_name,
    2024 - YEAR(date_of_birth) AS age
FROM students;
```

### DISTINCT — Remove Duplicates

```sql
SELECT DISTINCT grade FROM students;
```

> **Why DISTINCT?**  
> If you want to know what grades exist in your school (not how many students are in each grade), you need `DISTINCT` to remove duplicate grade values.

---

### 📝 Practice Questions — Chapter 7

1. Write a query to select `title` and `author` from the `books` table.
2. Write a query that selects all unique authors from the `books` table.
3. Write a query that selects `title` and shows the price with a 10% discount, aliased as `discounted_price`.
4. What is the difference between `SELECT *` and selecting specific columns?

---

## 8. Filtering Data (WHERE)

### Basic WHERE Clause

```sql
SELECT * FROM students WHERE grade = 10;
```

> **Why do we filter data?**  
> A real database can have millions of rows. Fetching all of them every time would be extremely slow. The `WHERE` clause lets the database engine narrow down results *before* sending them to you, which is vastly more efficient.

### Comparison Operators

| Operator | Meaning | Example |
|----------|---------|---------|
| `=` | Equal | `grade = 10` |
| `!=` or `<>` | Not equal | `grade != 10` |
| `>` | Greater than | `grade > 9` |
| `<` | Less than | `grade < 12` |
| `>=` | Greater than or equal | `grade >= 10` |
| `<=` | Less than or equal | `grade <= 11` |

```sql
-- Students in grade 11 or higher
SELECT * FROM students WHERE grade >= 11;
```

### Logical Operators (AND, OR, NOT)

```sql
-- Students in grade 10 AND last name is 'Johnson'
SELECT * FROM students WHERE grade = 10 AND last_name = 'Johnson';

-- Students in grade 9 OR grade 12
SELECT * FROM students WHERE grade = 9 OR grade = 12;

-- Students NOT in grade 10
SELECT * FROM students WHERE NOT grade = 10;
```

> **Why use AND vs OR carefully?**  
> `AND` makes the condition stricter (both must be true). `OR` makes it looser (either can be true). Mixing them incorrectly is one of the most common SQL bugs. Always use parentheses to be explicit:

```sql
-- Get grade 10 students named Alice OR any grade 12 student
SELECT * FROM students 
WHERE (grade = 10 AND first_name = 'Alice') OR grade = 12;
```

### BETWEEN

```sql
-- Students in grades 10 through 12 (inclusive)
SELECT * FROM students WHERE grade BETWEEN 10 AND 12;
```

### IN

```sql
-- Students in grade 9, 10, or 11
SELECT * FROM students WHERE grade IN (9, 10, 11);

-- Same as:
SELECT * FROM students WHERE grade = 9 OR grade = 10 OR grade = 11;
```

> **Why use IN?**  
> `IN` is cleaner and more readable than chaining multiple `OR` conditions. It also performs better in some database engines.

### LIKE — Pattern Matching

```sql
-- First names starting with 'A'
SELECT * FROM students WHERE first_name LIKE 'A%';

-- Emails containing 'example'
SELECT * FROM students WHERE email LIKE '%example%';

-- Last names exactly 5 characters long
SELECT * FROM students WHERE last_name LIKE '_____';
```

| Wildcard | Meaning |
|----------|---------|
| `%` | Zero or more characters |
| `_` | Exactly one character |

> **Why LIKE and not =?**  
> `=` requires an exact match. `LIKE` allows flexible pattern matching. Useful for search features (e.g., "find all products whose name *contains* 'shirt'").

### IS NULL / IS NOT NULL

```sql
-- Students without a date of birth recorded
SELECT * FROM students WHERE date_of_birth IS NULL;

-- Students with a date of birth recorded
SELECT * FROM students WHERE date_of_birth IS NOT NULL;
```

> **Why IS NULL instead of = NULL?**  
> NULL means "unknown" or "missing". In SQL, `NULL = NULL` is *not* true — you can't compare unknowns. The correct way to check for NULL is always `IS NULL`.

---

### 📝 Practice Questions — Chapter 8

1. Select all students in grade 12.
2. Select all students whose first name starts with the letter 'C'.
3. Select all books priced between $10 and $30.
4. Select all students whose email contains 'gmail'.
5. Select all students in grades 9, 10, or 11 using `IN`.
6. What is the difference between `WHERE grade = NULL` and `WHERE grade IS NULL`? Which is correct?
7. Select all books that do NOT have a price listed (price is NULL).

---

## 9. Updating Data (UPDATE)

### Basic UPDATE

```sql
UPDATE students
SET grade = 11
WHERE student_id = 1;
```

> **Why always include a WHERE clause with UPDATE?**  
> Without `WHERE`, **every row** in the table will be updated! This is one of the most common (and painful) mistakes in SQL. Always double-check your WHERE clause.

### Updating Multiple Columns

```sql
UPDATE students
SET 
    grade = 11,
    email = 'alice.johnson@school.edu'
WHERE student_id = 1;
```

### Using Expressions in UPDATE

```sql
-- Give all grade 12 students a grade boost (hypothetical)
UPDATE students
SET grade = grade + 1
WHERE grade = 12;
```

### Safe Update Mode
MySQL has a "safe updates" mode that prevents UPDATE/DELETE without a WHERE clause using a primary key. Enable it with:

```sql
SET SQL_SAFE_UPDATES = 1;
```

---

### 📝 Practice Questions — Chapter 9

1. Update Alice's email to `alice@newschool.edu`.
2. Increase the price of all books by $5.
3. What happens if you run `UPDATE students SET grade = 12` without a WHERE clause?
4. Update all students in grade 9 to have grade 10.

---

## 10. Deleting Data (DELETE)

### Basic DELETE

```sql
DELETE FROM students WHERE student_id = 5;
```

> **Why always include a WHERE clause with DELETE?**  
> Without `WHERE`, **all rows** are deleted from the table. The table structure remains, but the data is gone. Unlike `DROP TABLE`, `DELETE` removes rows, not the table itself.

### DELETE vs TRUNCATE vs DROP

| Command | What it removes | Can be rolled back? | Resets AUTO_INCREMENT? |
|---------|----------------|--------------------|-----------------------|
| `DELETE` | Specific rows (or all rows) | Yes (in a transaction) | No |
| `TRUNCATE` | All rows | No | Yes |
| `DROP TABLE` | Entire table including structure | No | N/A |

```sql
-- Remove all rows but keep the table structure
TRUNCATE TABLE students;

-- Remove the entire table
DROP TABLE students;
```

> **Why use TRUNCATE instead of DELETE to clear a table?**  
> `TRUNCATE` is faster because it doesn't log each row deletion individually. It also resets `AUTO_INCREMENT` counters. Use it when you want to completely empty a table, not delete specific rows.

---

### 📝 Practice Questions — Chapter 10

1. Delete the book with `book_id = 3`.
2. Delete all books with a price greater than $50.
3. What is the difference between `DELETE FROM books` and `TRUNCATE TABLE books`?
4. What is the difference between `TRUNCATE` and `DROP TABLE`?

---

## 11. Sorting Results (ORDER BY)

### Ascending and Descending Order

```sql
-- Sort students by last name A-Z (ascending is the default)
SELECT * FROM students ORDER BY last_name ASC;

-- Sort by grade, highest first
SELECT * FROM students ORDER BY grade DESC;
```

### Sorting by Multiple Columns

```sql
-- Sort by grade (highest first), then by last name (A-Z) within each grade
SELECT * FROM students ORDER BY grade DESC, last_name ASC;
```

> **Why sort in multiple columns?**  
> When the first sort column has ties (e.g., multiple students in grade 10), the second sort column breaks the tie. This makes results predictable and professional.

### Sorting by Column Position

```sql
SELECT first_name, last_name, grade FROM students ORDER BY 3 DESC;
-- 3 refers to the 3rd column in the SELECT list (grade)
```

> **Why avoid positional ORDER BY in production?**  
> If someone reorders the SELECT columns, the sort changes meaning without any warning. Always use column names for clarity.

---

### 📝 Practice Questions — Chapter 11

1. List all books sorted by price from cheapest to most expensive.
2. List all students sorted by last name, then first name, both ascending.
3. List all students sorted by grade (descending), then by date of birth (oldest first).

---

## 12. Limiting Results (LIMIT & OFFSET)

### LIMIT

```sql
-- Get only the first 5 students
SELECT * FROM students LIMIT 5;
```

> **Why use LIMIT?**  
> Fetching millions of rows when you only need to show 10 per page wastes memory and bandwidth. `LIMIT` makes queries faster and applications more responsive.

### OFFSET (for Pagination)

```sql
-- Page 1: rows 1-5
SELECT * FROM students ORDER BY student_id LIMIT 5 OFFSET 0;

-- Page 2: rows 6-10
SELECT * FROM students ORDER BY student_id LIMIT 5 OFFSET 5;

-- Page 3: rows 11-15
SELECT * FROM students ORDER BY student_id LIMIT 5 OFFSET 10;
```

> **Why ORDER BY when using LIMIT/OFFSET?**  
> Without `ORDER BY`, the database can return rows in any order, and different pages might show the same row or skip rows. Always sort your results when paginating.

### Shorthand Syntax

```sql
-- LIMIT offset, count (alternative syntax)
SELECT * FROM students LIMIT 5, 5;  -- Skip 5, take 5
```

---

### 📝 Practice Questions — Chapter 12

1. Get the 3 most expensive books.
2. Get books 6 through 10 when sorted by title alphabetically (simulate page 2 with 5 items per page).
3. Find the student with the earliest date of birth.

---

## 13. Aggregate Functions

Aggregate functions calculate a single result from a group of rows.

### COUNT

```sql
-- How many students are there?
SELECT COUNT(*) AS total_students FROM students;

-- How many students have an email? (NULL values are not counted)
SELECT COUNT(email) AS students_with_email FROM students;

-- How many distinct grades exist?
SELECT COUNT(DISTINCT grade) AS number_of_grades FROM students;
```

> **Why does COUNT(*) differ from COUNT(column)?**  
> `COUNT(*)` counts all rows including those with NULLs. `COUNT(column)` counts only rows where that column is NOT NULL. This distinction matters when you have optional (nullable) columns.

### SUM

```sql
SELECT SUM(price) AS total_book_value FROM books;
```

### AVG

```sql
SELECT AVG(price) AS average_price FROM books;
```

### MIN and MAX

```sql
SELECT 
    MIN(price) AS cheapest,
    MAX(price) AS most_expensive
FROM books;

SELECT MIN(date_of_birth) AS oldest_student FROM students;
```

### Combining Aggregate Functions

```sql
SELECT 
    COUNT(*)        AS total_books,
    AVG(price)      AS avg_price,
    MIN(price)      AS min_price,
    MAX(price)      AS max_price,
    SUM(price)      AS total_value
FROM books;
```

---

### 📝 Practice Questions — Chapter 13

1. How many students are in grade 10?
2. What is the average grade of all students?
3. What is the most expensive book?
4. What is the total price of all books under $20?
5. How many different grades are represented in the students table?

---

## 14. Grouping Data (GROUP BY & HAVING)

### GROUP BY

`GROUP BY` divides rows into groups and lets aggregate functions work on each group separately.

```sql
-- Count how many students are in each grade
SELECT grade, COUNT(*) AS student_count
FROM students
GROUP BY grade;
```

> **Why use GROUP BY?**  
> Without `GROUP BY`, `COUNT(*)` gives you a single total. With `GROUP BY grade`, you get a count *per grade*. It's how you answer questions like "how many students are in each grade?" or "what is the average price per category?"

```sql
-- Average price per book category (assuming a 'category' column exists)
SELECT category, AVG(price) AS avg_price, COUNT(*) AS book_count
FROM books
GROUP BY category
ORDER BY avg_price DESC;
```

### HAVING — Filtering Groups

`HAVING` is like `WHERE` but for groups (i.e., it filters *after* aggregation).

```sql
-- Show only grades that have more than 1 student
SELECT grade, COUNT(*) AS student_count
FROM students
GROUP BY grade
HAVING COUNT(*) > 1;
```

> **Why HAVING and not WHERE?**  
> `WHERE` filters rows *before* grouping. You can't use aggregate functions like `COUNT()` in a `WHERE` clause because the count hasn't been calculated yet. `HAVING` filters *after* the groups are formed and aggregates are calculated.

### WHERE + GROUP BY + HAVING together

```sql
-- Among grade 10 and 11 students, show grades with more than 2 students
SELECT grade, COUNT(*) AS student_count
FROM students
WHERE grade IN (10, 11)      -- Filter rows BEFORE grouping
GROUP BY grade
HAVING COUNT(*) > 2;         -- Filter groups AFTER aggregation
```

### Order of Execution (Important!)

SQL clauses execute in this order:
1. `FROM` — which table?
2. `WHERE` — filter rows
3. `GROUP BY` — form groups
4. `HAVING` — filter groups
5. `SELECT` — choose columns
6. `ORDER BY` — sort results
7. `LIMIT` — restrict count

> **Why learn the order of execution?**  
> This explains why you can't use a SELECT alias in a WHERE clause (the alias isn't defined yet at the WHERE step), but you *can* use it in ORDER BY (which runs after SELECT).

---

### 📝 Practice Questions — Chapter 14

1. Count the number of students in each grade.
2. Find the average price of books, grouped by author.
3. Show only authors who have written more than 2 books.
4. Find grades where the average student age is above 16.
5. What is the difference between WHERE and HAVING?

---

## 15. Joining Tables (JOINs)

This is one of the most powerful features of relational databases. JOINs let you combine rows from two or more tables based on a related column.

### Setting Up Example Tables

```sql
CREATE TABLE departments (
    dept_id   INT AUTO_INCREMENT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL
);

CREATE TABLE employees (
    emp_id    INT AUTO_INCREMENT PRIMARY KEY,
    name      VARCHAR(100) NOT NULL,
    dept_id   INT,
    salary    DECIMAL(10, 2),
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

INSERT INTO departments (dept_name) VALUES ('Engineering'), ('Marketing'), ('HR');

INSERT INTO employees (name, dept_id, salary) VALUES
    ('Alice',   1, 90000),
    ('Bob',     1, 85000),
    ('Carol',   2, 70000),
    ('David',   NULL, 60000),  -- No department assigned
    ('Emma',    2, 75000);
```

> **What is a FOREIGN KEY?**  
> A foreign key is a column that refers to the primary key of another table. Here, `employees.dept_id` points to `departments.dept_id`. This relationship ensures data integrity — you can't assign an employee to a department that doesn't exist.

### INNER JOIN

Returns only rows where there is a match in **both** tables.

```sql
SELECT 
    e.name        AS employee_name,
    d.dept_name   AS department
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;
```

Result: David (who has no department) is **excluded** because there's no matching `dept_id`.

> **Why use table aliases (e, d)?**  
> When joining tables, column names might exist in both tables. Aliases (`e` for employees, `d` for departments) make it clear which table each column comes from, and make queries shorter to write.

### LEFT JOIN (LEFT OUTER JOIN)

Returns **all rows from the left table**, plus matching rows from the right table. If there's no match, right-table columns are NULL.

```sql
SELECT 
    e.name        AS employee_name,
    d.dept_name   AS department
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

Result: David appears with `department = NULL`.

> **When to use LEFT JOIN?**  
> Use it when you want to keep all records from one table regardless of whether they have a match. "Give me all employees, and show their department if they have one."

### RIGHT JOIN (RIGHT OUTER JOIN)

Returns **all rows from the right table**, plus matching rows from the left table.

```sql
SELECT 
    e.name        AS employee_name,
    d.dept_name   AS department
FROM employees e
RIGHT JOIN departments d ON e.dept_id = d.dept_id;
```

Result: All departments appear, even if no employees are assigned to them.

### FULL OUTER JOIN

Returns rows from **both** tables, with NULLs where there's no match. MySQL doesn't support FULL OUTER JOIN directly, so we simulate it:

```sql
SELECT e.name, d.dept_name
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id

UNION

SELECT e.name, d.dept_name
FROM employees e
RIGHT JOIN departments d ON e.dept_id = d.dept_id;
```

### Self JOIN

A table joined with itself. Useful for hierarchical data.

```sql
-- Add a manager_id column to employees
ALTER TABLE employees ADD COLUMN manager_id INT;
UPDATE employees SET manager_id = 1 WHERE emp_id IN (2, 3);

-- Find each employee and their manager's name
SELECT 
    e.name        AS employee,
    m.name        AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.emp_id;
```

### JOIN with Multiple Tables

```sql
CREATE TABLE projects (
    project_id   INT AUTO_INCREMENT PRIMARY KEY,
    project_name VARCHAR(100),
    dept_id      INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);

INSERT INTO projects (project_name, dept_id) VALUES ('Website Redesign', 2), ('API Gateway', 1);

-- Employees and the projects their department is working on
SELECT 
    e.name         AS employee,
    d.dept_name    AS department,
    p.project_name AS project
FROM employees e
INNER JOIN departments d  ON e.dept_id = d.dept_id
INNER JOIN projects p     ON d.dept_id = p.dept_id;
```

### Visual Summary of JOINs

```
Table A: employees     Table B: departments
+-----+--------+       +---------+-------------+
| id  | dept_id|       | dept_id | dept_name   |
+-----+--------+       +---------+-------------+
| 1   |   1    |       |    1    | Engineering |
| 2   |   1    |       |    2    | Marketing   |
| 3   |   2    |       |    3    | HR          |
| 4   | NULL   |       +---------+-------------+
| 5   |   2    |

INNER JOIN: rows 1, 2, 3, 5 (has match in both)
LEFT JOIN:  rows 1, 2, 3, 4, 5 (all employees, dept=NULL for row 4)
RIGHT JOIN: rows 1, 2, 3, 5 + HR row with emp=NULL
```

---

### 📝 Practice Questions — Chapter 15

1. List all employees with their department names using INNER JOIN.
2. List all employees, including those without a department, showing NULL for the department if none exists.
3. List all departments and how many employees are in each department.
4. What is the difference between INNER JOIN and LEFT JOIN?
5. Join the `students` and a new `courses` table (create it yourself) to show which courses each student is enrolled in.

---

## 16. Subqueries

A **subquery** is a query nested inside another query.

### Subquery in WHERE

```sql
-- Find employees who earn more than the average salary
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

> **Why use a subquery here?**  
> The average salary isn't a fixed number — it's calculated from the data. A subquery lets you compute it dynamically without first running a separate query to find the average.

### Subquery with IN

```sql
-- Find employees in departments that have projects
SELECT name
FROM employees
WHERE dept_id IN (SELECT DISTINCT dept_id FROM projects);
```

### Subquery in FROM (Derived Table)

```sql
-- Find departments with an average salary above 80000
SELECT dept_name, avg_salary
FROM (
    SELECT d.dept_name, AVG(e.salary) AS avg_salary
    FROM employees e
    INNER JOIN departments d ON e.dept_id = d.dept_id
    GROUP BY d.dept_name
) AS dept_averages
WHERE avg_salary > 80000;
```

> **Why use a derived table?**  
> You can't use aggregate functions directly in a WHERE clause. By treating a query as a temporary table (a "derived table"), you can then filter on its aggregated results.

### Correlated Subquery

A correlated subquery references columns from the outer query — it runs once per row.

```sql
-- Find employees who earn more than the average salary in their own department
SELECT e.name, e.salary, e.dept_id
FROM employees e
WHERE e.salary > (
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.dept_id = e.dept_id   -- references outer query's dept_id
);
```

### EXISTS / NOT EXISTS

```sql
-- Find departments that have at least one employee
SELECT dept_name
FROM departments d
WHERE EXISTS (
    SELECT 1 FROM employees e WHERE e.dept_id = d.dept_id
);
```

> **Why EXISTS instead of IN?**  
> `EXISTS` stops as soon as it finds the first match (short-circuit), which can be faster than `IN` for large datasets. Also, `EXISTS` handles NULLs more predictably.

---

### 📝 Practice Questions — Chapter 16

1. Find students whose grade is above the average grade of all students.
2. Find books priced above the average price of all books.
3. Find all employees who are in the same department as 'Alice'.
4. Find departments that have no employees assigned.
5. What is a correlated subquery? Why is it potentially slow?

---

## 17. Indexes

### What is an Index?
An index is a data structure that speeds up data retrieval. Think of it like the index at the back of a textbook — instead of reading every page to find "photosynthesis", you look it up in the index and jump directly to the right pages.

> **Why do indexes matter?**  
> Without an index on a column, MySQL does a **full table scan** — checking every single row. On a table with 10 million rows, that can take seconds. An index lets MySQL jump directly to the matching rows in milliseconds.

### Creating an Index

```sql
-- Create an index on the email column for faster lookups
CREATE INDEX idx_email ON students(email);

-- Create an index on the last_name column
CREATE INDEX idx_last_name ON students(last_name);

-- Composite index (speeds up queries that filter by both columns)
CREATE INDEX idx_name ON students(last_name, first_name);
```

### Primary Key Index
When you define a PRIMARY KEY, MySQL automatically creates an index on that column. This is why lookups by primary key are always fast.

### UNIQUE Index

```sql
CREATE UNIQUE INDEX idx_unique_email ON students(email);
-- Same effect as adding UNIQUE constraint to the column
```

### Viewing Indexes

```sql
SHOW INDEX FROM students;
```

### Dropping an Index

```sql
DROP INDEX idx_email ON students;
```

### The Cost of Indexes

> **Why not just index every column?**  
> Indexes speed up reads but slow down writes (INSERT, UPDATE, DELETE) because the index must be updated whenever data changes. They also use extra disk space. Add indexes on columns you frequently search, filter, sort, or join on — not on every column.

### EXPLAIN — Analyzing Query Performance

```sql
EXPLAIN SELECT * FROM students WHERE email = 'alice@example.com';
```

The `EXPLAIN` output shows whether MySQL used an index or did a full table scan. Look at the `type` column:
- `const` or `ref` → using an index efficiently ✅
- `ALL` → full table scan, consider adding an index ⚠️

---

### 📝 Practice Questions — Chapter 17

1. Create an index on the `author` column of the `books` table.
2. Why should you not index every column?
3. What command shows you the indexes on a table?
4. Use `EXPLAIN` to check if a query on `books.author` uses an index.
5. What type of index is automatically created when you define a PRIMARY KEY?

---

## 18. Views

### What is a View?
A **view** is a saved SQL query that you can treat like a virtual table. The data isn't stored separately — when you query the view, MySQL runs the underlying query behind the scenes.

> **Why use views?**  
> 1. **Simplicity** — complex joins written once, reused many times  
> 2. **Security** — show users only certain columns (hide sensitive data like salaries)  
> 3. **Consistency** — ensures everyone uses the same query logic  

### Creating a View

```sql
-- View that shows employee names and their department names
CREATE VIEW employee_details AS
SELECT 
    e.emp_id,
    e.name          AS employee_name,
    d.dept_name     AS department,
    e.salary
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

### Using a View

```sql
-- Use the view just like a table
SELECT * FROM employee_details;
SELECT employee_name, department FROM employee_details WHERE salary > 80000;
```

### Updating a View

```sql
CREATE OR REPLACE VIEW employee_details AS
SELECT 
    e.emp_id,
    e.name          AS employee_name,
    d.dept_name     AS department
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

### Dropping a View

```sql
DROP VIEW IF EXISTS employee_details;
```

### Are Views Always Up to Date?
Yes. A view doesn't store data — it stores the query. Every time you query the view, MySQL executes the underlying SQL fresh against the current data.

---

### 📝 Practice Questions — Chapter 18

1. Create a view called `grade_10_students` that shows all students in grade 10.
2. Create a view called `book_summary` that shows the title, author, and price of each book.
3. How do you update an existing view?
4. Does a view store data? Explain why or why not.

---

## 19. Stored Procedures

### What is a Stored Procedure?
A stored procedure is a block of SQL code saved in the database that you can call by name. Think of it like a function in programming.

> **Why use stored procedures?**  
> 1. **Reuse** — write complex logic once, call it many times  
> 2. **Performance** — the database parses and optimizes the procedure once  
> 3. **Security** — applications can call a procedure without needing direct table access  
> 4. **Maintainability** — change the logic in one place without modifying application code  

### Basic Stored Procedure

```sql
DELIMITER $$

CREATE PROCEDURE GetAllStudents()
BEGIN
    SELECT * FROM students;
END$$

DELIMITER ;
```

> **Why change the DELIMITER?**  
> By default, MySQL treats `;` as the end of a statement. But inside a procedure, we have multiple `;` statements. We temporarily change the delimiter to `$$` so MySQL knows the entire block is one unit.

### Calling a Procedure

```sql
CALL GetAllStudents();
```

### Procedure with Parameters

```sql
DELIMITER $$

CREATE PROCEDURE GetStudentsByGrade(IN p_grade INT)
BEGIN
    SELECT * FROM students WHERE grade = p_grade;
END$$

DELIMITER ;

-- Usage:
CALL GetStudentsByGrade(10);
```

**Parameter modes:**
| Mode | Direction | Description |
|------|-----------|-------------|
| `IN` | Input | Caller passes a value in |
| `OUT` | Output | Procedure sends a value back |
| `INOUT` | Both | Value goes both ways |

### Procedure with OUT Parameter

```sql
DELIMITER $$

CREATE PROCEDURE CountStudentsByGrade(IN p_grade INT, OUT p_count INT)
BEGIN
    SELECT COUNT(*) INTO p_count
    FROM students
    WHERE grade = p_grade;
END$$

DELIMITER ;

-- Usage:
CALL CountStudentsByGrade(10, @result);
SELECT @result AS student_count;
```

### Variables and Control Flow

```sql
DELIMITER $$

CREATE PROCEDURE GradeCategory(IN p_grade INT, OUT p_category VARCHAR(20))
BEGIN
    IF p_grade >= 11 THEN
        SET p_category = 'Upperclassman';
    ELSEIF p_grade = 10 THEN
        SET p_category = 'Sophomore';
    ELSE
        SET p_category = 'Freshman';
    END IF;
END$$

DELIMITER ;

CALL GradeCategory(11, @cat);
SELECT @cat;
```

### Dropping a Procedure

```sql
DROP PROCEDURE IF EXISTS GetAllStudents;
```

---

### 📝 Practice Questions — Chapter 19

1. Create a stored procedure `GetBooksByAuthor(IN p_author VARCHAR(100))` that returns all books by a given author.
2. Create a stored procedure `GetBookCount(OUT p_count INT)` that returns the total number of books.
3. What is the purpose of changing the DELIMITER?
4. What is the difference between IN, OUT, and INOUT parameters?

---

## 20. User-Defined Functions

### What is a User-Defined Function (UDF)?
Like a stored procedure, but it **returns a single value** and can be used directly inside SQL queries (like built-in functions such as `UPPER()`, `NOW()`).

> **Why use functions instead of procedures?**  
> Functions return a value and can be embedded in SELECT, WHERE, and ORDER BY. Procedures are called with `CALL` and are better for multi-step operations or when you need OUT parameters.

### Creating a Function

```sql
DELIMITER $$

CREATE FUNCTION FullName(first VARCHAR(50), last VARCHAR(50))
RETURNS VARCHAR(101)
DETERMINISTIC
BEGIN
    RETURN CONCAT(first, ' ', last);
END$$

DELIMITER ;
```

> **Why DETERMINISTIC?**  
> `DETERMINISTIC` tells MySQL that the same inputs always produce the same output (no randomness, no reading external data). This allows MySQL to cache and optimize the function calls.

### Using a Function

```sql
SELECT FullName(first_name, last_name) AS full_name FROM students;
```

### Another Example — Age Calculation

```sql
DELIMITER $$

CREATE FUNCTION CalculateAge(dob DATE)
RETURNS INT
DETERMINISTIC
BEGIN
    RETURN TIMESTAMPDIFF(YEAR, dob, CURDATE());
END$$

DELIMITER ;

SELECT first_name, last_name, CalculateAge(date_of_birth) AS age FROM students;
```

### Dropping a Function

```sql
DROP FUNCTION IF EXISTS FullName;
```

---

### 📝 Practice Questions — Chapter 20

1. Create a function `DiscountedPrice(price DECIMAL(10,2), discount_pct INT)` that returns the price after applying the discount percentage.
2. What is the key difference between a stored procedure and a user-defined function?
3. Can you use a stored procedure inside a SELECT statement? Why or why not?

---

## 21. Triggers

### What is a Trigger?
A trigger is SQL code that **automatically executes** in response to an event (INSERT, UPDATE, or DELETE) on a table.

> **Why use triggers?**  
> 1. **Audit logging** — automatically record who changed what and when  
> 2. **Data validation** — enforce rules that can't be expressed as constraints  
> 3. **Derived data** — automatically update summary tables  
> 4. **Consistency** — ensure related tables stay in sync  

### Trigger Events and Timing

| When | Event | Example |
|------|-------|---------|
| `BEFORE INSERT` | Before a new row is added | Validate data before saving |
| `AFTER INSERT` | After a new row is added | Log the new record |
| `BEFORE UPDATE` | Before a row is changed | Record old value |
| `AFTER UPDATE` | After a row is changed | Update a summary table |
| `BEFORE DELETE` | Before a row is removed | Archive the row |
| `AFTER DELETE` | After a row is removed | Log the deletion |

### Creating an Audit Log Table and Trigger

```sql
-- Audit log table
CREATE TABLE student_audit (
    audit_id     INT AUTO_INCREMENT PRIMARY KEY,
    student_id   INT,
    action       VARCHAR(10),
    changed_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    changed_by   VARCHAR(50)
);

-- Trigger: after a student row is updated, log it
DELIMITER $$

CREATE TRIGGER after_student_update
AFTER UPDATE ON students
FOR EACH ROW
BEGIN
    INSERT INTO student_audit (student_id, action, changed_by)
    VALUES (OLD.student_id, 'UPDATE', USER());
END$$

DELIMITER ;
```

> **NEW and OLD inside a trigger:**  
> - `OLD.column` — the value *before* the change  
> - `NEW.column` — the value *after* the change  
> - `INSERT` triggers: only `NEW` is available  
> - `DELETE` triggers: only `OLD` is available  
> - `UPDATE` triggers: both `NEW` and `OLD` are available  

### BEFORE Trigger for Validation

```sql
DELIMITER $$

CREATE TRIGGER before_book_insert
BEFORE INSERT ON books
FOR EACH ROW
BEGIN
    IF NEW.price < 0 THEN
        SIGNAL SQLSTATE '45000'
            SET MESSAGE_TEXT = 'Price cannot be negative';
    END IF;
END$$

DELIMITER ;
```

### Viewing and Dropping Triggers

```sql
SHOW TRIGGERS;
DROP TRIGGER IF EXISTS after_student_update;
```

---

### 📝 Practice Questions — Chapter 21

1. Create a trigger that logs whenever a book is deleted into a `deleted_books_log` table.
2. What is the difference between `BEFORE` and `AFTER` triggers?
3. In an UPDATE trigger, what does `OLD.price` refer to?
4. Create a trigger that prevents inserting a student with grade < 1 or grade > 12.

---

## 22. Transactions

### What is a Transaction?
A transaction is a group of SQL statements that are treated as a single unit. Either **all succeed**, or **none of them take effect**. This is the foundation of data integrity in databases.

> **Why do we need transactions?**  
> Imagine transferring $100 from Account A to Account B. This requires two operations:  
> 1. Subtract $100 from Account A  
> 2. Add $100 to Account B  
>  
> If the system crashes between step 1 and step 2, Account A lost $100 and Account B never got it. Transactions ensure that either both steps succeed together, or neither does (rolling back the debit if the credit fails).

### ACID Properties

| Property | Meaning |
|----------|---------|
| **A**tomicity | All or nothing — transactions complete fully or not at all |
| **C**onsistency | The database remains in a valid state before and after |
| **I**solation | Concurrent transactions don't interfere with each other |
| **D**urability | Once committed, data survives crashes |

### Basic Transaction Syntax

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

COMMIT;  -- Make the changes permanent
```

### ROLLBACK — Undoing a Transaction

```sql
START TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
-- Something went wrong!
ROLLBACK;  -- Undo all changes since START TRANSACTION
```

### SAVEPOINT — Partial Rollback

```sql
START TRANSACTION;

INSERT INTO orders (customer_id, total) VALUES (1, 250.00);
SAVEPOINT order_created;

INSERT INTO order_items (order_id, product_id, qty) VALUES (LAST_INSERT_ID(), 5, 2);
-- This fails for some reason
ROLLBACK TO SAVEPOINT order_created;  -- Undo just the order_items insert

COMMIT;  -- But commit the order itself
```

### Autocommit

By default, MySQL runs each statement in its own automatic transaction (autocommit = ON). When you use `START TRANSACTION`, you take manual control.

```sql
SET autocommit = 0;  -- Turn off autocommit
-- Now every statement must be manually committed or rolled back
SET autocommit = 1;  -- Turn it back on
```

---

### 📝 Practice Questions — Chapter 22

1. Write a transaction that transfers $500 from account 3 to account 4, with a ROLLBACK if an error occurs.
2. What does ACID stand for?
3. What is the difference between COMMIT and ROLLBACK?
4. What is a SAVEPOINT and when would you use one?
5. What happens to your data if MySQL crashes during a transaction that hasn't been committed yet?

---

## 23. User Management & Security

### Why Manage Users?

> **Why not just use the root user for everything?**  
> The root user has unlimited access — it can drop databases, delete tables, modify system settings. If your application's database credentials are ever compromised and they have root access, an attacker can destroy everything. Giving applications only the permissions they need (the **principle of least privilege**) limits the damage from breaches.

### Creating a User

```sql
CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'StrongPassword123!';
CREATE USER 'readonly_user'@'%' IDENTIFIED BY 'ReadOnly456!';
-- '%' means the user can connect from any host
-- 'localhost' restricts to local connections only
```

### Granting Privileges

```sql
-- Grant specific privileges on a specific database
GRANT SELECT, INSERT, UPDATE ON school.* TO 'app_user'@'localhost';

-- Grant read-only access
GRANT SELECT ON school.* TO 'readonly_user'@'%';

-- Grant all privileges on all databases (admin-level — use sparingly)
GRANT ALL PRIVILEGES ON *.* TO 'admin_user'@'localhost';

-- Apply the privilege changes immediately
FLUSH PRIVILEGES;
```

### Common Privilege Types

| Privilege | What it allows |
|-----------|---------------|
| `SELECT` | Read data |
| `INSERT` | Add new rows |
| `UPDATE` | Modify existing rows |
| `DELETE` | Remove rows |
| `CREATE` | Create databases and tables |
| `DROP` | Delete databases and tables |
| `EXECUTE` | Run stored procedures |
| `ALL PRIVILEGES` | Everything |

### Viewing Grants

```sql
SHOW GRANTS FOR 'app_user'@'localhost';
```

### Revoking Privileges

```sql
REVOKE DELETE ON school.* FROM 'app_user'@'localhost';
```

### Changing a Password

```sql
ALTER USER 'app_user'@'localhost' IDENTIFIED BY 'NewStrongerPassword789!';
FLUSH PRIVILEGES;
```

### Dropping a User

```sql
DROP USER IF EXISTS 'readonly_user'@'%';
```

### SQL Injection — A Critical Security Warning

> **What is SQL injection?**  
> SQL injection is an attack where a malicious user inserts SQL code into input fields to manipulate your database. Example:  
>  
> If your application does: `"SELECT * FROM users WHERE username = '" + input + "'"` and the user types `' OR '1'='1`, the query becomes:  
> `SELECT * FROM users WHERE username = '' OR '1'='1'`  
> which returns all users!  
>  
> **The fix: Always use prepared statements / parameterized queries** in your application code. Never concatenate raw user input into SQL.

---

### 📝 Practice Questions — Chapter 23

1. Create a user `student_app` who can only connect from localhost, with password `Secure123!`.
2. Grant `student_app` the ability to SELECT and INSERT in the `school` database.
3. What is the principle of least privilege?
4. What is SQL injection and how do you prevent it?
5. Revoke the INSERT privilege from `student_app`.

---

## 24. Backup and Restore

### Why Backup?

> **Why is backup critical?**  
> Hardware fails, software has bugs, humans make mistakes. Without backups, a single `DROP DATABASE` or a hardware failure can permanently destroy years of data. Regular backups are the safety net that lets you recover.

### mysqldump — Export a Database

```bash
# Backup a single database to a .sql file
mysqldump -u root -p school > school_backup.sql

# Backup with date in filename
mysqldump -u root -p school > school_$(date +%Y%m%d).sql

# Backup all databases
mysqldump -u root -p --all-databases > all_databases_backup.sql

# Backup only specific tables
mysqldump -u root -p school students books > partial_backup.sql
```

### Restoring a Database

```bash
# Restore from a backup file
mysql -u root -p school < school_backup.sql

# If restoring to a new database, create it first:
mysql -u root -p -e "CREATE DATABASE school_restored;"
mysql -u root -p school_restored < school_backup.sql
```

### What's Inside a mysqldump File?
Open the `.sql` file in a text editor — you'll see:
- `DROP TABLE IF EXISTS` statements
- `CREATE TABLE` statements
- `INSERT INTO` statements with all the data

### Automating Backups
On Linux/macOS, add this to crontab (`crontab -e`) to back up nightly at 2 AM:
```
0 2 * * * mysqldump -u root -pYourPassword school > /backups/school_$(date +\%Y\%m\%d).sql
```

---

### 📝 Practice Questions — Chapter 24

1. Write the command to back up the `library` database to a file called `library_backup.sql`.
2. Write the command to restore `library_backup.sql` into a database called `library`.
3. Why should backups be stored on a different physical machine or cloud storage?
4. What does `--all-databases` do in mysqldump?

---

## 25. Performance Optimization

### Why Performance Matters?

> **Why optimize queries?**  
> A slow query that takes 2 seconds doesn't matter when 1 person uses it. But if 1,000 people hit that query per minute, each waiting 2 seconds, your server is under enormous load. Optimization makes applications fast, scalable, and cost-effective.

### 1. Use Indexes Wisely (recap)

```sql
-- Check if your query uses indexes
EXPLAIN SELECT * FROM students WHERE last_name = 'Johnson';

-- Add index if not present
CREATE INDEX idx_last_name ON students(last_name);
```

### 2. Select Only What You Need

```sql
-- BAD: retrieves all columns
SELECT * FROM students WHERE grade = 10;

-- GOOD: retrieves only needed columns
SELECT student_id, first_name, last_name FROM students WHERE grade = 10;
```

### 3. Use LIMIT

```sql
-- If you only need 10 results, tell MySQL to stop after 10
SELECT * FROM students ORDER BY last_name LIMIT 10;
```

### 4. Avoid Functions on Indexed Columns in WHERE

```sql
-- BAD: MySQL can't use the index on last_name because of the function
SELECT * FROM students WHERE UPPER(last_name) = 'JOHNSON';

-- GOOD: store data consistently, query without transformation
SELECT * FROM students WHERE last_name = 'Johnson';
```

### 5. Use Joins Instead of Subqueries When Possible

In many cases, a JOIN performs better than a correlated subquery because MySQL can optimize joins more effectively.

```sql
-- Subquery approach (potentially slower)
SELECT name FROM employees
WHERE dept_id IN (SELECT dept_id FROM departments WHERE dept_name = 'Engineering');

-- JOIN approach (often faster)
SELECT e.name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id
WHERE d.dept_name = 'Engineering';
```

### 6. Analyze with EXPLAIN

```sql
EXPLAIN SELECT e.name, d.dept_name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id
WHERE d.dept_name = 'Engineering';
```

Key columns in EXPLAIN output:
| Column | What to look for |
|--------|----------------|
| `type` | `const`, `ref`, `range` are good; `ALL` means full scan |
| `rows` | Estimated rows MySQL must examine |
| `key` | Which index is being used |
| `Extra` | "Using index" is good; "Using filesort" / "Using temporary" are expensive |

### 7. Normalisation vs Denormalisation

**Normalisation** — splitting data into multiple related tables to eliminate redundancy.  
**Denormalisation** — intentionally introducing redundancy for read performance.

> **Why normalize?**  
> Storing `department_name` in every employee row means if a department renames, you update thousands of rows. Normalising puts `department_name` in one place.  
>  
> **Why denormalize?**  
> Sometimes a heavily-read reporting table benefits from having pre-joined data to avoid costly JOINs at query time.

---

### 📝 Practice Questions — Chapter 25

1. Run `EXPLAIN` on a query that searches students by email. Is an index being used?
2. Rewrite this query to be more performant: `SELECT * FROM books WHERE YEAR(published_date) = 2020;`
3. What does the `type: ALL` in an EXPLAIN output mean?
4. Why should you avoid `SELECT *` in production?

---

## 26. Advanced Topics: CTEs, Window Functions & JSON

### Common Table Expressions (CTEs)

A CTE is a named temporary result set defined within the query using `WITH`. It improves readability for complex queries.

```sql
-- Without CTE (harder to read)
SELECT dept_name, avg_salary
FROM (
    SELECT d.dept_name, AVG(e.salary) AS avg_salary
    FROM employees e
    INNER JOIN departments d ON e.dept_id = d.dept_id
    GROUP BY d.dept_name
) sub
WHERE avg_salary > 75000;

-- With CTE (cleaner)
WITH dept_avg AS (
    SELECT d.dept_name, AVG(e.salary) AS avg_salary
    FROM employees e
    INNER JOIN departments d ON e.dept_id = d.dept_id
    GROUP BY d.dept_name
)
SELECT dept_name, avg_salary
FROM dept_avg
WHERE avg_salary > 75000;
```

### Recursive CTEs

Used for hierarchical data like org charts or category trees.

```sql
WITH RECURSIVE org_chart AS (
    -- Base case: top-level employees (no manager)
    SELECT emp_id, name, manager_id, 0 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive case: find reports of each employee
    SELECT e.emp_id, e.name, e.manager_id, oc.level + 1
    FROM employees e
    INNER JOIN org_chart oc ON e.manager_id = oc.emp_id
)
SELECT REPEAT('  ', level) || name AS hierarchy, level
FROM org_chart
ORDER BY level, name;
```

### Window Functions (MySQL 8.0+)

Window functions perform calculations across a "window" of rows related to the current row, **without collapsing rows** like `GROUP BY` does.

```sql
-- Rank employees by salary within each department
SELECT 
    name,
    dept_id,
    salary,
    RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS salary_rank
FROM employees;
```

> **Why use window functions instead of GROUP BY?**  
> `GROUP BY` aggregates — it reduces multiple rows into one. Window functions let you see both the individual row AND the aggregate result. You get the best of both worlds.

### Common Window Functions

```sql
-- ROW_NUMBER: unique sequential number
SELECT name, salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
FROM employees;

-- RANK: same rank for ties, gaps after ties (1, 1, 3)
SELECT name, salary,
    RANK() OVER (ORDER BY salary DESC) AS rnk
FROM employees;

-- DENSE_RANK: same rank for ties, no gaps (1, 1, 2)
SELECT name, salary,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rnk
FROM employees;

-- LAG: value from the previous row
SELECT name, salary,
    LAG(salary) OVER (ORDER BY salary) AS prev_salary
FROM employees;

-- LEAD: value from the next row
SELECT name, salary,
    LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM employees;

-- Running total
SELECT name, salary,
    SUM(salary) OVER (ORDER BY emp_id) AS running_total
FROM employees;
```

### JSON Support (MySQL 5.7+)

MySQL can store and query JSON documents natively.

```sql
-- Create a table with a JSON column
CREATE TABLE products (
    product_id   INT AUTO_INCREMENT PRIMARY KEY,
    name         VARCHAR(100),
    attributes   JSON
);

-- Insert JSON data
INSERT INTO products (name, attributes) VALUES 
('Laptop', '{"color": "silver", "ram": 16, "storage": 512, "tags": ["electronics", "computing"]}'),
('Phone',  '{"color": "black",  "ram": 8,  "storage": 256, "tags": ["electronics", "mobile"]}');

-- Query a JSON field
SELECT name, attributes->>'$.color' AS color FROM products;
SELECT name, JSON_EXTRACT(attributes, '$.ram') AS ram FROM products;

-- Query JSON array
SELECT name FROM products
WHERE JSON_CONTAINS(attributes->'$.tags', '"electronics"');

-- Update a JSON field
UPDATE products 
SET attributes = JSON_SET(attributes, '$.ram', 32)
WHERE product_id = 1;
```

---

### 📝 Practice Questions — Chapter 26

1. Rewrite the following query using a CTE:
   ```sql
   SELECT author, COUNT(*) FROM books GROUP BY author HAVING COUNT(*) > 1;
   ```
2. Use `RANK()` to rank books by price within each author group.
3. Use `LAG()` to compare each employee's salary with the previous employee's salary in order of `emp_id`.
4. Insert a student record into a `students_json` table where the `metadata` JSON column stores `{"hobbies": ["reading", "chess"], "gpa": 3.8}`.
5. Query the `metadata` column to find students whose GPA is above 3.5.

---

## 27. Final Practice Project

### Project: Library Management System

Build a complete database for a library. This project uses everything you've learned.

### Step 1 — Create the Database and Tables

```sql
CREATE DATABASE IF NOT EXISTS library_mgmt;
USE library_mgmt;

CREATE TABLE authors (
    author_id   INT AUTO_INCREMENT PRIMARY KEY,
    full_name   VARCHAR(100) NOT NULL,
    country     VARCHAR(50),
    birth_year  YEAR
);

CREATE TABLE books (
    book_id         INT AUTO_INCREMENT PRIMARY KEY,
    title           VARCHAR(200) NOT NULL,
    author_id       INT NOT NULL,
    isbn            VARCHAR(20) UNIQUE,
    published_year  YEAR,
    price           DECIMAL(8,2) CHECK (price >= 0),
    stock           INT DEFAULT 0,
    FOREIGN KEY (author_id) REFERENCES authors(author_id)
);

CREATE TABLE members (
    member_id   INT AUTO_INCREMENT PRIMARY KEY,
    full_name   VARCHAR(100) NOT NULL,
    email       VARCHAR(150) UNIQUE NOT NULL,
    joined_date DATE DEFAULT (CURRENT_DATE),
    is_active   BOOLEAN DEFAULT TRUE
);

CREATE TABLE loans (
    loan_id         INT AUTO_INCREMENT PRIMARY KEY,
    book_id         INT NOT NULL,
    member_id       INT NOT NULL,
    loaned_on       DATE DEFAULT (CURRENT_DATE),
    due_date        DATE NOT NULL,
    returned_on     DATE,
    FOREIGN KEY (book_id)   REFERENCES books(book_id),
    FOREIGN KEY (member_id) REFERENCES members(member_id)
);
```

### Step 2 — Populate with Sample Data

```sql
INSERT INTO authors (full_name, country, birth_year) VALUES
('Robert C. Martin',   'USA',    1952),
('Martin Fowler',      'UK',     1963),
('Andrew Hunt',        'USA',    NULL),
('Yuval Noah Harari',  'Israel', 1976);

INSERT INTO books (title, author_id, isbn, published_year, price, stock) VALUES
('Clean Code',          1, '9780132350884', 2008, 34.99, 5),
('The Clean Coder',     1, '9780137081073', 2011, 29.99, 3),
('Refactoring',         2, '9780201485677', 1999, 39.99, 2),
('The Pragmatic Programmer', 3, '9780135957059', 2019, 44.99, 4),
('Sapiens',             4, '9780062316097', 2011, 17.99, 8);

INSERT INTO members (full_name, email, joined_date) VALUES
('Alice Thompson',  'alice@email.com',   '2023-01-15'),
('Bob Carter',      'bob@email.com',     '2023-03-22'),
('Carol White',     'carol@email.com',   '2024-06-01');

INSERT INTO loans (book_id, member_id, loaned_on, due_date, returned_on) VALUES
(1, 1, '2024-01-10', '2024-01-24', '2024-01-20'),
(3, 2, '2024-02-05', '2024-02-19', NULL),
(5, 1, '2024-02-10', '2024-02-24', NULL),
(2, 3, '2024-03-01', '2024-03-15', '2024-03-14');
```

### Step 3 — Practical Queries

```sql
-- 1. List all books with their author's name
SELECT b.title, a.full_name AS author, b.price, b.stock
FROM books b
INNER JOIN authors a ON b.author_id = a.author_id;

-- 2. Find all overdue loans (past due date, not yet returned)
SELECT 
    m.full_name AS member,
    b.title     AS book,
    l.due_date,
    DATEDIFF(CURDATE(), l.due_date) AS days_overdue
FROM loans l
INNER JOIN members m ON l.member_id = m.member_id
INNER JOIN books   b ON l.book_id   = b.book_id
WHERE l.returned_on IS NULL AND l.due_date < CURDATE();

-- 3. Count books per author
SELECT a.full_name, COUNT(b.book_id) AS books_written
FROM authors a
LEFT JOIN books b ON a.author_id = b.author_id
GROUP BY a.full_name
ORDER BY books_written DESC;

-- 4. Most popular books (most loaned)
SELECT b.title, COUNT(l.loan_id) AS times_loaned
FROM books b
LEFT JOIN loans l ON b.book_id = l.book_id
GROUP BY b.title
ORDER BY times_loaned DESC;

-- 5. Members who have never returned a book
SELECT m.full_name
FROM members m
WHERE EXISTS (
    SELECT 1 FROM loans l
    WHERE l.member_id = m.member_id AND l.returned_on IS NULL
);
```

### Step 4 — Add a View, Procedure, and Trigger

```sql
-- View: active loans summary
CREATE VIEW active_loans AS
SELECT 
    l.loan_id,
    m.full_name  AS member,
    b.title      AS book,
    l.loaned_on,
    l.due_date
FROM loans l
INNER JOIN members m ON l.member_id = m.member_id
INNER JOIN books   b ON l.book_id   = b.book_id
WHERE l.returned_on IS NULL;

-- Procedure: checkout a book
DELIMITER $$
CREATE PROCEDURE CheckoutBook(IN p_book_id INT, IN p_member_id INT, IN p_days INT)
BEGIN
    DECLARE v_stock INT;
    SELECT stock INTO v_stock FROM books WHERE book_id = p_book_id;
    IF v_stock > 0 THEN
        INSERT INTO loans (book_id, member_id, due_date)
        VALUES (p_book_id, p_member_id, DATE_ADD(CURDATE(), INTERVAL p_days DAY));
        UPDATE books SET stock = stock - 1 WHERE book_id = p_book_id;
        SELECT 'Book checked out successfully' AS message;
    ELSE
        SELECT 'Sorry, this book is out of stock' AS message;
    END IF;
END$$
DELIMITER ;

-- Trigger: restore stock when a book is returned
DELIMITER $$
CREATE TRIGGER after_book_returned
AFTER UPDATE ON loans
FOR EACH ROW
BEGIN
    IF OLD.returned_on IS NULL AND NEW.returned_on IS NOT NULL THEN
        UPDATE books SET stock = stock + 1 WHERE book_id = NEW.book_id;
    END IF;
END$$
DELIMITER ;
```

### Step 5 — Final Challenges

Try to write these queries yourself:
1. List the top 3 most active members (who have borrowed the most books).
2. Find all books that have never been borrowed.
3. Calculate the average loan duration (in days) for returned books.
4. Find members who have overdue books, along with the number of days each book is overdue.
5. Create a stored procedure `ReturnBook(IN p_loan_id INT)` that marks a loan as returned (sets `returned_on = CURDATE()`) and triggers the stock update.
6. Using a CTE, find authors whose books have an average price above $30.
7. Use a window function to rank members by total number of books borrowed.

---

## Quick Reference Cheat Sheet

```sql
-- DATABASE
CREATE DATABASE db_name;
DROP DATABASE db_name;
USE db_name;

-- TABLE
CREATE TABLE t (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(50) NOT NULL);
ALTER TABLE t ADD COLUMN age INT;
DROP TABLE t;

-- CRUD
INSERT INTO t (name) VALUES ('Alice');
SELECT * FROM t WHERE id = 1;
UPDATE t SET name = 'Bob' WHERE id = 1;
DELETE FROM t WHERE id = 1;

-- FILTERING
WHERE col = val
WHERE col BETWEEN a AND b
WHERE col IN (a, b, c)
WHERE col LIKE 'pat%'
WHERE col IS NULL

-- SORTING & LIMITING
ORDER BY col ASC|DESC
LIMIT n OFFSET m

-- AGGREGATES
COUNT(*), SUM(col), AVG(col), MIN(col), MAX(col)
GROUP BY col HAVING condition

-- JOINS
INNER JOIN t2 ON t1.id = t2.t1_id
LEFT  JOIN t2 ON t1.id = t2.t1_id
RIGHT JOIN t2 ON t1.id = t2.t1_id

-- INDEXES
CREATE INDEX idx ON t(col);
DROP INDEX idx ON t;

-- VIEWS
CREATE VIEW v AS SELECT ...;
DROP VIEW v;

-- TRANSACTIONS
START TRANSACTION; ... COMMIT;
START TRANSACTION; ... ROLLBACK;

-- USERS
CREATE USER 'u'@'host' IDENTIFIED BY 'pass';
GRANT SELECT ON db.* TO 'u'@'host';
REVOKE SELECT ON db.* FROM 'u'@'host';
DROP USER 'u'@'host';
```

---

## Recommended Learning Path

| Stage | Topics | Goal |
|-------|--------|------|
| **Week 1** | Chapters 1–6 | Understand databases, create tables, insert data |
| **Week 2** | Chapters 7–11 | Master SELECT, WHERE, UPDATE, DELETE, ORDER BY |
| **Week 3** | Chapters 12–15 | Aggregates, GROUP BY, JOINs |
| **Week 4** | Chapters 16–18 | Subqueries, Indexes, Views |
| **Week 5** | Chapters 19–22 | Procedures, Functions, Triggers, Transactions |
| **Week 6** | Chapters 23–27 | Security, Backup, Performance, Advanced, Project |

---

## Further Resources

- 📖 [MySQL Official Documentation](https://dev.mysql.com/doc/)
- 🎯 [SQLZoo — Interactive SQL exercises](https://sqlzoo.net/)
- 🏋️ [LeetCode SQL problems](https://leetcode.com/problemset/database/)
- 🎓 [MySQL for Developers — PlanetScale course](https://planetscale.com/courses/mysql-for-developers/introduction/course-introduction)

---

*Happy querying! 🎉 Remember: the best way to learn SQL is to practice every day. Start small, build the library project, then apply these skills to your own real-world data.*