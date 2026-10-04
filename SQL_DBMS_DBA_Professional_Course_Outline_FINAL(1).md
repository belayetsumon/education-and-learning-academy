# SQL, Database Management System & DBA Professional Course

## Course Title
**SQL, Database Management System, NoSQL & DBA Professional Program**

## Course Level
Beginner → Intermediate → Advanced → Professional DBA

## Supported Database Platforms
- Oracle Database
- PostgreSQL
- Microsoft SQL Server
- MySQL
- MongoDB
- Redis

## Supporting Technologies
- Linux
- Bash / PowerShell / Python
- Docker
- Flyway / Liquibase
- Cloud Databases
- High Availability
- Backup & Recovery
- Performance Tuning
- Database Security
- Replication
- Monitoring

---

# 1. Learning Path

```text
Database Fundamentals
        ↓
SQL Basic
        ↓
SQL Intermediate
        ↓
Advanced SQL
        ↓
Professional SQL
        ↓
SQL Performance
        ↓
Database Internals
        ↓
DBA Fundamentals
        ↓
Vendor DBA Specialization
        ↓
Backup & Recovery
        ↓
Security
        ↓
Performance Tuning
        ↓
Replication / HA / DR
        ↓
NoSQL
        ↓
Linux + Automation
        ↓
Cloud Database
        ↓
Enterprise Database Engineering
```

---

# 2. Track 1 — Database & DBMS Fundamentals

## Module 1: Introduction to Databases

### Topics
- What is data?
- Database vs file system
- DBMS vs RDBMS
- SQL vs NoSQL
- OLTP vs OLAP
- Structured data
- Semi-structured data
- Unstructured data
- Database server architecture
- Client/server architecture
- Database users
- DBA responsibilities
- Database developer responsibilities
- Data engineer responsibilities

---

## Module 2: Relational Database Fundamentals

### Topics
- Tables
- Rows
- Columns
- Data types
- Primary key
- Foreign key
- Candidate key
- Composite key
- Unique constraint
- NULL
- Referential integrity

### Relationships
- One-to-One
- One-to-Many
- Many-to-Many

---

## Module 3: Database Design Fundamentals

### Topics
- Requirement analysis
- Entity
- Attribute
- Relationship
- ER diagrams
- Logical database design
- Physical database design
- Normalization
- 1NF
- 2NF
- 3NF
- BCNF
- Denormalization
- Database naming standards

---

# 3. Track 2 — SQL Basic

## Module 4: SQL Environment

- Create database
- Create schema
- Create table
- Data types
- SQL syntax
- SQL comments
- Database objects

## Module 5: Basic SELECT

- SELECT
- FROM
- WHERE
- DISTINCT
- ORDER BY
- Column aliases
- Expressions
- NULL handling

## Module 6: Filtering Data

- Comparison operators
- AND
- OR
- NOT
- BETWEEN
- IN
- LIKE
- Wildcards
- IS NULL
- Boolean expressions

## Module 7: SQL Functions

- String functions
- Numeric functions
- Date/time functions
- Conversion functions
- NULL-handling functions
- CASE expressions

## Module 8: Aggregate SQL

- COUNT
- SUM
- AVG
- MIN
- MAX
- GROUP BY
- HAVING

## Module 9: Joining Tables

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN
- CROSS JOIN
- SELF JOIN
- Multiple-table joins

## Module 10: Data Modification

- INSERT
- UPDATE
- DELETE
- TRUNCATE
- MERGE concepts
- Transactions during DML

---

# 4. Track 3 — Intermediate SQL

## Module 11: Subqueries

- Scalar subquery
- Multiple-row subquery
- Correlated subquery
- EXISTS
- NOT EXISTS
- IN vs EXISTS
- Nested queries

## Module 12: Set Operations

- UNION
- UNION ALL
- INTERSECT
- EXCEPT
- Oracle MINUS

## Module 13: Database Objects

- Views
- Materialized views
- Sequences
- Identity columns
- Indexes
- Synonyms
- Temporary tables

## Module 14: Constraints

- PRIMARY KEY
- FOREIGN KEY
- UNIQUE
- NOT NULL
- CHECK
- DEFAULT
- Cascading operations

## Module 15: Transactions

- ACID
- COMMIT
- ROLLBACK
- SAVEPOINT
- Transaction isolation levels
- Dirty reads
- Non-repeatable reads
- Phantom reads

---

# 5. Track 4 — Advanced SQL

## Module 16: Common Table Expressions

- CTE
- Multiple CTEs
- Recursive CTE
- Hierarchical data
- Tree structures

## Module 17: Window and Analytical Functions

- OVER()
- PARTITION BY
- ORDER BY
- ROW_NUMBER()
- RANK()
- DENSE_RANK()
- NTILE()
- LAG()
- LEAD()
- FIRST_VALUE()
- LAST_VALUE()
- Running totals
- Moving averages

## Module 18: Advanced Query Techniques

- Conditional aggregation
- Pivoting
- Unpivoting
- Dynamic reporting
- Complex joins
- Relational division
- Anti-joins
- Semi-joins
- Greatest-N-per-group
- Gap-and-island problems

## Module 19: Advanced DML

- MERGE
- UPSERT
- Bulk insert
- Bulk update
- Batch processing
- Returning generated values
- Error handling

---

# 6. Track 5 — Professional SQL Development

## Module 20: Stored Programming

| Concept | Oracle | PostgreSQL | SQL Server | MySQL |
|---|---|---|---|---|
| Stored language | PL/SQL | PL/pgSQL | T-SQL | Stored Program SQL |
| Procedures | Yes | Yes | Yes | Yes |
| Functions | Yes | Yes | Yes | Yes |
| Triggers | Yes | Yes | Yes | Yes |

### Topics
- Variables
- Conditions
- Loops
- Cursors
- Procedures
- Functions
- Packages
- Exception handling
- Dynamic SQL
- Triggers

## Module 21: Professional Database Programming

- Transaction-safe code
- Idempotency
- Optimistic locking
- Pessimistic locking
- Concurrency handling
- Audit tables
- History tables
- Soft delete
- Temporal data
- Generated columns
- JSON processing

---

# 7. Track 6 — SQL Performance Engineering

## Module 22: Index Fundamentals

- B-tree
- Hash
- Bitmap
- Composite index
- Covering index
- Partial / filtered index
- Function-based index
- Clustered index
- Nonclustered index
- Index selectivity
- Cardinality

## Module 23: Query Execution

- SQL parser
- Optimizer
- Cost-based optimization
- Statistics
- Execution plans
- Table scans
- Index scans
- Index seeks
- Nested loop join
- Hash join
- Merge join

## Module 24: Query Optimization

```text
Slow Query
    ↓
Execution Plan
    ↓
Statistics
    ↓
Indexes
    ↓
Join Strategy
    ↓
SQL Rewrite
    ↓
Re-test
```

### Topics
- SARGability
- Predicate optimization
- Query rewriting
- Pagination optimization
- Large-table querying
- Partition pruning
- Parameter-related performance issues

---

# 8. Track 7 — Database Architecture & Internals

## Module 25: Database Internal Architecture

### Core Concepts
- Instance
- Database
- Memory architecture
- Background processes
- Pages / blocks
- Data files
- Control files
- Log files
- WAL
- Redo
- Undo
- Buffer cache
- Shared memory
- Checkpoints

### Vendor Comparison

```text
Oracle       → SGA / PGA / Redo / Undo
PostgreSQL   → Shared Buffers / WAL / MVCC
SQL Server   → Buffer Pool / Transaction Log
MySQL        → InnoDB Buffer Pool / Redo / Undo
```

---

# 9. Track 8 — DBA Beginner

## Module 26: DBA Fundamentals

- DBA responsibilities
- Installation
- Configuration
- Instance management
- Database creation
- Startup and shutdown
- Configuration files
- Storage
- Users
- Roles
- Permissions
- Monitoring
- Logs

## Module 27: User & Security Administration

- Authentication
- Authorization
- Users
- Roles
- Privileges
- GRANT
- REVOKE
- Least privilege
- Password policies
- Service accounts
- Database ownership
- Schema security

---

# 10. Track 9 — Backup & Recovery

## Module 28: Backup Fundamentals

- Full backup
- Differential backup
- Incremental backup
- Logical backup
- Physical backup
- Online backup
- Offline backup
- Backup retention

### Oracle
- RMAN
- Data Pump

### PostgreSQL
- pg_dump
- pg_restore
- pg_basebackup
- WAL archiving

### SQL Server
- Full backup
- Differential backup
- Transaction-log backup

### MySQL
- mysqldump
- MySQL Shell
- Physical backup concepts

