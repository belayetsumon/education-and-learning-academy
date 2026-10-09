# PROFESSIONAL SQL PROGRAMMING & ENTERPRISE DATABASE ENGINEERING

**Comprehensive Course Syllabus and Delivery Specification | 2026 Edition**

**Document status:** Revised curriculum proposal  
**Version:** 1.1 | **Issued:** 9 October 2026  
**Level:** Foundation to advanced professional practice  
**Primary platform:** PostgreSQL | **Application stack:** Java and Spring Boot

> **Programme purpose**  
> Develop job-ready SQL and database engineering capabilities for transactional, data-intensive enterprise systems. The programme progresses from relational design and SQL programming to concurrency, financial correctness, distributed workflows, production operations, and responsible AI-assisted database access.

## 1. Programme at a glance

| Programme parameter | Specification |
|---|---|
| Total guided learning | **240 hours** |
| Delivery schedule | **24 weeks × 10 hours/week** |
| Curriculum | **16 integrated modules** |
| Theory and guided discussion | **84 hours (35%)** |
| Practical labs, projects and assessment | **156 hours (65%)** |
| Learning model | Concept → demonstration → guided practice → independent implementation → verification |
| Principal domains | ERP, accounting and finance, e-commerce, banking, SaaS and operational analytics |
| Final assessment | Integrated multi-tenant ERP finance and sales capstone |
| Target participants | Software developers, database engineers, backend developers, technical leads and advanced learners |

**Entry expectations.** Learners should understand basic programming constructs, be comfortable using a command line, and have introductory knowledge of data structures or relational tables. Prior knowledge of Java is helpful for Module 15, but SQL concepts and PostgreSQL workflows are introduced from first principles. Learners without Java experience may complete the integration lab with instructor-provided scaffolding.

**Scope statement.** This is a **course syllabus**, not a 240-hour textbook or a claim of formal institutional accreditation. Course completion criteria below are proposed programme standards; an adopting institution may align them with its own qualification framework.

## 2. Programme rationale and professional outcomes

Modern databases are not merely repositories for application records: they enforce business invariants, coordinate concurrent operations, support reliable integration, and enable secure analytics. Learners therefore study SQL as both a query language and a foundation for dependable enterprise software.

Upon successful completion, learners will be able to:

| Code | Course learning outcome | Evidence of achievement |
|---|---|---|
| CLO-01 | Model normalized, maintainable relational schemas with sound constraints and migration practices. | ERD, DDL and migration scripts |
| CLO-02 | Write correct SQL for data manipulation, joins, subqueries, reporting and advanced analytics. | Tested SQL scripts and reports |
| CLO-03 | Implement functions, procedures and triggers with explicit business rules and testable behaviour. | PL/pgSQL artefacts and tests |
| CLO-04 | Apply ACID principles, isolation levels and transactional recovery to protect financial data. | Concurrent transaction and ledger tests |
| CLO-05 | Diagnose contention, MVCC effects, locks, deadlocks and serialization failures. | Reproduction logs and corrective implementation |
| CLO-06 | Design idempotent commands and reliable Inbox/Outbox-based event processing. | Duplicate-request and crash-recovery tests |
| CLO-07 | Evaluate distributed consistency trade-offs and implement a failure-aware Saga workflow. | Service workflow and compensation demonstrations |
| CLO-08 | Profile and improve PostgreSQL queries and maintain recoverable database operations. | Query plans, before/after measurements and restore evidence |
| CLO-09 | Protect enterprise data through access control, SQL injection prevention and multi-tenant isolation. | Security configuration and negative test results |
| CLO-10 | Integrate SQL with Spring Boot and constrained AI/RAG use cases without compromising data integrity or access control. | Tested application endpoints and read-only AI demonstration |

## 3. Reference and learning-resource framework

The following texts are retained from the source curriculum as **thematic learning references**; chapter assignments and bibliographic publication details should be confirmed against the specific editions acquired by the teaching institution.

| Code | Recommended reference | Intended application in this course |
|---|---|---|
| **B1** | *SQL: The Practical Guide* (listed as 2026) | SQL foundations, table design and essential programming |
| **B2** | *Advanced SQL* (listed as 2026) | Analytical SQL, complex queries and advanced SQL techniques |
| **B3** | *Learn PostgreSQL*, Third Edition (listed as 2026) | PostgreSQL implementation, MVCC, transactions and performance |
| **B4** | *Designing Data-Intensive Applications*, Second Edition (listed as 2026) | Data reliability, distributed systems, consistency and scalability |

