
## ✅ **TASK**

### 1. **Create a Database**

```sql
CREATE DATABASE IF NOT EXISTS bank_db;
```

> Creates the `bank_db` database if it doesn't already exist.

---

### 2. **Use the Database**

```sql
USE bank_db;
```

---

### 3. **Create a Table – `employees`**

```sql
CREATE TABLE employees (
    emp_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    desig VARCHAR(50) DEFAULT 'Probation',
    dept VARCHAR(50)
);
```

### 🔍 Column Constraints:

| Column   | Constraint Description                                |
| -------- | ----------------------------------------------------- |
| `emp_id` | No NULLs, no duplicates, auto-increment (Primary Key) |
| `name`   | No NULLs                                              |
| `desig`  | Defaults to `'Probation'` if no value provided        |
| `dept`   | Optional field                                        |

---

## ✅ **Query Examples**

### 🔹 Select rows where `emp_id` is 101 or 103:

```sql
SELECT * FROM employees WHERE emp_id = 101 OR emp_id = 103;
```

**Result:**

| emp\_id | name | desig     | dept |
| ------- | ---- | --------- | ---- |
| 101     | abc  | Manager   | Loan |
| 103     | GHI  | Associate | Loan |

---

### 🔹 Correct comparison operator:

> ❌ `==` is invalid in MySQL
> ✅ Use `=` instead:

```sql
SELECT * FROM employees WHERE name = 'Raju';
```

---

### 🔹 General SELECT Syntax:

```sql
SELECT column1, column2 FROM table_name WHERE condition;
-- or
SELECT * FROM table_name WHERE condition;
```

---

### 🔹 Select with column alias:

```sql
SELECT emp_id AS 'Employee Id', name AS 'Name' FROM employees WHERE emp_id = 101;
```

**Result:**

| Employee Id | Name |
| ----------- | ---- |
| 101         | abc  |

---

### 🔹 Delete a specific row:

```sql
DELETE FROM employees WHERE emp_id = 102;
```

---

### 🔹 Current table data:

```sql
SELECT * FROM employees;
```

**Result:**

| emp\_id | name | desig      | dept    |
| ------- | ---- | ---------- | ------- |
| 101     | abc  | Manager    | Loan    |
| 103     | GHI  | Associate  | IT      |
| 104     | JKL  | Accountant | Account |
| 105     | pqr  | Associate  | Deposit |

---

## 🔍 **Identify the Column with a Common Value**

Look at the `desig` column:

* Values:

  * Manager
  * Associate ✅
  * Accountant
  * Associate ✅

> ✅ **Conclusion: `desig` has a common value: `Associate` appears more than once.**


