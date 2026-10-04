# Practical Intermediate SQL, DBMS & Multi-Vendor Database Administration Program

**Creation Date:** October 5, 2026  
**Prepared by:** Md Belayet Hossain  
**Designation:** Software Engineer  
**Organization:** IT Garden  

## Program Title
**Practical Intermediate SQL, DBMS & Multi-Vendor Database Administration — 400 Hours**

## Program Level
**Intermediate / Job-Oriented / Practical**

## Total Duration
**400 Hours**

## Training Philosophy

This program is designed as a **hands-on database training program**, not a theory-only course.

Recommended delivery model:

- **30% Concepts and Demonstration**
- **55% Guided Hands-on Lab**
- **10% Assignments / Troubleshooting**
- **5% Assessment / Viva / Review**

Students should spend most of the course working directly with real database servers, SQL scripts, backup files, execution plans, users, security settings, logs, performance problems, and recovery scenarios.

---

# 1. Target Database Platforms

Students will practice with:

- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- MySQL

Supporting exposure:

- MongoDB
- Redis
- Linux
- Git
- Docker
- Flyway / Liquibase
- Basic Cloud Database concepts

---

# 2. Entry Requirements

Students should already understand:

- Basic computer operation
- Basic database terminology
- Tables, rows, columns
- Simple `SELECT`
- Simple `INSERT`
- Simple `UPDATE`
- Simple `DELETE`
- Basic primary key / foreign key concepts

Students do **not** need prior DBA experience.

---

# 3. Program Outcomes

After completing the 400-hour program, a learner should be able to:

1. Design a relational database from business requirements.
2. Write intermediate and advanced SQL queries.
3. Work confidently with joins, subqueries, CTEs, aggregates, and window functions.
4. Build views, indexes, constraints, functions, procedures, and triggers.
5. Analyze query execution plans.
6. Diagnose common SQL performance problems.
7. Install and configure major database platforms.
8. Create users, roles, schemas, and permissions.
9. Perform backup and restore operations.
10. Diagnose locks, blocking, connection, storage, and performance issues.
11. Perform basic PostgreSQL, Oracle, SQL Server, and MySQL administration.
12. Build a small data warehouse and analytical reporting solution.
13. Perform safe database migrations.
14. Use databases from an application securely.
15. Complete a realistic database implementation and administration capstone project.

---

# 4. Job / Competency Unit Duration Summary

| Competency Unit | Job / Competency Unit | Tasks | Hours |
|---|---|---|---:|
| CU-01 | Configure Database Environments and Design Relational Databases | Task 1.1 + Task 1.2 | 40 |
| CU-02 | Develop Intermediate SQL Queries and Data Retrieval Solutions | Task 2.1 + Task 2.2 | 60 |
| CU-03 | Develop Advanced SQL and Stored Database Solutions | Task 3.1 + Task 3.2 | 60 |
| CU-04 | Manage Transactions and Optimize Database Performance | Task 4.1 + Task 4.2 | 56 |
| CU-05 | Administer PostgreSQL and Oracle Databases | Task 5.1 + Task 5.2 | 68 |
| CU-06 | Administer Microsoft SQL Server and MySQL Databases | Task 6.1 + Task 6.2 | 52 |
| CU-07 | Perform Database Recovery, Security and Application Integration | Task 7.1 + Task 7.2 | 36 |
| CU-08 | Manage Database Change, Automation, Analytics and NoSQL Solutions | Task 8.1 + Task 8.2 | 28 |
| **Total** |  |  | **400 Hours** |

## Competency Structure

Each original course module is preserved as a **Task** under one of the eight Job / Competency Units. All original topic, lab, practical, assessment, deliverable, and minimum-practice sections are preserved as **Task Elements**.

---

# Job / Competency Unit 1 — Configure Database Environments and Design Relational Databases

**Competency Unit Code:** CU-01

**Duration:** 40 Hours

### Tasks in this Competency Unit

- **Task 1.1:** Lab Environment & Multi-Vendor Setup — 16 Hours
- **Task 1.2:** Relational Modeling & Database Design — 24 Hours

