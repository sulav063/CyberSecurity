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

Example – Creating a `users` table:*