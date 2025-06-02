

---

### **Database & DBMS**

* A **Database** is an organized collection of data. It provides a method to **store**, **manipulate**, and **access** data.
* A **Database Management System (DBMS)** is software used to **manage**, **fetch**, and **manipulate** data in a database.

  * Examples: MySQL, Oracle, etc.

---

### **Types of Data in the Digital Age**

* Data can be broadly categorized into **Operational Data** and **Analytical Data**:

1. **Operational Data**:

   * Used for day-to-day transactions.
   * Needs to be **fresh** (real-time), e.g., product inventory or bank balance.
   * Captured in real-time using **OLTP (Online Transaction Processing)** systems.

2. **Analytical Data**:

   * Used for insights such as customer behavior, product performance, and forecasting.
   * Collected over time.
   * Stored in **OLAP (Online Analytical Processing)** systems, data warehouses, or data lakes.

> Most businesses use both **OLTP** (for operations) and **OLAP** (for analytics), and may use **relational**, **non-relational**, or a combination of both types of databases.

---

### **RDBMS (Relational Database Management System)**

* Software that allows interaction with **relational databases**.
* A collection of programs that allow developers to manage **tabular data** without knowing the physical storage details.
* **SQL (Structured Query Language)** is the language used to interact with RDBMS.

---

### **Data Storage in RDBMS**

* RDBMS allows the creation of **relational tables** to store and retrieve data.
* Manages how data is:

  * **Organized** on disk.
  * **Located** on disk.
  * **Moved/updated** during operations.
  * **Deleted** and how **empty spaces** are handled.
* Data and tables are stored in **database files**.

---

### **Structure of a Table**

* A **table** is a collection of **rows** (records) and **columns** (fields).
* A column with unique values is called a **Primary Key**.
* When a primary key from one table is used in another, it becomes a **Foreign Key** in the second table.

---

### **SQL Overview**

* SQL is used for **CRUD** operations:

  * **Create**
  * **Read**
  * **Update**
  * **Delete**

* A table can have **only one primary key**, but that key can span **multiple columns**.

---

### **Popular Databases**

* Relational: MySQL, Oracle, SQLite, PostgreSQL, MaxDB, Firebird
* Non-relational: MongoDB, Redis

---

### **MySQL Basics**

* **MySQL** is a DBMS that uses **SQL** to interact with databases.

#### SQL Commands:

```sql
-- Select the database to use
USE <database_name>;

-- Check current database
SELECT DATABASE();

-- Delete a database
DROP DATABASE <database_name>;

-- Create a table
CREATE TABLE <table_name> (
    <column_name> <data_type>,
    <column_name> <data_type>
);

-- View all tables
SHOW TABLES;

-- View structure of a table
DESC <table_name>;

-- Insert data into table
INSERT INTO <table_name>(<column1>, <column2>)
VALUES (<value1>, <value2>);

-- Insert in default column order
INSERT INTO <table_name>
VALUES (<value1>, <value2>);

-- Insert multiple rows
INSERT INTO <table_name>
VALUES 
(<value1>, <value2>),
(<value1>, <value2>),
(<value1>, <value2>);
```

---

### **Reading Data**

```sql
-- Read all data
SELECT * FROM <table_name>;

-- Read one column
SELECT <column_name> FROM <table_name>;

-- Read multiple columns
SELECT <column1>, <column2> FROM <table_name>;

-- Read with a condition
SELECT * FROM <table_name> WHERE <column_name> = <value>;
```

---

### **Updating & Deleting Data**

```sql
-- Update data
UPDATE <table_name>
SET <column_name> = <new_value>
WHERE <column_name> = <condition>;

-- Delete data
DELETE FROM <table_name>
WHERE <column_name> = <value>;
```

---

### **Constraints and Defaults**

* **NOT NULL** ensures a column must have a value.

```sql
CREATE TABLE <table_name> (
    <column1> <data_type> NOT NULL,
    <column2> <data_type> NOT NULL
);
```

* By default, all columns can have `NULL` values unless specified.
* To set a **default value**:

```sql
CREATE TABLE <table_name> (
    <column1> <data_type> DEFAULT <default_value>,
    <column2> <data_type>
);
```

> **Important Note**:
> If you set a default value without specifying `NOT NULL`, MySQL:
>
> * Uses the default **only** when:
>
>   * The column is **omitted** in the `INSERT` statement.
>   * You **don’t explicitly insert `NULL`** into that column.

---

### **Modifying Table Structure**

```sql
-- Add columns
ALTER TABLE <table_name>
ADD COLUMN <column1> <data_type> CONSTRAINTS,
ADD COLUMN <column2> <data_type> CONSTRAINTS;

-- Delete columns
ALTER TABLE <table_name>
DROP COLUMN <column1>,
DROP COLUMN <column2>;
```
---