---

## Task 1.1 — Lab Environment & Multi-Vendor Setup


### Task Element 1.1.1 — Duration
**16 Hours**

**Concept / Demonstration**
4 Hours

**Practical Lab**
10 Hours

**Review / Assessment**
2 Hours

### Task Element 1.1.2 — Topics

- Database client/server architecture
- Database service vs database instance
- Ports and connectivity
- Database command-line tools
- GUI administration tools
- Environment variables
- Database service management

### Task Element 1.1.3 — Practical Installation

**PostgreSQL**
- Install PostgreSQL
- Configure service
- Create database
- Connect with `psql`
- Connect with pgAdmin

**Oracle**
- Oracle Database environment overview
- SQL*Plus
- Oracle SQL Developer
- Database connectivity

**Microsoft SQL Server**
- Install SQL Server
- Configure instance
- Install SSMS
- Connect to database

**MySQL**
- Install MySQL Server
- MySQL Shell
- MySQL Workbench
- Create first database

### Task Element 1.1.4 — Lab Tasks

1. Install at least two database engines locally.
2. Connect using command-line clients.
3. Connect using GUI tools.
4. Create a training database.
5. Create a test user.
6. Start and stop a database service.
7. Identify default database ports.
8. Test local and remote connectivity.

### Task Element 1.1.5 — Deliverable

`LAB-01-DATABASE-ENVIRONMENT-REPORT.md`

---


---

## Task 1.2 — Relational Modeling & Database Design


### Task Element 1.2.1 — Duration
**24 Hours**

**Concept**
7 Hours

**Guided Design Lab**
13 Hours

**Assessment**
4 Hours

### Task Element 1.2.2 — Topics

- Business requirement to database model
- Entities
- Attributes
- Relationships
- Cardinality
- Primary keys
- Foreign keys
- Natural vs surrogate keys
- Composite keys
- Candidate keys
- Unique constraints
- Referential integrity
- One-to-one
- One-to-many
- Many-to-many
- Junction tables
- Weak entities
- Lookup tables
- Master tables
- Transaction tables

### Task Element 1.2.3 — Normalization

- 1NF
- 2NF
- 3NF
- BCNF concepts
- Controlled denormalization

### Task Element 1.2.4 — Practical Project

Design a database for:

**Sales + Inventory + Procurement System**

Required entities:

- customers
- suppliers
- products
- categories
- warehouses
- inventory
- orders
- order_items
- purchase_orders
- purchase_order_items
- payments
- employees
- departments

### Task Element 1.2.5 — Lab Tasks

- Draw ERD
- Identify keys
- Define relationships
- Normalize tables
- Add business constraints
- Create physical schema
- Review naming standards

---


---

# Job / Competency Unit 2 — Develop Intermediate SQL Queries and Data Retrieval Solutions

**Competency Unit Code:** CU-02

**Duration:** 60 Hours

### Tasks in this Competency Unit

- **Task 2.1:** Intermediate SQL Querying — 32 Hours
- **Task 2.2:** Joins, Subqueries & Set Operations — 28 Hours

---

## Task 2.1 — Intermediate SQL Querying


### Task Element 2.1.1 — Duration
**32 Hours**

**Concept**
8 Hours

**Practical SQL**
20 Hours

**Assessment**
4 Hours

### Task Element 2.1.2 — Topics

**Query Construction**

- SELECT
- aliases
- expressions
- DISTINCT
- ORDER BY
- LIMIT
- OFFSET
- TOP
- FETCH

**Filtering**

- WHERE
- AND
- OR
- NOT
- BETWEEN
- IN
- LIKE
- NULL
- complex conditions

**Functions**

- string functions
- numeric functions
- date functions
- conversion
- NULL handling
- CASE

**Aggregation**

- COUNT
- SUM
- AVG
- MIN
- MAX
- GROUP BY
- HAVING
- conditional aggregation

### Task Element 2.1.3 — Practical Exercises

- Monthly sales report
- Customer purchase summary
- Product price analysis
- Inventory shortage report
- Employee salary analysis
- Branch-wise sales report

