A **database** is a structured system designed to **store, organize, retrieve, and manage data efficiently**. It allows users or applications to handle large volumes of data systematically, ensuring **accuracy, consistency, and accessibility**.

Key Points:
- Stores data in a **structured or semi-structured format**.
- Provides fast **retrieval** and **manipulation** of data.
- Ensures **data integrity** and **security**.
- Often interacts with **server-side applications** to provide dynamic content.

---
## Types of Databases
### 1. SQL Databases (Relational Databases)
SQL databases store data in **tables with rows and columns**. They use **Structured Query Language (SQL)** to create, read, update, and delete data.

**Features:**
- Structured **table-based** storage.
- **Fixed schema**: the structure of tables is predefined.
- Ensures **data integrity and consistency** through relationships and constraints.
- Supports **ACID properties** (Atomicity, Consistency, Isolation, Durability)

Examples:
- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle Database

Use Case:
Finance, banking, inventory management, enterprise systems where data integrity is critical.

Example SQL Query:
```bash
SELECT u.name, u.email, COUNT(o.id) AS total_orders
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE u.status = 'active'
GROUP BY u.name, u.email
HAVING COUNT(o.id) > 5
ORDER BY total_orders DESC;
```

- `JOIN`: Combines **users** and **orders** tables.
- `WHERE`: Filters only **active users**.
- `GROUP BY`: Groups results by user.
- `COUNT()`: Counts total orders per user.
- `HAVING`: Filters users with **more than 5 orders**.
- `ORDER BY`: Sorts users by number of orders in **descending order**.

---

### 2. NoSQL Databases (Non-Relational Databases)
NoSQL databases store data in **flexible, non-tabular formats**, such as **documents, key-value pairs, or graphs**. They are designed for **high performance and scalability**, especially for large and dynamic datasets.

Features:
- Schema-less or **flexible schema**.
- High **horizontal scalability** (easy to distribute across servers).
- Handles **big data** and **real-time applications** efficiently.
- Optimized for **speed and performance** rather than strict relationships.

Examples:
- MongoDB (document-based)
- Redis (key-value store)
- Cassandra (column-based)
- Neo4j (graph-based)

Use Case:
Big data, IoT, real-time analytics, social media platforms.

Example NoSQL Document (MongoDB):
```bash
{     
	"name": "Alice",
	"email": "alice@example.com",
	"status": "active"
}
```

----
## SQL vs NoSQL
|Factor|SQL (Relational)|NoSQL (Non-Relational)|
|---|---|---|
|**Data Structure**|Table-based (rows & columns)|Document-based, key-value, graph, or column-family|
|**Schema**|Fixed, predefined|Flexible, dynamic schema|
|**Query Language**|SQL|No standard language (varies by DB, e.g., MongoDB uses JSON queries)|
|**Scalability**|Vertical scaling (upgrade server hardware)|Horizontal scaling (add more servers)|
|**Consistency**|Strong consistency|Eventual consistency (some DBs allow tunable consistency)|
|**Transactions**|Supports ACID properties|Limited or BASE properties (Basically Available, Soft state, Eventual consistency)|
|**Performance**|Good for structured data & complex queries|High performance for large or unstructured data|
|**Use Case**|Finance, banks, ERP, inventory management|Big data, IoT, social media, real-time apps|
|**Examples**|MySQL, PostgreSQL, Oracle|MongoDB, Redis, Cassandra, Neo4j|
|**Data Relationships**|Supports complex joins and relationships|Relationships often managed in application code|
|**Flexibility**|Less flexible – schema changes require migrations|Highly flexible – schema can evolve easily|
|**Storage**|Relational tables|Documents, key-value pairs, graphs, columns|