Here is your **🔹 Day 14 – Functions, CTE, Triggers** note (PostgreSQL-focused, using `psql` only), complete with detailed explanations and practice questions.

---

## 🔹 Day 14 – Functions, CTE, Triggers

---

### 🎥 Topics:

* **04:03:05 – User Defined Functions**
* **04:13:39 – Window Functions**
* **04:27:06 – CTE (Common Table Expressions)**
* **04:39:34 – Triggers**

---

## ✅ 1. User Defined Functions (UDF)

---

### 🔹 What is a Function in PostgreSQL?

* A **stored logic block** that returns a value.
* Useful for calculations, reusable logic, data formatting, etc.

---

### 🔹 Syntax (Scalar Function):

```sql
CREATE OR REPLACE FUNCTION function_name(param1 type, param2 type)
RETURNS return_type
LANGUAGE plpgsql
AS $$
BEGIN
    -- logic
    RETURN value;
END;
$$;
```

---

### 🧪 Practice:

**1. Create a function to calculate discounted price:**

```sql
CREATE OR REPLACE FUNCTION get_discount(price NUMERIC, discount NUMERIC)
RETURNS NUMERIC
LANGUAGE plpgsql
AS $$
BEGIN
    RETURN price - (price * discount / 100);
END;
$$;
```

**Call:**

```sql
SELECT get_discount(500, 10);  -- returns 450
```

---

**2. Function to get full name:**

```sql
CREATE OR REPLACE FUNCTION full_name(fname TEXT, lname TEXT)
RETURNS TEXT
LANGUAGE plpgsql
AS $$
BEGIN
    RETURN INITCAP(fname || ' ' || lname);
END;
$$;
```

---

## ✅ 2. Window Functions

---

### 🔹 What are Window Functions?

* Functions that perform calculations **across a set of rows** related to the current row.
* Examples: `RANK()`, `ROW_NUMBER()`, `LAG()`, `LEAD()`, `SUM() OVER()`

---

### 🔹 Syntax:

```sql
SELECT column, 
       RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS rank
FROM employee;
```

---

### 🧪 Practice:

**1. Assign row numbers to employees by department:**

```sql
SELECT emp_id, name, department,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY emp_id) AS row_no
FROM employee;
```

**2. Running total of salaries:**

```sql
SELECT name, salary,
       SUM(salary) OVER (ORDER BY name) AS running_total
FROM employee;
```

---

## ✅ 3. CTE – Common Table Expressions

---

### 🔹 What is a CTE?

* A **temporary result set** defined using `WITH`, used to organize complex queries.

---

### 🔹 Syntax:

```sql
WITH cte_name AS (
    SELECT ...
)
SELECT * FROM cte_name;
```

---

### 🧪 Practice:

**1. Use CTE to get employees with max salary per department:**

```sql
WITH dept_max AS (
    SELECT department, MAX(salary) AS max_salary
    FROM employee
    GROUP BY department
)
SELECT e.*
FROM employee e
JOIN dept_max d ON e.department = d.department AND e.salary = d.max_salary;
```

---

**2. CTE with JOIN:**

```sql
WITH recent_orders AS (
    SELECT * FROM orders
    WHERE order_date > CURRENT_DATE - INTERVAL '30 days'
)
SELECT u.name, o.order_id
FROM users u
JOIN recent_orders o ON u.user_id = o.user_id;
```

---

## ✅ 4. Triggers

---

### 🔹 What is a Trigger?

* A procedure that **automatically runs** in response to certain events on a table (INSERT, UPDATE, DELETE).

---

### 🔹 Components:

1. Trigger function (logic)
2. Trigger itself (event + table)

---

### 🔹 Syntax (Function):

```sql
CREATE OR REPLACE FUNCTION log_insert()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO log_table(table_name, action, timestamp)
    VALUES (TG_TABLE_NAME, TG_OP, NOW());
    RETURN NEW;
END;
$$;
```

---

### 🔹 Syntax (Trigger):

```sql
CREATE TRIGGER after_insert_trigger
AFTER INSERT ON target_table
FOR EACH ROW
EXECUTE FUNCTION log_insert();
```

---

### 🧪 Practice:

**1. Create audit log table:**

```sql
CREATE TABLE audit_log (
    id SERIAL PRIMARY KEY,
    table_name TEXT,
    action TEXT,
    log_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**2. Create trigger function:**

```sql
CREATE OR REPLACE FUNCTION log_user_insert()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO audit_log(table_name, action)
    VALUES (TG_TABLE_NAME, TG_OP);
    RETURN NEW;
END;
$$;
```

**3. Create the trigger on `users` table:**

```sql
CREATE TRIGGER trigger_log_user_insert
AFTER INSERT ON users
FOR EACH ROW
EXECUTE FUNCTION log_user_insert();
```

**4. Test:**

```sql
INSERT INTO users(name, email) VALUES('Test User', 'test@mail.com');
SELECT * FROM audit_log;
```

---

## 🧠 Summary Table

| Feature         | Use Case                             | Example                        |
| --------------- | ------------------------------------ | ------------------------------ |
| **Function**    | Return result from reusable logic    | `get_discount(price, %) `      |
| **Window Func** | Rank, row number, aggregates w/ rows | `ROW_NUMBER() OVER (...)`      |
| **CTE**         | Organize nested/complex queries      | `WITH cte AS (...) SELECT ...` |
| **Trigger**     | Automate logging, validation, alerts | `AFTER INSERT ON table ...`    |

---

## 🧪 Bonus Practice:

1. Create a function to get employee tax based on salary.
2. Use `LAG()` to compare current and previous order total.
3. Create a CTE to find users who haven't ordered in the past 60 days.
4. Create a trigger to prevent insert if product stock is zero.

---

Let me know if you’d like:

* Combined notes as PDF
* Diagrams (function flow, CTEs, trigger lifecycle)
* Mock interview questions on these concepts
