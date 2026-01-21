# SQL Fundamentals 

## Task 1 - Introduction

**Cyber security** is a broad topic covering many subjects, but few are as important as **databases**. Whether you're securing a **web application**, working in a **SOC** using a **SIEM**, configuring **user authentication/access control**, or using **malware analysis/threat detection tools**, you will rely on **databases**.

### Use Cases

**Offensive Security:**
- Understanding **SQL vulnerabilities** like **SQL injections**
- Creating **queries** to tamper or retrieve data in compromised services

**Defensive Security:**
- Navigating databases to find suspicious activity
- Implementing restrictions to protect services
- Analyzing relevant information for security incidents

Because databases are everywhere, understanding them is crucial. This room covers the basics of **databases**, key terms, concepts, different types, and **SQL fundamentals**.

---

## Task 2 - Databases 101

### What is a Database?

**Databases** are organized collections of structured information or data that can be easily accessed, manipulated, or analyzed.

### Common Examples

- **User authentication data**: Usernames and passwords stored for login systems (like TryHackMe)
- **Social media data**: User posts, comments, likes on platforms like Instagram and Facebook
- **Streaming services**: Watch history used by Netflix to generate recommendations

Databases are used by both large-scale and small-scale businesses. Almost every business needs to configure a **database** to store their data.

---

### Different Types of Databases

There are two primary types of **databases**:

### 1. Relational Databases (SQL)

**Relational databases** store **structured data** following a specific format.

**Example:** User data contains `first_name`, `last_name`, `email_address`, `username`, and `password`. New user entries must follow this structure.

**Features:**
- Data stored in **rows** and **columns** in **tables**
- **Relationships** can be created between two or more tables
- Used when data is received in a consistent format
- Important for accuracy (e.g., e-commerce transactions)

### 2. Non-Relational Databases (NoSQL)

**Non-relational databases** store data in a **non-tabular format**.

**Example:**
```json
{
    _id: ObjectId("4556712cd2b2397ce1b47661"),
    name: { first: "Thomas", last: "Anderson" },
    date_of_birth: new Date('Sep 2, 1964'),
    occupation: [ "The One"],
    steps_taken : NumberLong(4738947387743977493)
}
```

**Features:**
- Data can vary greatly in format
- Better for collecting diverse user-generated content
- Used by social media platforms

---

### Tables, Rows and Columns

All data in a **relational database** is stored in **tables**.

**Example:** A bookstore might have a **"Books"** table.

### Creating a Table

When creating a table, you must define:
- **Columns**: Specific pieces of information (e.g., `id`, `Name`, `Published_date`)
- **Data types**: What type of data each column contains

### Common Data Types

- **Strings**: Text and characters
- **Integers**: Numbers
- **Floats/Decimals**: Numbers with decimal points
- **Times/Dates**: Date and time values

### Rows

Once a **table** is created and a **record** is inserted (e.g., book "Android Security Internals" with id "1" and date "2014-10-14"), the record is represented as a **row**.

---

## Primary and Foreign Keys

### Primary Keys

A **primary key** ensures data in a column is **unique**. It uniquely identifies each **record** in a table.

**Example:** Student matriculation numbers uniquely identify students (since names can be duplicated).

**Rules:**
- Must be unique for each record
- Only **one primary key** per table
- Often the `id` column is used as the **primary key**

### Foreign Keys

A **foreign key** is a column that exists in another table, creating a **link** between two tables.

**Example:** An `author_id` column in the **"Books"** table corresponds to the `id` column in the **"Authors"** table.

**Rules:**
- Creates **relationships** between tables
- A table can have **multiple foreign keys**

---

## Task 3 - SQL

### What is SQL?

**SQL** (**Structured Query Language**) is a programming language used to query, define, and manipulate data in **relational databases**.

### Database Management System (DBMS)

A **DBMS** is software that serves as an interface between users and the **database**.

**Examples:**
- **MySQL**
- **MongoDB**
- **Oracle Database**
- **MariaDB**

---

## Benefits of SQL and Relational Databases

### Fast Performance
**Relational databases** return massive batches of data almost instantly due to efficient storage and high processing speeds.

### Easy to Learn
**SQL** is written in plain English, making it much easier to learn than many programming languages. The readable syntax helps users focus on functions and commands.

### Reliable
**Relational databases** guarantee accuracy by enforcing a strict structure. Data must match the defined format to be inserted.

### Flexible
**SQL** provides extensive querying capabilities, allowing users to perform complex data analysis tasks efficiently.

---

## Task 4 - Database and Table Statements

### Database Statements

#### CREATE DATABASE

Create a new **database** using:
```sql
mysql> CREATE DATABASE database_name;
```

**Example:**
```sql
mysql> CREATE DATABASE thm_bookmarket_db;
```

#### SHOW DATABASES

View all existing **databases**:
```sql
mysql> SHOW DATABASES;
```

This returns a list including:
- Your created databases
- Default databases: `mysql`, `information_schema`, `performance_schema`, `sys`

