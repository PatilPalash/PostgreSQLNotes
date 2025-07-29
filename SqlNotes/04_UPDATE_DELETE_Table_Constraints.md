Here's your full **📘 Day 4 – UPDATE, DELETE, Table Constraints** study guide with explanations, MySQL + PostgreSQL syntax, practice questions, and hands-on examples.

---

## 📘 Day 4 – UPDATE, DELETE, Table Constraints

🎥 Watch: **37:40 – 54:21**

---

## 🎯 Topics Covered:

1. `UPDATE` – modify existing data
2. `DELETE` – remove specific rows
3. `DROP TABLE` – delete entire table
4. `NOT NULL` constraint – enforce non-empty columns

---

## 🧠 Concepts Explained (MySQL + PostgreSQL)

---

### 🔹 1. `UPDATE` – Modify Records

Used to change values in existing rows.

#### ✅ Syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

#### 🧾 Example:

```sql
UPDATE students
SET city = 'Hyderabad'
WHERE id = 3;
```

> ⚠️ Always use `WHERE` to avoid updating **all rows** by mistake.

---

### 🔹 2. `DELETE` – Remove Rows

Used to delete rows from a table.

#### ✅ Syntax:

```sql
DELETE FROM table_name
WHERE condition;
```

#### 🧾 Example:

```sql
DELETE FROM students
WHERE city = 'Mumbai';
```

> 🔴 If you skip `WHERE`, **all rows** will be deleted.

---

### 🔹 3. `DROP TABLE` – Delete Entire Table

Completely removes a table from the database.

#### ✅ Syntax:

```sql
DROP TABLE table_name;
```

#### 🧾 Example:

```sql
DROP TABLE students;
```

> This operation **cannot be undone** and deletes all structure + data.

---

### 🔹 4. `NOT NULL` – Constraint

Prevents null (empty) values in specific columns.

#### ✅ Syntax (while creating a table):

```sql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(100) NOT NULL
);
```

> You **cannot insert** or update a row that leaves a NOT NULL field empty.

---

## 🧪 Practice Tasks

### ✅ Step-by-step SQL (MySQL or PostgreSQL)

#### 1. Update a value:

```sql
-- Update student name
UPDATE students
SET name = 'Arjun Reddy'
WHERE id = 3;
```

#### 2. Delete a record:

```sql
-- Delete student from Delhi
DELETE FROM students
WHERE city = 'Delhi';
```

#### 3. Add a new table with NOT NULL:

```sql
CREATE TABLE employees (
  emp_id INT PRIMARY KEY,
  emp_name VARCHAR(50) NOT NULL,
  department VARCHAR(50)
);

-- Try inserting a row with NULL name (will fail)
-- INSERT INTO employees (emp_id, emp_name) VALUES (1, NULL); ❌
```

#### 4. Drop table (be careful!):

```sql
DROP TABLE employees;
```

---

## ❓ Practice Questions

### 💡 Conceptual

1. What happens if you run `UPDATE` without `WHERE`?
2. Can a `NOT NULL` column ever contain `NULL`? What error do you get if you try?
3. What's the difference between `DELETE` and `DROP`?
4. Why is `WHERE` clause important with both `UPDATE` and `DELETE`?

---

### 🧠 SQL Challenge (MySQL or PostgreSQL)

1. Update city of student named 'Ravi' to 'Chennai'
2. Delete all students with age less than 22
3. Create a `departments` table with:

```sql
CREATE TABLE departments (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) NOT NULL,
  location VARCHAR(50)
);
```

4. Insert 2–3 rows. Then delete one department using `WHERE`.

---

## ⚙️ Syntax Cheatsheet

| Task           | MySQL Syntax                      | PostgreSQL Syntax (psql) |
| -------------- | --------------------------------- | ------------------------ |
| Update Row     | `UPDATE table SET ... WHERE ...;` | Same                     |
| Delete Row     | `DELETE FROM table WHERE ...;`    | Same                     |
| Drop Table     | `DROP TABLE table_name;`          | Same                     |
| Add NOT NULL   | In `CREATE` or `ALTER TABLE`      | Same                     |
| List Tables    | `SHOW TABLES;`                    | `\dt`                    |
| Describe Table | `DESCRIBE table_name;`            | `\d table_name`          |

---

## 🔧 Tips for Safety

* **Use `SELECT` before `UPDATE` or `DELETE`** to preview rows you're targeting:

```sql
SELECT * FROM students WHERE city = 'Pune'; -- preview
UPDATE students SET city = 'Goa' WHERE city = 'Pune'; -- modify
```

* Use `IF EXISTS` with DROP:

```sql
DROP TABLE IF EXISTS students;
```

---

Here are complete and concise answers to your SQL questions:

---

### **1. What happens if you run `UPDATE` without `WHERE`?**

* Running an `UPDATE` statement **without a `WHERE` clause** will:
  ✅ **Update all rows** in the table.

🔹 Example:

```sql
UPDATE employees SET salary = 50000;
```

👉 This sets the `salary` to `50000` for **every employee** in the table — which may be a critical mistake.

---

### **2. Can a `NOT NULL` column ever contain `NULL`? What error do you get if you try?**

* ❌ **No**, a column defined with `NOT NULL` **cannot store NULL values**.
* If you try to insert or update it with `NULL`, you'll get an error.

🔹 Example error in MySQL:

```
ERROR 1048 (23000): Column 'name' cannot be null
```

---

### **3. What’s the difference between `DELETE` and `DROP`?**

| Operation               | `DELETE`                                     | `DROP`                                          |
| ----------------------- | -------------------------------------------- | ----------------------------------------------- |
| **Action**              | Removes rows (data) from a table             | Removes the **entire table** (structure + data) |
| **Can use WHERE?**      | ✅ Yes                                        | ❌ No (`DROP` removes the object entirely)       |
| **Undo?**               | Can be rolled back (if inside a transaction) | Cannot be rolled back (permanent)               |
| **Table Exists After?** | ✅ Yes, table remains empty                   | ❌ No, table no longer exists                    |

---

### **4. Why is the `WHERE` clause important with both `UPDATE` and `DELETE`?**

* The `WHERE` clause ensures that **only specific rows** are affected.
* Without it:

  * `UPDATE` will change **all rows**
  * `DELETE` will remove **all data**

🔴 **Risk:** Running `UPDATE` or `DELETE` without `WHERE` can **accidentally affect the entire table**, leading to **data loss or corruption**.

🔹 Example:

```sql
-- Dangerous without WHERE
DELETE FROM orders;          -- Deletes all orders!
UPDATE products SET price = 0;  -- Sets price to 0 for all products!
```

✅ **Always double-check your WHERE clause** before running such commands.

---