**Supplementary materials:** PostgreSQL documentation, instructor-maintained SQL lab scripts, Java/Spring Boot examples, pgvector guidance, database security checklists and reproducible concurrency test fixtures. AI, MCP, provider-specific APIs and library-version topics require supplementary materials rather than assuming comprehensive coverage in B1–B4.

## 4. Curriculum structure and time allocation

| No. | Module | Theory (h) | Practical (h) | Total (h) | Main references |
|---|---|---:|---:|---:|---|
| 01 | Database Fundamentals and Development Environment | 4 | 4 | **8** | B1, B3 |
| 02 | SQL Programming Fundamentals | 6 | 12 | **18** | B1 |
| 03 | Database Objects and Relational Design | 6 | 10 | **16** | B1, B3 |
| 04 | Advanced SQL Queries and Analytics | 6 | 12 | **18** | B2 |
| 05 | SQL Functions, Procedures and Triggers | 5 | 9 | **14** | B2, B3 |
| 06 | ACID Transactions and Isolation Levels | 6 | 10 | **16** | B3, B4 |
| 07 | Locks, Deadlocks, MVCC and Concurrency | 5 | 9 | **14** | B3, B4 |
| 08 | Idempotency and Reliable Transaction Processing | 6 | 10 | **16** | B3, B4 |
| 09 | Distributed Transactions and Consistency | 6 | 10 | **16** | B4 |
| 10 | PostgreSQL Query Optimization and Performance | 6 | 12 | **18** | B2, B3 |
| 11 | PostgreSQL Administration and Reliability | 5 | 7 | **12** | B3, B4 |
| 12 | Database Security and Multi-Tenant Design | 4 | 8 | **12** | B3, B4 |
| 13 | Modern SQL, JSONB and Hybrid Data Models | 4 | 6 | **10** | B2, B3 |
| 14 | AI, LLM, RAG and SQL Integration | 4 | 8 | **12** | B2 + supplemental labs |
| 15 | Enterprise Database Integration with Spring Boot | 5 | 11 | **16** | B3, B4 + Java labs |
| 16 | Enterprise Capstone Project and Assessment | 6 | 18 | **24** | All |
| | **TOTAL** | **84** | **156** | **240** | |

**Delivery guidance.** Theory time includes structured discussion, worked examples and instructor demonstrations. Practical time includes supervised labs, independent implementation, test execution, technical review, and assessed project work. Module teaching and laboratory sessions may span adjacent weeks; the 24-week calendar in Appendix A allocates exactly 10 hours per week.

## 5. Detailed module specifications

### Module 01 — Database Fundamentals and Development Environment
**Duration:** 8 hours (4 theory / 4 practical)  
**Purpose:** Establish the conceptual and technical foundation for a reproducible SQL development environment.

**Essential content:** DBMS/RDBMS concepts; SQL standards versus PostgreSQL implementation; relations, attributes, tuples, keys and relationships; DDL, DML, DQL, DCL and TCL terminology; installation and configuration of PostgreSQL, pgAdmin and `psql`; script organisation and execution.

**Performance outcomes:** Learners can distinguish relational concepts from vendor-specific features, establish a local database, use both graphical and command-line tools, and execute repeatable setup scripts.

**Practical deliverable:** Configured PostgreSQL environment, initial ERP database and a documented setup/verification script.  
**Evidence:** Successful schema creation, connection and script replay.

### Module 02 — SQL Programming Fundamentals
**Duration:** 18 hours (6 theory / 12 practical)  
**Purpose:** Develop accurate and safe everyday SQL programming skills.

**Essential content:** `SELECT`, `INSERT`, `UPDATE`, `DELETE`; `WHERE`, boolean logic, `DISTINCT`, `ORDER BY`, `LIMIT/OFFSET`; `NULL`, `CASE`, `COALESCE`; numeric, text and date functions; inner/outer joins; aggregate queries, `GROUP BY`, `HAVING`; subqueries, `EXISTS`, `IN`; `UNION`, `INTERSECT`, `EXCEPT`; parameterized queries and safe update/delete practices.

**Performance outcomes:** Learners can implement CRUD operations, combine related data, produce grouped reports, reason correctly about `NULL`, and prevent common query mistakes.

