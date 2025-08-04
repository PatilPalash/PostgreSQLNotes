Here’s your full breakdown for **🔹 Day 5 – DataTypes & Constraints**, covering **PostgreSQL concepts, examples, psql practice, and question-based learning.** Perfect for building a strong foundation in table design.

---

## 🔹 **Day 5 – DataTypes & Constraints**

---

### 🎥 Topics:

---

### ✅ **52:00 – DataTypes**

PostgreSQL supports a rich variety of **data types**. Here are the most common:

| Type               | Example          | Description                                |
| ------------------ | ---------------- | ------------------------------------------ |
| `INTEGER` or `INT` | `25`             | Whole numbers                              |
| `SERIAL`           | Auto-incremented | Used for auto-incrementing IDs             |
| `VARCHAR(n)`       | `'John'`         | String with max length `n`                 |
| `TEXT`             | `'Any string'`   | Unlimited-length string                    |
| `BOOLEAN`          | `TRUE / FALSE`   | True/False values                          |
| `DATE`             | `'2025-07-29'`   | Calendar date                              |
| `NUMERIC(p,s)`     | `123.45`         | Precise numbers (p = precision, s = scale) |

---

### ✅ **57:00 – PRIMARY KEY**

A **Primary Key** uniquely identifies each row in a table.

🔸 Rules:

* Must be **unique**.
* Cannot be **NULL**.
* One per table only.

```sql
CREATE TABLE employee (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);
```

---

### ✅ **58:13 – NOT NULL & DEFAULT**

* `NOT NULL`: column must always have a value.
* `DEFAULT`: assigns a value if none is provided.

```sql
CREATE TABLE department (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    is_active BOOLEAN DEFAULT TRUE
);
```

---

### ✅ **59:39 – Other Constraints**

| Constraint    | Description                             |
| ------------- | --------------------------------------- |
| `UNIQUE`      | Ensures no duplicate values in a column |
| `CHECK`       | Validates a condition on values         |
| `FOREIGN KEY` | Links to primary key of another table   |

```sql
CREATE TABLE project (
    id SERIAL PRIMARY KEY,
    name TEXT UNIQUE,
    budget NUMERIC CHECK (budget > 0)
);
```

---

## 💻 Practice Task: Create `employee` Table with Constraints

```sql
CREATE TABLE employee (
    id SERIAL PRIMARY KEY,                        -- Auto ID
    name VARCHAR(100) NOT NULL,                   -- Cannot be null
    email TEXT UNIQUE,                            -- Must be unique
    salary NUMERIC(10,2) CHECK (salary > 0),      -- Positive values only
    join_date DATE DEFAULT CURRENT_DATE,          -- Auto set to today
    is_active BOOLEAN DEFAULT TRUE                -- Defaults to true
);
```

---

## 📘 Practice Questions (PostgreSQL Only)

---

### Q1. What is the difference between `SERIAL` and `INTEGER`?

> `SERIAL` auto-generates a sequence (for IDs), while `INTEGER` is a plain number field that requires manual input.

---

### Q2. Write a query to create a `course` table with:

* `id` (Primary Key)
* `title` (cannot be null)
* `duration` in months (positive number)
* `start_date` with a default value

```sql
CREATE TABLE course (
    id SERIAL PRIMARY KEY,
    title TEXT NOT NULL,
    duration INT CHECK (duration > 0),
    start_date DATE DEFAULT CURRENT_DATE
);
```

---

### Q3. What happens if you try to insert a NULL value in a `NOT NULL` column?

> PostgreSQL will raise an error:

```text
ERROR: null value in column "name" violates not-null constraint
```

---

### Q4. Write a command to make sure `email` in `employee` table is unique.

> Already included in table:

```sql
email TEXT UNIQUE
```

---

### Q5. What constraint would you use to ensure `salary` is never negative?

```sql
salary NUMERIC CHECK (salary >= 0)
```

---

### Q6. Insert sample records into the `employee` table:

```sql
INSERT INTO employee (name, email, salary)
VALUES
('Ravi Kumar', 'ravi@example.com', 40000.00),
('Sneha Roy', 'sneha@example.com', 52000.50),
('Karan Mehta', 'karan@example.com', 61000.00);
```

---

### Q7. View table data:

```sql
SELECT * FROM employee;
```

---

Let me know if you want **Day 6: Constraints Deep Dive (Foreign Key, Composite Key, etc.)**, or want a **PDF with all 5 days' notes and exercises** for offline study.
