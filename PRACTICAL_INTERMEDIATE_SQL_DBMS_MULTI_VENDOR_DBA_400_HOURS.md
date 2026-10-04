# Practical Intermediate SQL, DBMS & Multi-Vendor Database Administration Program

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

# 4. Program Duration Summary

| Module | Topic | Hours |
|---|---|---:|
| 1 | Lab Environment & Multi-Vendor Setup | 16 |
| 2 | Relational Modeling & Database Design | 24 |
| 3 | Intermediate SQL Querying | 32 |
| 4 | Joins, Subqueries & Set Operations | 28 |
| 5 | Advanced SQL & Analytical Functions | 32 |
| 6 | Database Objects & Stored Programming | 28 |
| 7 | Transactions, Concurrency & Data Integrity | 20 |
| 8 | Indexing, Execution Plans & Performance Tuning | 36 |
| 9 | PostgreSQL Administration Lab | 32 |
| 10 | Oracle Administration Lab | 36 |
| 11 | Microsoft SQL Server Administration Lab | 28 |
| 12 | MySQL Administration Lab | 24 |
| 13 | Backup, Recovery & Disaster Scenarios | 20 |
| 14 | Database Security & Application Integration | 16 |
| 15 | Migration, Git, Automation & DevOps | 12 |
| 16 | Data Warehouse, Analytics & NoSQL Exposure | 16 |
| **Total** |  | **400 Hours** |

---

# 5. Module 1 — Lab Environment & Multi-Vendor Setup

## Duration
**16 Hours**

### Concept / Demonstration
4 Hours

### Practical Lab
10 Hours

### Review / Assessment
2 Hours

## Topics

- Database client/server architecture
- Database service vs database instance
- Ports and connectivity
- Database command-line tools
- GUI administration tools
- Environment variables
- Database service management

## Practical Installation

### PostgreSQL
- Install PostgreSQL
- Configure service
- Create database
- Connect with `psql`
- Connect with pgAdmin

### Oracle
- Oracle Database environment overview
- SQL*Plus
- Oracle SQL Developer
- Database connectivity

### Microsoft SQL Server
- Install SQL Server
- Configure instance
- Install SSMS
- Connect to database

### MySQL
- Install MySQL Server
- MySQL Shell
- MySQL Workbench
- Create first database

## Lab Tasks

1. Install at least two database engines locally.
2. Connect using command-line clients.
3. Connect using GUI tools.
4. Create a training database.
5. Create a test user.
6. Start and stop a database service.
7. Identify default database ports.
8. Test local and remote connectivity.

## Deliverable

`LAB-01-DATABASE-ENVIRONMENT-REPORT.md`

---

# 6. Module 2 — Relational Modeling & Database Design

## Duration
**24 Hours**

### Concept
7 Hours

### Guided Design Lab
13 Hours

### Assessment
4 Hours

## Topics

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

## Normalization

- 1NF
- 2NF
- 3NF
- BCNF concepts
- Controlled denormalization

## Practical Project

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

## Lab Tasks

- Draw ERD
- Identify keys
- Define relationships
- Normalize tables
- Add business constraints
- Create physical schema
- Review naming standards

---

# 7. Module 3 — Intermediate SQL Querying

## Duration
**32 Hours**

### Concept
8 Hours

### Practical SQL
20 Hours

### Assessment
4 Hours

## Topics

### Query Construction

- SELECT
- aliases
- expressions
- DISTINCT
- ORDER BY
- LIMIT
- OFFSET
- TOP
- FETCH

### Filtering

- WHERE
- AND
- OR
- NOT
- BETWEEN
- IN
- LIKE
- NULL
- complex conditions

### Functions

- string functions
- numeric functions
- date functions
- conversion
- NULL handling
- CASE

### Aggregation

- COUNT
- SUM
- AVG
- MIN
- MAX
- GROUP BY
- HAVING
- conditional aggregation

## Practical Exercises

- Monthly sales report
- Customer purchase summary
- Product price analysis
- Inventory shortage report
- Employee salary analysis
- Branch-wise sales report

## Minimum Practice

**80 SQL exercises**

---

# 8. Module 4 — Joins, Subqueries & Set Operations

## Duration
**28 Hours**

### Concept
7 Hours

### Lab
17 Hours

### Assessment
4 Hours

## Joins

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

## Subqueries

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

## Set Operations

- UNION
- UNION ALL
- INTERSECT
- EXCEPT
- Oracle MINUS

## Labs

1. Customers without orders.
2. Products never sold.
3. Products priced above average.
4. Employees above departmental average.
5. Supplier purchase comparison.
6. Salespersons without current sales.
7. Customer lifetime value.
8. Revenue comparison across branches.

## Minimum Practice

**60 SQL exercises**

---

# 9. Module 5 — Advanced SQL & Analytical Functions