**Practical deliverable:** Customer, supplier, product and sales-order SQL workbook with expected outputs and edge-case tests.  
**Evidence:** Correct result sets, parameterization examples and repeatable test data.

### Module 03 — Database Objects and Relational Design
**Duration:** 16 hours (6 theory / 10 practical)  
**Purpose:** Convert domain requirements into reliable and maintainable relational structures.

**Essential content:** PostgreSQL types; `CREATE`, `ALTER`, `DROP`; primary, foreign, unique, check and non-null constraints; identity, sequences and UUIDs; schemas; views and materialized views; normalization through 3NF, with BCNF introduction; relationships and ERDs; indexing fundamentals; schema migrations; audit-column conventions.

**Performance outcomes:** Learners can produce ERDs, select appropriate types, express business invariants through constraints, and evolve a schema without manual drift.

**Practical deliverable:** Normalized ERP schema containing Customers, Invoices, InvoiceLines, Payments, Accounts and JournalEntries, delivered as versioned migration scripts.  
**Evidence:** ERD, DDL, referential-integrity tests and migration history.

### Module 04 — Advanced SQL Queries and Analytics
**Duration:** 18 hours (6 theory / 12 practical)  
**Purpose:** Build expressive SQL for operational reporting and analytical workloads.

**Essential content:** CTEs and recursive CTEs; window functions including `ROW_NUMBER`, `RANK`, `DENSE_RANK`, `LAG` and `LEAD`; `PARTITION BY`; grouping sets, `ROLLUP`, `CUBE`; `LATERAL` joins; correlated subqueries; conditional aggregation; offset and keyset pagination; report correctness and test data design.

**Performance outcomes:** Learners can generate running balances, aging reports and rankings and explain the choice of analytical SQL constructs.

**Practical deliverable:** Financial and sales reporting pack covering receivables aging, stock movements, customer rankings and trend dashboards.  
**Evidence:** Verified SQL queries and reconciled report totals.

### Module 05 — SQL Functions, Procedures and Triggers
**Duration:** 14 hours (5 theory / 9 practical)  
**Purpose:** Encapsulate database-side behaviour where it strengthens consistency and reuse.

**Essential content:** SQL functions and PL/pgSQL; variables, branching, loops, exceptions; stored procedures; permissible transaction-control contexts; row/statement triggers; audit trails; validation routines; set-returning functions; error reporting; testability and appropriate boundaries for database-side business logic.

**Performance outcomes:** Learners can implement reusable routines, understand execution side effects, and test failure behaviour.

**Practical deliverable:** Invoice-validation routine, payment-posting procedure and auditable change trigger.  
**Evidence:** Runnable routine definitions and positive/negative tests.

### Module 06 — ACID Transactions and Isolation Levels
**Duration:** 16 hours (6 theory / 10 practical)  
**Purpose:** Preserve correctness in multi-step financial and operational transactions.

**Essential content:** Atomicity, Consistency, Isolation and Durability; `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`; business transaction boundaries; dirty/non-repeatable/phantom reads; serialization anomalies; `READ COMMITTED`, `REPEATABLE READ` and `SERIALIZABLE`; PostgreSQL treatment of `READ UNCOMMITTED`; retry boundaries and failure recovery.

**Performance outcomes:** Learners can choose transaction scopes, predict isolation outcomes and design safe rollback/retry behaviour.

**Practical deliverable:** Balanced general-ledger posting and concurrent account-transfer test suite.  
**Evidence:** No partial posting after rollback, reconciled balances and documented isolation observations.

### Module 07 — Locks, Deadlocks, MVCC and Concurrency
**Duration:** 14 hours (5 theory / 9 practical)  
**Purpose:** Diagnose and resolve conflicting access to shared records.

**Essential content:** MVCC and snapshot visibility; row and table locks; `SELECT ... FOR UPDATE`, `NOWAIT`, `SKIP LOCKED`; advisory locks; optimistic versus pessimistic locking; deadlock detection; timeouts; serialization failures; lock acquisition order; reducing contention and bounded retries.

**Performance outcomes:** Learners can reproduce a deadlock, analyse blocked sessions, select suitable locking controls and verify the absence of lost updates.

**Practical deliverable:** Deadlock reproduction report and concurrency-safe inventory reservation operation.  
**Evidence:** Session timelines, observed database errors and passing race-condition tests.