### Task Element 2.1.4 — Minimum Practice

**80 SQL exercises**

---


---

## Task 2.2 — Joins, Subqueries & Set Operations


### Task Element 2.2.1 — Duration
**28 Hours**

**Concept**
7 Hours

**Lab**
17 Hours

**Assessment**
4 Hours

### Task Element 2.2.2 — Joins

- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN
- CROSS JOIN
- SELF JOIN
- multiple-table joins
- non-equi joins
- anti joins
- semi joins

### Task Element 2.2.3 — Subqueries

- scalar subqueries
- single-row
- multi-row
- correlated subqueries
- EXISTS
- NOT EXISTS
- ANY
- ALL
- subquery in SELECT
- subquery in FROM
- subquery in WHERE

### Task Element 2.2.4 — Set Operations

- UNION
- UNION ALL
- INTERSECT
- EXCEPT
- Oracle MINUS

### Task Element 2.2.5 — Labs

1. Customers without orders.
2. Products never sold.
3. Products priced above average.
4. Employees above departmental average.
5. Supplier purchase comparison.
6. Salespersons without current sales.
7. Customer lifetime value.
8. Revenue comparison across branches.

### Task Element 2.2.6 — Minimum Practice

**60 SQL exercises**

---


---

# Job / Competency Unit 3 — Develop Advanced SQL and Stored Database Solutions

**Competency Unit Code:** CU-03

**Duration:** 60 Hours

### Tasks in this Competency Unit

- **Task 3.1:** Advanced SQL & Analytical Functions — 32 Hours
- **Task 3.2:** Database Objects & Stored Programming — 28 Hours

---

## Task 3.1 — Advanced SQL & Analytical Functions


### Task Element 3.1.1 — Duration
**32 Hours**

**Concept**
8 Hours

**Lab**
20 Hours

**Assessment**
4 Hours

### Task Element 3.1.2 — Common Table Expressions

- CTE
- multiple CTEs
- recursive CTE
- hierarchical data

### Task Element 3.1.3 — Window Functions

- OVER
- PARTITION BY
- ORDER BY
- window frames
- ROWS
- RANGE

**Ranking**

- ROW_NUMBER
- RANK
- DENSE_RANK
- NTILE
- CUME_DIST
- PERCENT_RANK

**Analytical Functions**

- LAG
- LEAD
- FIRST_VALUE
- LAST_VALUE
- running totals
- moving averages

### Task Element 3.1.4 — Business Problems

- Top 5 customers by month
- Product ranking by category
- Running inventory balance
- Customer retention analysis
- Month-over-month sales
- Salary history comparison
- Duplicate detection
- Sales target achievement
- Price history analysis
- Employee hierarchy

### Task Element 3.1.5 — Minimum Practice

**50 advanced SQL problems**

---


---

## Task 3.2 — Database Objects & Stored Programming


### Task Element 3.2.1 — Duration
**28 Hours**

**Concept**
7 Hours

**Lab**
17 Hours

**Assessment**
4 Hours

### Task Element 3.2.2 — Objects

- Views
- Materialized views
- Temporary tables
- Sequences
- Identity columns
- Indexes
- Synonyms concepts
- CTAS
- Generated columns

### Task Element 3.2.3 — Stored Programming

**PostgreSQL**
- PL/pgSQL functions
- procedures

**Oracle**
- PL/SQL
- procedures
- functions
- packages overview

**SQL Server**
- T-SQL procedures
- functions

**MySQL**
- stored procedures
- stored functions

### Task Element 3.2.4 — Common Topics

- variables
- parameters
- IF / ELSE
- loops
- exception handling
- cursors
- dynamic SQL
- triggers

### Task Element 3.2.5 — Practical Project

Build stored database logic for:

- order confirmation
- stock validation
- stock reduction
- payment recording
- audit logging

---


---

# Job / Competency Unit 4 — Manage Transactions and Optimize Database Performance

**Competency Unit Code:** CU-04

**Duration:** 56 Hours

### Tasks in this Competency Unit

