Here’s your full note for **🔹 Day 9 – String Functions** in **PostgreSQL (psql)** — with detailed explanations, function examples, usage on your `student` and `employee` tables, and practice questions.

---

## 🔹 **Day 9 – String Functions**

---

### 🎥 Topics:

**🕐 01:49:59 – CONCAT, REPLACE, SUBSTR, UPPER/LOWER, etc.**

---

## ✅ 1. **CONCAT()** – Combine Strings

```sql
SELECT CONCAT('Hello ', 'World');
-- Result: Hello World
```

📌 Combine first and last name (or name + email):

```sql
SELECT CONCAT(name, ' - ', email) AS full_info FROM student;
```

You can also use `||` as the concatenation operator:

```sql
SELECT name || ' <' || email || '>' AS contact FROM employee;
```

---

## ✅ 2. **REPLACE()** – Replace Substring

```sql
SELECT REPLACE('postgresql is cool', 'cool', 'awesome');
-- Result: postgresql is awesome
```

📌 Replace domain in email:

```sql
SELECT name, REPLACE(email, '@example.com', '@company.com') AS updated_email
FROM employee;
```

---

## ✅ 3. **SUBSTRING() or SUBSTR()** – Extract Part of a String

```sql
SELECT SUBSTRING('employee123' FROM 1 FOR 8);
-- Result: employee
```

```sql
-- Get first 3 letters of student names
SELECT SUBSTRING(name FROM 1 FOR 3) FROM student;
```

---

## ✅ 4. **UPPER() / LOWER()** – Convert Case

```sql
SELECT UPPER(name) FROM student;
SELECT LOWER(email) FROM employee;
```

---

## ✅ 5. **TRIM() / LTRIM() / RTRIM()** – Remove Spaces

```sql
SELECT TRIM('   name   ');
-- Result: 'name'
```

---

## ✅ 6. **LENGTH()** – Length of String

```sql
SELECT LENGTH(name) FROM student;
```

---

## ✅ 7. **INITCAP()** – Capitalize First Letter of Each Word

```sql
SELECT INITCAP('sneha roy') AS proper_name;
```

---

## 💻 Practice Examples (Use on `student` / `employee`)

---

### ✅ 1. Show name in uppercase

```sql
SELECT UPPER(name) FROM student;
```

---

### ✅ 2. Get domain part of each employee's email

```sql
SELECT SUBSTRING(email FROM POSITION('@' IN email) + 1) AS domain
FROM employee;
```

---

### ✅ 3. Replace `.com` with `.org` in email

```sql
SELECT REPLACE(email, '.com', '.org') FROM student;
```

---

### ✅ 4. Show name + email in one column

```sql
SELECT name || ' <' || email || '>' AS contact_info FROM employee;
```

---

### ✅ 5. Find employees with names longer than 5 characters

```sql
SELECT * FROM employee WHERE LENGTH(name) > 5;
```

---

### ✅ 6. Capitalize student names properly

```sql
SELECT INITCAP(name) FROM student;
```

---

## 📘 Practice Questions (PostgreSQL Only)

---

### Q1. Convert all student emails to lowercase.

```sql
SELECT LOWER(email) FROM student;
```

---

### Q2. Show first 4 letters of each employee name.

```sql
SELECT SUBSTRING(name FROM 1 FOR 4) FROM employee;
```

---

### Q3. Replace all `@example.com` with `@test.com` in employee emails.

```sql
SELECT REPLACE(email, '@example.com', '@test.com') FROM employee;
```

---

### Q4. Show student name and grade in format: “Name (Grade)”

```sql
SELECT name || ' (' || grade || ')' AS student_info FROM student;
```

---

### Q5. Display length of each student’s name.

```sql
SELECT name, LENGTH(name) FROM student;
```

---

## Summary:

✅ Use string functions to clean, format, and transform text data.
✅ Combine them with `SELECT`, `WHERE`, `ORDER BY`, etc. for powerful queries.

---

Let me know if you're ready for:

* 🔜 **Day 10: Numeric Functions, Rounding, Math**
* 📄 Or want a **PDF of Days 1–9 notes + psql practice for revision & interview prep**
