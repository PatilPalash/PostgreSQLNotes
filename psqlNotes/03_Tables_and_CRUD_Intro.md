Here’s your full breakdown for **🔹 Day 3 – Tables & CRUD Intro** including **detailed notes, explanations, PostgreSQL (psql) commands, and practice questions.**

---

## 🔹 **Day 3 – Tables & CRUD Intro**

---

### 🎥 Topics:

---

### ✅ **34:35 – What is CRUD?**

**CRUD** = Four basic operations used to interact with a database:

| Operation  | SQL Command | Purpose                 |
| ---------- | ----------- | ----------------------- |
| **C**reate | `INSERT`    | Add new records         |
| **R**ead   | `SELECT`    | Read/retrieve records   |
| **U**pdate | `UPDATE`    | Modify existing records |
| **D**elete | `DELETE`    | Remove records          |

---

### ✅ **36:23 – CREATE TABLE**

To create a table, use the `CREATE TABLE` command with column names, data types, and constraints.

---

#### 📌 Example: Create `student` table

```sql
CREATE TABLE student (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    grade VARCHAR(5),
    email TEXT
);
```

**Explanation:**

* `id`: auto-incremented using `SERIAL`
* `PRIMARY KEY`: uniquely identifies each row
* `VARCHAR(n)`: string with max `n` characters
* `TEXT`: unlimited-length string
* `INT`: integer data type

---

### ✅ **39:43 – INSERT data**

The `INSERT INTO` command is used to add rows to a table.

---

#### 📌 Example: Insert Records

```sql
INSERT INTO student (name, age, grade, email)
VALUES 
('Aarav', 18, 'A', 'aarav@example.com'),
('Diya', 17, 'B', 'diya@example.com'),
('Kabir', 19, 'A', 'kabir@example.com'),
('Meera', 18, 'C', 'meera@example.com'),
('Rohan', 17, 'B', 'rohan@example.com');
```

---

## 💻 Practice (in psql)

---

### ✅ 1. Create a Table

```sql
CREATE TABLE student (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    grade VARCHAR(5),
    email TEXT
);
```

---

### ✅ 2. Insert 5–10 Records

```sql
INSERT INTO student (name, age, grade, email) VALUES
('Aarav', 18, 'A', 'aarav@example.com'),
('Diya', 17, 'B', 'diya@example.com'),
('Kabir', 19, 'A', 'kabir@example.com'),
('Meera', 18, 'C', 'meera@example.com'),
('Rohan', 17, 'B', 'rohan@example.com'),
('Sneha', 18, 'A', 'sneha@example.com'),
('Tanvi', 17, 'B', 'tanvi@example.com'),
('Ishaan', 19, 'C', 'ishaan@example.com');
```

---

### ✅ 3. View Inserted Data

```sql
SELECT * FROM student;
```

---

## 📘 Practice Questions (PSQL Only)

---

### Q1. What is the full form of CRUD and what does each operation do?

> **C**reate – Insert new records
> **R**ead – Retrieve records
> **U**pdate – Modify existing records
> **D**elete – Remove records

---

### Q2. Write a command to create a table named `courses` with columns:

* `id` (auto-incremented)
* `course_name` (text)
* `duration_months` (integer)

```sql
CREATE TABLE courses (
    id SERIAL PRIMARY KEY,
    course_name TEXT,
    duration_months INT
);
```

---

### Q3. Write a SQL query to insert a new student into the `student` table.

```sql
INSERT INTO student (name, age, grade, email)
VALUES ('Anjali', 18, 'A', 'anjali@example.com');
```

---

### Q4. How can you view all the data from the `student` table?

```sql
SELECT * FROM student;
```

---

Let me know when you're ready for **Day 4: UPDATE, DELETE & Constraints**, or if you'd like all notes in a downloadable format (PDF or DOCX).