- **Task 4.1:** Transactions, Concurrency & Data Integrity — 20 Hours
- **Task 4.2:** Indexing, Execution Plans & Performance Tuning — 36 Hours

---

## Task 4.1 — Transactions, Concurrency & Data Integrity


### Task Element 4.1.1 — Duration
**20 Hours**

**Concept**
6 Hours

**Practical**
11 Hours

**Assessment**
3 Hours

### Task Element 4.1.2 — Topics

- ACID
- COMMIT
- ROLLBACK
- SAVEPOINT
- isolation levels
- transaction boundaries
- autocommit
- locking
- blocking
- deadlocks
- MVCC
- optimistic locking
- pessimistic locking

### Task Element 4.1.3 — Concurrency Problems

- dirty read
- non-repeatable read
- phantom read
- lost update

### Task Element 4.1.4 — Practical Labs

1. Two users update the same row.
2. Reproduce blocking.
3. Reproduce a deadlock.
4. Inspect lock information.
5. Roll back a failed order transaction.
6. Use savepoints.
7. Compare isolation levels.

---


---

## Task 4.2 — Indexing, Execution Plans & Performance Tuning


### Task Element 4.2.1 — Duration
**36 Hours**

**Concept**
10 Hours

**Performance Lab**
22 Hours

**Assessment**
4 Hours

### Task Element 4.2.2 — Indexes

- B-tree
- hash concepts
- bitmap concepts
- clustered
- nonclustered
- composite
- covering
- unique
- filtered / partial
- function-based
- columnstore concepts

### Task Element 4.2.3 — Core Performance Concepts

- cardinality
- selectivity
- statistics
- cost
- optimizer
- query planner

### Task Element 4.2.4 — Execution Plans

**PostgreSQL**
- EXPLAIN
- EXPLAIN ANALYZE

**Oracle**
- EXPLAIN PLAN
- execution plan interpretation

**SQL Server**
- estimated plan
- actual plan

**MySQL**
- EXPLAIN
- EXPLAIN ANALYZE where supported

### Task Element 4.2.5 — Join Algorithms

- nested loop
- hash join
- merge join

### Task Element 4.2.6 — Performance Labs

1. Create a large test table.
2. Run query without index.
3. Capture plan.
4. Add index.
5. Compare cost and runtime.
6. Build composite indexes.
7. Detect bad index order.
8. Demonstrate SARGable vs non-SARGable predicates.
9. Test pagination.
10. Analyze sorting.
11. Diagnose slow joins.
12. Detect unnecessary indexes.

### Task Element 4.2.7 — Minimum Dataset

At least **100,000 rows** for intermediate performance labs.

---


---

# Job / Competency Unit 5 — Administer PostgreSQL and Oracle Databases

**Competency Unit Code:** CU-05

**Duration:** 68 Hours

### Tasks in this Competency Unit

- **Task 5.1:** PostgreSQL Administration Lab — 32 Hours
- **Task 5.2:** Oracle Administration Lab — 36 Hours

---

## Task 5.1 — PostgreSQL Administration Lab


### Task Element 5.1.1 — Duration
**32 Hours**

**Concept**
8 Hours

**Administration Lab**
20 Hours

**Assessment**
4 Hours

### Task Element 5.1.2 — Architecture

- cluster
- instance concepts
- database
- schema
- tablespace
- process architecture

### Task Element 5.1.3 — Configuration

- `postgresql.conf`
- `pg_hba.conf`
- connection settings
- logging

### Task Element 5.1.4 — Security

- roles
- users
- privileges
- schemas
- ownership
- search path

### Task Element 5.1.5 — Maintenance

- VACUUM
- AUTOVACUUM
- ANALYZE
- statistics
- table bloat concepts

### Task Element 5.1.6 — Monitoring

- `pg_stat_activity`
- locks
- long-running transactions
- active connections

### Task Element 5.1.7 — Backup

- pg_dump
- pg_restore
- pg_dumpall concepts
- pg_basebackup

### Task Element 5.1.8 — Recovery Concepts

- WAL
- WAL archiving
- PITR

### Task Element 5.1.9 — Replication Exposure

