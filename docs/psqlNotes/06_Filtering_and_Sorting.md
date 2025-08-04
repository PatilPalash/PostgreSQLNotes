Here’s a complete breakdown for **🔹 Day 6 – Filtering & Sorting** with **clear explanations, psql commands, and practice questions** using your `student` and `employee` tables in **PostgreSQL**.

---

## 🔹 **Day 6 – Filtering & Sorting**

---

### 🎥 Topics:

---

### ✅ **01:17:15 – WHERE, ORDER BY, DISTINCT, LIMIT, LIKE**

---

### ✅ 1. `WHERE` – Filter Rows

Use `WHERE` to filter records based on conditions.

```sql
-- Students older than 18
SELECT * FROM student WHERE age > 18;

-- Employees with salary above 50000
SELECT * FROM employee WHERE salary > 50000;
```

📌 **Comparison Operators**:

* `=` equal
* `!=` or `<>` not equal
* `<`, `<=`, `>`, `>=`

---

### ✅ 2. `ORDER BY` – Sort Records

Sort the output by one or more columns.

```sql
-- Students sorted by age
SELECT * FROM student ORDER BY age ASC;

-- Employees sorted by salary (highest first)
SELECT * FROM employee ORDER BY salary DESC;
```

📌 Add `NULLS LAST` or `NULLS FIRST` if needed:

```sql
ORDER BY join_date DESC NULLS LAST;
```

---

### ✅ 3. `DISTINCT` – Remove Duplicates

Returns only **unique values**.

```sql
-- Unique grades
SELECT DISTINCT grade FROM student;

-- Unique employee statuses
SELECT DISTINCT is_active FROM employee;
```

---

### ✅ 4. `LIMIT` – Restrict Number of Rows

Limit the number of results returned.

```sql
-- Top 3 highest paid employees
SELECT * FROM employee ORDER BY salary DESC LIMIT 3;

-- First 5 students
SELECT * FROM student LIMIT 5;
```

---

### ✅ 5. `LIKE` – Pattern Matching (Case-Sensitive)

Use `LIKE` with `%` and `_` for matching patterns.

| Symbol | Meaning                  |
| ------ | ------------------------ |
| `%`    | Any number of characters |
| `_`    | A single character       |

```sql
-- Students with names starting with 'S'
SELECT * FROM student WHERE name LIKE 'S%';

-- Employees with email ending in 'example.com'
SELECT * FROM employee WHERE email LIKE '%@example.com';
```

🔹 Use `ILIKE` for **case-insensitive** match:

```sql
SELECT * FROM student WHERE name ILIKE 's%';
```

---

## 💻 Practice Queries (Use on `student` or `employee`)

---

### ✅ 1. Filter students who are 18+ years old.

```sql
SELECT * FROM student WHERE age >= 18;
```

---

### ✅ 2. Find employees with salary below 50,000.

```sql
SELECT * FROM employee WHERE salary < 50000;
```

---

### ✅ 3. List unique grades from student table.

```sql
SELECT DISTINCT grade FROM student;
```

---

### ✅ 4. Show top 2 youngest students.

```sql
SELECT * FROM student ORDER BY age ASC LIMIT 2;
```

---

### ✅ 5. Find employees whose name starts with 'R'.

```sql
SELECT * FROM employee WHERE name LIKE 'R%';
```

---

### ✅ 6. Find students whose names have exactly 5 letters.

```sql
SELECT * FROM student WHERE name LIKE '_____';
```

---

## 📘 Practice Questions (PSQL Only)

---

### Q1. How would you get only distinct `is_active` values from `employee`?

```sql
SELECT DISTINCT is_active FROM employee;
```

---

### Q2. What is the difference between `LIKE` and `ILIKE`?

> `LIKE` is case-sensitive; `ILIKE` is case-insensitive.

---

### Q3. Get the highest paid employee.

```sql
SELECT * FROM employee ORDER BY salary DESC LIMIT 1;
```

---

### Q4. List students whose name ends with 'a'.

```sql
SELECT * FROM student WHERE name LIKE '%a';
```

---

### Q5. Get the first 3 employees who joined most recently.

```sql
SELECT * FROM employee ORDER BY join_date DESC LIMIT 3;
```

---

Let me know if you want **Day 7: Functions, Expressions, Aggregates (e.g., COUNT, SUM, AVG)** or if you'd like a **PDF file with all 6 days' notes and psql practice**.
