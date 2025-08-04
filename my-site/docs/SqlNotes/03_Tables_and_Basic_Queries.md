Absolutely! Here's your detailed **📘 Day 3 – Tables & Basic Queries** note for both **MySQL** and **PostgreSQL (psql)** including concepts, syntax, practice exercises, and common questions.

---

## 📘 Day 3 – Tables & Basic Queries

🎥 Watch: **23:28 – 37:40**

---

## 🎯 Topics Covered:

1. `CREATE TABLE`
2. `INSERT INTO`
3. `SELECT`
4. `WHERE` clause

---

## 🧠 Concepts Explained (with MySQL + PostgreSQL Syntax)

---

### 🔹 1. `CREATE TABLE`

Used to define the structure of a new table.

#### ✅ Basic Syntax:

```sql
CREATE TABLE table_name (
  column1 datatype constraints,
  column2 datatype constraints,
  ...
);
```

#### 🧾 Example:

```sql
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT,
  city VARCHAR(50)
);
```

✅ **Works the same** in **MySQL** and **PostgreSQL**.

---

### 🔹 2. `INSERT INTO`

Used to add rows into the table.

#### ✅ Syntax:

```sql
INSERT INTO table_name (col1, col2, col3)
VALUES (val1, val2, val3);
```

#### 🧾 Example:

```sql
INSERT INTO students (id, name, age, city)
VALUES 
(1, 'Ravi', 21, 'Pune'),
(2, 'Sneha', 22, 'Mumbai'),
(3, 'Arjun', 23, 'Delhi'),
(4, 'Priya', 20, 'Bangalore'),
(5, 'Aman', 24, 'Pune');
```

---

### 🔹 3. `SELECT`

Used to retrieve data from one or more columns.

#### ✅ Syntax:

```sql
SELECT * FROM table_name;
SELECT column1, column2 FROM table_name;
```

#### 🧾 Example:

```sql
SELECT name, city FROM students;
```

---

### 🔹 4. `WHERE` Clause

Used to filter records based on a condition.

#### ✅ Syntax:

```sql
SELECT * FROM table_name
WHERE condition;
```

#### 🧾 Examples:

```sql
SELECT * FROM students WHERE city = 'Pune';
SELECT name FROM students WHERE age > 22;
```

✅ Same syntax in **MySQL** and **PostgreSQL**.

---

## 🧪 Practice Tasks

### ✅ Step-by-step in **MySQL or PostgreSQL**:

```sql
-- Step 1: Create students table
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT,
  city VARCHAR(50)
);

-- Step 2: Insert 5 rows
INSERT INTO students (id, name, age, city) VALUES
(1, 'Ravi', 21, 'Pune'),
(2, 'Sneha', 22, 'Mumbai'),
(3, 'Arjun', 23, 'Delhi'),
(4, 'Priya', 20, 'Bangalore'),
(5, 'Aman', 24, 'Pune');

-- Step 3: View all records
SELECT * FROM students;

-- Step 4: Apply filters using WHERE
SELECT * FROM students WHERE city = 'Pune';
SELECT name FROM students WHERE age < 23;
SELECT * FROM students WHERE name = 'Priya';
```

> 💡 PostgreSQL Tip: Always use semicolons (`;`) at the end of SQL statements in `psql`.

---

## ❓ Practice Questions

### 💡 Conceptual

1. What is the purpose of a `PRIMARY KEY` in a table?
2. What does the `WHERE` clause do in SQL?
3. Can you insert multiple rows in a single `INSERT` command?
4. What happens if you insert a row with a duplicate primary key?

---

### 🧠 SQL Exercise Prompts

1. Create a table `books` with columns: `id (int)`, `title (varchar)`, `author (varchar)`, `year (int)`
2. Insert 4–5 records into `books`
3. Fetch:

   * All books
   * Books written after 2010
   * Only titles of books by author "R.K. Narayan"

---

## ⚙️ Syntax Cheatsheet: MySQL vs PostgreSQL

| Task           | MySQL Syntax                         | PostgreSQL Syntax (psql) |
| -------------- | ------------------------------------ | ------------------------ |
| Create Table   | `CREATE TABLE ...`                   | Same                     |
| Insert Rows    | `INSERT INTO ... VALUES (...);`      | Same                     |
| Select Rows    | `SELECT * FROM table_name;`          | Same                     |
| Filter (WHERE) | `SELECT * FROM ... WHERE condition;` | Same                     |
| List Tables    | `SHOW TABLES;`                       | `\dt`                    |
| Describe Table | `DESCRIBE table_name;`               | `\d table_name`          |

---

## 🧑‍💻 Tools for Practice

* **MySQL Workbench** for GUI
* **pgAdmin** or **psql CLI** for PostgreSQL
* **Online playgrounds**:

  * [DB Fiddle](https://www.db-fiddle.com/)
  * [SQL Fiddle](http://sqlfiddle.com/)

---

Here are clear answers to your SQL-related questions:

---

### **1. What is the purpose of a `PRIMARY KEY` in a table?**

* A **`PRIMARY KEY`** uniquely identifies each row in a table.
* It ensures:

  * **Uniqueness** – No duplicate values allowed.
  * **Non-nullability** – Cannot be NULL.
* It can be a single column or a combination of multiple columns (composite key).

🔹 Example:

```sql
CREATE TABLE students (
  student_id INT PRIMARY KEY,
  name VARCHAR(100)
);
```

---

### **2. What does the `WHERE` clause do in SQL?**

* The **`WHERE` clause** filters records based on a given condition.
* It is used in `SELECT`, `UPDATE`, `DELETE`, and sometimes `INSERT ... SELECT`.

🔹 Example:

```sql
SELECT * FROM employees WHERE department = 'HR';
```

👉 Returns only rows where the `department` is `'HR'`.

---

### **3. Can you insert multiple rows in a single `INSERT` command?**

✅ **Yes**, you can insert multiple rows using a single `INSERT` statement.

🔹 Example:

```sql
INSERT INTO products (product_id, name, price)
VALUES 
  (101, 'Pen', 10.0),
  (102, 'Pencil', 5.0),
  (103, 'Eraser', 3.0);
```

👉 This inserts **three rows** at once.

---

### **4. What happens if you insert a row with a duplicate primary key?**

❌ You will get an **error** because the `PRIMARY KEY` must be **unique**.

* In **MySQL**, you'll see:

  ```
  ERROR 1062 (23000): Duplicate entry '...' for key 'PRIMARY'
  ```

🔹 To avoid this:

* Use `INSERT IGNORE` (skips duplicates)
* Or `INSERT ... ON DUPLICATE KEY UPDATE` (updates existing row)

---

Let me know if you want MCQs, practice exercises, or a quick quiz for revision!
