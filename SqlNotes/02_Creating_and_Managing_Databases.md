Sure! Here's your **📘 Day 2 – Creating & Managing Databases** study note with clear explanations, MySQL + PostgreSQL syntax, and practice questions.

---

## 📘 Day 2 – Creating & Managing Databases

🎥 Watch: **14:05 – 23:28**

---

## 🎯 Topics Covered:

1. `CREATE DATABASE`
2. `SHOW DATABASES` / `\l` (list)
3. `USE` (MySQL) / `\c` (psql)
4. `DROP DATABASE`

---

## 🧠 Concepts Explained (with MySQL + PostgreSQL)

---

### 🔹 1. `CREATE DATABASE`

Used to create a new database.

#### ✅ Syntax:

* **MySQL:**

```sql
CREATE DATABASE db_name;
```

* **PostgreSQL (psql):**

```sql
CREATE DATABASE db_name;
```

> ⚠️ In PostgreSQL, you **cannot create a DB inside another DB** (no `USE` like MySQL). You must connect to DB using `\c`.

---

### 🔹 2. List All Databases

Used to view all available databases.

#### ✅ Syntax:

* **MySQL:**

```sql
SHOW DATABASES;
```

* **PostgreSQL (psql):**

```sql
\l
```

---

### 🔹 3. Switch to a Database

Used to start working inside a specific database.

#### ✅ Syntax:

* **MySQL:**

```sql
USE db_name;
```

* **PostgreSQL (psql):**

```bash
\c db_name
```

> In PostgreSQL, this command **connects to the database** from the terminal or psql shell.

---

### 🔹 4. Drop (Delete) a Database

Used to delete the entire database and its contents. This **cannot be undone**.

#### ✅ Syntax:

* **MySQL:**

```sql
DROP DATABASE db_name;
```

* **PostgreSQL (psql):**

```sql
DROP DATABASE db_name;
```

---

## 🧪 Practice Tasks

### 🔄 **Practice 1: MySQL**

```sql
-- Create 3 databases
CREATE DATABASE company;
CREATE DATABASE college;
CREATE DATABASE test_db;

-- List all databases
SHOW DATABASES;

-- Switch to 'college'
USE college;

-- Drop one
DROP DATABASE test_db;
```

### 🔄 **Practice 2: PostgreSQL (in psql shell)**

```sql
-- Create 3 databases
CREATE DATABASE company;
CREATE DATABASE college;
CREATE DATABASE test_db;

-- List all databases
\l

-- Connect to 'college'
\c college

-- Drop one
\c postgres     -- You cannot drop a DB you are currently using!
DROP DATABASE test_db;
```

---

## ❓ Practice Questions

### 💡 Conceptual

1. What is the difference between `USE` in MySQL and `\c` in PostgreSQL?
2. Can we recover a database once dropped? If yes, how?
3. Why should we always switch to the correct database before running queries?
4. What happens when you try to create a database that already exists?

---

### 🧠 SQL Problem Set

#### MySQL:

1. Create two databases: `library`, `hospital`
2. Switch to `library` and create a table `books(id, title)`
3. List all databases
4. Drop `hospital`

#### PostgreSQL:

1. Create two databases: `gym`, `shop`
2. Switch to `gym` and create table `members(id, name)`
3. List databases
4. Drop `shop`

---

## 🧑‍💻 Pro Tips:

* PostgreSQL is case-sensitive for names unless quoted (`"DbName"`).
* Avoid using reserved keywords as database names.
* Use `IF EXISTS` and `IF NOT EXISTS` for safety:

```sql
CREATE DATABASE IF NOT EXISTS db_name;   -- MySQL
DROP DATABASE IF EXISTS db_name;         -- Both
```

---
Here are the clear and complete answers to your questions:

---

### **1. What is the difference between `USE` in MySQL and `\c` in PostgreSQL?**

| Feature         | `USE` in MySQL                   | `\c` in PostgreSQL                           |
| --------------- | -------------------------------- | -------------------------------------------- |
| **Purpose**     | Changes the **current database** | Connects to a **different database**         |
| **Usage**       | SQL command: `USE db_name;`      | Meta-command: `\c db_name` in `psql` shell   |
| **Scope**       | Works **within a session**       | Actually **re-establishes a new connection** |
| **Environment** | Used in **MySQL CLI or tools**   | Used only in **psql (PostgreSQL terminal)**  |

🔹 **Key Difference:**

* `USE` just sets the working database within the same connection (MySQL).
* `\c` disconnects and **reconnects to another database** (PostgreSQL).

---

### **2. Can we recover a database once dropped? If yes, how?**

* By default: ❌ **No**, once a database is dropped, it is **permanently deleted**.
* ✅ **Recovery is possible only if:**

  * You have a **backup** (e.g., `.sql` file from `mysqldump` or `pg_dump`)
  * You have **binary logs or WAL logs** (for advanced recovery in MySQL/PostgreSQL)
  * Point-in-time recovery (if properly configured beforehand)

🔹 **Best Practice:** Always take regular backups before running destructive commands like `DROP`.

---

### **3. Why should we always switch to the correct database before running queries?**

* Ensures that:

  * **Queries affect the correct database**
  * **Tables are created, modified, or deleted** in the **intended location**
  * Prevents **data corruption or loss** due to accidental operations on the wrong database

🔹 Especially important when working in a shared server with multiple databases.

---

### **4. What happens when you try to create a database that already exists?**

* In **MySQL**:

  * You get an error:
    `ERROR 1007 (HY000): Can't create database 'db_name'; database exists`

* ✅ You can avoid this error using:

  ```sql
  CREATE DATABASE IF NOT EXISTS db_name;
  ```

* In **PostgreSQL**:

  * You also get an error unless you use:

  ```sql
  CREATE DATABASE db_name WITH ...;
  -- Or use
  DO $$ BEGIN
    IF NOT EXISTS (SELECT FROM pg_database WHERE datname = 'db_name') THEN
      CREATE DATABASE db_name;
    END IF;
  END $$;
  ```

---