## Module 29: Recovery

- Crash recovery
- Point-in-time recovery
- Media recovery
- Accidental DELETE recovery
- Corruption recovery
- Disaster recovery

---

# 11. Track 10 — PostgreSQL DBA

- PostgreSQL architecture
- Cluster / database / schema structure
- `postgresql.conf`
- `pg_hba.conf`
- Roles
- Tablespaces
- WAL
- MVCC
- VACUUM
- AUTOVACUUM
- ANALYZE
- EXPLAIN
- EXPLAIN ANALYZE
- `pg_stat` views
- Locks
- Deadlocks
- Bloat
- Partitioning
- Extensions
- pg_dump / restore
- PITR
- Streaming replication
- Logical replication
- PgBouncer
- High availability concepts

---

# 12. Track 11 — Oracle DBA

## Architecture
- Instance
- Database
- SGA
- PGA
- Background processes
- Tablespaces
- Datafiles
- Control files
- Redo logs
- Undo
- Archived logs

## Administration
- Oracle installation
- Database creation
- SQL*Plus
- Users
- Profiles
- Roles
- Privileges
- Tablespaces
- Storage
- Listener
- Networking
- Data dictionary

## Backup & Recovery
- RMAN
- ARCHIVELOG
- Flashback
- Data Pump
- PITR

## Advanced
- AWR
- ASH
- Explain Plan
- SQL tuning
- Data Guard concepts
- RAC concepts
- ASM concepts

---

# 13. Track 12 — Microsoft SQL Server DBA

- SQL Server architecture
- Instance
- Database
- MDF / NDF / LDF
- TempDB
- SQL Server Agent
- SSMS
- Authentication
- Logins
- Users
- Roles
- T-SQL
- Execution plans
- Statistics
- Index maintenance
- Backup
- Restore
- Recovery models
- SQL Server Agent jobs
- Always On concepts
- Log shipping
- Replication
- Extended Events
- Query Store

---

# 14. Track 13 — MySQL DBA

- MySQL architecture
- Installation
- Configuration
- `my.cnf`
- MySQL Shell
- Users
- Privileges
- Storage engines
- InnoDB
- Buffer pool
- Redo
- Undo
- Binary log
- Slow query log
- EXPLAIN
- Indexing
- Backup
- Restore
- Replication
- Group Replication concepts
- InnoDB Cluster concepts

---

# 15. Track 14 — NoSQL Fundamentals

## Module 30: NoSQL Concepts

- Why NoSQL?
- CAP theorem
- BASE
- Eventual consistency
- Horizontal scaling
- Sharding
- Replication

```text
NoSQL
├── Document
├── Key-Value
├── Column-Family
└── Graph
```

| Type | Technology |
|---|---|
| Document | MongoDB |
| Key-value | Redis |
| Column-family | Cassandra |
| Graph | Neo4j |

---

# 16. Track 15 — MongoDB Beginner to Advanced

- Documents
- Collections
- BSON
- CRUD
- Query operators
- Projection
- Arrays
- Embedded documents
- Indexes
- Aggregation pipeline
- Schema design
- Transactions
- Replication
- Replica sets
- Sharding
- Backup
- Restore
- Security
- Monitoring
- Performance tuning

---

# 17. Track 16 — Redis

- Strings
- Hashes
- Lists
- Sets
- Sorted sets
- Streams
- TTL
- Transactions
- Pub/Sub
- Persistence
- RDB
- AOF
- Replication
- Sentinel
- Redis Cluster

### Practical Uses
- Cache
- Session
- OTP
- Rate limiting
- Distributed lock
- Leaderboard
- Queue
- Pub/Sub

---

# 18. Track 17 — Advanced DBA

## Module 31: Database Performance Administration

- CPU analysis
- Memory analysis
- Disk I/O
- Database waits
- Connection bottlenecks
- Lock contention
- Deadlocks
- Long-running queries
- Index fragmentation / bloat
- Statistics
- Capacity planning

## Module 32: Database Security

- Authentication
- Authorization
- Encryption at rest
- Encryption in transit
- TLS
- Data masking
- Auditing
- Row-level security
- Column-level security
- Secrets management
- Privileged account management
- SQL injection protection
- Compliance concepts

---

# 19. Track 18 — High Availability & Disaster Recovery

- HA vs DR
- RPO
- RTO
- Replication
- Synchronous replication
- Asynchronous replication
- Primary / replica
- Failover
- Switchover
- Quorum
- Split-brain
- Load balancing
- Backup-site strategy

```text
PostgreSQL → Streaming Replication
Oracle     → Data Guard / RAC
SQL Server → Always On
MySQL      → Replication / Group Replication
```

---

# 20. Track 19 — Enterprise Database Design

## Module 33: Enterprise Data Modeling

- OLTP design
- Master data
- Transaction tables
- Reference tables
- Audit structures
- Multi-tenancy
- Multi-company databases
- Multi-country architecture
- Currency handling
- Time zones
- Localization

## Module 34: Large Database Design

- Partitioning
- Sharding
- Archiving
- Data lifecycle management
- Billions-of-row strategies
- Hot / cold data
- Read replicas
- Distributed databases

---

# 21. Track 20 — Data Warehouse & Analytics Fundamentals

- OLTP vs OLAP
- Data warehouse
- Fact tables
- Dimension tables
- Star schema
- Snowflake schema
- Slowly changing dimensions
- ETL
- ELT
- Data marts
- Materialized views
- Analytical SQL

---

# 22. Track 21 — Linux for Database Administrators

- Linux filesystem
- Users and groups
- Permissions
- systemd
- SSH
- Processes
- Memory
- CPU
- Disks
- Networking
- Cron
- Logs
- Shell scripting

### Important Commands

```bash
top
htop
ps
df
du
free
iostat
vmstat
ss
netstat
systemctl
journalctl
grep
awk
sed
```

---

# 23. Track 22 — Database Automation

- Bash
- PowerShell
- Python fundamentals
- Scheduled maintenance
- Backup automation
- Monitoring scripts
- Automated health checks
- Automated reports
- Schema migrations
- Flyway
- Liquibase

---

# 24. Track 23 — Cloud Database Administration

## AWS
- Amazon RDS
- Aurora

## Microsoft Azure
- Azure SQL
- Azure Database for PostgreSQL
- Azure Database for MySQL

## Google Cloud
- Cloud SQL

### Topics
- Managed databases
- Automated backups
- Read replicas
- Failover
- Scaling
- Monitoring
- Encryption
- Cost optimization

---

# 25. Track 24 — DevOps for Databases

- Git
- Database version control
- Migration scripts
- CI/CD
- Docker
- Database containers
- Kubernetes database concepts
- Secrets
- Configuration management
- Infrastructure as Code concepts
- Zero-downtime migrations
- Blue/green database considerations

---

# 26. Track 25 — Production Troubleshooting Labs

Students should solve realistic incidents.

1. Database CPU reaches 100%.
2. A query suddenly becomes slow.
3. Disk usage reaches 95%.
4. Deadlocks occur.
5. A user accidentally deletes 500,000 records.
6. Primary database crashes.
7. Replication stops.
8. Backup cannot be restored.
9. Connection pool becomes exhausted.
10. Database becomes unavailable during peak traffic.

---

# 27. Track 26 — Professional DBA Operations

## Daily
- Database health checks
- Backup verification
- Replication verification
- Disk usage
- Failed jobs
- Blocking sessions
- Error logs

## Weekly
- Performance analysis
- Capacity trends
- Index health
- Slow SQL
- Security audit

## Monthly
- Restore test
- DR test
- Access review
- Capacity forecast
- Patch review

---

# 28. Recommended Certification Structure

| Level | Course | Approx. Hours |
|---|---|---:|
| 1 | Database & SQL Fundamentals | 40 |
| 2 | SQL Intermediate | 40 |
| 3 | Advanced SQL | 50 |
| 4 | Professional SQL & Performance | 60 |
| 5 | DBA Fundamentals | 60 |
| 6 | Vendor DBA Specialization | 120 |
| 7 | Advanced / Enterprise DBA | 80 |
| 8 | NoSQL, Cloud & Database Engineering | 80 |
| **Total** | **Complete Professional Program** | **~530 Hours** |

---

# 29. Practice Database

The following practice schema is designed to support:

- Beginner SELECT exercises
- JOIN exercises
- Aggregate exercises
- Subqueries
- CTEs
- Window functions
- Transactions
- Views
- Indexes
- Stored procedures
- Reporting
- Performance tuning
- DBA labs

The model represents a small multi-branch sales and inventory business.

---