- streaming replication
- logical replication
- PgBouncer concepts

### Task Element 5.1.10 — Practical Labs

- Create roles
- Configure access
- Backup database
- Restore database
- Analyze a slow query
- Inspect locks
- Terminate a test session
- Configure logging
- Run VACUUM / ANALYZE

---


---

## Task 5.2 — Oracle Administration Lab


### Task Element 5.2.1 — Duration
**36 Hours**

**Concept**
10 Hours

**DBA Lab**
22 Hours

**Assessment**
4 Hours

### Task Element 5.2.2 — Architecture

- Oracle instance
- Oracle database
- SGA
- PGA
- background processes
- datafiles
- control files
- redo logs

### Task Element 5.2.3 — Configuration

- initialization parameters
- PFILE
- SPFILE
- startup
- shutdown

### Task Element 5.2.4 — Storage

- tablespaces
- datafiles
- undo
- temp
- segment concepts

### Task Element 5.2.5 — Multitenant

- CDB
- PDB
- creating PDB
- opening / closing PDB
- common vs local users

### Task Element 5.2.6 — Users & Security

- CREATE USER
- roles
- privileges
- profiles
- least privilege

### Task Element 5.2.7 — Networking

- listener concepts
- services
- client connectivity

### Task Element 5.2.8 — Recovery Environment

- ARCHIVELOG
- Fast Recovery Area

### Task Element 5.2.9 — RMAN

- RMAN connection
- full backup
- incremental concepts
- restore
- recover
- backup validation
- PITR demonstration

### Task Element 5.2.10 — Data Movement

- Data Pump
- expdp
- impdp

### Task Element 5.2.11 — Practical Labs

- Create tablespace
- Create user
- Assign quota
- Create role
- Perform backup
- Restore test
- Export schema
- Import schema
- Inspect alert log

---


---

# Job / Competency Unit 6 — Administer Microsoft SQL Server and MySQL Databases

**Competency Unit Code:** CU-06

**Duration:** 52 Hours

### Tasks in this Competency Unit

- **Task 6.1:** Microsoft SQL Server Administration Lab — 28 Hours
- **Task 6.2:** MySQL Administration Lab — 24 Hours

---

## Task 6.1 — Microsoft SQL Server Administration Lab


### Task Element 6.1.1 — Duration
**28 Hours**

**Concept**
7 Hours

**Lab**
17 Hours

**Assessment**
4 Hours

### Task Element 6.1.2 — Architecture

- instance
- database
- MDF
- NDF
- LDF
- TempDB

### Task Element 6.1.3 — Security

- Windows authentication
- SQL authentication
- logins
- users
- roles
- permissions

### Task Element 6.1.4 — Administration

- SSMS
- database properties
- database files
- SQL Server Agent
- jobs

### Task Element 6.1.5 — Performance

- execution plans
- statistics
- indexes
- fragmentation
- Query Store concepts
- Extended Events concepts

### Task Element 6.1.6 — Backup

- full backup
- differential backup
- transaction log backup
- restore

### Task Element 6.1.7 — Recovery Models

- Simple
- Full
- Bulk-logged concepts

### Task Element 6.1.8 — HA Exposure

- Always On overview
- log shipping overview
- replication overview

### Task Element 6.1.9 — Practical Labs

- Create database
- Create login
- Create role
- Create SQL Agent job
- Backup and restore
- Test recovery model
- Analyze Query Store information
- Investigate blocking

---


---

## Task 6.2 — MySQL Administration Lab


### Task Element 6.2.1 — Duration
**24 Hours**

**Concept**
6 Hours

**Lab**
15 Hours

**Assessment**
3 Hours

### Task Element 6.2.2 — Architecture

- MySQL Server
- schemas
- storage engines
- InnoDB

### Task Element 6.2.3 — Configuration

- `my.cnf`
- connections
- server variables

### Task Element 6.2.4 — Security

- users
- hosts
- privileges
- roles where supported

### Task Element 6.2.5 — InnoDB

- buffer pool
- redo
- undo
- transactions

### Task Element 6.2.6 — Logging

- error log
- slow query log
- binary log