#### USE DATABASE

Set the active **database** for subsequent queries:
```sql
mysql> USE thm_bookmarket_db;
```

#### DROP DATABASE

Remove a **database** (use with caution):
```sql
mysql> DROP DATABASE database_name;
```

---

### Table Statements

#### CREATE TABLE

Create a new **table** with defined **columns** and **data types**:
```sql
mysql> CREATE TABLE example_table_name (
    example_column1 data_type,
    example_column2 data_type,
    example_column3 data_type
);
```

**Example:**
```sql
mysql> CREATE TABLE book_inventory (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    book_name VARCHAR(255) NOT NULL,
    publication_date DATE
);
```

**Explanation:**
- `book_id`: **Integer** with **AUTO_INCREMENT** (automatically assigns 1, 2, 3...) and set as **PRIMARY KEY**
- `book_name`: **VARCHAR(255)** (text up to 255 characters) with **NOT NULL** (cannot be empty)
- `publication_date`: **DATE** data type

#### SHOW TABLES

List all **tables** in the active **database**:
```sql
mysql> SHOW TABLES;
```

#### DESCRIBE

View **column** details in a **table**:
```sql
mysql> DESCRIBE book_inventory;
```

**Output:**
```
+------------------+--------------+------+-----+---------+----------------+
| Field            | Type         | Null | Key | Default | Extra          |
+------------------+--------------+------+-----+---------+----------------+
| book_id          | int          | NO   | PRI | NULL    | auto_increment |
| book_name        | varchar(255) | NO   |     | NULL    |                |
| publication_date | date         | YES  |     | NULL    |                |
+------------------+--------------+------+-----+---------+----------------+
```

#### ALTER

Modify an existing **table** (add, rename, or change columns):
```sql
mysql> ALTER TABLE book_inventory
ADD page_count INT;
```

#### DROP TABLE

Remove a **table**:
```sql
mysql> DROP TABLE table_name;
```

---

## Task 5 - CRUD Operations

**CRUD** stands for **Create, Read, Update, Delete** - the four basic operations for managing data.

### INSERT (Create)

Add new **records** to a **table**:
```sql
mysql> INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```

**Example:**
```sql
mysql> INSERT INTO book_inventory (book_name, publication_date, page_count)
VALUES ('Android Security Internals', '2014-10-14', 560);
```

### SELECT (Read)

Retrieve data from a **table**:
```sql
mysql> SELECT column1, column2 FROM table_name;
```

**Select all columns:**
```sql
mysql> SELECT * FROM book_inventory;
```

**Select specific columns:**
```sql
mysql> SELECT book_name, publication_date FROM book_inventory;
```

### UPDATE (Update)