# 30. Practice Database Tables

## Main Entities

```text
customers
employees
departments
branches
categories
products
suppliers
orders
order_items
payments
inventory
purchase_orders
purchase_order_items
```

## Relationship Overview

```text
departments
    ↓
employees

branches
    ↓
employees

customers
    ↓
orders
    ↓
order_items
    ↓
products
    ↓
categories

suppliers
    ↓
products

branches
    ↓
inventory
    ↓
products

purchase_orders
    ↓
purchase_order_items
    ↓
products
```

---

# 31. Practice Schema SQL

> The following SQL is intentionally close to standard SQL.  
> Minor syntax changes may be necessary for Oracle, PostgreSQL, SQL Server, and MySQL.

```sql
CREATE TABLE departments (
    department_id INTEGER PRIMARY KEY,
    department_name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE branches (
    branch_id INTEGER PRIMARY KEY,
    branch_name VARCHAR(100) NOT NULL,
    city VARCHAR(100) NOT NULL,
    country VARCHAR(100) NOT NULL
);

CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(120) UNIQUE,
    salary DECIMAL(12,2) NOT NULL,
    hire_date DATE NOT NULL,
    department_id INTEGER,
    branch_id INTEGER,
    manager_id INTEGER,
    FOREIGN KEY (department_id) REFERENCES departments(department_id),
    FOREIGN KEY (branch_id) REFERENCES branches(branch_id),
    FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
);

CREATE TABLE customers (
    customer_id INTEGER PRIMARY KEY,
    customer_name VARCHAR(150) NOT NULL,
    email VARCHAR(120) UNIQUE,
    phone VARCHAR(30),
    city VARCHAR(100),
    country VARCHAR(100),
    registration_date DATE NOT NULL,
    customer_status VARCHAR(20) DEFAULT 'ACTIVE'
);

CREATE TABLE categories (
    category_id INTEGER PRIMARY KEY,
    category_name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE suppliers (
    supplier_id INTEGER PRIMARY KEY,
    supplier_name VARCHAR(150) NOT NULL,
    contact_name VARCHAR(120),
    phone VARCHAR(30),
    city VARCHAR(100),
    country VARCHAR(100)
);

CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name VARCHAR(150) NOT NULL,
    category_id INTEGER NOT NULL,
    supplier_id INTEGER,
    unit_price DECIMAL(12,2) NOT NULL,
    cost_price DECIMAL(12,2) NOT NULL,
    stock_status VARCHAR(20) DEFAULT 'ACTIVE',
    FOREIGN KEY (category_id) REFERENCES categories(category_id),
    FOREIGN KEY (supplier_id) REFERENCES suppliers(supplier_id)
);

CREATE TABLE inventory (
    inventory_id INTEGER PRIMARY KEY,
    branch_id INTEGER NOT NULL,
    product_id INTEGER NOT NULL,
    quantity_on_hand INTEGER NOT NULL DEFAULT 0,
    reorder_level INTEGER NOT NULL DEFAULT 10,
    UNIQUE (branch_id, product_id),
    FOREIGN KEY (branch_id) REFERENCES branches(branch_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

CREATE TABLE orders (
    order_id INTEGER PRIMARY KEY,
    customer_id INTEGER NOT NULL,
    employee_id INTEGER,
    branch_id INTEGER NOT NULL,
    order_date DATE NOT NULL,
    order_status VARCHAR(30) NOT NULL,
    discount_amount DECIMAL(12,2) DEFAULT 0,
    tax_amount DECIMAL(12,2) DEFAULT 0,
    shipping_amount DECIMAL(12,2) DEFAULT 0,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id),
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id),
    FOREIGN KEY (branch_id) REFERENCES branches(branch_id)
);

CREATE TABLE order_items (
    order_item_id INTEGER PRIMARY KEY,
    order_id INTEGER NOT NULL,
    product_id INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(12,2) NOT NULL,
    discount_percent DECIMAL(5,2) DEFAULT 0,
    FOREIGN KEY (order_id) REFERENCES orders(order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);

CREATE TABLE payments (
    payment_id INTEGER PRIMARY KEY,
    order_id INTEGER NOT NULL,
    payment_date DATE NOT NULL,
    payment_method VARCHAR(30) NOT NULL,
    amount DECIMAL(12,2) NOT NULL,
    payment_status VARCHAR(20) NOT NULL,
    FOREIGN KEY (order_id) REFERENCES orders(order_id)
);

CREATE TABLE purchase_orders (
    purchase_order_id INTEGER PRIMARY KEY,
    supplier_id INTEGER NOT NULL,
    branch_id INTEGER NOT NULL,
    order_date DATE NOT NULL,
    expected_date DATE,
    purchase_status VARCHAR(30) NOT NULL,
    FOREIGN KEY (supplier_id) REFERENCES suppliers(supplier_id),
    FOREIGN KEY (branch_id) REFERENCES branches(branch_id)
);

CREATE TABLE purchase_order_items (
    purchase_order_item_id INTEGER PRIMARY KEY,
    purchase_order_id INTEGER NOT NULL,
    product_id INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    unit_cost DECIMAL(12,2) NOT NULL,
    FOREIGN KEY (purchase_order_id) REFERENCES purchase_orders(purchase_order_id),
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
```

---

# 32. Seed Data

## Departments

```sql
INSERT INTO departments VALUES (1, 'Management');
INSERT INTO departments VALUES (2, 'Sales');
INSERT INTO departments VALUES (3, 'Finance');
INSERT INTO departments VALUES (4, 'Information Technology');
INSERT INTO departments VALUES (5, 'Operations');
INSERT INTO departments VALUES (6, 'Procurement');
```

## Branches

```sql
INSERT INTO branches VALUES (1, 'Dhaka Head Office', 'Dhaka', 'Bangladesh');
INSERT INTO branches VALUES (2, 'Chattogram Branch', 'Chattogram', 'Bangladesh');
INSERT INTO branches VALUES (3, 'Khulna Branch', 'Khulna', 'Bangladesh');
INSERT INTO branches VALUES (4, 'Sylhet Branch', 'Sylhet', 'Bangladesh');
```

## Employees

```sql
INSERT INTO employees VALUES
(1, 'Rahim', 'Ahmed', 'rahim@example.com', 120000, '2021-01-15', 1, 1, NULL);

INSERT INTO employees VALUES
(2, 'Karim', 'Hossain', 'karim@example.com', 70000, '2022-03-10', 2, 1, 1);

INSERT INTO employees VALUES
(3, 'Nusrat', 'Jahan', 'nusrat@example.com', 75000, '2022-05-21', 3, 1, 1);

INSERT INTO employees VALUES
(4, 'Tanvir', 'Hasan', 'tanvir@example.com', 90000, '2021-11-05', 4, 1, 1);

INSERT INTO employees VALUES
(5, 'Sadia', 'Islam', 'sadia@example.com', 65000, '2023-02-12', 5, 2, 1);

INSERT INTO employees VALUES
(6, 'Imran', 'Khan', 'imran@example.com', 68000, '2023-08-01', 2, 2, 2);

INSERT INTO employees VALUES
(7, 'Maliha', 'Rahman', 'maliha@example.com', 62000, '2024-01-18', 6, 1, 1);

INSERT INTO employees VALUES
(8, 'Farhan', 'Ahmed', 'farhan@example.com', 60000, '2024-04-10', 2, 3, 2);
```

## Customers

```sql
INSERT INTO customers VALUES
(1, 'ABC Traders', 'abc@demo.com', '01710000001', 'Dhaka', 'Bangladesh', '2024-01-01', 'ACTIVE');

INSERT INTO customers VALUES
(2, 'Green Mart', 'green@demo.com', '01710000002', 'Chattogram', 'Bangladesh', '2024-01-10', 'ACTIVE');

INSERT INTO customers VALUES
(3, 'City Electronics', 'city@demo.com', '01710000003', 'Dhaka', 'Bangladesh', '2024-02-05', 'ACTIVE');

INSERT INTO customers VALUES
(4, 'Modern Office', 'modern@demo.com', '01710000004', 'Khulna', 'Bangladesh', '2024-03-12', 'ACTIVE');

INSERT INTO customers VALUES
(5, 'Smart Solutions', 'smart@demo.com', '01710000005', 'Sylhet', 'Bangladesh', '2024-04-01', 'ACTIVE');

INSERT INTO customers VALUES
(6, 'Digital Point', 'digital@demo.com', '01710000006', 'Dhaka', 'Bangladesh', '2024-04-15', 'ACTIVE');

INSERT INTO customers VALUES
(7, 'National Store', 'national@demo.com', '01710000007', 'Rajshahi', 'Bangladesh', '2024-05-20', 'INACTIVE');

INSERT INTO customers VALUES
(8, 'Tech World', 'techworld@demo.com', '01710000008', 'Dhaka', 'Bangladesh', '2024-06-10', 'ACTIVE');

INSERT INTO customers VALUES
(9, 'Business Hub', 'businesshub@demo.com', '01710000009', 'Chattogram', 'Bangladesh', '2024-07-03', 'ACTIVE');

INSERT INTO customers VALUES
(10, 'Global Enterprise', 'global@demo.com', '01710000010', 'Dhaka', 'Bangladesh', '2024-08-14', 'ACTIVE');
```

