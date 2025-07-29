Here’s your complete **🔹 Day 8 – Aggregate Functions & GROUP BY** note for PostgreSQL (psql), including detailed explanations, real examples, and hands-on practice — using the `employee` and `student` tables.

---

## 🔹 **Day 8 – Aggregate Functions & GROUP BY**

---

### 🎥 Topics:

* **01:38:56** – COUNT, MIN, MAX, AVG
* **01:43:19** – GROUP BY

---

## ✅ 1. **Aggregate Functions**

Aggregate functions **perform calculations on groups of rows** and return a single value.

| Function  | Description                   | Example       |
| --------- | ----------------------------- | ------------- |
| `COUNT()` | Total number of rows          | `COUNT(*)`    |
| `MIN()`   | Minimum value in a column     | `MIN(salary)` |
| `MAX()`   | Maximum value in a column     | `MAX(age)`    |
| `AVG()`   | Average of numeric column     | `AVG(salary)` |
| `SUM()`   | Total sum of a numeric column | `SUM(salary)` |

---

### 📌 Examples:

```sql
-- Total number of students
SELECT COUNT(*) FROM student;

-- Highest salary
SELECT MAX(salary) FROM employee;

-- Average age of students
SELECT AVG(age) FROM student;

-- Sum of all salaries
SELECT SUM(salary) FROM employee;
```

---

## ✅ 2. **GROUP BY Clause**

`GROUP BY` is used to **group rows with the same value** in a column and apply aggregate functions to each group.

---

### 📌 Syntax:

```sql
SELECT column, AGG_FUNC(column2)
FROM table
GROUP BY column;
```

---

### 📌 Examples:

```sql
-- Count of students by grade
SELECT grade, COUNT(*) 
FROM student
GROUP BY grade;

-- Average salary by employee active status
SELECT is_active, AVG(salary)
FROM employee
GROUP BY is_active;

-- Average salary by joining year
SELECT EXTRACT(YEAR FROM join_date) AS join_year, AVG(salary)
FROM employee
GROUP BY join_year;
```

---

### 🛑 Note:

* You **must use `GROUP BY`** when selecting non-aggregated columns along with aggregate functions.
* Use `ORDER BY` to sort grouped results.

```sql
-- Sorted average salary by is_active
SELECT is_active, AVG(salary)
FROM employee
GROUP BY is_active
ORDER BY AVG(salary) DESC;
```

---

## 💻 Practice: Use on `employee` table

---

### ✅ 1. Average Salary by Active Status

```sql
SELECT is_active, AVG(salary)
FROM employee
GROUP BY is_active;
```

---

### ✅ 2. Count of Employees by Join Year

```sql
SELECT EXTRACT(YEAR FROM join_date) AS year_joined, COUNT(*)
FROM employee
GROUP BY year_joined;
```

---

### ✅ 3. Total Salary Paid per Active Status

```sql
SELECT is_active, SUM(salary)
FROM employee
GROUP BY is_active;
```

---

### ✅ 4. Highest Salary by Active Status

```sql
SELECT is_active, MAX(salary)
FROM employee
GROUP BY is_active;
```

---

## 📘 Practice Questions (PostgreSQL Only)

---

### Q1. How many students are there in each grade?

```sql
SELECT grade, COUNT(*) FROM student GROUP BY grade;
```

---

### Q2. What is the average age of students?

```sql
SELECT AVG(age) FROM student;
```

---

### Q3. What’s the total salary of all active employees?

```sql
SELECT SUM(salary) FROM employee WHERE is_active = TRUE;
```

---

### Q4. Find min and max salary per active status.

```sql
SELECT is_active, MIN(salary), MAX(salary)
FROM employee
GROUP BY is_active;
```

---

### Q5. How many employees joined each year?

```sql
SELECT EXTRACT(YEAR FROM join_date) AS year, COUNT(*)
FROM employee
GROUP BY year;
```

---

## Summary:

* ✅ Use aggregate functions to calculate stats from columns
* ✅ Use `GROUP BY` to group and summarize by categories
* ✅ Combine with `ORDER BY` for better presentation

---

Let me know if you'd like:

* 🔜 **Day 9: HAVING Clause, Filtering Groups, Aliases**
* 📄 A **PDF/DOCX file of Days 1–8 Notes + Practice Sets** for revision!
