

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