## Categories

```sql
INSERT INTO categories VALUES (1, 'Laptop');
INSERT INTO categories VALUES (2, 'Desktop');
INSERT INTO categories VALUES (3, 'Monitor');
INSERT INTO categories VALUES (4, 'Networking');
INSERT INTO categories VALUES (5, 'Accessories');
INSERT INTO categories VALUES (6, 'Printer');
```

## Suppliers

```sql
INSERT INTO suppliers VALUES
(1, 'Tech Distribution Ltd', 'Mahmud Hasan', '01810000001', 'Dhaka', 'Bangladesh');

INSERT INTO suppliers VALUES
(2, 'Global IT Supply', 'Fahim Rahman', '01810000002', 'Chattogram', 'Bangladesh');

INSERT INTO suppliers VALUES
(3, 'Computer Source Ltd', 'Nabila Islam', '01810000003', 'Dhaka', 'Bangladesh');

INSERT INTO suppliers VALUES
(4, 'Office Solutions Ltd', 'Arif Khan', '01810000004', 'Khulna', 'Bangladesh');
```

## Products

```sql
INSERT INTO products VALUES
(1, 'Dell Latitude Laptop', 1, 1, 85000, 72000, 'ACTIVE');

INSERT INTO products VALUES
(2, 'HP ProBook Laptop', 1, 1, 78000, 66000, 'ACTIVE');

INSERT INTO products VALUES
(3, 'Lenovo ThinkPad', 1, 2, 92000, 79000, 'ACTIVE');

INSERT INTO products VALUES
(4, 'Desktop Core i5', 2, 2, 65000, 54000, 'ACTIVE');

INSERT INTO products VALUES
(5, 'Dell 24 Inch Monitor', 3, 3, 22000, 17500, 'ACTIVE');

INSERT INTO products VALUES
(6, 'HP 22 Inch Monitor', 3, 3, 18500, 14500, 'ACTIVE');

INSERT INTO products VALUES
(7, 'TP-Link Router', 4, 2, 4500, 3200, 'ACTIVE');

INSERT INTO products VALUES
(8, 'Gigabit Network Switch', 4, 2, 12000, 9000, 'ACTIVE');

INSERT INTO products VALUES
(9, 'Wireless Keyboard', 5, 3, 2500, 1600, 'ACTIVE');

INSERT INTO products VALUES
(10, 'Wireless Mouse', 5, 3, 1800, 1000, 'ACTIVE');

INSERT INTO products VALUES
(11, 'Laser Printer', 6, 4, 28000, 22500, 'ACTIVE');

INSERT INTO products VALUES
(12, 'Color Printer', 6, 4, 36000, 29000, 'ACTIVE');
```

## Inventory

```sql
INSERT INTO inventory VALUES (1, 1, 1, 25, 5);
INSERT INTO inventory VALUES (2, 1, 2, 30, 5);
INSERT INTO inventory VALUES (3, 1, 3, 15, 5);
INSERT INTO inventory VALUES (4, 1, 4, 20, 5);
INSERT INTO inventory VALUES (5, 1, 5, 40, 10);
INSERT INTO inventory VALUES (6, 1, 6, 35, 10);
INSERT INTO inventory VALUES (7, 1, 7, 100, 20);
INSERT INTO inventory VALUES (8, 1, 8, 50, 10);
INSERT INTO inventory VALUES (9, 1, 9, 80, 15);
INSERT INTO inventory VALUES (10, 1, 10, 90, 15);
INSERT INTO inventory VALUES (11, 1, 11, 18, 5);
INSERT INTO inventory VALUES (12, 1, 12, 12, 5);

INSERT INTO inventory VALUES (13, 2, 1, 10, 5);
INSERT INTO inventory VALUES (14, 2, 2, 12, 5);
INSERT INTO inventory VALUES (15, 2, 5, 20, 5);
INSERT INTO inventory VALUES (16, 2, 7, 35, 10);
INSERT INTO inventory VALUES (17, 2, 9, 40, 10);
INSERT INTO inventory VALUES (18, 2, 10, 50, 10);

INSERT INTO inventory VALUES (19, 3, 3, 8, 5);
INSERT INTO inventory VALUES (20, 3, 4, 10, 5);
INSERT INTO inventory VALUES (21, 3, 6, 15, 5);
INSERT INTO inventory VALUES (22, 3, 11, 7, 3);

INSERT INTO inventory VALUES (23, 4, 1, 6, 5);
INSERT INTO inventory VALUES (24, 4, 5, 10, 5);
INSERT INTO inventory VALUES (25, 4, 7, 18, 5);
INSERT INTO inventory VALUES (26, 4, 12, 6, 3);
```

## Orders

```sql
INSERT INTO orders VALUES
(1001, 1, 2, 1, '2025-01-05', 'COMPLETED', 2000, 1500, 500);

INSERT INTO orders VALUES
(1002, 2, 6, 2, '2025-01-06', 'COMPLETED', 0, 1200, 600);

INSERT INTO orders VALUES
(1003, 3, 2, 1, '2025-01-10', 'COMPLETED', 1500, 2200, 500);

INSERT INTO orders VALUES
(1004, 4, 8, 3, '2025-01-15', 'COMPLETED', 500, 800, 600);

INSERT INTO orders VALUES
(1005, 5, 5, 4, '2025-01-20', 'PROCESSING', 0, 950, 700);

INSERT INTO orders VALUES
(1006, 6, 2, 1, '2025-02-01', 'COMPLETED', 3000, 2700, 500);

INSERT INTO orders VALUES
(1007, 8, 2, 1, '2025-02-05', 'CANCELLED', 0, 0, 0);

INSERT INTO orders VALUES
(1008, 9, 6, 2, '2025-02-10', 'COMPLETED', 1000, 1250, 600);

INSERT INTO orders VALUES
(1009, 10, 2, 1, '2025-02-15', 'COMPLETED', 2500, 3200, 500);

INSERT INTO orders VALUES
(1010, 1, 2, 1, '2025-03-01', 'PROCESSING', 1000, 1500, 500);
```

## Order Items

```sql
INSERT INTO order_items VALUES (1, 1001, 1, 1, 85000, 0);
INSERT INTO order_items VALUES (2, 1001, 9, 2, 2500, 5);

INSERT INTO order_items VALUES (3, 1002, 5, 2, 22000, 0);
INSERT INTO order_items VALUES (4, 1002, 7, 3, 4500, 0);

INSERT INTO order_items VALUES (5, 1003, 3, 1, 92000, 5);
INSERT INTO order_items VALUES (6, 1003, 10, 2, 1800, 0);

INSERT INTO order_items VALUES (7, 1004, 4, 1, 65000, 0);
INSERT INTO order_items VALUES (8, 1004, 6, 1, 18500, 0);

INSERT INTO order_items VALUES (9, 1005, 12, 1, 36000, 0);
INSERT INTO order_items VALUES (10, 1005, 9, 3, 2500, 0);

INSERT INTO order_items VALUES (11, 1006, 1, 2, 85000, 5);
INSERT INTO order_items VALUES (12, 1006, 5, 2, 22000, 0);

INSERT INTO order_items VALUES (13, 1007, 2, 1, 78000, 0);

INSERT INTO order_items VALUES (14, 1008, 11, 1, 28000, 0);
INSERT INTO order_items VALUES (15, 1008, 10, 5, 1800, 0);

INSERT INTO order_items VALUES (16, 1009, 3, 2, 92000, 5);
INSERT INTO order_items VALUES (17, 1009, 8, 2, 12000, 0);
INSERT INTO order_items VALUES (18, 1009, 9, 5, 2500, 0);

INSERT INTO order_items VALUES (19, 1010, 5, 3, 22000, 0);
INSERT INTO order_items VALUES (20, 1010, 7, 5, 4500, 0);
```

## Payments

