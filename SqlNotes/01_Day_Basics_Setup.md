**📘 Day 1 – MySQL Basics & Setup: Detailed Notes + Practice**

---

### 🎯 Topics Covered (00:00 – 14:05 of the video):

1. **What is a Database (DB)?**
2. **What is DBMS (Database Management System)?**
3. **What is RDBMS (Relational DBMS)?**
4. **SQL vs MySQL**
5. **Installation of MySQL & Workbench**
6. **Creating a Sample Database**

---

## 🧠 Concepts Explained

---

### 1. **What is a Database (DB)?**

* A **database** is an organized collection of data that is stored and accessed electronically.
* Examples: Contact list, Library records, Online shopping data.

#### ✅ Features:

* Stores **structured data**
* Enables **easy retrieval and modification**
* Can be small (like a file) or massive (like Facebook's DB)

---

### 2. **What is DBMS?**

* **DBMS** is a software tool used to **create**, **manage**, and **manipulate** databases.

#### ✅ Functions:

* Data insertion, deletion, updating
* User access control
* Backup and recovery

#### ✅ Examples:

* MySQL, Oracle DB, Microsoft SQL Server, SQLite

---

### 3. **What is RDBMS?**

* **Relational DBMS** is a type of DBMS that stores data in **tables** (rows and columns).
* Each table can have **relationships** (foreign keys) with other tables.

#### ✅ Features:

* Based on **E.F. Codd's Relational Model**
* Supports **ACID properties** (Atomicity, Consistency, Isolation, Durability)
* Enforces **data integrity**

#### ✅ Examples:

* MySQL, PostgreSQL, Oracle, MS SQL Server

---

### 4. **SQL vs MySQL**

| SQL                                       | MySQL                           |
| ----------------------------------------- | ------------------------------- |
| Structured Query Language                 | RDBMS tool based on SQL         |
| A language for interacting with databases | A software that implements SQL  |
| Created by IBM                            | Developed by Oracle Corporation |
| Used in various DBMSs                     | One specific RDBMS              |

---

### 5. **MySQL Installation Overview**

* Install **MySQL Server** and **MySQL Workbench**
* Setup user/password (default: root)
* MySQL Workbench is a GUI for writing SQL commands

🔗 [Installation Guide](https://dev.mysql.com/downloads/installer/) (if needed)

---

### 6. **Create Sample Database**

✅ Open MySQL Workbench > Login > Write this SQL:

```sql
CREATE DATABASE sample_db;
USE sample_db;

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50)
);

INSERT INTO students VALUES (1, 'Ravi', 'Pune'), (2, 'Sneha', 'Mumbai');
```

🧾 Now run:

```sql
SELECT * FROM students;
```

---

## ✅ Practice Questions

### 🎯 Conceptual (Theory)

1. What is the difference between DBMS and RDBMS?
2. List 3 advantages of using a database over storing data in Excel.
3. Explain how tables are related in RDBMS.

---

### 🔍 SQL Practice

1. Create a database called `school_db`.
2. Inside `school_db`, create a table called `teachers`:

```sql
CREATE TABLE teachers (
    id INT,
    name VARCHAR(100),
    subject VARCHAR(50)
);
```

3. Insert 2 records.
4. Select all records using:

```sql
SELECT * FROM teachers;
```

---

## 🧑‍💻 Suggested Tools for Practice:

* **MySQL Workbench** (GUI)
* **DBeaver** (alternative)
* **DB Fiddle** (online playground): [https://www.db-fiddle.com/](https://www.db-fiddle.com/)

---

Would you like a PDF of this note or a printable sheet with syntax + practice blocks?
