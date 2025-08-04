Here’s your **📘 Day 5 – Primary Key, Auto Increment, Alias** study notes with complete explanation, syntax for **MySQL** and **PostgreSQL**, and hands-on practice questions.

---

## 📘 Day 5 – Primary Key, Auto Increment, Alias

🎥 Watch: **54:21 – 01:13:23**

---

## 🎯 Topics Covered:

1. `PRIMARY KEY` – unique row identifier
2. `AUTO_INCREMENT` (MySQL) / `SERIAL` (PostgreSQL) – auto-generate ID
3. `AS` (Alias) – rename columns/tables in results

---

## 🧠 Concepts Explained

---

### 🔹 1. `PRIMARY KEY`

A **Primary Key** is a unique identifier for each row in a table.

#### ✅ Features:

* Must be **unique**
* Cannot be **NULL**
* One table can only have **one primary key**, but it can span multiple columns (composite key)

#### ✅ Syntax:

```sql
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50)
);
```

✅ Same in **MySQL** and **PostgreSQL**

---

### 🔹 2. `AUTO_INCREMENT` / `SERIAL`

Used to auto-generate unique ID values.

#### ✅ MySQL Syntax:

```sql
CREATE TABLE students (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(50)
);
```

#### ✅ PostgreSQL Syntax:

```sql
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50)
);
```

> 💡 `SERIAL` in PostgreSQL auto-increments and creates an internal sequence.
> 🔒 You **don’t insert** a value manually into an auto-increment field.

---

### 🔹 3. `AS` – Alias

Used to rename a **column** or **table** temporarily in the result.

#### ✅ Syntax:

```sql
SELECT column_name AS alias_name
FROM table_name;

SELECT s.name AS student_name
FROM students AS s;
```

> Aliases improve readability or formatting in results.

✅ Works the same in **MySQL** and **PostgreSQL**

---

## 🧪 Practice Tasks

### ✅ MySQL & PostgreSQL Practice

#### Step 1: Create table with auto-increment ID

```sql
-- MySQL
CREATE TABLE books (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(100),
  author VARCHAR(100)
);

-- PostgreSQL
CREATE TABLE books (
  id SERIAL PRIMARY KEY,
  title VARCHAR(100),
  author VARCHAR(100)
);
```

#### Step 2: Insert data (no need to insert `id`)

```sql
INSERT INTO books (title, author) VALUES
('Wings of Fire', 'A.P.J Abdul Kalam'),
('The Alchemist', 'Paulo Coelho'),
('Harry Potter', 'J.K. Rowling');
```

#### Step 3: Use alias in queries

```sql
-- Alias for column
SELECT title AS book_title, author AS written_by FROM books;

-- Alias for table
SELECT b.title FROM books AS b;
```

---

## ❓ Practice Questions

### 💡 Conceptual

1. Can a table have more than one primary key?
2. What happens if you try to insert a duplicate value into a primary key column?
3. What is the difference between `AUTO_INCREMENT` and `SERIAL`?
4. Why do we use aliases in SQL?

---

### 🧠 SQL Challenges

1. Create a `students` table with:

   * `id` (auto-increment & primary key)
   * `name`, `age`
2. Insert 3–4 students without specifying `id`
3. Use alias to:

   * Rename `name` column to `student_name`
   * Rename table to `s` in a `SELECT` query
4. Try inserting a row **with existing id** and see what error you get

---

## ⚙️ Syntax Cheatsheet

| Task              | MySQL                            | PostgreSQL  |
| ----------------- | -------------------------------- | ----------- |
| Auto-increment ID | `id INT AUTO_INCREMENT`          | `id SERIAL` |
| Primary Key       | `id PRIMARY KEY`                 | Same        |
| Column Alias      | `SELECT name AS student_name`    | Same        |
| Table Alias       | `FROM students AS s`             | Same        |
| Insert without ID | `INSERT INTO table (col1, col2)` | Same        |

---

## 🧑‍💻 Tools for Practice

* **MySQL Workbench**
* **pgAdmin** or **psql shell**
* **Online playground**: [DB Fiddle](https://www.db-fiddle.com/)

---

Here are clear and complete answers to your SQL questions:

---

### **1. Can a table have more than one primary key?**

❌ **No**, a table **cannot have more than one primary key**.

* But a primary key can be **composite**, meaning it includes **multiple columns**.
* The **primary key must be unique and not null**, and only **one** such constraint is allowed per table.

🔹 Example:

```sql
PRIMARY KEY (order_id, product_id)  -- Composite primary key
```

---

### **2. What happens if you try to insert a duplicate value into a primary key column?**

* ❌ The database will **reject the insert** and throw an error because **primary keys must be unique**.

🔹 Example error in MySQL:

```
ERROR 1062 (23000): Duplicate entry '101' for key 'PRIMARY'
```

👉 This helps maintain **data integrity** by ensuring no two rows share the same primary key.

---

### **3. What is the difference between `AUTO_INCREMENT` and `SERIAL`?**

| Feature              | `AUTO_INCREMENT` (MySQL)                      | `SERIAL` (PostgreSQL)                            |
| -------------------- | --------------------------------------------- | ------------------------------------------------ |
| **Purpose**          | Automatically generates unique integer values | Automatically generates unique integer values    |
| **Usage**            | Used with `PRIMARY KEY` or unique fields      | Shorthand for `INTEGER` + `SEQUENCE` + `DEFAULT` |
| **Syntax**           | `id INT AUTO_INCREMENT`                       | `id SERIAL`                                      |
| **Database support** | MySQL, MariaDB                                | PostgreSQL                                       |

🔹 **Note:** In MySQL, `SERIAL` is an alias for `BIGINT UNSIGNED NOT NULL AUTO_INCREMENT UNIQUE`.

---

### \*\*4. Why do we use **aliases** in SQL?

* **Aliases** give **temporary names** to:

  * Columns
  * Tables

✅ This improves **readability**, simplifies complex queries, and helps in **joining tables or renaming output**.

🔹 Column Alias Example:

```sql
SELECT first_name AS name FROM employees;
```

🔹 Table Alias Example:

```sql
SELECT e.name, d.department_name
FROM employees AS e
JOIN departments AS d ON e.dept_id = d.id;
```

---

Let me know if you want a mini test or real-world examples using these concepts!
