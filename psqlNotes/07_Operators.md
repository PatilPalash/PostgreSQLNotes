Here’s your complete **🔹 Day 7 – Operators** study note, covering **Relational and Logical Operators** in **PostgreSQL (psql)** with clear examples, explanations, and practice questions — all focused on using them in `WHERE` clauses for filtering data.

---

## 🔹 **Day 7 – Operators**

---

### 🎥 Topic:

**🕐 01:25:25 – Relational & Logical Operators**

---

## ✅ 1. **Relational Operators**

These compare values and return `TRUE` or `FALSE`. Mostly used in the `WHERE` clause.

| Operator | Meaning               | Example           |
| -------- | --------------------- | ----------------- |
| `=`      | Equal to              | `age = 18`        |
| `!=`     | Not equal to          | `grade != 'A'`    |
| `<`      | Less than             | `salary < 50000`  |
| `>`      | Greater than          | `age > 17`        |
| `<=`     | Less than or equal    | `age <= 19`       |
| `>=`     | Greater than or equal | `salary >= 40000` |

---

## ✅ 2. **Logical Operators**

Used to combine multiple conditions in `WHERE` clause.

| Operator | Description                         | Example                      |
| -------- | ----------------------------------- | ---------------------------- |
| `AND`    | All conditions must be true         | `age >= 18 AND grade = 'A'`  |
| `OR`     | At least one condition must be true | `grade = 'A' OR grade = 'B'` |
| `NOT`    | Reverses the result of a condition  | `NOT (grade = 'F')`          |

---

## 💻 PSQL Examples Using `student` and `employee` Tables

---

### ✅ Relational Operators:

```sql
-- Students aged 18
SELECT * FROM student WHERE age = 18;

-- Employees with salary not equal to 50000
SELECT * FROM employee WHERE salary != 50000;
```

---

### ✅ Logical Operators:

```sql
-- Students who are 18 and have grade A
SELECT * FROM student WHERE age = 18 AND grade = 'A';

-- Employees with salary > 50000 OR joined today
SELECT * FROM employee 
WHERE salary > 50000 OR join_date = CURRENT_DATE;

-- Students NOT in grade 'C'
SELECT * FROM student WHERE NOT grade = 'C';
```

---

## 🔄 Combined Operators Example

```sql
-- Employees active and have salary more than 40000
SELECT * FROM employee
WHERE is_active = TRUE AND salary > 40000;

-- Students younger than 19 but not in grade 'B'
SELECT * FROM student
WHERE age < 19 AND NOT grade = 'B';
```

---

## 📘 Practice Questions (PostgreSQL Only)

---

### Q1. Write a query to find students who are either 17 or 18 years old.

```sql
SELECT * FROM student WHERE age = 17 OR age = 18;
```

---

### Q2. Find employees with salary between 40000 and 60000.

```sql
SELECT * FROM employee 
WHERE salary >= 40000 AND salary <= 60000;
```

---

### Q3. List students who are not in grade 'C'.

```sql
SELECT * FROM student WHERE NOT grade = 'C';
```

---

### Q4. Find employees who joined today **and** are active.

```sql
SELECT * FROM employee 
WHERE join_date = CURRENT_DATE AND is_active = TRUE;
```

---

### Q5. Show students who are either in grade 'A' **or** older than 18.

```sql
SELECT * FROM student 
WHERE grade = 'A' OR age > 18;
```

---

## Summary:

✅ Use **Relational operators** to compare values
✅ Use **Logical operators** to combine conditions
✅ Combine them in `WHERE` to create powerful filters

---

Let me know if you're ready for:

* 🔜 **Day 8: Aggregate Functions (COUNT, SUM, AVG, etc.)**
* 📄 Or want **Days 1–7 as a single PDF or DOCX file** for revision and printing!