### Task Element 6.2.7 — Performance

- EXPLAIN
- indexes
- slow queries

### Task Element 6.2.8 — Backup & Recovery

- mysqldump
- logical restore
- MySQL Shell concepts
- physical backup concepts

### Task Element 6.2.9 — Replication Exposure

- primary / replica
- binary log
- Group Replication concepts
- InnoDB Cluster concepts

### Task Element 6.2.10 — Labs

- User creation
- Permission management
- Slow-query logging
- Backup
- Restore
- Index tuning
- Configuration inspection

---


---

# Job / Competency Unit 7 — Perform Database Recovery, Security and Application Integration

**Competency Unit Code:** CU-07

**Duration:** 36 Hours

### Tasks in this Competency Unit

- **Task 7.1:** Backup, Recovery & Disaster Scenarios — 20 Hours
- **Task 7.2:** Database Security & Application Integration — 16 Hours

---

## Task 7.1 — Backup, Recovery & Disaster Scenarios


### Task Element 7.1.1 — Duration
**20 Hours**

**Concept**
5 Hours

**Recovery Lab**
12 Hours

**Assessment**
3 Hours

### Task Element 7.1.2 — Backup Types

- logical
- physical
- full
- differential
- incremental
- transaction log
- WAL / redo

### Task Element 7.1.3 — Core Concepts

- backup retention
- backup rotation
- restore
- recovery
- RPO
- RTO
- PITR
- disaster recovery

### Task Element 7.1.4 — Practical Scenarios

**Scenario 1**
User deletes important records.

**Scenario 2**
Database table is dropped.

**Scenario 3**
Database server crashes.

**Scenario 4**
Backup job fails.

**Scenario 5**
Disk becomes full.

**Scenario 6**
Transaction log / WAL usage grows.

**Scenario 7**
Latest backup is corrupted.

### Task Element 7.1.5 — Requirement

Students must perform at least:

- 4 backup operations
- 4 restore operations
- 2 recovery simulations

---


---

## Task 7.2 — Database Security & Application Integration


### Task Element 7.2.1 — Duration
**16 Hours**

**Concept**
5 Hours

**Lab**
9 Hours

**Assessment**
2 Hours

### Task Element 7.2.2 — Security

- authentication
- authorization
- least privilege
- roles
- service accounts
- password policies
- TLS concepts
- encryption concepts
- auditing
- sensitive data protection

### Task Element 7.2.3 — SQL Injection

- vulnerable SQL
- SQL injection demonstration
- prepared statements
- parameterized queries
- safe dynamic SQL

### Task Element 7.2.4 — Application Integration

- connection strings
- connection pools
- transactions
- repository pattern
- application database users
- connection timeout
- connection leaks

### Task Element 7.2.5 — Testing

- test database
- test data
- schema isolation
- cleanup
- integration tests

---


---

# Job / Competency Unit 8 — Manage Database Change, Automation, Analytics and NoSQL Solutions

**Competency Unit Code:** CU-08

**Duration:** 28 Hours

### Tasks in this Competency Unit

- **Task 8.1:** Migration, Git, Automation & DevOps — 12 Hours
- **Task 8.2:** Data Warehouse, Analytics & NoSQL Exposure — 16 Hours

---

## Task 8.1 — Migration, Git, Automation & DevOps


### Task Element 8.1.1 — Duration
**12 Hours**

**Concept**
4 Hours

**Lab**
7 Hours

**Assessment**
1 Hour

### Task Element 8.1.2 — Version Control

- Git basics
- SQL script versioning
- database change documentation

### Task Element 8.1.3 — Migration

- schema migrations
- data migrations
- forward migration
- rollback
- backward compatibility
- zero-downtime migration concepts

### Task Element 8.1.4 — Tools

- Flyway
- Liquibase

### Task Element 8.1.5 — Automation

- Bash overview
- PowerShell overview
- Python database scripting overview
- scheduled backup scripts
- health-check scripts

### Task Element 8.1.6 — Containers

- Docker database containers
- persistent volumes
- environment variables
- development database setup

---


---