```sql
INSERT INTO payments VALUES
(1, 1001, '2025-01-05', 'BANK_TRANSFER', 90000, 'PAID');

INSERT INTO payments VALUES
(2, 1002, '2025-01-06', 'CARD', 59300, 'PAID');

INSERT INTO payments VALUES
(3, 1003, '2025-01-10', 'BANK_TRANSFER', 92800, 'PAID');

INSERT INTO payments VALUES
(4, 1004, '2025-01-15', 'CASH', 84400, 'PAID');

INSERT INTO payments VALUES
(5, 1005, '2025-01-20', 'MOBILE_BANKING', 45150, 'PENDING');

INSERT INTO payments VALUES
(6, 1006, '2025-02-01', 'BANK_TRANSFER', 205200, 'PAID');

INSERT INTO payments VALUES
(7, 1008, '2025-02-10', 'CARD', 37850, 'PAID');

INSERT INTO payments VALUES
(8, 1009, '2025-02-15', 'BANK_TRANSFER', 221700, 'PAID');

INSERT INTO payments VALUES
(9, 1010, '2025-03-01', 'MOBILE_BANKING', 89500, 'PENDING');
```

## Purchase Orders

```sql
INSERT INTO purchase_orders VALUES
(5001, 1, 1, '2024-12-20', '2024-12-28', 'RECEIVED');

INSERT INTO purchase_orders VALUES
(5002, 2, 1, '2024-12-22', '2024-12-30', 'RECEIVED');

INSERT INTO purchase_orders VALUES
(5003, 3, 2, '2025-01-02', '2025-01-10', 'RECEIVED');

INSERT INTO purchase_orders VALUES
(5004, 4, 3, '2025-02-01', '2025-02-10', 'OPEN');

INSERT INTO purchase_orders VALUES
(5005, 1, 4, '2025-02-15', '2025-02-25', 'OPEN');
```

## Purchase Order Items

```sql
INSERT INTO purchase_order_items VALUES (1, 5001, 1, 20, 72000);
INSERT INTO purchase_order_items VALUES (2, 5001, 2, 20, 66000);

INSERT INTO purchase_order_items VALUES (3, 5002, 3, 15, 79000);
INSERT INTO purchase_order_items VALUES (4, 5002, 7, 50, 3200);
INSERT INTO purchase_order_items VALUES (5, 5002, 8, 20, 9000);

INSERT INTO purchase_order_items VALUES (6, 5003, 5, 30, 17500);
INSERT INTO purchase_order_items VALUES (7, 5003, 6, 25, 14500);
INSERT INTO purchase_order_items VALUES (8, 5003, 9, 50, 1600);
INSERT INTO purchase_order_items VALUES (9, 5003, 10, 60, 1000);

INSERT INTO purchase_order_items VALUES (10, 5004, 11, 15, 22500);
INSERT INTO purchase_order_items VALUES (11, 5004, 12, 10, 29000);

INSERT INTO purchase_order_items VALUES (12, 5005, 1, 10, 72000);
INSERT INTO purchase_order_items VALUES (13, 5005, 2, 10, 66000);
```

---

# 33. Beginner Practice Exercises

1. Show all customers.
2. Show customer name, city, and country.
3. Show all active customers.
4. Find customers from Dhaka.
5. List all products with a price greater than 20,000.
6. List products ordered by price from highest to lowest.
7. Find employees earning more than 70,000.
8. Find customers whose names contain `Tech`.
9. List all completed orders.
10. Count the number of customers.
11. Find the average product price.
12. Find the highest employee salary.
13. Find the lowest product cost.
14. Count products by category.
15. Calculate total inventory quantity.

---

# 34. Intermediate Practice Exercises

1. Show every product with its category.
2. Show products with supplier information.
3. Show orders with customer names.
4. Show orders with employee names.
5. Show all order items with product names.
6. Calculate the gross value of each order item.
7. Calculate the total value of each order.
8. Find the total sales amount by customer.
9. Find the total sales amount by branch.
10. Find the total sales amount by employee.
11. Find customers who have never placed an order.
12. Find products that have never been ordered.
13. Find customers with more than one order.
14. Find products priced above the average product price.
15. Find employees earning more than their department's average salary.

---

# 35. Advanced SQL Practice Exercises

1. Rank products by price inside each category.
2. Rank employees by salary inside each department.
3. Calculate running sales totals by order date.
4. Calculate monthly sales.
5. Compare each month's sales with the previous month using `LAG`.
6. Find the top three products by revenue.
7. Find the top customer for every month.
8. Find the most expensive product in each category.
9. Use a recursive CTE to display employee-manager hierarchy.
10. Calculate cumulative sales per customer.
11. Find customers whose spending is above average.
12. Find products contributing to the top 80% of revenue.
13. Calculate gross profit by product.
14. Calculate gross profit by category.
15. Calculate gross profit by branch.

---

# 36. Example Practice Queries

## Basic SELECT

```sql
SELECT *
FROM customers;
```

## Filtering

```sql
SELECT customer_name, city
FROM customers
WHERE customer_status = 'ACTIVE'
  AND city = 'Dhaka';
```

## JOIN

```sql
SELECT
    p.product_name,
    c.category_name,
    p.unit_price
FROM products p
JOIN categories c
    ON c.category_id = p.category_id;
```

## Aggregate

```sql
SELECT
    c.category_name,
    COUNT(*) AS product_count,
    AVG(p.unit_price) AS average_price
FROM products p
JOIN categories c
    ON c.category_id = p.category_id
GROUP BY c.category_name;
```

## Order Revenue

```sql
SELECT
    oi.order_id,
    SUM(
        oi.quantity
        * oi.unit_price
        * (1 - oi.discount_percent / 100.0)
    ) AS order_value
FROM order_items oi
GROUP BY oi.order_id
ORDER BY oi.order_id;
```

## Customer Revenue

```sql
SELECT
    c.customer_name,
    SUM(
        oi.quantity
        * oi.unit_price
        * (1 - oi.discount_percent / 100.0)
    ) AS total_sales
FROM customers c
JOIN orders o
    ON o.customer_id = c.customer_id
JOIN order_items oi
    ON oi.order_id = o.order_id
WHERE o.order_status <> 'CANCELLED'
GROUP BY c.customer_name
ORDER BY total_sales DESC;
```

## Window Function

```sql
SELECT
    p.product_name,
    c.category_name,
    p.unit_price,
    RANK() OVER (
        PARTITION BY p.category_id
        ORDER BY p.unit_price DESC
    ) AS price_rank
FROM products p
JOIN categories c
    ON c.category_id = p.category_id;
```

## Employee Hierarchy with Recursive CTE

```sql
WITH RECURSIVE employee_tree AS (
    SELECT
        employee_id,
        first_name,
        last_name,
        manager_id,
        1 AS level_no
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    SELECT
        e.employee_id,
        e.first_name,
        e.last_name,
        e.manager_id,
        t.level_no + 1
    FROM employees e
    JOIN employee_tree t
        ON e.manager_id = t.employee_id
)
SELECT *
FROM employee_tree
ORDER BY level_no, employee_id;
```

> `WITH RECURSIVE` syntax differs by database platform.  
> Oracle commonly uses hierarchical queries or recursive subquery factoring, while SQL Server uses recursive CTE syntax without the `RECURSIVE` keyword.

---

# 37. DBA Practice Labs

## Beginner DBA Labs

1. Create a database.
2. Create a schema.
3. Create database users.
4. Create roles.
5. Grant read-only access.
6. Grant read/write access.
7. Revoke privileges.
8. Inspect active sessions.
9. Check database size.
10. Check table size.
11. Review database logs.

## Backup Labs

1. Create a logical backup.
2. Restore a logical backup.
3. Create a physical backup.
4. Delete test data.
5. Restore deleted data.
6. Perform point-in-time recovery in a lab environment.
7. Verify backups.

## Performance Labs

1. Run a query without an index.
2. Capture its execution plan.
3. Add an index.
4. Run it again.
5. Compare execution plans.
6. Compare elapsed time.
7. Compare I/O.
8. Test composite indexes.
9. Test low-selectivity indexes.
10. Detect an unused index.

## Security Labs

1. Create a read-only reporting user.
2. Create an application user.
3. Restrict access to selected tables.
4. Revoke direct table access.
5. Test role-based access.
6. Configure encrypted connections.
7. Review failed login attempts.
8. Audit sensitive table access.

---

# 38. Suggested Student Projects

## Project 1 — Sales Database

Build a small sales system containing:

- Customers
- Products
- Categories
- Orders
- Order items
- Payments

## Project 2 — Inventory Management Database

Add:

- Warehouses / branches
- Inventory
- Stock movements
- Reorder levels
- Purchase orders
- Suppliers

## Project 3 — HR Database