Modify existing **records**:
```sql
mysql> UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

**Example:**
```sql
mysql> UPDATE book_inventory
SET page_count = 570
WHERE book_id = 1;
```

**Warning:** Always use **WHERE** clause to avoid updating all records!

### DELETE (Delete)

Remove **records** from a **table**:
```sql
mysql> DELETE FROM table_name WHERE condition;
```

**Example:**
```sql
mysql> DELETE FROM book_inventory WHERE book_id = 1;
```

**Warning:** Without **WHERE** clause, all records will be deleted!

---

## Task 6 - Clauses

**Clauses** specify criteria for data manipulation and retrieval.

### DISTINCT Clause

Return only **unique values**, avoiding duplicates:
```sql
mysql> SELECT DISTINCT name FROM books;
```

**Without DISTINCT:**
```
| Ethical Hacking |
| Ethical Hacking |
```

**With DISTINCT:**
```
| Ethical Hacking |
```

### GROUP BY Clause

Aggregate data and group results by columns:
```sql
mysql> SELECT name, COUNT(*)
FROM books
GROUP BY name;
```

**Output:**
```
+----------------------------+----------+
| name                       | COUNT(*) |
+----------------------------+----------+
| Android Security Internals |        1 |
| Ethical Hacking            |        2 |
+----------------------------+----------+
```

### ORDER BY Clause

Sort results in **ascending** or **descending** order:

**Ascending order:**
```sql
mysql> SELECT * FROM books
ORDER BY published_date ASC;
```

**Descending order:**
```sql
mysql> SELECT * FROM books
ORDER BY published_date DESC;
```

### HAVING Clause

Filter grouped results based on a condition (used with **GROUP BY**):
```sql
mysql> SELECT name, COUNT(*)
FROM books
GROUP BY name
HAVING name LIKE '%Hack%';
```

**Output:**
```
+-----------------------+----------+
| name                  | COUNT(*) |
+-----------------------+----------+
| Car Hacker's Handbook |        1 |
| Ethical Hacking       |        2 |
+-----------------------+----------+
```

---

## Task 7 - Operators

**Operators** filter and manipulate data in **queries**.

### Logical Operators

#### LIKE Operator

Filter for specific patterns:
```sql
mysql> SELECT * FROM books
WHERE description LIKE "%guide%";
```

#### AND Operator

Return results where **all conditions** are true:
```sql
mysql> SELECT * FROM books
WHERE category = "Offensive Security" AND name = "Bug Bounty Bootcamp";
```

#### OR Operator

Return results where **at least one condition** is true:
```sql
mysql> SELECT * FROM books
WHERE name LIKE "%Android%" OR name LIKE "%iOS%";
```

#### NOT Operator

Reverse a condition (exclude results):
```sql
mysql> SELECT * FROM books
WHERE NOT description LIKE "%guide%";
```

#### BETWEEN Operator

Test if a value exists within a range:
```sql
mysql> SELECT * FROM books
WHERE id BETWEEN 2 AND 4;
```

---

### Comparison Operators

#### Equal To (=)

Check if values are equal:
```sql
mysql> SELECT * FROM books
WHERE name = "Designing Secure Software";
```

#### Not Equal To (!=)

Check if values are not equal:
```sql
mysql> SELECT * FROM books
WHERE category != "Offensive Security";
```

#### Less Than (<)

Check if value is less than:
```sql
mysql> SELECT * FROM books
WHERE published_date < "2020-01-01";
```

#### Greater Than (>)

Check if value is greater than:
```sql
mysql> SELECT * FROM books
WHERE published_date > "2020-01-01";
```

#### Less Than or Equal To (<=)

Check if value is less than or equal:
```sql
mysql> SELECT * FROM books
WHERE published_date <= "2021-11-15";
```

#### Greater Than or Equal To (>=)

Check if value is greater than or equal:
```sql
mysql> SELECT * FROM books
WHERE published_date >= "2021-11-02";
```

---

## Task 8 - Functions

**Functions** perform operations on data and return results.

### String Functions

#### CONCAT() Function

Combine multiple strings:
```sql
mysql> SELECT CONCAT(name, " is a type of ", category, " book.") AS book_info FROM books;
```

**Output:**
```
+------------------------------------------------------------------+
| book_info                                                         |
+------------------------------------------------------------------+
| Android Security Internals is a type of Defensive Security book. |
+------------------------------------------------------------------+
```

#### GROUP_CONCAT() Function

Concatenate data from multiple rows into one field:
```sql
mysql> SELECT category, GROUP_CONCAT(name SEPARATOR ", ") AS books
FROM books
GROUP BY category;
```

**Output:**
```
+--------------------+-------------------------------------------------------------+
| category           | books                                                       |
+--------------------+-------------------------------------------------------------+
| Defensive Security | Android Security Internals, Designing Secure Software       |
| Offensive Security | Bug Bounty Bootcamp, Car Hacker's Handbook, Ethical Hacking |
+--------------------+-------------------------------------------------------------+
```

#### SUBSTRING() Function

Extract part of a string:
```sql
mysql> SELECT SUBSTRING(published_date, 1, 4) AS published_year FROM books;
```

**Output:**
```
+----------------+
| published_year |
+----------------+
| 2014           |
| 2021           |
+----------------+
```

#### LENGTH() Function

Return the number of characters in a string:
```sql
mysql> SELECT LENGTH(name) AS name_length FROM books;
```

**Output:**
```
+-------------+
| name_length |
+-------------+
|          26 |
|          19 |
+-------------+
```

---

### Aggregate Functions

#### COUNT() Function

Count the number of records:
```sql
mysql> SELECT COUNT(*) AS total_books FROM books;
```

**Output:**
```
+-------------+
| total_books |
+-------------+
|           5 |
+-------------+
```

#### SUM() Function

Calculate the sum of values in a column:
```sql
mysql> SELECT SUM(price) AS total_price FROM books;
```

#### MAX() Function

Find the maximum value:
```sql
mysql> SELECT MAX(published_date) AS latest_book FROM books;
```

**Output:**
```
+-------------+
| latest_book |
+-------------+
| 2021-12-21  |
+-------------+
```

#### MIN() Function

Find the minimum value:
```sql
mysql> SELECT MIN(published_date) AS earliest_book FROM books;
```

**Output:**
```
+---------------+
| earliest_book |
+---------------+
| 2014-10-14    |
+---------------+
```

---

## Task 9 - Conclusion

This room covered:

- **Databases** are organized collections of data that are easily accessible and can be manipulated or analyzed
- Two primary types: **Relational databases** (structured data) and **Non-relational databases** (non-tabular format)
- **Relational databases** use **tables**, **columns**, and **rows**
- **Primary keys** ensure records are unique; **foreign keys** create relationships between tables
- **SQL** is an easy-to-learn language for interacting with **relational databases**
- **Database and Table statements** create and manipulate databases and tables
- **CRUD Operations** (INSERT, SELECT, UPDATE, DELETE) manage data
- **Clauses** define how data is retrieved, filtered, sorted, or grouped
- **Operators** and **functions** help filter and manipulate data efficiently