### Module 08 — Idempotency and Reliable Transaction Processing
**Duration:** 16 hours (6 theory / 10 practical)  
**Purpose:** Make externally retried commands safe without duplicating business effects.

**Essential content:** Idempotency semantics; request keys and fingerprints; uniqueness constraints; `INSERT ... ON CONFLICT`, `MERGE`; duplicate submission and replay handling; concurrent duplicate requests; atomic state transitions; financial ledger consistency; transactionally persisted Inbox/Outbox records; crash/restart behaviour; reconciliation.

**Performance outcomes:** Learners can distinguish a repeated request from a new transaction, return consistent results for valid retries, and prevent duplicate posting under concurrency.

**Practical deliverable:** Idempotent payment API and durable processing record with retry/recovery scenarios.  
**Evidence:** One financial effect per logical payment, fingerprint-mismatch rejection and concurrency test results.

### Module 09 — Distributed Transactions and Consistency
**Duration:** 16 hours (6 theory / 10 practical)  
**Purpose:** Coordinate business workflows that span services and infrastructure failures.

**Essential content:** Distributed data fundamentals; consistency models and CAP trade-offs; two-phase commit and operational limitations; Saga orchestration versus choreography; transactional Outbox and CDC; at-least-once message delivery and consumer deduplication; eventual consistency; compensating actions; CQRS; message replay and operational recovery.

**Performance outcomes:** Learners can identify unavoidable trade-offs, implement explicit recovery states and explain why compensations are not equivalent to a global database rollback.

**Practical deliverable:** Order → Payment → Inventory → Shipment Saga using durable Outbox events, retries and compensating actions.  
**Evidence:** Success, timeout, duplicate-event and partial-failure scenarios with recoverable outcomes.

### Module 10 — PostgreSQL Query Optimization and Performance
**Duration:** 18 hours (6 theory / 12 practical)  
**Purpose:** Make SQL performance observable, explainable and measurable.

**Essential content:** PostgreSQL planner and cost estimation; `EXPLAIN (ANALYZE, BUFFERS)`; sequential/index scans and joins; B-tree, GIN, GiST, BRIN; multicolumn, partial, expression and covering indexes; query rewriting; table statistics; partitioning; materialized views; `pg_stat_statements`; benchmarking with representative data and `pgbench`.

**Performance outcomes:** Learners can find bottlenecks, justify index and query changes, and compare baseline and improved performance without overgeneralizing from small test datasets.

**Practical deliverable:** Optimized sales-report query accompanied by annotated plans and repeatable benchmarks.  
**Evidence:** Before/after execution plans, timings and a documented tuning rationale.

### Module 11 — PostgreSQL Administration and Reliability
**Duration:** 12 hours (5 theory / 7 practical)  
**Purpose:** Operate PostgreSQL with measurable recoverability and observability.

**Essential content:** Configuration and server processes; WAL and checkpoints; `VACUUM`, `ANALYZE`, autovacuum; logical/physical backup concepts; restore and point-in-time recovery concepts; replication fundamentals; connection pooling; monitoring; maintenance plans; RPO and RTO; deployment and schema migration safety.

**Performance outcomes:** Learners can execute and verify a backup/restore exercise, identify operational health signals and explain recovery objectives.

**Practical deliverable:** ERP database backup and verified restoration with a short recovery runbook.  
**Evidence:** Restored row counts and business invariants, operation logs and recovery notes.

### Module 12 — Database Security and Multi-Tenant Design
**Duration:** 12 hours (4 theory / 8 practical)  
**Purpose:** Enforce least privilege and prevent cross-tenant data exposure.

**Essential content:** Users and roles, `GRANT`/`REVOKE`; Row-Level Security; SQL injection and parameterization; TLS and encryption concepts; protection of personal data; audit and retention practices; shared-schema `tenant_id`, schema-per-tenant and database-per-tenant isolation; tenant-aware migrations, backups and isolation tests.

**Performance outcomes:** Learners can evaluate tenancy models, apply access policies and demonstrate that unauthorised cross-tenant reads and writes are blocked.

**Practical deliverable:** Secure shared-schema tenancy example with documented alternatives for stronger isolation.  
**Evidence:** Role matrix, RLS configuration and cross-tenant negative tests.

### Module 13 — Modern SQL, JSONB and Hybrid Data Models
**Duration:** 10 hours (4 theory / 6 practical)  
**Purpose:** Extend relational schemas without sacrificing transactional control.