## Duration
**32 Hours**

### Concept
8 Hours

### Lab
20 Hours

### Assessment
4 Hours

## Common Table Expressions

- CTE
- multiple CTEs
- recursive CTE
- hierarchical data

## Window Functions

- OVER
- PARTITION BY
- ORDER BY
- window frames
- ROWS
- RANGE

### Ranking

- ROW_NUMBER
- RANK
- DENSE_RANK
- NTILE
- CUME_DIST
- PERCENT_RANK

### Analytical Functions

- LAG
- LEAD
- FIRST_VALUE
- LAST_VALUE
- running totals
- moving averages

## Business Problems

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

## Minimum Practice

**50 advanced SQL problems**

---

# 10. Module 6 — Database Objects & Stored Programming

## Duration
**28 Hours**

### Concept
7 Hours

### Lab
17 Hours

### Assessment
4 Hours

## Objects

- Views
- Materialized views
- Temporary tables
- Sequences
- Identity columns
- Indexes
- Synonyms concepts
- CTAS
- Generated columns

## Stored Programming

### PostgreSQL
- PL/pgSQL functions
- procedures

### Oracle
- PL/SQL
- procedures
- functions
- packages overview

### SQL Server
- T-SQL procedures
- functions

### MySQL
- stored procedures
- stored functions

## Common Topics

- variables
- parameters
- IF / ELSE
- loops
- exception handling
- cursors
- dynamic SQL
- triggers

## Practical Project

Build stored database logic for:

- order confirmation
- stock validation
- stock reduction
- payment recording
- audit logging

---

# 11. Module 7 — Transactions, Concurrency & Data Integrity

## Duration
**20 Hours**

### Concept
6 Hours

### Practical
11 Hours

### Assessment
3 Hours

## Topics

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

## Concurrency Problems

- dirty read
- non-repeatable read
- phantom read
- lost update

## Practical Labs

1. Two users update the same row.
2. Reproduce blocking.
3. Reproduce a deadlock.
4. Inspect lock information.
5. Roll back a failed order transaction.
6. Use savepoints.
7. Compare isolation levels.

---

# 12. Module 8 — Indexing, Execution Plans & Performance Tuning

## Duration
**36 Hours**

### Concept
10 Hours

### Performance Lab
22 Hours

### Assessment
4 Hours

## Indexes

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

## Core Performance Concepts

- cardinality
- selectivity
- statistics
- cost
- optimizer
- query planner

## Execution Plans

### PostgreSQL
- EXPLAIN
- EXPLAIN ANALYZE

### Oracle
- EXPLAIN PLAN
- execution plan interpretation

### SQL Server
- estimated plan
- actual plan

### MySQL
- EXPLAIN
- EXPLAIN ANALYZE where supported

## Join Algorithms

- nested loop
- hash join
- merge join

## Performance Labs

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

## Minimum Dataset

At least **100,000 rows** for intermediate performance labs.

---

# 13. Module 9 — PostgreSQL Administration Lab

## Duration
**32 Hours**

### Concept
8 Hours

### Administration Lab
20 Hours

### Assessment
4 Hours

## Architecture

- cluster
- instance concepts
- database
- schema
- tablespace
- process architecture

## Configuration

- `postgresql.conf`
- `pg_hba.conf`
- connection settings
- logging

## Security

- roles
- users
- privileges
- schemas
- ownership
- search path

## Maintenance

- VACUUM
- AUTOVACUUM
- ANALYZE
- statistics
- table bloat concepts

## Monitoring

- `pg_stat_activity`
- locks
- long-running transactions
- active connections

## Backup

- pg_dump
- pg_restore
- pg_dumpall concepts
- pg_basebackup

## Recovery Concepts

- WAL
- WAL archiving
- PITR

## Replication Exposure

- streaming replication
- logical replication
- PgBouncer concepts

## Practical Labs

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

# 14. Module 10 — Oracle Administration Lab

## Duration
**36 Hours**

### Concept
10 Hours

### DBA Lab
22 Hours

### Assessment
4 Hours

## Architecture

- Oracle instance
- Oracle database
- SGA
- PGA
- background processes
- datafiles
- control files
- redo logs

## Configuration

- initialization parameters
- PFILE
- SPFILE
- startup
- shutdown

## Storage

- tablespaces
- datafiles
- undo
- temp
- segment concepts

## Multitenant

- CDB
- PDB
- creating PDB
- opening / closing PDB
- common vs local users

## Users & Security

- CREATE USER
- roles
- privileges
- profiles
- least privilege

## Networking

- listener concepts
- services
- client connectivity

## Recovery Environment

- ARCHIVELOG
- Fast Recovery Area

## RMAN

- RMAN connection
- full backup
- incremental concepts
- restore
- recover
- backup validation
- PITR demonstration

## Data Movement

