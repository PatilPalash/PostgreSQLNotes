Here’s your complete **🔹 Day 12 – Many-to-Many & Mini Project (E-Store)** PostgreSQL (psql-only) notes with schema design, examples, and practice exercises.

---

## 🔹 Day 12 – Many-to-Many & Mini Project (E-Store)

---

### 🎥 Topics:

* **03:12:25 – Many-to-Many Relationship**
* **03:25:42 – E-STORE Mini Project**

---

## ✅ 1. Many-to-Many Relationship in SQL

### 🔹 What is Many-to-Many?

* A record in **Table A** can relate to **multiple records** in **Table B** — and vice versa.
* Example:

  * A **user** can buy **multiple products**
  * A **product** can be purchased by **multiple users**

### 🔹 Solution: Use a **Junction Table**

A **third table** is created with **foreign keys** from both tables.

---

### 🎯 Real Example: Products and Orders

#### Schema:

* `products` (product\_id, name, price)
* `orders` (order\_id, user\_id, order\_date)
* `order_items` (junction table with product\_id, order\_id, quantity)

---

### ✅ 2. E-Store Project Design

#### 📦 Tables:

1. `users`
2. `products`
3. `orders`
4. `order_items` (junction)
5. `cart` (optional mini-feature for extra practice)

---

## 🧱 DATABASE SCHEMA (PostgreSQL)

```sql
-- USERS
CREATE TABLE users (
    user_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100) UNIQUE
);

-- PRODUCTS
CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    price NUMERIC(10,2),
    stock INT
);

-- ORDERS
CREATE TABLE orders (
    order_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    order_date DATE DEFAULT CURRENT_DATE
);

-- ORDER_ITEMS (junction table)
CREATE TABLE order_items (
    order_id INT REFERENCES orders(order_id),
    product_id INT REFERENCES products(product_id),
    quantity INT CHECK (quantity > 0),
    PRIMARY KEY (order_id, product_id)
);
```

---

### 🛒 Optional CART Table

```sql
CREATE TABLE cart (
    cart_id SERIAL PRIMARY KEY,
    user_id INT REFERENCES users(user_id),
    product_id INT REFERENCES products(product_id),
    quantity INT CHECK (quantity > 0)
);
```

---

## 💻 PRACTICE TASKS (PSQL ONLY)

---

### ✅ Insert Sample Data

```sql
-- USERS
INSERT INTO users (name, email) VALUES
('Palash', 'palash@email.com'),
('Neha', 'neha@email.com');

-- PRODUCTS
INSERT INTO products (name, price, stock) VALUES
('Laptop', 60000.00, 5),
('Phone', 25000.00, 10),
('Headphones', 3000.00, 15);

-- ORDERS
INSERT INTO orders (user_id) VALUES (1), (2);

-- ORDER_ITEMS
INSERT INTO order_items (order_id, product_id, quantity) VALUES
(1, 1, 1), -- Palash buys 1 Laptop
(1, 3, 2), -- Palash buys 2 Headphones
(2, 2, 1); -- Neha buys 1 Phone
```

---

## 📊 PRACTICE QUERIES

---

### 1. List all users and their orders

```sql
SELECT u.name, o.order_id, o.order_date
FROM users u
JOIN orders o ON u.user_id = o.user_id;
```

---

### 2. Show all products in each order

```sql
SELECT o.order_id, p.name AS product_name, oi.quantity
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
JOIN orders o ON oi.order_id = o.order_id;
```

---

### 3. Calculate total amount per order

```sql
SELECT 
  oi.order_id,
  SUM(oi.quantity * p.price) AS total_amount
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
GROUP BY oi.order_id;
```

---

### 4. List users who bought a specific product

```sql
SELECT DISTINCT u.name
FROM users u
JOIN orders o ON u.user_id = o.user_id
JOIN order_items oi ON o.order_id = oi.order_id
WHERE oi.product_id = 1; -- Laptop
```

---

### 5. Show cart items for a user

```sql
SELECT c.user_id, u.name, p.name AS product_name, c.quantity
FROM cart c
JOIN users u ON c.user_id = u.user_id
JOIN products p ON c.product_id = p.product_id
WHERE u.name = 'Palash';
```

---

## 📘 Key Concepts Recap

| Concept                     | Use                                            |
| --------------------------- | ---------------------------------------------- |
| **Junction Table**          | Handles many-to-many relationships             |
| **Foreign Key**             | Connects related tables                        |
| **Aggregate Functions**     | Used for totals (e.g. `SUM(quantity * price)`) |
| **Primary Key (Composite)** | Uniquely identifies rows in junction tables    |
| **Constraints**             | Enforce rules like `quantity > 0`              |

---

## 🧠 Extra Mini Challenges

1. Find the user who spent the most money.
2. Add a new product to a user’s cart.
3. Count total quantity of each product sold.
4. List all orders containing more than 1 item.

---

Let me know if you’d like:

* ✅ Full E-Store schema ER diagram (visual)
* 📥 All 12-day SQL notes compiled into a PDF
* 🔜 Day 13 – Subqueries & Views (next lesson)