## Task 8.2 — Data Warehouse, Analytics & NoSQL Exposure


### Task Element 8.2.1 — Duration
**16 Hours**

**Concept**
5 Hours

**Lab**
9 Hours

**Assessment**
2 Hours

### Task Element 8.2.2 — Data Warehouse

- OLTP vs OLAP
- facts
- dimensions
- star schema
- snowflake schema
- measures
- SCD concepts

### Task Element 8.2.3 — ETL / ELT

- extraction
- transformation
- loading
- Bronze layer
- Silver layer
- Gold layer

### Task Element 8.2.4 — Analytics

- sales analysis
- customer segmentation
- product performance
- time-series reporting
- cumulative analysis
- ranking

### Task Element 8.2.5 — NoSQL Exposure

**MongoDB**
- document
- collection
- CRUD
- indexes
- aggregation concepts

**Redis**
- key/value
- strings
- hashes
- TTL
- caching
- sessions
- Pub/Sub concepts

---


---

# Program-Wide Practical, Assessment and Completion Requirements

The following sections are preserved from the original course without changing their content.

# 21. Practice Database

The entire course should use one evolving practical database.

## Business Scenario

**Multi-Branch Sales, Inventory & Procurement Company**

## Core Tables

```text
departments
employees
branches
customers
customer_addresses
suppliers
categories
products
product_prices
warehouses
inventory
stock_movements
orders
order_items
payments
purchase_orders
purchase_order_items
sales_targets
employee_salary_history
currencies
exchange_rates
audit_log
login_history
database_incidents
backup_history
job_execution_history
regions
```

---

# 22. Recommended Seed Data Volume

## Phase 1
**500 rows**

Used for:
- basic SQL
- data validation
- joins

## Phase 2
**10,000 rows**

Used for:
- aggregation
- reporting
- subqueries
- CTE

## Phase 3
**100,000+ rows**

Used for:
- window functions
- indexing
- execution plans
- performance labs

## Phase 4
**1,000,000+ rows optional**

Used for:
- advanced performance testing
- partitioning demonstrations
- large-table tuning

---

# 23. Weekly Practical Routine

A recommended 20-hour training week:

| Activity | Hours |
|---|---:|
| Instructor concept session | 5 |
| Guided lab | 7 |
| Independent lab | 4 |
| Assignment / troubleshooting | 2 |
| Review / viva / assessment | 2 |
| **Total** | **20** |

At **20 hours per week**, the program runs for approximately:

**20 weeks × 20 hours = 400 hours**

---

# 24. Assessment Model

| Assessment | Weight |
|---|---:|
| SQL Lab Exercises | 20% |
| Database Design Project | 10% |
| Vendor DBA Labs | 20% |
| Performance Tuning Labs | 15% |
| Backup / Recovery Practical | 10% |
| Security / Migration Lab | 5% |
| Final Capstone Project | 15% |
| Viva / Professional Review | 5% |
| **Total** | **100%** |

---

# 25. Minimum Practical Requirements

Before receiving completion certification, every student should complete at least:

- **200+ SQL queries**
- **10+ database design exercises**
- **20+ advanced analytical SQL exercises**
- **10+ execution-plan investigations**
- **10+ index experiments**
- **4 database engines configured**
- **10+ user/role/security labs**
- **8+ backup/restore operations**
- **2 recovery simulations**
- **3 migration exercises**
- **5 performance troubleshooting cases**
- **1 data warehouse mini-project**
- **1 final capstone project**

---

# 26. Practical Troubleshooting Cases

## Case 1 — Slow Query

Symptoms:

```text
Report normally runs in 2 seconds.
Today it requires 90 seconds.
```

Student must investigate:

- execution plan
- indexes
- statistics
- filtering
- joins
- row count
- data changes

---

## Case 2 — Blocking

Symptoms:

```text
Order update waits indefinitely.
```

Student must:

- identify blocking session
- inspect transaction
- decide whether to wait or terminate
- explain root cause

---

## Case 3 — Deadlock

Students reproduce a deadlock using two sessions and explain:

- resource order
- transaction order
- prevention strategy

