Here’s your detailed **🔹 Day 11 – Relationships & JOINS** note with explanations, syntax, examples, and PostgreSQL (psql-only) practice exercises.

---

## 🔹 Day 11 – Relationships & JOINS (PostgreSQL)

---

### 🎥 Topics:

* **02:46:41 – Relationships**
* **02:54:48 – Foreign Key**
* **02:55:49 – One-to-One Example**
* **03:00:41 – JOINS (INNER, LEFT, RIGHT)**

---

## ✅ 1. RELATIONSHIPS in SQL

**Relationships** connect data across multiple tables using **keys**:

* **Primary Key (PK)**: Uniquely identifies each record in a table.
* **Foreign Key (FK)**: References a PK in another table.

### 🔹 Common Relationship Types:

* **One-to-One**: One record in A = One in B.
* **One-to-Many** (most common): One in A = Many in B.
* **Many-to-Many**: Requires a junction table.

---

## ✅ 2. FOREIGN KEY

Used to create **a relationship between two tables**.

### 📌 Example: customers & orders

```sql
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    order_date DATE,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

* `customer_id` in `orders` is a **foreign key** referencing `customers`.

---

## ✅ 3. One-to-One Example

Let’s say each employee has one profile:

```sql
CREATE TABLE employee (
    emp_id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE employee_profile (
    profile_id SERIAL PRIMARY KEY,
    emp_id INT UNIQUE,
    phone VARCHAR(20),
    address TEXT,
    FOREIGN KEY (emp_id) REFERENCES employee(emp_id)
);
```

* `emp_id` in `employee_profile` has a `UNIQUE` constraint, so only one profile per employee.

---

## ✅ 4. JOINS

Joins allow us to combine rows from **multiple tables** based on related columns.

---

### 🔹 INNER JOIN

Returns **only matching rows** from both tables.

```sql
SELECT c.name, o.order_id, o.order_date
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```

---

### 🔹 LEFT JOIN

Returns **all rows from the left table** and matching ones from the right (if any).

```sql
SELECT c.name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

---

### 🔹 RIGHT JOIN

Returns **all rows from the right table** and matching ones from the left.

```sql
SELECT c.name, o.order_id
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```

---

## 💻 Practice Exercises (PostgreSQL only)

---

### ✅ Step 1: Create Tables

```sql
-- Customers
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100)
);

-- Orders
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    order_date DATE,
    amount NUMERIC,
    customer_id INT,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

---

### ✅ Step 2: Insert Sample Data

```sql
-- Insert into customers
INSERT INTO customers (name, email) VALUES
('Arjun', 'arjun@gmail.com'),
('Sneha', 'sneha@gmail.com'),
('Ravi', 'ravi@gmail.com');

-- Insert into orders
INSERT INTO orders (order_date, amount, customer_id) VALUES
('2025-07-10', 1200, 1),
('2025-07-12', 850, 1),
('2025-07-14', 450, 2);
```

---

### ✅ Step 3: Practice Queries

#### Q1. INNER JOIN - Customers with orders

```sql
SELECT c.name, o.order_id, o.amount
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```

---

#### Q2. LEFT JOIN - All customers (even if no orders)

```sql
SELECT c.name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

---

#### Q3. RIGHT JOIN - All orders (even if no customer — rare, only if orphaned)

```sql
SELECT c.name, o.order_id
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```

---

#### Q4. One-to-One: Create employee and profile, then join

```sql
-- Tables
CREATE TABLE employee (
    emp_id SERIAL PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE profile (
    profile_id SERIAL PRIMARY KEY,
    emp_id INT UNIQUE,
    phone VARCHAR(15),
    FOREIGN KEY (emp_id) REFERENCES employee(emp_id)
);

-- Data
INSERT INTO employee (name) VALUES ('Amit'), ('Sita');

INSERT INTO profile (emp_id, phone) VALUES (1, '1234567890');
```

Join:

```sql
SELECT e.name, p.phone
FROM employee e
INNER JOIN profile p ON e.emp_id = p.emp_id;
```

---

## 📘 Quick Summary Table

| Join Type  | Returns                            |
| ---------- | ---------------------------------- |
| INNER JOIN | Matching rows only                 |
| LEFT JOIN  | All from left, matching from right |
| RIGHT JOIN | All from right, matching from left |

---

## 📚 Additional Practice Questions

1. Write a query to get customer names and total order amount.
2. List all orders with customer names, even if customer info is missing.
3. Find customers who **have not placed any order**.
4. Show order dates and names of customers who placed orders after July 11, 2025.

---

Let me know when you’re ready for:

* 🔜 **Day 12: Subqueries & Nested SELECT**
* 📥 Or a **PDF version of Day 1–11 notes with all psql practice**.