Build:

- Departments
- Employees
- Managers
- Salary history
- Attendance
- Leave
- Payroll

## Project 4 — Enterprise ERP Database

Build a more complete model containing:

- Finance
- Sales
- Procurement
- Inventory
- CRM
- HR
- Suppliers
- Customers
- Audit logs

## Project 5 — Professional DBA Lab

Deploy and administer:

- PostgreSQL
- MySQL
- SQL Server
- Oracle

Perform:

- User administration
- Backup
- Recovery
- Monitoring
- Performance tuning
- Replication
- Failover testing

---

# 39. Recommended Final Qualification

## Certificate 1 — SQL Developer Professional

Covers:

- Database fundamentals
- SQL Basic
- SQL Intermediate
- Advanced SQL
- Stored programming
- SQL optimization

## Certificate 2 — Database Administrator Professional

Covers:

- Installation
- Configuration
- User administration
- Storage
- Security
- Backup
- Recovery
- Monitoring
- Performance
- HA / DR

## Certificate 3 — Multi-Vendor Database Administrator

Hands-on administration of:

- Oracle
- PostgreSQL
- Microsoft SQL Server
- MySQL

## Certificate 4 — Enterprise Database Engineer

Covers:

- SQL
- DBA
- NoSQL
- Linux
- Automation
- Cloud
- Security
- HA / DR
- Enterprise architecture
- Performance engineering

---

# 40. Teaching Principle

Teach the **database concept first**, and then teach how different database vendors implement that concept.

Example:

```text
Transaction Concept
        ↓
Oracle Implementation
PostgreSQL Implementation
SQL Server Implementation
MySQL Implementation
```

Use the same approach for:

- Data types
- Identity / sequence
- Transactions
- Locks
- MVCC
- Indexing
- Execution plans
- Stored procedures
- Functions
- Backup
- Recovery
- Replication
- High availability
- Security

This approach produces database engineers who understand concepts instead of only memorizing vendor-specific commands.

---

# 41. Added Topics from `SQL_DEVELOPER.docx`

The following topics were added because they are present in the Word course material and were missing or not detailed enough in the original Markdown curriculum.

---

## 41.1 Professional SQL Application Integration

### Database Connectivity
- Application-to-database connectivity
- Connection strings
- Database credentials
- Connection lifecycle
- Connection pooling
- Pool sizing concepts
- Connection validation
- Connection timeout handling
- Connection cleanup
- Multi-database application setup

### Repository and Data Access Patterns
- Repository pattern
- Data access layer responsibilities
- Query abstraction
- Parameter binding
- Transaction boundaries
- Database access testing

### Secure SQL Development
- SQL injection fundamentals
- SQL injection attack examples
- Prepared statements
- Parameterized SQL
- Escaping identifiers
- Input validation
- Safe dynamic SQL
- Secure credential handling
- Principle of least privilege for application accounts

### Database Integration Testing
- Connecting to a database from automated tests
- Test database setup
- Test teardown
- Database state cleanup
- Parallel test problems
- Schema-based test isolation
- Programmatic schema creation
- Search-path management
- Multi-database test strategies

---

## 41.2 Database Migration Engineering

### Core Topics
- What is a database migration?
- Migration files
- Versioned migrations
- Schema migrations
- Data migrations
- Forward migrations
- Rollback / revert strategies
- Migration ordering
- Migration dependencies
- Migration history tables
- Safe production migrations

### Professional Migration Practices
- Schema vs data migration
- Risks of large data migrations
- Backward-compatible schema changes
- Application/database compatibility
- Expand-and-contract migration pattern
- Zero-downtime schema migration
- Migration testing
- Deployment sequencing
- Reversible migrations
- Migration failure recovery
- Flyway
- Liquibase

---

## 41.3 Extended Window and Analytical Functions

Add the following to the advanced SQL track:

- Window frames
- `ROWS`
- `RANGE`
- `CUME_DIST()`
- `PERCENT_RANK()`
- Percentile analysis concepts
- Duplicate detection with `ROW_NUMBER()`
- Top-N / Bottom-N analysis
- Month-over-month analysis
- Customer retention analysis
- Time-gap analysis
- Running totals
- Moving averages
- Ranking analysis
- Window aggregate functions
- Window value functions

---

## 41.4 Advanced SQL Server Indexing and Optimization

### Additional Index Topics
- Rowstore indexes
- Columnstore indexes
- Clustered columnstore indexes
- Nonclustered columnstore indexes
- Filtered indexes
- Unique indexes
- Composite indexes
- Index usage monitoring
- Missing-index analysis
- Duplicate-index analysis
- Statistics updates
- Index fragmentation
- Index maintenance strategies

### Additional Performance Topics
- SQL Server query hints
- Estimated execution plans
- Actual execution plans
- Cost analysis
- Cardinality estimation concepts
- Statistics maintenance
- Performance comparison before and after indexing

---

## 41.5 SQL Analytics and Business Reporting

### Exploratory Data Analysis
- What is EDA?
- Database exploration
- Dimension exploration
- Date exploration
- Measure exploration

### Analytical Techniques
- Dimensions vs measures
- Magnitude analysis
- Ranking analysis
- Change-over-time analysis
- Cumulative analysis
- Performance analysis
- Part-to-whole analysis
- Data segmentation
- Customer analysis
- Product analysis

### Reporting Projects
- Customer report
- Product report
- Sales analysis report
- KPI reporting
- Business trend analysis
- SQL technical interview exercises

---

## 41.6 Modern Data Warehouse Project Architecture

### Data Warehouse Delivery Lifecycle
- Requirement analysis
- Source-system analysis
- Data architecture
- Naming conventions
- Git repository setup
- Data model documentation
- Data catalog creation

### Bronze Layer
- Raw source ingestion
- Source-system analysis
- Landing tables
- Load scripts
- Stored loading procedures
- Raw-data documentation

### Silver Layer
- Data cleansing
- Standardization
- Validation
- Deduplication
- Transformation
- Conformed data structures
- Load procedures

### Gold Layer
- Business-ready data
- Dimension tables
- Fact tables
- Star schema
- Analytical views
- Business metrics
- Data catalog
- Reporting models

### Additional Topics
- ETL
- ELT
- Staging layers
- Data lineage concepts
- Data quality checks
- Data transformation documentation

---

# 42. Expanded Oracle DBA Professional Topics

The original Oracle DBA section is extended with the following subjects from the Word course.

---

## 42.1 Oracle Initialization and Configuration

- Initialization parameters
- Static parameters
- Dynamic parameters
- SPFILE
- PFILE
- Parameter modification
- Parameter validation
- Instance startup configuration
- Oracle data dictionary
- Dynamic performance views
- `V$` views
- `DBA_` views
- `ALL_` views
- `USER_` views

---

## 42.2 Oracle Multitenant Architecture

### Concepts
- Container Database (CDB)
- Pluggable Database (PDB)
- Root container
- Seed PDB
- Application containers concepts

### Administration
- Creating CDBs
- Creating PDBs
- Opening and closing PDBs
- PDB startup state
- PDB cloning concepts
- PDB relocation concepts
- Local users
- Common users
- Local privileges
- Common privileges
- Container data objects

---

## 42.3 Oracle Memory Management

- Database memory concepts
- SGA components
- PGA concepts
- Shared pool
- Database buffer cache
- Redo log buffer
- Large pool
- Java pool concepts
- Automatic Shared Memory Management
- Automatic Memory Management
- PGA management
- Memory monitoring

---

## 42.4 Oracle Storage Administration

- Logical storage structures
- Physical storage structures
- Tablespaces
- Datafiles
- Tempfiles
- Segments
- Extents
- Blocks
- Datafile management
- Tablespace management
- Resumable space allocation
- Undo tablespaces
- Undo retention
- Segment shrinking
- Deferred segment creation
- Table compression

---

## 42.5 Oracle User and Authentication Administration

- Local users
- Common users
- Administrative users
- Roles
- System privileges
- Object privileges
- User profiles
- Password policies
- Resource limits
- Least privilege
- OS authentication
- Password-file authentication
- Administrative privileges
- SYSDBA
- SYSOPER concepts

---

## 42.6 Oracle Network Administration

- Oracle Net architecture
- Listener
- Listener configuration
- Service names
- TNS configuration
- Client connectivity
- Network troubleshooting
- Database links
- Shared Server architecture
- Dedicated Server vs Shared Server

---

## 42.7 Fast Recovery Area and Redo Administration

- Fast Recovery Area (FRA)
- FRA sizing
- FRA monitoring
- Online redo logs
- Redo log groups
- Redo log members
- Log switches
- Archived redo logs
- ARCHIVELOG mode
- Archive destinations
- Archive-log monitoring

