Here’s your complete **🔹 Day 4 – Read, Update, Delete** PostgreSQL (psql) note with clear explanations, practical examples, and practice questions — focused on **SELECT**, **UPDATE**, and **DELETE**.

---

## 🔹 **Day 4 – Read, Update, Delete**

---

### 🎥 Topics:

---

### ✅ **43:52 – SELECT**

The `SELECT` command is used to **read** data from a table.

---

#### 📌 Basic Usage:

```sql
SELECT * FROM student;
```

* `*` selects **all columns**.
* You can also select specific columns:

```sql
SELECT name, age FROM student;
```

---

#### 📌 Filtering with `WHERE`:

```sql
SELECT * FROM student WHERE grade = 'A';
```

```sql
SELECT name, age FROM student WHERE age > 18;
```

---

#### 📌 Sorting Results:

```sql
SELECT * FROM student ORDER BY age DESC;
```

---

### ✅ **45:21 – UPDATE**

The `UPDATE` command is used to **modify existing records**.

---

#### 📌 Syntax:

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

---

#### 📌 Example:

```sql
UPDATE student
SET grade = 'B'
WHERE name = 'Diya';
```

> ⚠️ Always use `WHERE` to avoid updating all rows by mistake.

---

#### 📌 View changes:

```sql
SELECT * FROM student WHERE name = 'Diya';
```

---

### ✅ **48:16 – DELETE**

The `DELETE` command is used to **remove records** from a table.

---

#### 📌 Syntax:

```sql
DELETE FROM table_name
WHERE condition;
```

---

#### 📌 Example:

```sql
DELETE FROM student
WHERE name = 'Rohan';
```

---

#### ⚠️ Danger of Missing `WHERE`:

```sql
-- This deletes ALL records from the student table
DELETE FROM student;
```

Always use a `WHERE` clause unless you're sure you want to delete everything.

---

## 💻 Practice Tasks (PSQL Only)

---

### ✅ 1. Read All Records

```sql
SELECT * FROM student;
```

---

### ✅ 2. Read Students Aged 18+

```sql
SELECT * FROM student WHERE age >= 18;
```

---

### ✅ 3. Update Grade for a Student

```sql
UPDATE student
SET grade = 'A'
WHERE name = 'Kabir';
```

---

### ✅ 4. Delete a Student Record

```sql
DELETE FROM student
WHERE name = 'Meera';
```

---

### ✅ 5. Verify Updates/Deletions

```sql
SELECT * FROM student;
```

---

## 📘 Practice Questions (PostgreSQL Only)

---

### Q1. Write a query to select only the `name` and `email` of students with grade ‘A’.

```sql
SELECT name, email FROM student WHERE grade = 'A';
```

---

### Q2. Update the age of student `Sneha` to 19.

```sql
UPDATE student
SET age = 19
WHERE name = 'Sneha';
```

---

### Q3. Delete all students who have grade 'C'.

```sql
DELETE FROM student
WHERE grade = 'C';
```

---

### Q4. Show students sorted by age in descending order.

```sql
SELECT * FROM student ORDER BY age DESC;
```

---

### Q5. What happens if you run UPDATE without WHERE?

> All rows will be updated. Example:

```sql
UPDATE student SET grade = 'F';
```

This will change the grade of every student to 'F'.

---

Let me know if you’d like to continue with **Day 5: Primary Key, Auto Increment, Aliases**, or want all notes compiled in a **PDF format** for download.