**Essential content:** JSON versus JSONB; operators and JSONPath; GIN indexing; arrays and composite types; generated columns; `UPSERT` and `MERGE`; recursive structures; current SQL/JSON features; relational versus document-oriented modelling; validation and schema constraints.

**Performance outcomes:** Learners can identify appropriate uses for flexible attributes while retaining relational keys and enforceable business rules.

**Practical deliverable:** JSONB-backed payment-gateway and shipping-carrier configurations linked to normalized transaction tables.  
**Evidence:** Validated documents, query/index examples and negative tests for invalid configuration.

### Module 14 — AI, LLM, RAG and SQL Integration
**Duration:** 12 hours (4 theory / 8 practical)  
**Purpose:** Enable useful AI-assisted database interactions while constraining risk.

**Essential content:** Embeddings and vector similarity; pgvector and index choices; hybrid keyword/structured/vector retrieval; RAG architecture; natural-language-to-SQL; read-only query execution, schema allowlists, result limits and runtime restrictions; hallucinations and prompt injection; tenant-scoped retrieval; Spring AI integration and an introduction to the Model Context Protocol (MCP).

**Performance outcomes:** Learners can explain retrieval limitations, build a small grounded retrieval workflow and reject unsafe or unauthorised generated SQL.

**Practical deliverable:** Product/policy information assistant with tenant-aware retrieval and controlled read-only SQL reporting.  
**Evidence:** Retrieval evaluation examples, denied write attempts, and SQL access-control tests.

### Module 15 — Enterprise Database Integration with Spring Boot
**Duration:** 16 hours (5 theory / 11 practical)  
**Purpose:** Apply SQL reliability patterns through a production-oriented backend application.

**Essential content:** JDBC, Spring Data JPA, Hibernate, native SQL; repository/service separation; `@Transactional` boundaries and proxy semantics; propagation/isolation; optimistic and pessimistic locking; HikariCP pooling; Flyway or Liquibase migrations; database exception handling; retry policies; Testcontainers and integration tests; API-to-database consistency.

**Performance outcomes:** Learners can implement a transaction-safe service, identify ORM and SQL boundary issues and validate behaviour against a real PostgreSQL instance.

**Practical deliverable:** Spring Boot sales/payment API with idempotency, transaction boundaries and concurrency integration tests.  
**Evidence:** Versioned code, executable tests and documented failure handling.

### Module 16 — Enterprise Capstone Project and Assessment
**Duration:** 24 hours (6 guided review / 18 practical)  
**Purpose:** Integrate the programme's competencies into a single demonstrable enterprise solution.

**Essential content:** Requirements and invariant review; relational model approval; implementation and versioned migration; test scenarios; fault injection; query profiling; access-control verification; recovery proof; AI demonstration; documentation and technical defence.

**Performance outcomes:** Learners can deliver and defend a consistent, secure, recoverable transaction-processing design and distinguish demonstrated properties from untested assumptions.

**Practical deliverable:** Multi-tenant ERP finance and sales database and its Java integration, as specified in Section 8.  
**Evidence:** Completed capstone package, automated test results, performance report and demonstration.

## 6. Teaching, practice and verification methodology

A professional learning cycle is used throughout the course:

1. **Explain the requirement.** Identify the business rule, data model and relevant failure modes.
2. **Demonstrate the construct.** Show the SQL/PostgreSQL feature on a small, inspectable dataset.
3. **Implement the scenario.** Complete a realistic finance, sales, inventory or SaaS lab.
4. **Test negative cases.** Include invalid data, concurrency, duplicate requests, failures and rejected access.
5. **Measure and review.** Record correctness evidence, plans, timings and any unresolved limitations.
6. **Retain reusable artefacts.** Commit migration files, scripts, tests and lab notes to version control.

Laboratory submissions should include a README, setup instructions, versioned SQL, sample data or fixtures, expected results and test evidence. Database operations that alter data must be exercised against disposable training environments, not production systems.

## 7. Assessment and competency standards

| Assessment component | Weight | Principal evidence |
|---|---:|---|
| Written quizzes and concept checks | 20% | SQL semantics, architecture and failure-mode reasoning |
| SQL laboratory assignments | 35% | Working scripts, routines, query plans and tests |
| Midterm practical examination | 15% | Independent database development and transaction tasks |
| Enterprise capstone project | 30% | Integrated implementation, demonstration and technical defence |
| **TOTAL** | **100%** | |