---

## Case 4 — Failed Backup

Students identify:

- job status
- error log
- disk space
- permissions
- destination availability

---

## Case 5 — Deleted Data

Student must decide:

- rollback possible?
- restore needed?
- PITR needed?
- audit data available?

---

## Case 6 — Disk Full

Student investigates:

- data files
- logs
- backups
- temp usage
- archive/WAL/log growth

---

## Case 7 — Too Many Connections

Students investigate:

- active sessions
- idle sessions
- application connection pool
- max connection settings
- connection leaks

---

# 27. Intermediate Capstone Project

## Project Title

**Enterprise Sales, Inventory & Database Operations Lab**

## Part A — Database Design

Design:

- ERD
- normalized schema
- constraints
- indexes

## Part B — SQL Development

Develop:

- sales reports
- inventory reports
- customer analysis
- supplier analysis
- employee performance reports
- advanced window-function reports

## Part C — Stored Logic

Develop:

- order procedure
- inventory update logic
- audit trigger
- reporting function

## Part D — Security

Create:

- DBA role
- developer role
- reporting role
- application role
- read-only user

## Part E — Performance

Students must:

- create large datasets
- find slow queries
- analyze plans
- create indexes
- compare performance

## Part F — Backup / Recovery

Students must:

- backup
- simulate failure
- restore
- document recovery

## Part G — Vendor Comparison

Compare the implementation in:

- PostgreSQL
- Oracle
- SQL Server
- MySQL

---

# 28. Final Practical Examination

## Duration
**8 Hours inside the allocated module assessment hours**

### Section A — SQL
- joins
- CTE
- subqueries
- window functions

### Section B — Performance
- inspect slow SQL
- execution plan
- index recommendation

### Section C — DBA
- create user
- create role
- assign permissions
- inspect sessions

### Section D — Backup
- create backup
- restore database

### Section E — Troubleshooting
One randomly assigned incident:

- blocking
- disk issue
- failed backup
- slow query
- authentication issue

---

# 29. Completion Standard

Recommended passing criteria:

- Overall score: **60% minimum**
- Practical assessment: **60% minimum**
- Capstone project: mandatory
- Backup and recovery practical: mandatory
- Attendance recommendation: **80% minimum**
- All critical DBA labs must be completed

---

# 30. Recommended Certification Name

> **Professional Certificate in Practical SQL, DBMS & Multi-Vendor Database Administration — Intermediate Level**

## Duration

**400 Training Hours**

## Graduate Role Preparation

This course prepares students for junior-to-intermediate roles such as:

- SQL Developer
- Database Support Engineer
- Junior Database Administrator
- Application Database Developer
- Database Operations Engineer
- PostgreSQL Support DBA
- Oracle Junior DBA
- SQL Server Junior DBA
- MySQL Junior DBA
- Data / Reporting SQL Developer

---

# 31. Progression After This Course

After successfully completing this intermediate 400-hour course, students can progress to:

1. **Advanced SQL Performance Engineering**
2. **Professional PostgreSQL DBA**
3. **Professional Oracle DBA**
4. **Professional Microsoft SQL Server DBA**
5. **Professional MySQL DBA**
6. **Enterprise Backup, HA & Disaster Recovery**
7. **Cloud Database Engineering**
8. **NoSQL Professional**
9. **Database DevOps / SRE**
10. **Senior DBA / Database Architect**

---

# 32. 400-Hour Verification

```text
Module 01   16
Module 02   24
Module 03   32
Module 04   28
Module 05   32
Module 06   28
Module 07   20
Module 08   36
Module 09   32
Module 10   36
Module 11   28
Module 12   24
Module 13   20
Module 14   16
Module 15   12
Module 16   16
----------------
TOTAL      400 HOURS
```

**Verified Total: 400 Hours**

---

# 8-Competency-Unit Hour Verification

```text
CU-01    40
CU-02    60
CU-03    60
CU-04    56
CU-05    68
CU-06    52
CU-07    36
CU-08    28
----------------
TOTAL   400 HOURS
```

**Verified Total: 400 Hours**