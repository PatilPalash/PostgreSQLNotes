Here’s your complete **🔹 Day 10 – ALTER, CHECK, CASE** PostgreSQL (psql) note with concept explanations, syntax, practical examples, and practice questions.

---

## 🔹 Day 10 – ALTER, CHECK, CASE (PostgreSQL)

---

### 🎥 Topics:

* **02:22:45 – ALTER TABLE**
* **02:30:46 – CHECK Constraint**
* **02:37:23 – CASE Expression**

---

## ✅ 1. ALTER TABLE

Used to **modify the structure** of an existing table (add/remove columns, rename, etc.).

---

### 📌 Add a Column

```sql
ALTER TABLE student
ADD COLUMN phone VARCHAR(15);
```

---

### 📌 Drop a Column

```sql
ALTER TABLE student
DROP COLUMN phone;
```

---

### 📌 Rename Column

```sql
ALTER TABLE student
RENAME COLUMN age TO student_age;
```

---

### 📌 Change Data Type

```sql
ALTER TABLE student
ALTER COLUMN student_age TYPE SMALLINT;
```

---

## ✅ 2. CHECK Constraint

Used to **limit the values** allowed in a column.

---

### 📌 Syntax (during table creation):

```sql
CREATE TABLE employee (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT CHECK (age >= 18),
    salary NUMERIC CHECK (salary > 0)
);
```

---

### 📌 Add CHECK Constraint using ALTER:

```sql
ALTER TABLE employee
ADD CONSTRAINT check_age CHECK (age >= 18);
```

---

### 📌 Example: Reject invalid insert

```sql
INSERT INTO employee (name, age, salary)
VALUES ('Sneha', 16, 50000);

-- ERROR:  new row for relation "employee" violates check constraint "check_age"
```

---

## ✅ 3. CASE Expression

Used in `SELECT` to create **conditional outputs**, similar to `IF...ELSE`.

---

### 📌 Syntax:

```sql
SELECT name,
       CASE
           WHEN grade = 'A' THEN 'Excellent'
           WHEN grade = 'B' THEN 'Good'
           ELSE 'Needs Improvement'
       END AS performance
FROM student;
```

---

### 📌 Example: Classify salary range

```sql
SELECT name, salary,
       CASE
           WHEN salary >= 100000 THEN 'High'
           WHEN salary >= 50000 THEN 'Medium'
           ELSE 'Low'
       END AS salary_level
FROM employee;
```

---

## 💻 Practice Tasks (PostgreSQL Only)

---

### ✅ 1. Add a column to student for phone number

```sql
ALTER TABLE student ADD COLUMN phone VARCHAR(15);
```

---

### ✅ 2. Drop the phone column

```sql
ALTER TABLE student DROP COLUMN phone;
```

---

### ✅ 3. Add a CHECK constraint that salary must be > 10000

```sql
ALTER TABLE employee
ADD CONSTRAINT check_salary CHECK (salary > 10000);
```

---

### ✅ 4. Use CASE to categorize student grades

```sql
SELECT name, grade,
       CASE
           WHEN grade = 'A' THEN 'Topper'
           WHEN grade = 'B' THEN 'Average'
           ELSE 'Needs Work'
       END AS category
FROM student;
```

---

## 📘 Practice Questions (psql)

---

### Q1. Alter the `employee` table to rename the column `salary` to `monthly_salary`.

```sql
ALTER TABLE employee RENAME COLUMN salary TO monthly_salary;
```

---

### Q2. Add a `CHECK` constraint to ensure `monthly_salary >= 12000`.

```sql
ALTER TABLE employee
ADD CONSTRAINT check_salary_limit CHECK (monthly_salary >= 12000);
```

---

### Q3. Use `CASE` to tag employees older than 50 as “Senior” and others as “Junior”.

```sql
SELECT name, age,
       CASE
           WHEN age > 50 THEN 'Senior'
           ELSE 'Junior'
       END AS age_category
FROM employee;
```

---

### Q4. Add a column `status` to the `student` table.

```sql
ALTER TABLE student ADD COLUMN status VARCHAR(20);
```

---

### Q5. Drop the `status` column.

```sql
ALTER TABLE student DROP COLUMN status;
```

---

## ✅ Summary:

| Topic         | Key Use                |
| ------------- | ---------------------- |
| `ALTER TABLE` | Modify table structure |
| `CHECK`       | Validate column values |
| `CASE`        | Add logic to `SELECT`  |

---

Let me know if you're ready for:

* 🔜 **Day 11: JOINS – INNER, LEFT, RIGHT, FULL**
* 📄 Or want a **combined PDF of Day 1–10 notes** with all queries and explanations.