**Proposed completion threshold:** At least **60% overall**, together with satisfactory demonstrations of SQL foundations, ACID correctness, concurrency safety, idempotent payment processing and capstone data-integrity checks. These essential competency gates must be passed even if the numeric overall grade is sufficient.

**Capstone grading rubric (within the 30% capstone component):**

| Evaluation dimension | Share of capstone score |
|---|---:|
| Relational design, migrations and constraints | 20% |
| Financial and transactional correctness | 25% |
| Idempotency, messaging and failure recovery | 20% |
| Performance diagnosis and benchmark quality | 10% |
| Tenant isolation and database security | 10% |
| Constrained AI-assisted retrieval/reporting | 5% |
| Automated tests, documentation and defence | 10% |
| **TOTAL** | **100%** |

**Assessment integrity:** Correctness and security take precedence over presentation quality. For example, a visually complete capstone does not pass its mandatory gates if duplicate payments can create duplicate journal postings, financial entries become unbalanced, or a user can access another tenant's data.

## 8. Final capstone specification: Enterprise ERP Finance and Sales Database

### 8.1 Business scenario

Design a simplified **multi-tenant ERP** covering sales, inventory reservation, invoicing, payment collection and double-entry financial posting. The database is the system of record; service integration and AI-assisted reporting must respect its transactional boundaries and access policies.

### 8.2 Core process

```text
Customer Sales Order
        ↓
Inventory Reservation
        ↓
Sales Invoice
        ↓
Idempotent Payment Command
        ↓
Double-Entry General Ledger
        ↓
Transactional Outbox → Event Consumer(s)
        ↓
Financial Reports + Controlled AI-Assisted Queries
```

**Exception paths are mandatory:** payment failure, stock shortage, repeated submission, delayed event delivery, interrupted processing and rejected tenant access. Compensation and retry behaviour must be explicitly documented; an asynchronous workflow must not be represented as one global ACID transaction.

### 8.3 Required solution artefacts

1. Requirements brief, domain rules, ERD and tenancy decision record.
2. Version-controlled SQL DDL, constraints, indexes, seed data and schema migrations.
3. SQL queries for operational, financial and management reporting.
4. Transaction-safe posting operations and an idempotent payment interface.
5. Inventory reservation/concurrency controls and documented lock strategy.
6. Transactional Outbox and at-least-once consumer handling with deduplication.
7. Role/RLS policy implementation, negative isolation tests and audit evidence.
8. Query plans, benchmark procedure and before/after tuning results.
9. Backup/restore demonstration and a concise recovery procedure.
10. Java/Spring Boot integration with automated database tests.
11. Guardrailed AI/RAG demonstration for approved read-only reporting.
12. Technical report containing architecture, limitations, risks and test outcomes.

### 8.4 Mandatory acceptance tests

| Control objective | Required verification |
|---|---|
| Ledger integrity | Each posted journal is balanced; failed postings leave no partial journal. |
| Payment idempotency | Identical retries have one logical financial effect; conflicting replays are rejected. |
| Concurrent stock safety | Simultaneous reservations cannot violate the stock availability rule. |
| Recovery and event reliability | Interrupted work can be resumed or reconciled; replayed events do not duplicate effects. |
| Tenant isolation | Unauthorised cross-tenant reads and writes are denied by enforced controls. |
| SQL performance | At least one representative slow query is analysed and improved with reproducible evidence. |
| AI access safety | Generated SQL is read-only, constrained to authorised data and rejected when unsafe. |
| Operability | Migrations and restore instructions are executable and verified. |

**Success criterion:** Learners must demonstrate these controls with repeatable tests, not solely explain them in a presentation.

## 9. Software, infrastructure and laboratory environment

| Area | Recommended tools and components |
|---|---|
| Relational database | PostgreSQL 18 (or an institution-supported compatible release) |
| Database development | `psql`, pgAdmin, DBeaver |
| Backend application | Java 21+ and Spring Boot |
| SQL data access | JDBC, Spring Data JPA, Hibernate |
| Migration management | Flyway or Liquibase |
| Containers | Docker and Docker Compose |
| Automated verification | JUnit and Testcontainers |
| Messaging exercises | RabbitMQ or Kafka |
| Performance tools | `EXPLAIN (ANALYZE, BUFFERS)`, `pg_stat_statements`, `pgbench` |
| AI extension | pgvector and Spring AI |
| Source management | Git and GitHub or equivalent repository hosting |

