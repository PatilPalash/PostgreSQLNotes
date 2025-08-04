Here’s your detailed **🔹 Day 13 – Views, HAVING, Stored Procedures** note (PostgreSQL with psql-only focus), complete with explanation and practice questions.

---

## 🔹 Day 13 – Views, HAVING, Stored Procedures

---

### 🎥 Topics:

* **03:45:05 – VIEWS**
* **03:48:57 – HAVING Clause**
* **03:54:00 – Stored Procedure**

---

## ✅ 1. VIEWS in PostgreSQL

---

### 🔹 What is a VIEW?

* A **virtual table** based on a SQL query.
* Stores no actual data—only the query definition.
* Simplifies complex queries, improves readability, and can enhance security.

---

### 🔹 Syntax:

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table
WHERE condition;
```

---

### 🧪 Practice:

**1. Create a view showing user name and total amount spent per order:**

```sql
CREATE VIEW user_order_summary AS
SELECT 
  u.name,
  o.order_id,
  SUM(oi.quantity * p.price) AS total_amount
FROM users u
JOIN orders o ON u.user_id = o.user_id
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id
GROUP BY u.name, o.order_id;
```

**2. Query the view:**

```sql
SELECT * FROM user_order_summary;
```

---

### 🔧 Update a view:

```sql
CREATE OR REPLACE VIEW user_order_summary AS
-- updated query
```

---

### 🗑 Drop a view:

```sql
DROP VIEW IF EXISTS user_order_summary;
```

---

## ✅ 2. HAVING Clause

---

### 🔹 What is HAVING?

* Similar to `WHERE`, but used **with GROUP BY**.
* Filters grouped/aggregated results.

---

### 🔹 Syntax:

```sql
SELECT column, COUNT(*)
FROM table
GROUP BY column
HAVING COUNT(*) > 1;
```

---

### 🧪 Practice:

**1. Find products that appear in more than 1 order:**

```sql
SELECT product_id, COUNT(order_id) AS order_count
FROM order_items
GROUP BY product_id
HAVING COUNT(order_id) > 1;
```

**2. List users who have placed more than 1 order:**

```sql
SELECT user_id, COUNT(*) AS order_count
FROM orders
GROUP BY user_id
HAVING COUNT(*) > 1;
```

---

## ✅ 3. Stored Procedures

---

### 🔹 What is a Stored Procedure?

* A **block of SQL code** that can be stored and executed repeatedly.
* Can contain logic like IF/ELSE, loops, variables.

---

### 🔹 Syntax (PostgreSQL):

```sql
CREATE OR REPLACE PROCEDURE procedure_name()
LANGUAGE plpgsql
AS $$
BEGIN
    -- SQL statements
END;
$$;
```

---

### 🧪 Practice:

**1. Simple procedure to insert a user:**

```sql
CREATE OR REPLACE PROCEDURE insert_user(p_name TEXT, p_email TEXT)
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO users (name, email) VALUES (p_name, p_email);
END;
$$;
```

**Call it:**

```sql
CALL insert_user('Amit', 'amit@email.com');
```

---

**2. Procedure to update stock after order:**

```sql
CREATE OR REPLACE PROCEDURE update_stock(p_product_id INT, p_qty INT)
LANGUAGE plpgsql
AS $$
BEGIN
    UPDATE products
    SET stock = stock - p_qty
    WHERE product_id = p_product_id;
END;
$$;
```

**Call:**

```sql
CALL update_stock(1, 2);  -- reduces stock of product_id = 1 by 2
```

---

### 🔄 Drop Procedure:

```sql
DROP PROCEDURE IF EXISTS insert_user(TEXT, TEXT);
```

---

## 🧠 Summary Table

| Topic         | Description                     | Example                |
| ------------- | ------------------------------- | ---------------------- |
| **VIEW**      | Virtual table from SELECT query | `CREATE VIEW ...`      |
| **HAVING**    | Filters GROUP BY results        | `HAVING COUNT(*) > 1`  |
| **PROCEDURE** | Stored block of logic-based SQL | `CREATE PROCEDURE ...` |

---

## 🧪 Bonus Practice:

1. Create a view that shows all orders above ₹5000.
2. Write a procedure that deletes all users with no orders.
3. Use `HAVING` to find products with average quantity > 2 in orders.

---

Let me know if you'd like:

* All 13-day notes exported as PDF/Markdown
* ERD for the mini-project
* Next day’s content (Day 14 – Subqueries & Indexes)