- Data Pump
- expdp
- impdp

## Practical Labs

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

# 15. Module 11 — Microsoft SQL Server Administration Lab

## Duration
**28 Hours**

### Concept
7 Hours

### Lab
17 Hours

### Assessment
4 Hours

## Architecture

- instance
- database
- MDF
- NDF
- LDF
- TempDB

## Security

- Windows authentication
- SQL authentication
- logins
- users
- roles
- permissions

## Administration

- SSMS
- database properties
- database files
- SQL Server Agent
- jobs

## Performance

- execution plans
- statistics
- indexes
- fragmentation
- Query Store concepts
- Extended Events concepts

## Backup

- full backup
- differential backup
- transaction log backup
- restore

## Recovery Models

- Simple
- Full
- Bulk-logged concepts

## HA Exposure

- Always On overview
- log shipping overview
- replication overview

## Practical Labs

- Create database
- Create login
- Create role
- Create SQL Agent job
- Backup and restore
- Test recovery model
- Analyze Query Store information
- Investigate blocking

---

# 16. Module 12 — MySQL Administration Lab

## Duration
**24 Hours**

### Concept
6 Hours

### Lab
15 Hours

### Assessment
3 Hours

## Architecture

- MySQL Server
- schemas
- storage engines
- InnoDB

## Configuration

- `my.cnf`
- connections
- server variables

## Security

- users
- hosts
- privileges
- roles where supported

## InnoDB

- buffer pool
- redo
- undo
- transactions

## Logging

- error log
- slow query log
- binary log

## Performance

- EXPLAIN
- indexes
- slow queries

## Backup & Recovery

- mysqldump
- logical restore
- MySQL Shell concepts
- physical backup concepts

## Replication Exposure

- primary / replica
- binary log
- Group Replication concepts
- InnoDB Cluster concepts

## Labs

- User creation
- Permission management
- Slow-query logging
- Backup
- Restore
- Index tuning
- Configuration inspection

---

# 17. Module 13 — Backup, Recovery & Disaster Scenarios

## Duration
**20 Hours**

### Concept
5 Hours

### Recovery Lab
12 Hours

### Assessment
3 Hours

## Backup Types

- logical
- physical
- full
- differential
- incremental
- transaction log
- WAL / redo

## Core Concepts

- backup retention
- backup rotation
- restore
- recovery
- RPO
- RTO
- PITR
- disaster recovery

## Practical Scenarios

### Scenario 1
User deletes important records.

### Scenario 2
Database table is dropped.

### Scenario 3
Database server crashes.

### Scenario 4
Backup job fails.

### Scenario 5
Disk becomes full.

### Scenario 6
Transaction log / WAL usage grows.

### Scenario 7
Latest backup is corrupted.

## Requirement

Students must perform at least:

- 4 backup operations
- 4 restore operations
- 2 recovery simulations

---

# 18. Module 14 — Database Security & Application Integration

## Duration
**16 Hours**

### Concept
5 Hours

### Lab
9 Hours

### Assessment
2 Hours

## Security

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

## SQL Injection

- vulnerable SQL
- SQL injection demonstration
- prepared statements
- parameterized queries
- safe dynamic SQL

## Application Integration

- connection strings
- connection pools
- transactions
- repository pattern
- application database users
- connection timeout
- connection leaks

## Testing

- test database
- test data
- schema isolation
- cleanup
- integration tests

---

# 19. Module 15 — Migration, Git, Automation & DevOps

## Duration
**12 Hours**

### Concept
4 Hours

### Lab
7 Hours

### Assessment
1 Hour

## Version Control

- Git basics
- SQL script versioning
- database change documentation

## Migration

- schema migrations
- data migrations
- forward migration
- rollback
- backward compatibility
- zero-downtime migration concepts

## Tools

- Flyway
- Liquibase

## Automation

- Bash overview
- PowerShell overview
- Python database scripting overview
- scheduled backup scripts
- health-check scripts

## Containers

- Docker database containers
- persistent volumes
- environment variables
- development database setup

---

# 20. Module 16 — Data Warehouse, Analytics & NoSQL Exposure

## Duration
**16 Hours**

### Concept
5 Hours

### Lab
9 Hours

### Assessment
2 Hours

## Data Warehouse

- OLTP vs OLAP
- facts
- dimensions
- star schema
- snowflake schema
- measures
- SCD concepts

## ETL / ELT

- extraction
- transformation
- loading
- Bronze layer
- Silver layer
- Gold layer

## Analytics

- sales analysis
- customer segmentation
- product performance
- time-series reporting
- cumulative analysis
- ranking

## NoSQL Exposure

### MongoDB
- document
- collection
- CRUD
- indexes
- aggregation concepts

### Redis
- key/value
- strings
- hashes
- TTL
- caching
- sessions
- Pub/Sub concepts

---

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
