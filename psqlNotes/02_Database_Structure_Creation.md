Here’s your **🔹 Day 2 – Database Structure & Creation** full breakdown with clear explanations, PostgreSQL (psql) practice, and sample questions:

---

## 🔹 **Day 2 – Database Structure & Creation**

---

### 🎥 Topics:

---

### ✅ **25:40 – DB vs Schema vs Table**

#### 🟢 **1. Database (DB):**

* A **database** is a collection of schemas, tables, users, and other objects.
* It holds and organizes all your data logically.

**Create DB:**

```sql
CREATE DATABASE my_first_db;
```

---

#### 🟢 **2. Schema:**

* A **schema** is a logical container within a database.
* It groups related tables, views, functions, etc.
* PostgreSQL has a default schema called `public`.

**Create Schema:**

```sql
CREATE SCHEMA sales_data;
```

**Use custom schema in table creation:**

```sql
CREATE TABLE sales_data.orders (
    order_id SERIAL PRIMARY KEY,
    customer_name VARCHAR(100)
);
```

---

#### 🟢 **3. Table:**

* A **table** stores data in rows and columns.
* Tables live **inside schemas**, which live **inside databases**.

**Create Table:**

```sql
CREATE TABLE employees (
    emp_id SERIAL PRIMARY KEY,
    emp_name TEXT,
    department TEXT
);
```

---

### ✅ **27:56 – CREATE, DROP, LIST, SWITCH database**

---

#### 🔷 **Create a Database**

```sql
CREATE DATABASE my_first_db;
```

---

#### 🔷 **List All Databases**

```sql
\l
```

---

#### 🔷 **Drop a Database**

```sql
DROP DATABASE my_first_db;
```

⚠️ **Caution:** This permanently deletes all schema, tables, and data inside.

---

#### 🔷 **Connect / Switch to Another Database (psql)**

From terminal:

```bash
psql -U postgres -d my_first_db
```

Inside psql shell:

```sql
\c my_first_db
```

---

#### 🔷 **List Schemas in the Current DB**

```sql
\dn
```

---

#### 🔷 **List Tables in Current Schema**

```sql
\dt
```

---

### 💻 **Practice Tasks (in psql)**

---

#### ✅ 1. Create Your Own Database

```sql
CREATE DATABASE my_first_db;
```

---

#### ✅ 2. Switch to It

```sql
\c my_first_db
```

---

#### ✅ 3. Create a New Schema

```sql
CREATE SCHEMA company_info;
```

---

#### ✅ 4. Create a Table in That Schema

```sql
CREATE TABLE company_info.employees (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    role TEXT
);
```

---

#### ✅ 5. List All Databases

```sql
\l
```

---

#### ✅ 6. Drop a Database

⚠️ Switch to another DB first, you can't drop a DB you're currently using.

```sql
\c postgres
DROP DATABASE my_first_db;
```

---

### 📘 Day 2 – Practice Questions (PSQL Only)

---

#### Q1. What is the difference between a database and a schema?

> A **database** is a container for schemas, users, roles, and configurations. A **schema** is a logical grouping of tables/functions inside a single database.

---

#### Q2. Write SQL to create a database called `project_db`.

```sql
CREATE DATABASE project_db;
```

---

#### Q3. How do you connect to a different database inside psql?

```sql
\c project_db
```

---

#### Q4. How can you see all the databases?

```sql
\l
```

---

#### Q5. Create a schema called `dev` and a table inside it named `modules`.

```sql
CREATE SCHEMA dev;

CREATE TABLE dev.modules (
    id SERIAL PRIMARY KEY,
    module_name TEXT
);
```

---

#### Q6. Write a command to drop the database `test_data`.

```sql
DROP DATABASE test_data;
```

---

Let me know if you want **Day 3 notes**, or a **PDF of Day 1 + Day 2** bundled together!