**Environment notes:** Instructors should lock tested versions of PostgreSQL, Java, libraries and container images before each cohort; confirm compatible extension versions; provide disposable datasets; and avoid storing secrets in committed configuration. The exact technology versions above are curriculum recommendations rather than prerequisites for every individual lab.

## 10. Competency-to-module traceability

| Priority competency | Modules | Required applied evidence |
|---|---|---|
| Core SQL and relational design | 01–03 | CRUD, multi-table queries, constraints and migrations |
| Advanced SQL and analytical reports | 04–05 | Window-based reports, programmable SQL routines |
| ACID transactions and isolation | 06 | Atomic financial journal and isolation tests |
| Locks, deadlocks and MVCC | 07 | Documented deadlock and safe inventory reservation |
| Idempotency and reliable processing | 08 | Duplicate-safe payment processing |
| Distributed transactions and consistency | 09 | Saga, Outbox, replay and compensation |
| PostgreSQL tuning and operations | 10–11 | Query plans, measured improvements and restore demonstration |
| Security and multi-tenancy | 12 | Least privilege and negative tenant-leak tests |
| Modern SQL and hybrid data | 13 | Validated JSONB configuration with relational constraints |
| AI, LLM, RAG and SQL | 14 | Tenant-aware, read-only AI query demonstration |
| Java/Spring Boot enterprise integration | 15 | Tested transactional API |
| Cross-domain professional competency | 16 | Integrated capstone and technical defence |

## 11. Course governance and publication notes

- **Version control:** Maintain a dated syllabus revision log; retain module identifiers and hours when publishing updates.
- **Reproducibility:** Ship a frozen lab repository with database migrations, fixtures, verified exercises and tests.
- **Teaching currency:** Review PostgreSQL features, Spring APIs and AI safety controls before each new cohort.
- **Bibliographic accuracy:** Verify the exact titles, authors, publishers, editions and ISBNs of all recommended books before external publication; the original source identified references by short title only.
- **Qualification alignment:** If this course will be used within a formal skills or competency framework, map each learning outcome to the approved performance criteria, evidence guide and assessment conditions separately. This document does not purport to replace those standards.

## Appendix A — Indicative 24-week delivery calendar

The programme uses **10 guided hours per week**. Modules may begin or conclude within the same week; this schedule reconciles exactly to the module hour allocations in Section 4.

| Week | Learning allocation | Hours |
|---|---|---:|
| 01 | Module 01 (8h) + Module 02 (2h) | 10 |
| 02 | Module 02 (10h) | 10 |
| 03 | Module 02 (6h) + Module 03 (4h) | 10 |
| 04 | Module 03 (10h) | 10 |
| 05 | Module 03 (2h) + Module 04 (8h) | 10 |
| 06 | Module 04 (10h) | 10 |
| 07 | Module 05 (10h) | 10 |
| 08 | Module 05 (4h) + Module 06 (6h) | 10 |
| 09 | Module 06 (10h) | 10 |
| 10 | Module 07 (10h) | 10 |
| 11 | Module 07 (4h) + Module 08 (6h) | 10 |
| 12 | Module 08 (10h) | 10 |
| 13 | Module 09 (10h) | 10 |
| 14 | Module 09 (6h) + Module 10 (4h) | 10 |
| 15 | Module 10 (10h) | 10 |
| 16 | Module 10 (4h) + Module 11 (6h) | 10 |
| 17 | Module 11 (6h) + Module 12 (4h) | 10 |
| 18 | Module 12 (8h) + Module 13 (2h) | 10 |
| 19 | Module 13 (8h) + Module 14 (2h) | 10 |
| 20 | Module 14 (10h) | 10 |
| 21 | Module 15 (10h) | 10 |
| 22 | Module 15 (6h) + Module 16 (4h) | 10 |
| 23 | Module 16 (10h) | 10 |
| 24 | Module 16 (10h) | 10 |
| | **TOTAL** | **240** |

## Appendix B — Recommended assessment record

For each assessed activity, retain: **module/CLO mapping; learner identifier; task description; environment version; submitted code/scripts; expected result; observed result; failed cases; review feedback; competency decision; and resubmission record when applicable**.

---

*End of revised syllabus | Professional SQL Programming & Enterprise Database Engineering | Version 1.1 (2026)*