---

## 42.8 Advanced Oracle RMAN

### RMAN Configuration
- Persistent RMAN settings
- Backup retention policy
- Device configuration
- Control-file autobackup

### Backup Types
- Full backup
- Incremental backup
- Level 0 backup
- Level 1 backup
- Backup sets
- Image copies concepts

### Recovery
- `RESTORE`
- `RECOVER`
- Complete recovery
- Incomplete recovery
- Point-in-time recovery
- Datafile recovery
- Tablespace recovery concepts
- Control-file recovery concepts

### Advanced RMAN
- Automated RMAN backup jobs
- RMAN in multitenant databases
- Database duplication
- PDB duplication
- RMAN Recovery Catalog
- Data Recovery Advisor
- Backup validation
- Restore validation

---

## 42.9 Oracle Flashback Technologies

- Flashback Database
- Flashback Query concepts
- Flashback Table concepts
- Restore points
- Guaranteed restore points
- Recovery use cases

---

## 42.10 Oracle Data Movement Utilities

- Oracle Data Pump
- `expdp`
- `impdp`
- Export jobs
- Import jobs
- Schema export/import
- Table export/import
- Full-database export concepts
- SQL*Loader
- Control files
- Direct-path loading concepts
- External tables

---

## 42.11 Oracle Scheduler and Diagnostics

### Scheduler
- Oracle Scheduler
- Scheduler jobs
- Schedules
- Programs
- Job monitoring
- Automated administrative tasks

### Diagnostics
- ADR
- Automatic Diagnostic Repository
- ADRCI
- Alert log
- Trace files
- Incident management
- Diagnostic workflow

---

## 42.12 Oracle Patching and Upgrading

- Release Updates (RU)
- Patch planning
- Patch prerequisites
- OPatch concepts
- Database patching
- Oracle Restart patching
- Upgrade planning
- Database upgrade
- Grid Infrastructure upgrade concepts
- Post-upgrade validation

---

## 42.13 Oracle Automatic Storage Management

- ASM architecture
- ASM instance
- ASM disk groups
- ASM disks
- Redundancy concepts
- ASM file management
- Creating databases with ASM
- Oracle Restart with ASM
- ASM monitoring

---

# 43. Expanded Oracle SQL Specialization

Add a dedicated Oracle SQL specialization after core vendor-neutral SQL.

## Environment and Tools
- SQL*Plus
- Oracle SQL Developer
- Oracle Live SQL
- Oracle sample schemas
- `DESCRIBE`
- Oracle error messages

## Oracle-Specific SQL Features
- Q quoting operator
- `ROWNUM`
- `ROWID`
- `FETCH`
- `NULLS FIRST`
- `NULLS LAST`
- substitution variables
- `&`
- `&&`
- `DEFINE`
- `UNDEFINE`
- `ACCEPT`
- `PROMPT`
- SQL*Plus environment settings

## Oracle Character Functions
- `INITCAP`
- `INSTR`
- `LPAD`
- `RPAD`
- `LTRIM`
- `RTRIM`

## Oracle Conversion and NULL Functions
- `TO_CHAR`
- `TO_DATE`
- `TO_NUMBER`
- `NVL`
- `NVL2`
- `NULLIF`
- `COALESCE`

## Oracle Conditional and Aggregate Functions
- `DECODE`
- `LISTAGG`

## Oracle Join Features
- `NATURAL JOIN`
- `USING`
- non-equijoins
- ANSI join syntax
- Oracle legacy join syntax

## Oracle Subqueries
- single-row subqueries
- multiple-row subqueries
- multi-column subqueries
- scalar subqueries
- correlated subqueries
- `EXISTS`
- `NOT EXISTS`

## Oracle Set Operations
- `UNION`
- `UNION ALL`
- `INTERSECT`
- `MINUS`

## Oracle DDL Enhancements
- CTAS
- `SET UNUSED`
- read-only tables
- `COMMENT`
- `RENAME`

---

# 44. Updated Practice Database Expansion

To support the newly added topics, extend the practice database with the following tables.

## `warehouses`

```sql
CREATE TABLE warehouses (
    warehouse_id INTEGER PRIMARY KEY,
    warehouse_name VARCHAR(120) NOT NULL,
    branch_id INTEGER NOT NULL,
    city VARCHAR(100),
    country VARCHAR(100),
    FOREIGN KEY (branch_id) REFERENCES branches(branch_id)
);
```

## `stock_movements`

```sql
CREATE TABLE stock_movements (
    movement_id INTEGER PRIMARY KEY,
    product_id INTEGER NOT NULL,
    warehouse_id INTEGER NOT NULL,
    movement_type VARCHAR(30) NOT NULL,
    quantity INTEGER NOT NULL,
    movement_date DATE NOT NULL,
    reference_no VARCHAR(50),
    FOREIGN KEY (product_id) REFERENCES products(product_id),
    FOREIGN KEY (warehouse_id) REFERENCES warehouses(warehouse_id)
);
```

## `employee_salary_history`

```sql
CREATE TABLE employee_salary_history (
    salary_history_id INTEGER PRIMARY KEY,
    employee_id INTEGER NOT NULL,
    effective_from DATE NOT NULL,
    effective_to DATE,
    salary DECIMAL(12,2) NOT NULL,
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id)
);
```

## `customer_addresses`

```sql
CREATE TABLE customer_addresses (
    address_id INTEGER PRIMARY KEY,
    customer_id INTEGER NOT NULL,
    address_type VARCHAR(20) NOT NULL,
    address_line VARCHAR(200) NOT NULL,
    city VARCHAR(100),
    country VARCHAR(100),
    is_primary INTEGER DEFAULT 0,
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

## `product_prices`

```sql
CREATE TABLE product_prices (
    product_price_id INTEGER PRIMARY KEY,
    product_id INTEGER NOT NULL,
    effective_from DATE NOT NULL,
    effective_to DATE,
    unit_price DECIMAL(12,2) NOT NULL,
    FOREIGN KEY (product_id) REFERENCES products(product_id)
);
```

## `audit_log`

```sql
CREATE TABLE audit_log (
    audit_id INTEGER PRIMARY KEY,
    entity_name VARCHAR(100) NOT NULL,
    entity_id VARCHAR(100),
    action_type VARCHAR(30) NOT NULL,
    changed_by VARCHAR(120),
    changed_at TIMESTAMP NOT NULL,
    old_value VARCHAR(1000),
    new_value VARCHAR(1000)
);
```

## `login_history`

```sql
CREATE TABLE login_history (
    login_id INTEGER PRIMARY KEY,
    username VARCHAR(120) NOT NULL,
    login_time TIMESTAMP NOT NULL,
    logout_time TIMESTAMP,
    login_status VARCHAR(20) NOT NULL,
    source_ip VARCHAR(50)
);
```

## `sales_targets`

```sql
CREATE TABLE sales_targets (
    sales_target_id INTEGER PRIMARY KEY,
    employee_id INTEGER NOT NULL,
    target_month DATE NOT NULL,
    target_amount DECIMAL(14,2) NOT NULL,
    FOREIGN KEY (employee_id) REFERENCES employees(employee_id)
);
```

## `currencies`

```sql
CREATE TABLE currencies (
    currency_code VARCHAR(3) PRIMARY KEY,
    currency_name VARCHAR(100) NOT NULL,
    symbol VARCHAR(10)
);
```

## `exchange_rates`

```sql
CREATE TABLE exchange_rates (
    exchange_rate_id INTEGER PRIMARY KEY,
    from_currency VARCHAR(3) NOT NULL,
    to_currency VARCHAR(3) NOT NULL,
    effective_date DATE NOT NULL,
    rate DECIMAL(18,6) NOT NULL,
    FOREIGN KEY (from_currency) REFERENCES currencies(currency_code),
    FOREIGN KEY (to_currency) REFERENCES currencies(currency_code)
);
```

## `regions`

```sql
CREATE TABLE regions (
    region_id INTEGER PRIMARY KEY,
    region_name VARCHAR(120) NOT NULL,
    parent_region_id INTEGER,
    FOREIGN KEY (parent_region_id) REFERENCES regions(region_id)
);
```

## `database_incidents`

```sql
CREATE TABLE database_incidents (
    incident_id INTEGER PRIMARY KEY,
    incident_type VARCHAR(100) NOT NULL,
    severity VARCHAR(20) NOT NULL,
    opened_at TIMESTAMP NOT NULL,
    resolved_at TIMESTAMP,
    root_cause VARCHAR(500),
    resolution_note VARCHAR(1000)
);
```

## `backup_history`

```sql
CREATE TABLE backup_history (
    backup_id INTEGER PRIMARY KEY,
    database_name VARCHAR(120) NOT NULL,
    backup_type VARCHAR(30) NOT NULL,
    backup_started_at TIMESTAMP NOT NULL,
    backup_completed_at TIMESTAMP,
    backup_status VARCHAR(20) NOT NULL,
    backup_size_mb DECIMAL(14,2)
);
```

## `job_execution_history`

```sql
CREATE TABLE job_execution_history (
    execution_id INTEGER PRIMARY KEY,
    job_name VARCHAR(150) NOT NULL,
    started_at TIMESTAMP NOT NULL,
    completed_at TIMESTAMP,
    execution_status VARCHAR(20) NOT NULL,
    error_message VARCHAR(1000)
);
```

---

# 45. Seed Data for Added Practice Tables

```sql
INSERT INTO warehouses VALUES
(1, 'Dhaka Central Warehouse', 1, 'Dhaka', 'Bangladesh'),
(2, 'Chattogram Warehouse', 2, 'Chattogram', 'Bangladesh'),
(3, 'Khulna Warehouse', 3, 'Khulna', 'Bangladesh'),
(4, 'Sylhet Warehouse', 4, 'Sylhet', 'Bangladesh');

