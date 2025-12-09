MySQL is an **open-source relational database management system (RDBMS)** that uses **Structured Query Language (SQL)** to manage and manipulate relational databases. It allows you to store, organize, retrieve, and update data efficiently.

Key Points:
- Developed by **Oracle Corporation** (originally by MySQL AB).
- Works on multiple platforms (Windows, Linux, macOS).
- Uses **tables, rows, and columns** to store data.
- Supports **ACID properties** (Atomicity, Consistency, Isolation, Durability) for reliable transactions.
- Often used with **web applications** (like WordPress, e-commerce sites) and **server-side programming** (PHP, Python, NodeJS).
---
### Features of MySQL
- **Open-source and free** with optional commercial versions.
- **High performance** for large datasets.
- **Secure** with user authentication and access control.
- **Cross-platform** support.
- **Supports multiple storage engines**, e.g., InnoDB (supports transactions) and MyISAM (fast reads).
- **Scalable** for small apps to enterprise-level systems.
- **Integration with programming languages** like PHP, Python, Java, NodeJS.
- Supports **replication, clustering, and backup** for data reliability.

---
### Common MySQL Commands
| Command                                               | Description                                |
| ----------------------------------------------------- | ------------------------------------------ |
| `SHOW DATABASES;`                                     | Lists all databases on the server.         |
| `USE database_name;`                                  | Selects a database to work with.           |
| `SHOW TABLES;`                                        | Lists all tables in the selected database. |
| `SELECT * FROM table_name;`                           | Retrieves all data from a table.           |
| `UPDATE table_name SET column=value WHERE condition;` | Updates existing data in a table.          |
| `DELETE FROM table_name WHERE condition;`             | Deletes rows from a table.                 |
| `DROP TABLE table_name;`                              | Deletes a table permanently.               |
| `CREATE DATABASE database_name;`                      | Creates a new database.                    |

---
### ## Creating a Table in MySQL

```
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
- `id INT AUTO_INCREMENT PRIMARY KEY` → Unique identifier that increments automatically.
- `name VARCHAR(50) NOT NULL` → Name column, max 50 characters, cannot be empty.
- `email VARCHAR(100) UNIQUE NOT NULL` → Email must be unique.
- `created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP` → Records creation time automatically.

### Inserting Data into Table
```
INSERT INTO users (name, email)
VALUES ('Alice', 'alice@example.com'),
       ('Bob', 'bob@example.com');
```

### Querying Data (Select Example)
```
SELECT id, name, email 
FROM users 
WHERE id > 1
ORDER BY name ASC;
```
- `WHERE` → Filters records (id > 1).
- `ORDER BY` → Sorts results alphabetically by `name`.

### Updating Data
```
UPDATE users 
SET email = 'alice_new@example.com' 
WHERE name = 'Alice';
```
Updates Alice’s email in the table.

### Deleting Data
```
DELETE FROM users 
WHERE name = 'Bob';
```
Deletes Bob’s record from the table.

---
## Why Use MySQL?
- Reliable and proven **RDBMS** for web and enterprise apps.
- Supports **complex queries, joins, and transactions**.
- Works well with **server-side languages** like PHP, Python, and NodeJS.
- Provides **data security** and **backup options**.
- Easy to learn for beginners, yet powerful for advanced developers.
---
