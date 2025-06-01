---

# 🧪 MySQL Docker Setup for Data Scientists (with MySQL Workbench)

As a data scientist, setting up a local MySQL environment allows you to store, query, and manipulate structured datasets efficiently — all while ensuring reproducibility. This guide shows how to set up MySQL using Docker Compose, with persistent storage and connection access through **MySQL Workbench** or the **MySQL CLI**.

---

## 🎯 Why This Setup?

* ✅ **Reproducible:** Shareable environment configuration using Docker and `.env`
* ✅ **Persistent:** Data is stored in Docker volumes and survives container restarts
* ✅ **Workbench-Compatible:** Easily connect from desktop GUI (MySQL Workbench)
* ✅ **Command-Line Ready:** Run ad hoc queries or automation via MySQL CLI

---

## 🗂️ 1. Setup Files

### 📁 `.env` — Configuration

This file defines your MySQL credentials and database setup. Create a file named `.env`:

```env
MYSQL_ROOT_PASSWORD=rootpass
MYSQL_DATABASE=myappdb
MYSQL_USER=myuser
MYSQL_PASSWORD=userpass
```

---

### 📁 `docker-compose.yml` — Docker Services

This file sets up the MySQL container and persistent storage:

```yaml
version: '3.8'

services:
  mysql:
    image: mysql:8.0
    container_name: mysql_container
    restart: unless-stopped
    env_file: .env
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
```

---

## 🚀 Launch the Environment

In the terminal, navigate to the directory containing both files, then run:

```bash
docker compose up -d
```

This starts the MySQL container in detached mode (in the background).

---

## 🧑‍💻 How to Access the Database

### 🔹 Option 1: Use **MySQL Workbench**

1. Open **MySQL Workbench**
2. Click **+** to create a new connection
3. Fill in the connection details:

   * **Connection Name:** `MySQL Docker`
   * **Hostname:** `127.0.0.1`
   * **Port:** `3306`
   * **Username:** `myuser` *(or `root`)*
   * **Password:** Stored securely (from `.env`)
4. Click **Test Connection**, then **Connect**

You can now browse tables, run SQL queries, and manage your database visually.

---

### 🔹 Option 2: Use **MySQL CLI** (Command Line)

For direct access through the terminal:

```bash
docker exec -it mysql_container mysql -u root -p
```

* You'll be prompted for the root password (`rootpass` from `.env`)
* Sample commands:

  ```sql
  SHOW DATABASES;
  USE myappdb;
  SHOW TABLES;
  ```

---

## 💡 Tips for Data Scientists

* 🐍 Connect from Python using `pymysql` or `sqlalchemy` on `localhost:3306`
* 🧪 Use this containerized DB to simulate production pipelines or build ETL prototypes
* 📊 Store feature sets, results, or metadata cleanly during iterative experiments
* 🔄 The `mysql_data` volume keeps your data even if the container stops or is rebuilt

---