INSERT INTO stock_movements VALUES
(1, 1, 1, 'PURCHASE_RECEIPT', 20, '2025-01-02', 'GRN-001'),
(2, 1, 1, 'SALE_ISSUE', -1, '2025-01-05', 'SO-1001'),
(3, 5, 2, 'PURCHASE_RECEIPT', 30, '2025-01-08', 'GRN-002'),
(4, 5, 2, 'SALE_ISSUE', -2, '2025-01-10', 'SO-1003'),
(5, 7, 1, 'ADJUSTMENT', 5, '2025-01-15', 'ADJ-001');

INSERT INTO employee_salary_history VALUES
(1, 1, '2021-01-15', '2022-12-31', 95000),
(2, 1, '2023-01-01', NULL, 120000),
(3, 2, '2022-03-10', '2023-12-31', 60000),
(4, 2, '2024-01-01', NULL, 70000),
(5, 3, '2022-05-21', NULL, 75000);

INSERT INTO customer_addresses VALUES
(1, 1, 'BILLING', 'Dhanmondi', 'Dhaka', 'Bangladesh', 1),
(2, 1, 'SHIPPING', 'Mohammadpur', 'Dhaka', 'Bangladesh', 0),
(3, 2, 'BILLING', 'Agrabad', 'Chattogram', 'Bangladesh', 1),
(4, 3, 'BILLING', 'Gulshan', 'Dhaka', 'Bangladesh', 1);

INSERT INTO product_prices VALUES
(1, 1, '2024-01-01', '2024-12-31', 80000),
(2, 1, '2025-01-01', NULL, 85000),
(3, 5, '2024-01-01', '2024-12-31', 20000),
(4, 5, '2025-01-01', NULL, 22000);

INSERT INTO audit_log VALUES
(1, 'PRODUCT', '1', 'UPDATE', 'admin', '2025-01-01 10:00:00', '80000', '85000'),
(2, 'CUSTOMER', '7', 'STATUS_CHANGE', 'admin', '2025-02-01 11:30:00', 'ACTIVE', 'INACTIVE');

INSERT INTO login_history VALUES
(1, 'admin', '2025-01-01 08:00:00', '2025-01-01 17:00:00', 'SUCCESS', '10.0.0.10'),
(2, 'sales01', '2025-01-01 08:15:00', '2025-01-01 17:10:00', 'SUCCESS', '10.0.0.20'),
(3, 'unknown', '2025-01-01 09:00:00', NULL, 'FAILED', '10.0.0.99');

INSERT INTO sales_targets VALUES
(1, 2, '2025-01-01', 500000),
(2, 6, '2025-01-01', 400000),
(3, 8, '2025-01-01', 300000);

INSERT INTO currencies VALUES
('BDT', 'Bangladeshi Taka', '৳'),
('USD', 'US Dollar', '$'),
('EUR', 'Euro', '€');

INSERT INTO exchange_rates VALUES
(1, 'USD', 'BDT', '2025-01-01', 120.000000),
(2, 'EUR', 'BDT', '2025-01-01', 130.000000),
(3, 'USD', 'BDT', '2025-02-01', 121.500000);

INSERT INTO regions VALUES
(1, 'Bangladesh', NULL),
(2, 'Dhaka Division', 1),
(3, 'Dhaka District', 2),
(4, 'Chattogram Division', 1),
(5, 'Chattogram District', 4);

INSERT INTO database_incidents VALUES
(1, 'HIGH_CPU', 'HIGH', '2025-01-15 11:00:00', '2025-01-15 11:45:00', 'Missing index', 'Index created and query tuned'),
(2, 'LOCK_CONTENTION', 'MEDIUM', '2025-02-10 14:00:00', '2025-02-10 14:30:00', 'Long transaction', 'Transaction rolled back');

INSERT INTO backup_history VALUES
(1, 'training_db', 'FULL', '2025-01-01 01:00:00', '2025-01-01 01:20:00', 'SUCCESS', 1500),
(2, 'training_db', 'INCREMENTAL', '2025-01-02 01:00:00', '2025-01-02 01:07:00', 'SUCCESS', 210),
(3, 'training_db', 'FULL', '2025-01-08 01:00:00', '2025-01-08 01:25:00', 'FAILED', 0);

INSERT INTO job_execution_history VALUES
(1, 'DAILY_BACKUP', '2025-01-01 01:00:00', '2025-01-01 01:20:00', 'SUCCESS', NULL),
(2, 'DAILY_BACKUP', '2025-01-08 01:00:00', '2025-01-08 01:25:00', 'FAILED', 'Disk space unavailable'),
(3, 'MONTHLY_REPORT', '2025-02-01 03:00:00', '2025-02-01 03:05:00', 'SUCCESS', NULL);
```

---

# 46. New Advanced Practice Exercises

## Application and Security

1. Demonstrate the difference between unsafe string-concatenated SQL and parameterized SQL.
2. Create a read-only application role.
3. Create a read/write application role.
4. Design a schema-isolated integration test.
5. Identify failed logins from `login_history`.
6. Report users with repeated failed login attempts.

## Migration Engineering

1. Add a nullable column without breaking existing applications.
2. Backfill data in batches.
3. Convert the column to NOT NULL safely.
4. Design an expand-and-contract migration.
5. Create rollback steps for a failed release.

## Advanced Analytics

1. Rank salespeople against their monthly targets.
2. Calculate target achievement percentage.
3. Use `LAG` to compare salaries over time.
4. Find product price changes.
5. Calculate cumulative stock movement by product.
6. Detect abnormal stock movements.
7. Build a region hierarchy using recursive CTEs.
8. Calculate month-over-month revenue growth.

## DBA Operational Analytics

1. Calculate backup success rate.
2. Find databases without a successful recent full backup.
3. Calculate average backup duration.
4. Find failed scheduled jobs.
5. Calculate mean incident resolution time.
6. Group incidents by severity.
7. Identify recurring root causes.

---

# 47. Final Updated Course Positioning

The completed curriculum now combines:

- Vendor-neutral SQL
- PostgreSQL development
- PostgreSQL DBA
- Oracle SQL
- Oracle DBA
- Microsoft SQL Server SQL
- Microsoft SQL Server DBA
- MySQL DBA
- MongoDB
- Redis
- NoSQL concepts
- Data warehouse engineering
- SQL analytics
- Database application integration
- Database migration engineering
- Security
- Performance engineering
- Linux
- Automation
- DevOps
- Cloud databases
- High availability
- Disaster recovery
- Enterprise database architecture

## Final Program Name

> **Professional Database Engineering, SQL, NoSQL & Multi-Vendor DBA Program**

## Final Learning Path

```text
Database Foundations
        ↓
SQL Basic
        ↓
SQL Intermediate
        ↓
Advanced SQL
        ↓
Professional SQL Development
        ↓
Application Integration & Migration Engineering
        ↓
SQL Performance Engineering
        ↓
DBA Fundamentals
        ↓
PostgreSQL DBA
Oracle DBA
Microsoft SQL Server DBA
MySQL DBA
        ↓
NoSQL Professional
        ↓
Data Warehouse & SQL Analytics
        ↓
Linux + Automation + DevOps
        ↓
High Availability + Disaster Recovery
        ↓
Cloud Database Administration
        ↓
Enterprise Database Engineer / Database Architect
```
