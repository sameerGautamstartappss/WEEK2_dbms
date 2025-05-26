# WEEK2_dbms

## 📘 RDBMS & SQL - Day 1 Overview

Welcome to Day 1 of your RDBMS and SQL journey! This session introduces the core concepts of Relational Database Management Systems and essential SQL commands.

---

### 🗂️ RDBMS Overview

#### 📖 What is an RDBMS?
A **Relational Database Management System (RDBMS)** stores data in **tables (relations)**, where each table is made up of **rows** (records) and **columns** (fields). Relationships between data are maintained using **keys**.

---

#### ⭐ Key Features

- **ACID Properties** for transaction reliability:
    - **Atomicity**: All or nothing execution of transactions.
    - **Consistency**: Data remains valid before and after transactions.
    - **Isolation**: Transactions do not interfere with each other.
    - **Durability**: Committed data is permanently saved.

---

#### 🧬 Database Models

- **Hierarchical**: Tree-like structure.
- **Network**: Flexible, supports multiple relationships.
- **Relational**: Table-based, most widely used.

---

#### 🧱 Relational Concepts

- **Tables**: Store related data.
- **Rows**: Individual records.
- **Columns**: Attributes or fields.

---

#### 🔐 Data Integrity Constraints

- **Primary Key**: Uniquely identifies a row.
- **Foreign Key**: Links rows between tables.
- **Unique**: Ensures column values are distinct.
- **Not Null**: Disallows NULL values.

---

### 🛠️ SQL - Structured Query Language

#### 🏗️ DDL (Data Definition Language)

- `CREATE`: Create tables/databases.
- `ALTER`: Modify tables.
- `DROP`: Delete tables/databases.

---

#### ✍️ DML (Data Manipulation Language)

- `SELECT`: Retrieve data.
- `INSERT`: Add records.
- `UPDATE`: Modify records.
- `DELETE`: Remove records.

---

### 🔍 Basic SQL Queries

#### ✅ SELECT Statement

```sql
SELECT * FROM employees;
```

#### 🎯 WHERE Clause

```sql
SELECT * FROM employees WHERE department = 'HR';
```

#### 📊 ORDER BY Clause

```sql
SELECT * FROM employees ORDER BY salary DESC;
```

#### 🧹 DISTINCT Keyword

```sql
SELECT DISTINCT department FROM employees;
```