# 🌟 **Primary Keys in SQL**

## 🔑 What is a Primary Key?

In **database management**, a **primary key** is a **column or set of columns** that uniquely identifies each row in a table.

> ✅ A primary key ensures that **every row is unique** and **not null**, which is essential for maintaining **data integrity**.
>
> 🔁 It serves as the main reference point for operations like **searching**, **updating**, and **deleting** records.
>
> 🔗 In **relational databases**, it is used to **link tables** and form **relationships** between datasets.

---

## 🧱 Four Pillars of Data Integrity

1. **Accuracy** – Data is free from errors and correct.
2. **Completeness** – All necessary data is present; no missing values.
3. **Consistency** – Data values are in agreement and follow defined rules.
4. **Validity** – Data conforms to the correct **format and type** (e.g., date, email).

> ✅ When all four are maintained, **trust** is built with customers and stakeholders.

---

## 📏 Constraints of a Primary Key

* **Unique Values**: No duplicate values allowed.
* **Not NULL**: A primary key cannot contain `NULL`.
* **One per Table**: Only one primary key per table, which can be a single column or a **composite key**.
* **Non-numeric Allowed**: Though often integers, keys can be text, binary, or dates.

  > 🔍 Consider **performance** with non-numeric keys (e.g., more space & slower indexing).

---

## 🧩 Composite Keys

A **composite key** uses **multiple columns** when no single column is unique.

**Example:**

```sql
CREATE TABLE enrollments (
  StudentID INT,
  CourseID INT,
  PRIMARY KEY (StudentID, CourseID)
);
```

> This ensures uniqueness in **student-course combinations**.

---

## 🛠 Creating a Primary Key

### ✅ During Table Creation:

```sql
CREATE TABLE employee (
  employeeID INT NOT NULL,
  lastName VARCHAR(255) NOT NULL,
  firstName VARCHAR(255) NOT NULL,
  PRIMARY KEY (employeeID)
);
```

### 🔁 On an Existing Table:

```sql
ALTER TABLE employee ADD PRIMARY KEY (employeeID);
```

---

## Dropping a Primary Key

```sql
ALTER TABLE employee DROP PRIMARY KEY;
```

---

## 📊 Data Types for Primary Keys

* **INT / BIGINT** – most efficient (used with `AUTO_INCREMENT`)
* **VARCHAR / CHAR** – possible but less performant
* **DATE / BINARY** – rare but allowed

> Ensure the type matches the uniqueness and indexing strategy.

---

## ⚙️ AUTO\_INCREMENT in MySQL

Used for automatically generating **incrementing unique values** (typically in primary keys).

### ✅ When Creating a Table:

```sql
CREATE TABLE employees (
  id INT AUTO_INCREMENT,
  name VARCHAR(100),
  position VARCHAR(100),
  PRIMARY KEY (id)
);
```

### 🔁 Modifying an Existing Table:

**a) Add a new column with AUTO\_INCREMENT:**

```sql
ALTER TABLE employees
ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY;
```

**b) Modify an existing column:**

```sql
ALTER TABLE employees 
MODIFY COLUMN id INT AUTO_INCREMENT;
```

**c) Set Starting Value:**

```sql
ALTER TABLE employees AUTO_INCREMENT = 1000;
```

> 🔔 AUTO\_INCREMENT must be on a column that is **PRIMARY KEY or UNIQUE**.

---

## 🧪 Notes on NULL Values

| Value Type      | Length Result |
| --------------- | ------------- |
| `NULL` (SQL)    | `NULL`        |
| `"NULL"` (text) | `4`           |

**Test Example:**

```sql
SELECT id, name, account_type, LENGTH(account_type) AS length 
FROM customers WHERE id = 1;
```

---

## ⚠️ SQL CASE Syntax Reminder

No commas between `WHEN` clauses.

```sql
SELECT name,
  CASE 
    WHEN salary > 50000 THEN 'High'
    WHEN salary BETWEEN 30000 AND 50000 THEN 'Medium'
    ELSE 'Low'
  END AS salary_range
FROM employees;
```

---

## 📎 Working with ALIAS

Aliases rename columns or tables **temporarily** in the query result.

**Example:**

```sql
SELECT firstName AS 'First Name', lastName AS 'Last Name'
FROM employee;
```

---

In MySQL:

> **`NOT NULL` only prevents `NULL` values — it does not prevent empty strings (`''`).**

So when you see rows with an empty `first_name` even though the column is `NOT NULL`, it’s **not a bug** — because `''` is a valid, non-NULL string.

---

### 👉 To ensure `first_name` is not empty:

* Use a `CHECK` constraint like `CHECK (first_name <> '')` (MySQL 8.0.16+), **or**
* Create a `BEFORE INSERT` trigger to block empty strings in older versions.

---

### 🔹 **Command:**

```sql
TRUNCATE TABLE customers_one;
```

### 🧾 What it Does:

* **Deletes all rows** from the `customers_one` table.
* **Resets** any `AUTO_INCREMENT` counter back to its initial value (usually 1).
* Unlike `DELETE FROM customers_one;`, `TRUNCATE` is:

  * Much **faster**
  * Uses **less logging**
  * Cannot be **rolled back** (if you're not in a transaction-safe mode)

---

### 🔹 **Command:**

```sql
SELECT * FROM customers_one;
```

### 🧾 What it Shows:

* Returns an **empty result**, confirming that **all rows were removed** from the table.

---


## 📚 **MySQL String Functions**

* ✅ **Used primarily with `VARCHAR`, `CHAR`, and string-based columns.**
* ✅ **Typically used during data retrieval (`SELECT`) to format or combine string values.**

---

### 🔹 **1. `CONCAT()`**

The `CONCAT()` function joins two or more strings together into a single string.

#### 🧩 **Syntax:**

```sql
SELECT CONCAT(string1, string2, ...);
```

or when working with table columns:

```sql
SELECT CONCAT(column1, column2, ...) FROM table_name;
```

---

### 🔍 **Examples:**

#### ✅ Concatenating literal strings:

```sql
SELECT CONCAT('Hello', 'World');
```

**Result:**

```
HelloWorld
```

#### ✅ Concatenating column values (no space):

```sql
SELECT emp_id, CONCAT(first_name, last_name) AS 'Full name' FROM employees;
```

**Output:**

| emp\_id | Full name |
| ------- | --------- |
| 101     | ABCDEF    |
| 102     | UVWXYZ    |
| 103     | JKLRST    |

#### ✅ Concatenating with space:

```sql
SELECT emp_id, CONCAT(first_name, ' ', last_name) AS 'Full name' FROM employees;
```

**Output:**

| emp\_id | Full name |
| ------- | --------- |
| 101     | ABC DEF   |
| 102     | UVW XYZ   |
| 103     | JKL RST   |

---

### 🧠 **Key Notes:**

* You can concatenate any number of strings.
* If any argument is `NULL`, the result will be `NULL` unless `CONCAT_WS()` is used.
* `CONCAT()` is commonly used to display user-friendly names (like full names, addresses, etc.).

---

### 🔹 **2. `CONCAT_WS()`**

### 🧾 **Full Form:**

**WS = With Separator**

---

### ✅ **Purpose:**

Combines multiple strings into one, inserting a **separator** between them.
Unlike `CONCAT()`, it **ignores `NULL` values** instead of returning `NULL`.

---

### 🛠️ **Syntax:**

```sql
SELECT CONCAT_WS('separator', string1, string2, ...);
```

* **`'separator'`**: A character or string like `' '`, `':'`, `'&'`, `'#'` used to separate the values.
* **`string1, string2, ...`**: Columns or literal strings to concatenate.

---

## 🧪 **Examples using `employees` table:**

| emp\_id | first\_name | last\_name | desig     | dept |
| ------- | ----------- | ---------- | --------- | ---- |
| 101     | ABC         | DEF        | Manager   | Loan |
| 102     | UVW         | XYZ        | Cashier   | Cash |
| 103     | JKL         | RST        | Associate | Cash |

---

### 🔸 Example 1: Using Colon `:` as Separator

```sql
SELECT CONCAT_WS(':', emp_id, first_name, last_name, desig, dept) FROM employees;
```

| Output                         |
| ------------------------------ |
| 101\:ABC\:DEF\:Manager\:Loan   |
| 102\:UVW\:XYZ\:Cashier\:Cash   |
| 103\:JKL\:RST\:Associate\:Cash |

---

### 🔸 Example 2: Using Ampersand `&` as Separator

```sql
SELECT CONCAT_WS('&', emp_id, first_name, last_name, desig, dept) FROM employees;
```

| Output                         |
| ------------------------------ |
| 101\&ABC\&DEF\&Manager\&Loan   |
| 102\&UVW\&XYZ\&Cashier\&Cash   |
| 103\&JKL\&RST\&Associate\&Cash |

---

### 🔸 Example 3: Using Hash `#` as Separator

```sql
SELECT CONCAT_WS('#', emp_id, first_name, last_name, desig, dept) FROM employees;
```

| Output                     |
| -------------------------- |
| 101#ABC#DEF#Manager#Loan   |
| 102#UVW#XYZ#Cashier#Cash   |
| 103#JKL#RST#Associate#Cash |

---

### 🧠 **Key Points to Remember:**

* ✅ Automatically skips `NULL` values.
* ✅ Cleaner and safer than `CONCAT()` when working with optional fields.
* ✅ Widely used in formatting export strings, logs, key-value pairs, etc.

---
  


Here's the **final, complete guide** to MySQL’s `SUBSTRING()` function, fully integrated with **literal examples, table queries, positive & negative indexing**, and **real-world use cases** — organized systematically for learning or reference.

---

# 📘 MySQL String Function: `SUBSTRING()`

---

## 🧠 1. Purpose

The `SUBSTRING()` function extracts a specific part of a string based on position and optional length.

---

## 🧾 2. Syntax

```sql
SUBSTRING(string, start_position , length)
```

* `start_position`:

  * **Positive** — starts from the beginning (1-based).
  * **Negative** — starts from the end.
* `length` *(optional)* — how many characters to return.

🟡 Alias: `SUBSTR()` does the same.

---

## 🔍 3. Examples Using Literal Strings

### ▶️ A. Positive Indexing

```sql
SELECT SUBSTRING('hello Duniya', 1, 7);
```

| Result  |
| ------- |
| hello D |

```sql
SELECT SUBSTRING('hello Duniya', 3, 12);
```

| Result     |
| ---------- |
| llo Duniya |

```sql
SELECT SUBSTRING('hello Duniya', 5, 12);
```

| Result   |
| -------- |
| o Duniya |

```sql
SELECT SUBSTRING('hello Duniya', 7);
```

| Result |
| ------ |
| Duniya |

```sql
SELECT SUBSTRING('hello Duniya', 7, 12);
```

| Result |
| ------ |
| Duniya |

---

### ▶️ B. Negative Indexing

```sql
SELECT SUBSTRING('Hello Duniya', -6);
```

| Result |
| ------ |
| Duniya |

---

## 🧱 4. Examples Using Real Table: `employees`

### 🗂 Table: `employees`

| emp\_id | first\_name | last\_name | desig     | dept |
| ------- | ----------- | ---------- | --------- | ---- |
| 101     | ABC         | DEF        | Manager   | Loan |
| 102     | UVW         | XYZ        | Cashier   | Cash |
| 103     | JKL         | RST        | Associate | Cash |

---

### ▶️ A. Extracting Rightmost 2 Digits from `emp_id`

```sql
SELECT SUBSTRING(emp_id, -2) AS 'Emp Id', first_name FROM employees;
```

| Emp Id | first\_name |
| ------ | ----------- |
| 01     | ABC         |
| 02     | UVW         |
| 03     | JKL         |

---

### ▶️ B. Extracting from 3rd Character of `emp_id`

```sql
SELECT SUBSTRING(emp_id, 3) AS 'Emp Id', first_name AS 'First Name' FROM employees;
```

| Emp Id | First Name |
| ------ | ---------- |
| 1      | ABC        |
| 2      | UVW        |
| 3      | JKL        |

---

### ▶️ C. From Subquery (One Row Only)

```sql
SELECT SUBSTRING(
  (SELECT CONCAT('$', emp_id, first_name, last_name, desig, dept)
   FROM employees LIMIT 1),
  1, 5
);
```

| Result  |
| ------- |
| \$101AB |

---

### ▶️ D. Using `CONCAT_WS()` with Delimiter

```sql
SELECT SUBSTRING(
  (SELECT CONCAT_WS('&', first_name, last_name, desig, dept)
   FROM employees LIMIT 1),
  1, 15
);
```

| Result            |
| ----------------- |
| ABC\&DEF\&Manager |

---

### ▶️ E. Row-wise `SUBSTRING` from All Employee Fields

```sql
SELECT SUBSTRING(CONCAT_WS('&', emp_id, first_name, last_name, desig, dept), 1, 16)
FROM employees;
```

| Output              |
| ------------------- |
| 101\&ABC\&DEF\&Mana |
| 102\&UVW\&XYZ\&Cash |
| 103\&JKL\&RST\&Asso |

---

## 🧾 5. Summary Table

| Example                                 | Output         | Notes                        |
| --------------------------------------- | -------------- | ---------------------------- |
| `SUBSTRING('hello Duniya', 1, 7)`       | `hello D`      | First 7 characters           |
| `SUBSTRING('hello Duniya', 7)`          | `Duniya`       | From 7th char to end         |
| `SUBSTRING('Hello Duniya', -6)`         | `Duniya`       | 6 characters from the end    |
| `SUBSTRING(emp_id, -2)`                 | `01`, `02`...  | Last 2 digits of `emp_id`    |
| `SUBSTRING(emp_id, 3)`                  | `1`, `2`...    | 3rd character onward         |
| `SUBSTRING((SELECT ... LIMIT 1), 1, 5)` | `one row only` | Subquery must return one row |
| `SUBSTRING(CONCAT_WS(...), 1, 16)`      | `trimmed row`  | Combines fields then slices  |

---


