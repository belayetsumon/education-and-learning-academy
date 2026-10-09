# M01 — Database Fundamentals and Development Environment

**Professional SQL Programming & Enterprise Database Engineering — 2026 Edition**  
**Complete consolidated Markdown teaching resource**  
**Revision:** v0.1 · 10 October 2026  
**Guided learning:** 8 hours (4 theory + 4 practical)  
**Baseline:** PostgreSQL 16.x, psql 16.x and pgAdmin 4 v9.x target  
**Source requirements:** `SQL_Curriculum_Authoring_Standard_v1.0.md` (SQL-EDU-STD-001 v1.0) and 2026 syllabus v1.1  
**Approval:** **DRAFT — NOT APPROVED — SQL examples not executed as part of authoring**  
**Unit/lesson ID status:** **PROVISIONAL** until checked against the frozen 53-unit master register  

> **Audience and distribution:** This is a **learner-facing** consolidated module. Instructor-only model answers are deliberately excluded to preserve the mandatory separation required by GOV-09 and SQL-12. The instructor key remains a separate file inside the previously created ZIP package. Assessment evidence is to be gathered from actual learner-run commands; expected results below are not claims of runtime verification.

## Contents

1. [Module specification](#part-i--module-specification)
2. [Unit U01.01](#part-ii--unit-u0101-relational-concepts-and-sql-categories)
3. [Unit U01.02](#part-ii--unit-u0102-postgresql-environment-and-repeatable-scripts)
4. [Five lesson plans](#part-iii--lesson-l010101-dbms-rdbms-relations-and-keys)
5. [Learner resource and glossary](#part-iv--learner-resource-and-glossary)
6. [Four runnable SQL scripts](#part-v--sql-laboratory-scripts)
7. [Assessment tasks](#part-vi--assessment-asm-0101-01)
8. [Traceability and QA log](#part-vii--qa-traceability-and-change-log)

---

## Part I — Module specification

_Source: `M01-Module-Guide.md`_

### M01 — Database Fundamentals and Development Environment

#### M-01 Identity and control

| Field | Value |
|---|---|
| Course | Professional SQL Programming & Enterprise Database Engineering — 2026 Edition |
| Module ID / title | `M01` — Database Fundamentals and Development Environment |
| Baseline syllabus | v1.1, 9 October 2026, Module 01 |
| Authoring standard | SQL-EDU-STD-001 v1.0, 9 October 2026 |
| Draft / last revision | v0.1 / 10 October 2026 |
| Status | **DRAFT — NOT APPROVED / SQL NOT EXECUTED** |
| Author | Course development team — name and signature pending |
| Technical / instructional / editorial reviewers | To be appointed; no signatures recorded |
| Database and clients | PostgreSQL **16.x**, `psql` **16.x**, pgAdmin **4 v9.x target**; record installed exact patch/build in learner evidence |
| Extensions | None |
| Qualification note | Internal instructional unit design only; **no NTVQF accreditation claim** |

#### M-02 Why this module matters

A backend developer debugging a customer-order problem must know whether a PostgreSQL *server*, a named *database*, a *schema* or a client connection is at fault. In an ERP or e-commerce application, a mistaken connection can damage production data; an unrepeatable setup script leaves teammates with different structures. This module establishes the common relational vocabulary and a disposable, reproducible environment for the remainder of the programme.

**Workplace case:** Your development team is prototyping an ERP customer directory. A `company` owns multiple `customer` records. Your task is to communicate the model, install/configure tools, create `erp_m01_lab`, load two fictional customers, and show that a second script run neither duplicates customers nor bypasses the company reference.

#### M-03 Entry requirements

- No previous course module; basic file/folder navigation and elementary command-line usage recommended.
- A laptop or authorized lab machine with installation privileges, appropriate disk space, local port availability and internet access only for acquiring official installers.
- Approved installation route: host-based PostgreSQL 16 or instructor-provided PostgreSQL 16 training VM/container. Client tools: matching `psql` 16 and pgAdmin 4 v9.x target.
- Learners must have a *disposable* training DB, not access to operational ERP data or shared production administrator credentials.
- Students without admin rights may use an instructor-provisioned DB with permission to create objects within their assigned lab environment.

#### M-04 Scope and exclusions

**Required:** DBMS versus RDBMS, client/server flow, database/schema/table/row/column, relation/attribute/tuple, candidate/primary/foreign keys and one-to-many relationships, standard SQL versus PostgreSQL implementation, statement families DDL/DML/DQL/DCL/TCL (pedagogical classifications, not universal formal partitions), PostgreSQL 16 setup, pgAdmin/psql connections, naming scripts, seed/verify/replay, local configuration and safe error diagnosis.

**Not taught in depth:** normalization and enterprise logical modeling (M03), complex SELECT and joins (M02), access policy/roles and tenant-isolation design (M12), `ON CONFLICT` mechanics and idempotent payments (M08), performance measurement (M10), cloud hardening, SSL certificates, remote production deployment or Docker orchestration. Their incidental appearance in training scripts is labeled preview, not a new learning outcome.

#### M-05 Measurable module outcomes and programme alignment

| MLO | Under supervised lab conditions, learner can… | Linked CLO | Acceptance evidence |
|---|---|---|---|
| `MLO-01.1` | Label DBMS/RDBMS and at least **six** relational/server components correctly in a miniature ERP model. | `CLO-01` | Annotated conceptual diagram and answers |
| `MLO-01.2` | Classify **8 of 10** SQL examples by teaching family and identify at least two portability caveats. | `CLO-01`, `CLO-02` | Classifier worksheet |
| `MLO-01.3` | Show PostgreSQL 16 service reachable, record exact tool versions and connect to the **same** `erp_m01_lab` database through `psql` and pgAdmin. | `CLO-01` | Connection proof and version/config record |
| `MLO-01.4` | Run and replay the provided schema/seed/verify scripts with **one company and two customers**, then record an expected FK failure without modifying valid rows. | `CLO-01`, `CLO-02` | SQL files, row-count evidence, failure note |

`CLO-01`: design maintainable relational structures; `CLO-02`: write/test SQL. These are **foundation contributions**, not a declaration that the learners master all CLO requirements in M01.

#### M-06 Hour ledger (frozen total)

| Unit (provisional IDs) | Theory | Practical | Guided total | Minutes |
|---|---:|---:|---:|---:|
| `U01.01` Relational Concepts and SQL Categories | 2 h | 1 h | 3 h | 180 |
| `U01.02` PostgreSQL Environment and Repeatable Scripts | 2 h | 3 h | 5 h | 300 |
| **MODULE TOTAL** | **4 h** | **4 h** | **8 h** | **480** |

#### M-07 Unit map and dependencies

| Sequence | Unit | Entry condition | Coverage | Outcomes |
|---|---|---|---|---|
| 1 | `U01.01` | Entry expectations | relational vocabulary, client/server, key relationships, SQL taxonomy and portability | `ULO-01.01.1–3` |
| 2 | `U01.02` | `U01.01`, local VM/host access | PG 16/psql/pgAdmin setup, connection, scripts, safe replay and failure documentation | `ULO-01.02.1–3` |

Lessons: `L01.01.01` (90m:60T/30P), `L01.01.02` (90m:60T/30P), `L01.02.01` (120m:60T/60P), `L01.02.02` (90m:30T/60P), `L01.02.03` (90m:30T/60P).

#### M-08 Delivery method

- **Explain:** introduce one enterprise idea at a time using the same fictitious company/customer example.
- **Demonstrate:** instructor shows expected SQL commands and interprets output; demonstration time is **theory**.
- **Guide:** students label objects, install/connect and execute scripts together (practical time).
- **Independently apply:** each student connects with both tools, replays fixtures, captures evidence and diagnoses one error.
- **Feedback:** use the PC observation checklist, low-stakes knowledge checks and individual remediation followed by reassessment.

A typical in-person 8-hour delivery may be split across two sessions of 4 guided hours; breaks are outside the ledger.

#### M-09 Learner resources and assets

- `resources/M01-Setup-and-Glossary.md`: client/server diagram, OS-neutral setup guidance, glossary, worksheet and diagnostic decision tree.
- `labs/01_schema.sql`: safe CREATE SCHEMA / CREATE TABLE in a named training schema.
- `labs/02_seed.sql`: fictional, re-runnable fixture inserts.
- `labs/03_verify.sql`: connection context, expected tables and row counts.
- `labs/04_negative_case.sql`: intentionally failing child-row insert; **run separately**, not as part of replay sequence.
- `assessments/ASM-01.01-01.md` and `assessments/ASM-01.02-01.md`.
- Instructor reference: `instructor/INSTRUCTOR-KEY-M01.md` (distribution restricted).
- Instructor-created materials (pending): accessible slide deck, large-print diagram and localized installation screenshots corresponding to the exact lab OS.

#### M-10 ERP practical case and expected sequence

1. Map `company` 1 — many `customer` relationships.
2. Record PostgreSQL service, DB name, schema name, user, host, port and client tool versions.
3. Create the disposable `erp_m01_lab` database; run `01_schema.sql`, `02_seed.sql`, `03_verify.sql` in sequence.
4. Connect through both `psql` and pgAdmin to **the same database**.
5. Repeat steps 3 (scripts only); report unchanged counts (1 company, 2 customers).
6. Execute the separate negative test using a nonexistent company ID and explain why the FK rejects it.
7. Package learner screenshots/logs, edited notes, worksheet and original scripts; never include passwords.

All SQL observations in this authored package are **expected (not executed)**, pending technical review.

#### M-11 Assessment blueprint

| Assessment | Type | Focus / outcome | Mark allocation | Pass threshold |
|---|---|---|---:|---|
| `ASM-01.01-01` | Short written diagram/classifier | `MLO-01.1`, `MLO-01.2` | 30 | **≥24/30** and key/relationship criterion met |
| `ASM-01.02-01` | Supervised practical and log report | `MLO-01.3`, `MLO-01.4` | 70 | **≥56/70** **and all critical gates passed** |
| **Total** | | | **100** | **≥80/100 and all critical gates** |

**Critical gates:** connect to `erp_m01_lab` via both clients; no live data used; final valid row counts 1/2 after replay; FK negative test is rejected; evidence includes the database name and actual observed results. A failed critical gate fails the module regardless of percentage. Resubmit failed PC evidence after corrective coaching.

#### M-12 Expected evidence bundle

`EVD-01.01-01`: annotated ERP relational diagram; `EVD-01.01-02`: ten-statement classification worksheet; `EVD-01.02-01`: local environment + version record; `EVD-01.02-02`: command/tool connection logs; `EVD-01.02-03`: schema/seed/verify output on first and second run; `EVD-01.02-04`: separate FK failure observation + recovery note. Learner submission folder should include a plain `evidence.md`, relevant sanitized output and classroom diagram.

#### M-13 Integrity, safety and inclusive practice

- Only connect to the training DB. Confirm `current_database()` before creating or writing objects.
- Learners must not paste passwords/tokens/screenshots containing secrets into evidence. Use locally-entered passwords and least privilege where feasible.
- Never run `DROP SCHEMA`, unrestricted `DELETE`, or shared-service configuration changes as routine learner tasks.
- Schema names are hardcoded to `m01_training` as a teaching boundary, **not** a substitute for true tenant isolation.
- The sample foreign key prevents nonexistent company links. Real systems need additional controls explored in later modules.
- Provide keyboard-accessible instructions and text equivalents for diagrams; use terminal/GUI alternatives and extra time for setup where needed.

#### M-14 Instructor preparation and contingencies

- Verify a clean PostgreSQL **16.x** installation and a compatible GUI client in advance; record exact output of `SELECT version();` and `psql --version` and the pgAdmin About dialog.
- Create disposable student databases or an approved per-learner environment. Ensure database naming conflicts are resolved without overwriting existing work.
- Check port 5432 (or locally configured nondefault port), service status, localhost connection and local auth policy; never weaken remote security to make a class demo work.
- Rehearse the entire lab: first run, replay, negative FK failure, and service/password troubleshooting. Attach actual logs to QA; **not done in this package**.
- Common misconceptions: pgAdmin is the server (it is a client); a schema is a database; a primary key automatically allows child rows; `psql` backslash commands run in GUI SQL editors (they generally do not).
- Students lacking install rights: provide instructor-managed disposable environment and focus assessment on connectivity, script execution and analysis, while recording any approved accommodation.

#### M-15 References and baseline

- PostgreSQL 16: [PostgreSQL 16 documentation](https://www.postgresql.org/docs/16/) — *tutorial*, *data definition*, *SQL syntax*, `psql`, and `CREATE DATABASE`.
- [PostgreSQL 16 tutorial: relational concepts](https://www.postgresql.org/docs/16/tutorial-concepts.html).
- [PostgreSQL 16: psql client](https://www.postgresql.org/docs/16/app-psql.html).
- [PostgreSQL 16: CREATE DATABASE](https://www.postgresql.org/docs/16/sql-createdatabase.html).
- pgAdmin 4: [Official documentation](https://www.pgadmin.org/docs/) (match installed release).
- ISO/IEC 9075 SQL standard is the normative family; detailed standard text is not reproduced. Database vendors vary in SQL support.
- Course syllabus v1.1 and internal standard v1.0 named in `README.md`.

#### M-16 QA and approvals

| Gate | Reviewer / evidence | Status |
|---|---|---|
| Technical (PG scripts, negative test, portability claims) | Name pending; execution log pending | **NOT REVIEWED** |
| Instructional (duration, mapping, teaching readiness) | Name pending | **NOT REVIEWED** |
| Editorial/accessibility (terminology, links, presentation) | Name pending | **NOT REVIEWED** |
| Curriculum lead (unit-ID register and scope) | Name pending; **master unit register not located** | **PENDING** |

See `qa/M01-Traceability-QA-and-Change-Log.md`. **Publication status: NOT APPROVED.**

#### M-17 Completion and release decision

A learner completes M01 when scheduled 480 guided minutes are delivered, the evidence bundle contains real output for all six EVD items, written assessment reaches 24/30, lab assessment reaches 56/70, the combined mark is ≥80/100, and all critical gates pass. **Publishing** this course package additionally requires source register ID reconciliation, actually executed PostgreSQL verification and three signed QA approvals.

##### Change log

| Date | Revision | Change | Authorization |
|---|---|---|---|
| 2026-10-10 | Draft 0.1 | First complete M01 package aligned to supplied syllabus; unit IDs **provisional** | Curriculum lead pending |

---

## Part II — Unit U01.01: Relational Concepts and SQL Categories

_Source: `units/U01.01-Relational-Concepts-and-SQL-Categories.md`_

### U01.01 — Relational Concepts and SQL Categories

#### U-01 Identity
**Module:** `M01` · **Unit ID:** `U01.01` (PROVISIONAL; reconcile with frozen unit register) · **Version:** 0.1 draft · **Date:** 2026-10-10 · **Author/reviewer:** course team / TBD · **Tools:** PostgreSQL 16.x reference model; no extension · **QA:** not reviewed.

#### U-02 Workplace purpose
An ERP engineering team needs an unambiguous way to communicate business entities, columns, rows, keys, server/database boundaries and SQL command purposes before scripts can be shared and reviewed.

#### U-03 Prerequisites
No prior module. Basic table/file familiarity. Use the conceptual worksheet in `resources/M01-Setup-and-Glossary.md`. PostgreSQL access is optional for this first unit (the instructor may demonstrate without a local install).

#### U-04 Measurable ULOs
| ULO | Observable performance | Module linkage |
|---|---|---|
| `ULO-01.01.1` | Correctly label at least six of seven DBMS, RDBMS, server, database, schema, table and row/column terms in a workplace diagram. | `MLO-01.1` |
| `ULO-01.01.2` | Correctly classify at least eight of ten example SQL statements and state two portability caveats. | `MLO-01.2` |
| `ULO-01.01.3` | Draw an ERP company→customer 1:N relation with a correctly chosen primary and foreign key. | `MLO-01.1` |

#### U-05 Elements of competency
| EC | Operational element | Scheduled learning |
|---|---|---|
| `EC-01.01.1` | Interpret the relational database environment and vocabulary | `L01.01.01` |
| `EC-01.01.2` | Represent data relationships and keys | `L01.01.01` |
| `EC-01.01.3` | Distinguish SQL statement families and portability | `L01.01.02` |

#### U-06 Performance criteria and evidence
| PC | Pass condition | EVD / link |
|---|---|---|
| `PC-01.01.1` | Diagram labels ≥6/7 environment/relational terms accurately; differentiates server and client. | `EVD-01.01-01`, `ULO-01.01.1` |
| `PC-01.01.2` | One-to-many drawing identifies PK `company.company_id` and FK `customer.company_id` pointing to it; no reverse arrow confusion. | `EVD-01.01-01`, `ULO-01.01.3` |
| `PC-01.01.3` | Worksheet classifies ≥8/10 statement examples correctly using the course's DDL/DML/DQL/DCL/TCL categories. | `EVD-01.01-02`, `ULO-01.01.2` |
| `PC-01.01.4` | Identifies two legitimate standard-vs-vendor caveats, e.g. `LIMIT`, `SERIAL`/identity style, or client-only `\dt`. | `EVD-01.01-02`, `ULO-01.01.2` |

#### U-07 Boundaries
Introductory relational terminology and conceptual key relationships only. No normalization exercise, detailed SQL writing, privilege implementation, transaction internals or DBMS deployment architecture.

#### U-08 Hour allocation
**180 minutes = 120 theory + 60 practical.** No breaks inside allocation.

#### U-09 Ordered lesson map
| Lesson | Subject | Theory | Practical | Total |
|---|---|---:|---:|---:|
| `L01.01.01` | DBMS, RDBMS, Relations and Keys | 60m | 30m | 90m |
| `L01.01.02` | SQL Statement Families, Standards and PostgreSQL | 60m | 30m | 90m |
| **Total** | | **120m** | **60m** | **180m** |

#### U-10 Core teaching explanation
A **database** is an organized collection of related data; a **DBMS** provides storage, retrieval and control. An **RDBMS** exposes data as relations with constraints and SQL access. In a typical PostgreSQL deployment, the **server instance** hosts one or more named databases; inside each database, **schemas** organize tables and other objects. A **table** is the SQL implementation of a relation; its **columns/attributes** describe data fields, and **rows/tuples** represent records. A **primary key** identifies one row uniquely, a **foreign key** enforces a reference to an eligible parent key, and **one-to-many** means one company can relate to several customers.

SQL means *Structured Query Language*. ISO/IEC 9075 defines a standard family; PostgreSQL follows much of it and has dialect-specific features. Teaching labels commonly group commands into **DDL** (schema definitions), **DML** (row mutation), **DQL** (read queries; a teaching category, usually `SELECT`), **DCL** (grants/revokes) and **TCL** (transaction boundaries). These groupings are useful but not uniformly codified SQL language partitions; `SELECT` may be discussed within SQL data manipulation in formal treatments. PostgreSQL `\dt` belongs to the **psql client**, not SQL.

**Misconceptions to correct:** client application = database server (false); every column is a candidate key (false); vendor-specific syntax is guaranteed portable (false); `CREATE DATABASE` can always be run inside a transaction block (false in PostgreSQL).

#### U-11 Annotated worked example
**EX-01.01.01-01 (conceptual):** `company(company_id PK, company_name)` and `customer(customer_id PK, company_id FK, customer_name)`. If company row 1 exists, customer row 101 can reference it; a child with company ID 999 (absent parent) is rejected by a genuine FK. Draw arrow from `customer.company_id` to `company.company_id`. **Expected, not executed.**

**EX-01.01.02-01 (classification):** `CREATE TABLE` → DDL; `INSERT` → DML; `SELECT` → DQL for this course; `GRANT` → DCL; `COMMIT` → TCL. These are examples of purpose, not the full grammar. `\dt` → psql metacommand, outside SQL.

#### U-12 Application
**Guided:** label a diagram of server → database → schema → table → row/column, then place `company` and `customer` in a 1:N relationship. **Independent:** classify ten SQL samples and note two portability limitations in `ASM-01.01-01`. No production database needed.

#### U-13 Assessment and remediation
Formative: instructor checks arrow direction and quizzes SQL families. Summative: `ASM-01.01-01`, 30 marks, pass ≥24 plus correct key/relationship criterion. If learners confuse client/server, revisit environment diagram; if classification <8/10, reclassify five new commands and reassess equivalent task.

#### U-14 Evidence guide
Submit `EVD-01.01-01` (diagram with 6/7 labels and keys), `EVD-01.01-02` (10 examples + two portability cautions), assessment cover record with actual assessed responses, not invented results.

#### U-15 Negative/error coverage
Observe proposed invalid FK relation (child `company_id=999` without parent) and explain expected rejection; demonstrate `\dt` as client-only, not server SQL. Do not pretend the conceptual negative case was executed.

#### U-16 Resources
`L01.01.01`, `L01.01.02`, `resources/M01-Setup-and-Glossary.md`, `assessments/ASM-01.01-01.md`; instructor answers in restricted `instructor/INSTRUCTOR-KEY-M01.md`. PostgreSQL 16 tutorial: https://www.postgresql.org/docs/16/tutorial-concepts.html .

#### U-17 Review status
**DRAFT:** hour arithmetic reviewed editorially in package; technical/instructional/editorial approval **pending**; provisional IDs not reconciled. Do not publish as accredited competency standard.

---

## Part II — Unit U01.02: PostgreSQL Environment and Repeatable Scripts

_Source: `units/U01.02-PostgreSQL-Environment-and-Repeatable-Scripts.md`_

### U01.02 — PostgreSQL Environment and Repeatable Scripts

#### U-01 Identity
**Module:** `M01` · **Unit:** `U01.02` (PROVISIONAL) · **Version:** 0.1 draft · **Date:** 2026-10-10 · **Author/reviewer:** course team / TBD · **Platform:** PostgreSQL 16.x + psql 16.x + pgAdmin 4 v9.x target · **Status:** DRAFT / SQL NOT EXECUTED.

#### U-02 Purpose
Given an imaginary ERP customer directory, students must provision an authorized local PostgreSQL environment, connect using two tools, and build an auditable set of SQL files that is safe to replay.

#### U-03 Prerequisites
`U01.01`; access to a disposable PostgreSQL 16 instance and one training DB `erp_m01_lab`; permission to create schema/tables; compatible psql and pgAdmin; OS terminal. A pre-provisioned training database is an allowed accommodation if learners cannot install software.

#### U-04 Measurable ULOs
| ULO | Expected proof | MLO |
|---|---|---|
| `ULO-01.02.1` | Record server/psql/pgAdmin versions and local connection parameters (no password), verify service and reach assigned DB. | `MLO-01.3` |
| `ULO-01.02.2` | Connect to identical `erp_m01_lab` from both psql and pgAdmin and show `current_database()` in each. | `MLO-01.3` |
| `ULO-01.02.3` | Execute schema/seed/verify SQL twice, observe 1 company/2 customers after each run, then document FK error without corrupting valid data. | `MLO-01.4` |

#### U-05 Elements of competency
| EC | Element | Lessons |
|---|---|---|
| `EC-01.02.1` | Install/provision PostgreSQL and its development clients safely | `L01.02.01` |
| `EC-01.02.2` | Establish and diagnose CLI and GUI connections | `L01.02.02` |
| `EC-01.02.3` | Organize, replay and verify SQL fixtures | `L01.02.03` |

#### U-06 Performance criteria
| PC | Objective pass condition | Evidence |
|---|---|---|
| `PC-01.02.1` | Actual `psql --version`, `SELECT version()` or `SHOW server_version`, pgAdmin About version, server status and sanitized host/port/user recorded. | `EVD-01.02-01` |
| `PC-01.02.2` | Both tools show successful query against `erp_m01_lab`; client-only commands are not pasted into SQL editor. | `EVD-01.02-02` |
| `PC-01.02.3` | Correct run order 01→02→03 twice; after *both* runs there are 1 company and 2 customers; scripts unchanged. | `EVD-01.02-03` |
| `PC-01.02.4` | Invalid `company_id=999` insert is rejected by FK; valid 1/2 row counts remain after failure; diagnosis distinguishes deliberate error from installation failure. | `EVD-01.02-04` |

#### U-07 Boundaries
Focus on local dev environment and first SQL files, not remote hosting, Docker orchestration, OS hardening, schema migration engines, advanced constraints, row-level tenant isolation or payment idempotency. Introductory `ON CONFLICT DO NOTHING` is a provided fixture technique, not assessed syntax mastery.

#### U-08 Hour allocation
**300 minutes = 120 theory + 180 practical.**

#### U-09 Lesson sequence
| Lesson | Title | Theory | Practical | Total |
|---|---|---:|---:|---:|
| `L01.02.01` | Install and Configure PostgreSQL and Clients | 60m | 60m | 120m |
| `L01.02.02` | Connect with psql and pgAdmin | 30m | 60m | 90m |
| `L01.02.03` | Create, Replay and Verify ERP Setup Scripts | 30m | 60m | 90m |
| **Total** | | **120m** | **180m** | **300m** |

#### U-10 Theory and system explanation
A PostgreSQL server **process** listens for client requests; TCP host/port determines network destination; database name chooses one database inside an instance; a role authenticates and determines permissions; a **schema** groups objects inside that database. `psql` is a command-line client and pgAdmin a graphical administration/query client. Neither is the server itself. `postgres` is often an administrative role: never place its password in scripts or evidence. Connection failures may be due to service down, wrong host/port, missing DB/role, password mismatch, or local authentication policy. Inspect one cause at a time and do not turn off authentication for convenience.

**Repeatability principle:** execution order and stable fixture keys matter. `CREATE TABLE IF NOT EXISTS` is only a beginner-safe rerun convenience; it does not repair an existing incompatible table structure. `ON CONFLICT ... DO NOTHING` avoids duplicate rows for the exact primary-key fixture; this is **not** an assertion of full business idempotency. Keep an isolated negative test separate because its intentional error can stop a batch in `psql -v ON_ERROR_STOP=1`.

#### U-11 Worked examples
**EX-01.02.01-01:** `psql --version` (shell), `SELECT current_database(), current_user;` (SQL), `SELECT version();` (SQL). Identify the difference between shell and SQL prompts. **Expected, not executed.**

**EX-01.02.02-01:** In a shell (using locally entered credentials): `psql -h localhost -p 5432 -U postgres -d erp_m01_lab`; inside psql run `SELECT current_database();` then `\conninfo`. In pgAdmin connect to the **same** host/port/db and run the SQL query. Actual user may be a provisioned training role rather than `postgres`.

**EX-01.02.03-01:** `labs/01_schema.sql`, `labs/02_seed.sql`, `labs/03_verify.sql`. Read code comments, execute in order, then replay. Expected unchanged results: company count **1**, customer count **2**. Do not claim observed success until logs exist.

#### U-12 Guided and independent labs
**Guided (`LAB-01.02.01-01`):** follow `resources/M01-Setup-and-Glossary.md` to provision DB and confirm connection in both tools. **Guided (`LAB-01.02.03-01`):** run scripts with instructor and compare count queries. **Independent (`LAB-01.02.03-02`):** repeat scripts without editing, record evidence, intentionally execute `04_negative_case.sql` separately, and propose a safe recovery path.

#### U-13 Assessment/remediation
`ASM-01.02-01`, 70 marks. Passing requires ≥56/70 **plus** all four critical criteria (both tools, correct DB, stable replay 1/2 and FK rejection with no data corruption). For wrong database, stop and redo connection identity; for `relation does not exist`, replay script 01 then inspect schema; for duplicate rows, compare fixture keys and `ON CONFLICT` handling; reassess with instructor-observed rerun.

#### U-14 Evidence
`EVD-01.02-01`: environment table and versions; `EVD-01.02-02`: two sanitized connection proofs; `EVD-01.02-03`: captured output of first and second runs with row counts; `EVD-01.02-04`: separate FK error and subsequent unchanged counts. Include actual time, OS, commands, exit status and sanitizer checklist. Never include passwords.

#### U-15 Expected failures / safety
- Service refused: verify running service, host/port, not firewall removal or weakening security.
- Authentication error: confirm correct role and lab-specific password *privately*; instructor resets role locally if needed.
- Database missing: create *only* `erp_m01_lab` or use preprovisioned database.
- Intentional FK rejection: error **expected** for `04_negative_case.sql`; first three files must complete cleanly.
- No destructive resets in learner execution sequence. Instructor-only optional cleanup guarded by DB identity.

#### U-16 Assets/references
Three learner lessons, 4 SQL files, resource setup guide, lab assessment, instructor-only key; PostgreSQL 16 reference: https://www.postgresql.org/docs/16/app-psql.html and https://www.postgresql.org/docs/16/sql-createdatabase.html; pgAdmin documentation https://www.pgadmin.org/docs/ .

#### U-17 QA status
All code output is **EXPECTED — NOT EXECUTED**. No install/SQL logs or reviewer approvals yet. Unit identifier is provisional; release blocked pending master register and validation.

---

## Part III — Lesson L01.01.01: DBMS, RDBMS, Relations and Keys

_Source: `lessons/L01.01.01-DBMS-RDBMS-Relations-and-Keys.md`_

### L01.01.01 — DBMS, RDBMS, Relations and Keys

#### L-01 Identity
**Unit:** `U01.01` (provisional) · **Version:** 0.1 (2026-10-10) · **Author:** course team, reviewer TBD · **Status:** DRAFT / NOT QA APPROVED · **Tool baseline:** PostgreSQL 16.x conceptual reference.

#### L-02 Duration
**90 minutes = 60 minutes theory + 30 minutes practical.** Instructor demonstration counts toward theory; guided/independent student performance counts practical.

#### L-03 Prerequisites
Basic knowledge of a spreadsheet/table and folder structure. Printed/tactile or accessible copy of the enterprise data diagram; no database installation required.

#### L-04 Lesson outcomes and traceability
| LLO | Observable outcome | ULO / PC |
|---|---|---|
| `LLO-01.01.01.1` | Distinguish client, DBMS/RDBMS, PostgreSQL server, database, schema, table, column and row on a correctly labeled diagram (≥6/7 check items). | `ULO-01.01.1` / `PC-01.01.1` |
| `LLO-01.01.01.2` | Draw a company/customer relationship and label the parent PK and child FK correctly. | `ULO-01.01.3` / `PC-01.01.2` |

#### L-05 Essential concepts
A **DBMS** is software managing data storage and access. A **relational DBMS** organizes logical data into relations and enforces declared constraints. **PostgreSQL** is an RDBMS. A PostgreSQL **server instance** can contain several **databases**; each DB can have multiple **schemas**; schemas can contain **tables**. A **relation** is described by attributes (columns) and populated by tuples (rows). An **entity** refers to a modeled business subject, such as Company or Customer. A **primary key** (PK) uniquely identifies a row; a **foreign key** (FK) references eligible rows in a parent relation. Cardinality describes how many related rows are allowed. One-to-many (`1:N`) means one company may have several customers while each sample customer belongs to one company.

#### L-06 Timed instructional sequence
| Activity | Type | Minutes |
|---|---|---:|
| Open with incorrect-customer-company ERP support ticket | Theory | 10 |
| Explain DBMS/RDBMS, server/client, database/schema/table | Theory | 30 |
| Explain PK/FK and demonstrate a 1:N example | Theory | 20 |
| Guided annotate architecture and relation drawing | Practical | 15 |
| Independent 6/7-label check and key diagram | Practical | 10 |
| Exit check and formative feedback | Practical | 5 |
| **Total** | **60T / 30P** | **90** |

#### L-07 Learner-ready explanation
Imagine a back-office ERP company has 200 customers. A spreadsheet could store customer names, but does not automatically prevent an order pointing to a missing customer. An RDBMS lets developers model customers as rows and define integrity rules for references. The desktop interface **pgAdmin is not the server**; it sends requests to PostgreSQL. Likewise, `psql` is a command-line client. A request travels from a client to a running PostgreSQL server, which selects a database, uses SQL to locate schema objects, evaluates constraints, and returns data or an error.

Within a selected database, schemas such as `public` or the class schema `m01_training` are **namespaces**, not independent databases. A table belongs to one schema inside one database. A primary key cannot be null and must be unique; the sample child foreign key points to `company.company_id`. One company can have many customer rows; one customer in *this simplified design* has one `company_id` value. Do not assume this design already implements secure multi-tenant isolation.

#### L-08 Worked example (`EX-01.01.01-01`)

```text
client (psql or pgAdmin)
       | sends SQL over a database connection
       v
PostgreSQL server instance
       └── database: erp_m01_lab
            └── schema: m01_training
                 ├── company(company_id PK, company_name)
                 └── customer(customer_id PK, company_id FK → company.company_id,
                              customer_name, customer_email)
```

**Interpretation:** In fictional training data, `company_id=1` represents 'Demo Trading Ltd'; customers 101 and 102 can both refer to company 1. A customer referencing nonexistent company 999 should fail when a real FK exists. **This is expected behavior, not evidence of execution.**

#### L-09 Learner practice
**Guided 15m:** annotate a printed diagram, underline every key and draw the FK direction. Check with a peer which items represent a client, a server, a database and a table. **Independent 10m:** write three sentences distinguishing database from schema, classify the one-to-many relation, and add PK/FK labels to the diagram without notes.

#### L-10 Checks for learning
1. Does pgAdmin store PostgreSQL database files? Explain in one sentence.
2. Can `erp_m01_lab` contain schemas besides `m01_training`?
3. Can a real foreign key permit a customer pointing to no company, assuming the column is non-null?
4. Can the same company have customer rows 101 and 102 in a 1:N model?

#### L-11 Acceptance criteria
Instructor observes `PC-01.01.1` (≥6/7 labels, client and server not swapped) and `PC-01.01.2` (company PK, customer FK arrow correct). Submit `EVD-01.01-01` with the diagram and three explanatory sentences. Both lesson LLOs must have checked evidence.

#### L-12 Expected results (NOT EXECUTED)
A correctly marked schema diagram has server → database → schema → two tables; `customer.company_id` points to `company.company_id`, and two different customer IDs may refer to company 1. This lesson does not assert actual query results.

#### L-13 Common mistakes and corrections
- **Mistake:** “pgAdmin is PostgreSQL.” **Correction:** pgAdmin is a GUI client, PostgreSQL server is the DBMS.
- **Mistake:** “Schemas and databases are identical.” **Correction:** schemas are namespaces **within** a database.
- **Mistake:** putting the FK on the `company` table for the one-to-many example. **Correction:** dependent customers carry the reference.

#### L-14 Troubleshooting and safety
If the diagram is confusing, first draw only client→server, then database→schema→table. Avoid real company/customer names in submissions. Do not launch destructive SQL or connect to live servers for this conceptual activity.

#### L-15 Differentiation
**Support hint:** Mark 'one' above company and 'many' above customer before adding keys. **Extension:** discuss how an `order` entity might relate to customers, but defer physical schema complexity to M03.

#### L-16 Materials
Handout: `resources/M01-Setup-and-Glossary.md` (diagram and glossary); whiteboard or digital diagram editor; worksheet `ASM-01.01-01`; instructor-only rubric `instructor/INSTRUCTOR-KEY-M01.md`.

#### L-17 References
[PostgreSQL 16 tutorial](https://www.postgresql.org/docs/16/tutorial-concepts.html), and SQL-EDU-STD-001 v1.0 sections 3, 7, 9.

#### L-18 Wrap-up
Relational systems separate business data, its structure, and software clients. Keep `EVD-01.01-01` in the learner evidence folder; proceed to `L01.01.02` to classify SQL instructions used to work with those objects. **QA and observed outcome:** pending classroom delivery.

---

## Part III — Lesson L01.01.02: SQL Statement Families and Portability

_Source: `lessons/L01.01.02-SQL-Statement-Families-and-Portability.md`_

### L01.01.02 — SQL Statement Families, Standards and PostgreSQL

#### L-01 Identity
**Unit:** `U01.01` (provisional) · **Version:** 0.1 · **Revised:** 2026-10-10 · **Author/reviewer:** team / TBD · **Status:** DRAFT. **Platform context:** SQL standard family, PostgreSQL 16.x and `psql` 16.x.

#### L-02 Duration
**90 minutes = 60 theory + 30 practical.**

#### L-03 Prerequisites
`L01.01.01`, diagram with table/column/row terminology; text editor or learner worksheet.

#### L-04 Outcomes and PC linkage
| LLO | Observable result | ULO / PC |
|---|---|---|
| `LLO-01.01.02.1` | Classify ≥8/10 supplied statements by teaching family (DDL/DML/DQL/DCL/TCL). | `ULO-01.01.2` / `PC-01.01.3` |
| `LLO-01.01.02.2` | Name ≥2 features/commands that cannot be assumed portable unchanged across DBMSs. | `ULO-01.01.2` / `PC-01.01.4` |

#### L-05 Essential terms
SQL is the main declarative language for relational database structures and queries; ISO/IEC 9075 is the standards family. Common **teaching classifications**: DDL = define objects (`CREATE`, `ALTER`, `DROP`), DML = change rows (`INSERT`, `UPDATE`, `DELETE`), DQL = read query (`SELECT`), DCL = authority statements (`GRANT`, `REVOKE`), TCL = transactions (`BEGIN`, `COMMIT`, `ROLLBACK`). These categories overlap in formal literature; `SELECT` may be included in broad DML, and `BEGIN` syntax varies by implementation. A **dialect** is a DBMS-specific feature, syntax or behavior. A **psql metacommand** begins with `\` and is interpreted by the client rather than SQL parser.

#### L-06 Lesson flow
| Stage | Type | Minutes |
|---|---|---:|
| Opening: why Oracle SQL may differ from PostgreSQL SQL | Theory | 5 |
| Explain SQL language, 5 teaching groups and caveats | Theory | 35 |
| Annotated worked examples and portable/nonportable cases | Theory | 20 |
| Guided classroom classification of six examples | Practical | 15 |
| Independent 10-statement quiz and two caveats | Practical | 10 |
| Exit review and immediate corrective feedback | Practical | 5 |
| **Total** | **60T/30P** | **90** |

#### L-07 Core explanation
SQL emphasizes **what data or structure** is required, leaving execution choices to the DBMS. `CREATE TABLE` describes structure; `INSERT` contributes rows; `SELECT` reads rows; `GRANT` affects permissions; `ROLLBACK` ends an unfinished transaction with a reversal of its changes. The category of a command is a learning aid, not a guarantee that all DBMSs expose precisely identical grammar, transaction behavior or category definitions. SQL vendors implement subsets and extensions: PostgreSQL accepts `LIMIT`, while standards-oriented fetch syntax includes `FETCH FIRST`; identity syntax, data types and administrative commands vary. `\dt` is especially important: it works in `psql` but is **not an SQL statement** for pgAdmin's Query Tool.

Some commands are safe to discuss conceptually but unsafe to execute casually. `DROP TABLE` is DDL but destructive; `DELETE` without `WHERE` can remove all rows. `GRANT` needs appropriate privilege. In M01, merely **classify** these, do not apply them to a shared environment.

#### L-08 Annotated worked example (`EX-01.01.02-01`)

```sql
-- DDL: describe a table structure (example only; not required to execute now)
CREATE TABLE demo_note(note_id INTEGER PRIMARY KEY, body TEXT NOT NULL);

-- DML: add a row
INSERT INTO demo_note(note_id, body) VALUES (1, 'Training only');

-- DQL: request stored data
SELECT note_id, body FROM demo_note;

-- DCL: authority (classification only; do not execute without policy)
-- GRANT SELECT ON demo_note TO some_training_role;

-- TCL: transaction boundary examples (not run in this lesson)
-- BEGIN;
-- ROLLBACK;
```

**Expected, not executed:** after the first three commands on a clean disposable table, a query could return the one training row. The privilege/transaction examples are commented out and are for identification only. Script is illustrative and intentionally not part of the reproducible setup set.

#### L-09 Practice
**Guided:** classify `CREATE TABLE`, `INSERT`, `SELECT`, `GRANT`, `COMMIT`, `ALTER TABLE` in pairs, justify each label. **Independent:** complete `ASM-01.01-01` classification of ten SQL statements and write two examples of implementation/client-specific syntax. Do not assume all statements should be executed.

#### L-10 Checks
What family contains `DELETE`? Why should `\dt` never be pasted as ordinary SQL into the Query Tool? Does classifying a command as TCL show whether it changes data? Why should a portability note name a concrete vendor-dependent construct?

#### L-11 Acceptance conditions
`PC-01.01.3` ≥8/10 classification examples correctly identified; `PC-01.01.4` ≥2 accurate portability cautions. Keep scored response as `EVD-01.01-02`. Instructor checks correctness, not just completion.

#### L-12 Expected results (NOT EXECUTED)
Example `SELECT` above would show a single demo row **only if** DDL+INSERT ran successfully in a disposable database. In the assessment, correct categories are checked against an instructor-only key; no database execution is required.

#### L-13 Common mistakes
- **Mistake:** `SELECT` is universally a separate formal DQL language standard. **Correction:** DQL is a teaching category; classifications vary.
- **Mistake:** `\dt` is standard SQL. **Correction:** psql processes metacommands locally.
- **Mistake:** every DBMS supports PostgreSQL's `LIMIT` exactly. **Correction:** portable alternatives and vendor differences must be considered.

#### L-14 Troubleshooting/safety
If learners try running commented `GRANT` or `DROP`, redirect them to the paper classifier. Do not provide general admin roles or live database endpoints. Teach caution about executing a statement simply because one can name its SQL category.

#### L-15 Support and extension
**Support:** identify the statement's principal intent (define, modify, read, authorize, transact). **Extension:** compare SQL standard `FETCH FIRST n ROWS ONLY` with PostgreSQL `LIMIT n` at a conceptual level.

#### L-16 Materials
Assessment worksheet `assessments/ASM-01.01-01.md`; glossary; training-only DDL example above; restricted answer key.

#### L-17 References
[PostgreSQL 16 SQL commands](https://www.postgresql.org/docs/16/sql-commands.html), [PostgreSQL 16 psql](https://www.postgresql.org/docs/16/app-psql.html), ISO/IEC 9075 family overview as discussed in the course syllabus.

#### L-18 Wrap-up
File completed classifications as `EVD-01.01-02`. The next dependency is `L01.02.01`: install the engine and client tools used to run SQL. **QA/actual classroom results: pending.**

---

## Part III — Lesson L01.02.01: Install and Configure PostgreSQL and Clients

_Source: `lessons/L01.02.01-Install-and-Configure-PostgreSQL-and-Clients.md`_

### L01.02.01 — Install and Configure PostgreSQL and Clients

#### L-01 Identity
**Unit:** `U01.02` (provisional) · **Revision:** 0.1 / 2026-10-10 · **Author/reviewer:** team / TBD · **Status:** DRAFT / environment exercise not executed. **Target:** PostgreSQL 16.x, psql 16.x, pgAdmin 4 v9.x.

#### L-02 Time
**120 minutes = 60 theory + 60 practical.**

#### L-03 Prerequisites
`U01.01`; local installation permission **or** authorized classroom VM/service; enough machine resources; installer from vendor's official site; personal disposable database workspace and a safe way to store locally entered secrets.

#### L-04 Outcomes and mappings
| LLO | Success target | ULO/PC |
|---|---|---|
| `LLO-01.02.01.1` | Document chosen PostgreSQL 16 install/provision method, service state, host, port, `psql` version and pgAdmin version with sensitive values removed. | `ULO-01.02.1` / `PC-01.02.1` |
| `LLO-01.02.01.2` | Reach a local PostgreSQL endpoint and demonstrate that the intended disposable training database exists. | `ULO-01.02.1` / `PC-01.02.1` |

#### L-05 Concepts
A PostgreSQL installer provides a **server** (the database engine) and can provide the **psql client**. pgAdmin is a separate GUI client. A server may listen on port `5432` by default, but the real value comes from the classroom configuration. A role's authentication controls a connection and its privileges. An OS service/process state is distinct from SQL ability or privilege. **Do not expose the server publicly** or weaken `pg_hba.conf` / firewalls just to pass a beginner lab.

#### L-06 Timed lesson sequence
| Phase | Type | Minutes |
|---|---|---:|
| Opening: ticket “could not connect to database” | Theory | 10 |
| Client/server, endpoint and local service explanation | Theory | 20 |
| Instructor-directed installation method and security plan | Theory | 20 |
| Teacher shows expected version/service checks | Theory | 10 |
| Guided install or access instructor-provisioned instance | Practical | 35 |
| Independent capture of version and database name | Practical | 15 |
| Exit observation and fault analysis | Practical | 10 |
| **Total** | **60T/60P** | **120** |

#### L-07 Step-by-step explanation
1. Select your sanctioned route: Windows/macOS official installer, Linux packages from trusted distribution or PGDG repository, or an instructor-provisioned training environment. Use **PostgreSQL 16** rather than automatically installing an arbitrary newer major release.
2. During installation, choose local-only development settings; note the port and administrative role. Create a local password and store it outside source files and screenshots.
3. Verify the PostgreSQL server is running through your OS's services command/manager or classroom admin dashboard. Never presume a GUI launches the server.
4. Open an OS terminal. Verify client executable with `psql --version`. If it is not in `PATH`, locate the installed binaries rather than changing security settings.
5. Verify connectivity to the **local** PostgreSQL server with a permitted role. Use an instructor-provisioned role if the `postgres` account is restricted.
6. The database name for the rest of M01 is `erp_m01_lab`. Create it **only if it does not exist and you are authorized**. PostgreSQL `CREATE DATABASE` is a one-time action, not part of the replay scripts and cannot be executed inside a transaction block.
7. Install/open pgAdmin 4. Check the About dialog for the actual client version and set up an entry pointing to the intended **local** host/port/role. Do not put credentials in submitted notes.

#### L-08 Worked example (`EX-01.02.01-01`)
Run at OS terminal (not pgAdmin SQL editor):

```bash
psql --version
# First check that erp_m01_lab is absent or pre-provisioned.
# On an authorized clean local PostgreSQL instance only:
createdb -h localhost -p 5432 -U postgres erp_m01_lab
# Omit createdb if instructor already prepared the DB.
psql -h localhost -p 5432 -U postgres -d erp_m01_lab
```

Inside interactive psql (different prompt):

```sql
SELECT current_database(), current_user;
SHOW server_version;
```

**Expected, not executed:** client reports `psql (PostgreSQL) 16.x` (exact patch varies); `current_database()` reads `erp_m01_lab`; `SHOW server_version` returns 16.x. `createdb` fails if the database already exists—that is a **provisioning** conflict, not a cue to drop it. pgAdmin is versioned separately and may differ from the example target if instructor-approved.

#### L-09 Practice
**Guided 35m (`LAB-01.02.01-01`):** install/provision, verify service, check endpoint locally, create/choose `erp_m01_lab`, record versions. **Independent 15m:** complete an evidence table with OS, server version, psql version, pgAdmin version, DB name, host and port; omit passwords and hostnames not needed in a local demo.

#### L-10 Checks for learning
Where does `createdb` run: psql, terminal, or SQL editor? Is `5432` guaranteed for every installation? Why should install credentials not appear in `evidence.md`? How do you distinguish service down from missing database?

#### L-11 Acceptance criteria
`PC-01.02.1` is met only if actual observed versions, local endpoint, service state and exact training DB identity appear in `EVD-01.02-01`. Screenshots may support evidence but are not a substitute for readable recorded results.

#### L-12 Expected outcome (NOT EXECUTED)
With a running PostgreSQL 16 local instance, correct role authentication and a training database, opening psql succeeds and identity queries show the intended DB and server version. No installation or service check was run as part of preparing this lesson text.

#### L-13 Common mistakes
- **Mistake:** installs pgAdmin only, assumes PostgreSQL server exists. **Fix:** install/provision server separately.
- **Mistake:** pastes `createdb` into SQL editor. **Fix:** `createdb` is a shell application; SQL alternative is `CREATE DATABASE` in a suitable standalone SQL session.
- **Mistake:** edits firewall settings or stores plaintext passwords to make a connection. **Fix:** use authorized local setup and private credential entry.

#### L-14 Troubleshooting/safety
`psql: command not found`: fix PATH/client installation. `connection refused`: verify service and local port before attempting auth changes. `role does not exist`/`database does not exist`: verify chosen role/DB with instructor. Windows may require full executable path; Linux may use service/cluster commands and local authentication policies. Do not uninstall/overwrite a preexisting PostgreSQL server as part of learner remediation.

#### L-15 Differentiation
**Support:** use a preconfigured VM/teacher-provided database if installation rights are absent, still record connection evidence. **Extension:** explain why using a dedicated restricted training role is safer than reusing a database superuser.

#### L-16 Materials
`resources/M01-Setup-and-Glossary.md`; official installer instructions for OS; isolated machine; learner evidence template; instructor provision plan. No production data.

#### L-17 References
[PostgreSQL official downloads](https://www.postgresql.org/download/), [PostgreSQL 16 app-psql](https://www.postgresql.org/docs/16/app-psql.html), [CREATE DATABASE](https://www.postgresql.org/docs/16/sql-createdatabase.html), [pgAdmin docs](https://www.pgadmin.org/docs/).

#### L-18 Wrap-up
Capture `EVD-01.02-01`. `L01.02.02` assumes `erp_m01_lab` and clients are ready. If service cannot be installed, use the approved preprovisioned environment without compromising safety. **QA sign-off pending.**

---

## Part III — Lesson L01.02.02: Connect with psql and pgAdmin

_Source: `lessons/L01.02.02-Connect-with-psql-and-pgAdmin.md`_

### L01.02.02 — Connect with psql and pgAdmin

#### L-01 Identity
**Unit:** `U01.02` (provisional) · **Version/date:** 0.1 / 2026-10-10 · **Author/reviewer:** team / TBD · **Status:** DRAFT / SQL not executed · **Environment:** PostgreSQL 16.x, psql 16.x, pgAdmin 4 v9.x target.

#### L-02 Time
**90 minutes = 30 theory + 60 practical.**

#### L-03 Prerequisites
`L01.02.01` completed; running local PostgreSQL server, accessible `erp_m01_lab`, role/credentials held privately, both installed clients.

#### L-04 Outcomes and traceability
| LLO | Demonstration | ULO / PC |
|---|---|---|
| `LLO-01.02.02.1` | Execute an identity query via terminal psql and via pgAdmin, each showing `erp_m01_lab`. | `ULO-01.02.2` / `PC-01.02.2` |
| `LLO-01.02.02.2` | Diagnose a deliberately mismatched database name or port from the connection parameters without removing safeguards. | `ULO-01.02.1` / `PC-01.02.1` |

#### L-05 Concepts
A connection requires server host, port, database, user and authentication method. `psql -h ... -p ... -U ... -d ...` supplies parameters from a terminal. pgAdmin uses a saved server connection entry and its Query Tool executes **SQL**; the selected database of the Query Tool must be checked. `\conninfo` and `\dt` are psql metacommands. `SELECT current_database(), current_user;` is genuine SQL and runs in both interfaces. A CLI and GUI can connect to *different* databases on the same server, so opening both clients alone proves nothing.

#### L-06 Teaching timeline
| Step | Type | Minutes |
|---|---|---:|
| Set goal: verify same database via two client types | Theory | 5 |
| Explain connection tuple and client-only commands | Theory | 15 |
| Instructor demonstrates psql and pgAdmin query | Theory | 10 |
| Guided connection with psql then Query Tool | Practical | 30 |
| Independent verify context and compare evidence | Practical | 15 |
| Safe troubleshooting drills with incorrect DB name | Practical | 10 |
| Exit observation + feedback | Practical | 5 |
| **Total** | **30T/60P** | **90** |

#### L-07 Core explanation
First confirm the instance is running, then connect through one client and record a server/database identity query. **Explicit `-d erp_m01_lab`** prevents connecting accidentally to a database with the same name as the username. In pgAdmin, choose Register Server, input the local host and port, choose the database (maintenance DB or per-registration setting depends on pgAdmin version), then open the `erp_m01_lab` database's Query Tool. Do not assume a maintenance DB equals your training DB. Compare `current_database()` and `current_user` results across both clients. A mismatch must be fixed before writing any schema objects.

#### L-08 Worked example (`EX-01.02.02-01`)
Terminal:

```bash
psql -h localhost -p 5432 -U postgres -d erp_m01_lab
```

Interactive psql:

```sql
SELECT current_database() AS database_name,
       current_user AS connected_role;
SELECT version();
```

Client-only instruction *in psql, not pgAdmin*:

```text
\conninfo
```

In pgAdmin Query Tool for `erp_m01_lab`, run the **same SQL SELECT** statements. **Expected, not executed:** both `database_name` fields are `erp_m01_lab`; connected roles may be different if authorized credentials differ, and that does not invalidate DB identity. `\conninfo` typed as SQL in pgAdmin should be rejected as invalid syntax or handled as unsupported client command; do not include that mistake in production scripts.

#### L-09 Lab instructions
**Guided (`LAB-01.02.02-01`, 30m):** connect through both clients, run identity SQL and capture a text transcript or readable sanitized screenshots. **Independent (15m):** record a table: client, host (localhost), port, database, role, result and observation date. **Diagnosis (10m):** switch to an intentionally wrong nonexistent DB name in a disposable connection profile, note the error, then revert; never change real server security policy.

#### L-10 Knowledge checks
What happens when `-d` is omitted? Why does the connected user not have to equal `postgres`? Why do SQL statements run in pgAdmin but `\conninfo` does not? What must be checked before executing a write script?

#### L-11 Acceptance criteria
Both client observations provide unambiguous `current_database()='erp_m01_lab'` in `EVD-01.02-02`; learner identifies the wrong-database failure without editing firewall or authentication. Evidence is sanitized.

#### L-12 Expected results (NOT EXECUTED)
A successful connection displays a 1-row result for the context query. Wrong database may produce `FATAL: database "..." does not exist`; exact message depends on setup. Do not insert fake screenshot data or claim this was observed.

#### L-13 Common errors
- **Wrong DB selected in GUI:** a server registration is not necessarily the intended Query Tool database; run identity query.
- **psql metacommand copied into Query Tool:** use actual `SELECT` for portable connection proof.
- **Mixing OS terminal and psql prompt:** recognize `$`/`>` versus `dbname=>` prompts before typing commands.

#### L-14 Troubleshooting and safety
For auth errors inspect role/DB, not arbitrary wide `pg_hba.conf` changes; for `connection refused` inspect service/host/port. Always visually reconfirm `erp_m01_lab` before the next lesson. Do not store raw password in terminal transcript.

#### L-15 Support/extension
**Support:** instructor provides a sanitized connection-parameter checklist. **Extension:** explain why `current_database()` is necessary even when the same server port appears in both clients.

#### L-16 Materials
Terminal and pgAdmin connection sheet, `resources/M01-Setup-and-Glossary.md`, student logs in `EVD-01.02-02`, instructor-only assessor notes.

#### L-17 References
https://www.postgresql.org/docs/16/app-psql.html ; https://www.pgadmin.org/docs/ .

#### L-18 Wrap-up
Keep CLI and GUI connection proofs. `L01.02.03` reuses the confirmed database for repeatable scripts. **Actual technical verification pending.**

---

## Part III — Lesson L01.02.03: Create, Replay and Verify ERP Setup Scripts

_Source: `lessons/L01.02.03-Create-Replay-and-Verify-ERP-Scripts.md`_

### L01.02.03 — Create, Replay and Verify ERP Setup Scripts

#### L-01 Identity
**Unit:** `U01.02` (provisional) · **Version/date:** 0.1 / 2026-10-10 · **Author/reviewer:** team / TBD · **Status:** DRAFT — example SQL NOT EXECUTED · **DB:** PostgreSQL 16.x.

#### L-02 Duration
**90 minutes = 30 theory + 60 practical.**

#### L-03 Prerequisites
`L01.02.02`, connection to local disposable `erp_m01_lab` via psql and pgAdmin, training-role permission to create schema/tables and insert records; learner access to the four script files. Verify current DB **first**.

#### L-04 Measurable outcomes
| LLO | Assessment | ULO / PC |
|---|---|---|
| `LLO-01.02.03.1` | Run scripts 01→02→03 twice and demonstrate stable result count (company 1, customer 2). | `ULO-01.02.3` / `PC-01.02.3` |
| `LLO-01.02.03.2` | Run intentionally invalid FK child insert in an independent test, record rejection and confirm valid counts unchanged. | `ULO-01.02.3` / `PC-01.02.4` |

#### L-05 Core concepts
A **setup script** stores SQL so developers can review and replay it. We separate **structure** (`01_schema.sql`), **sample data** (`02_seed.sql`), **verification** (`03_verify.sql`) and an **intentional failure** (`04_negative_case.sql`). SQL DDL builds schema objects; constraints define allowable states; SQL insert creates sample rows. `IF NOT EXISTS` helps with a fresh repeated setup but does **not** compare existing columns with desired design; do not use it instead of formal migrations. `ON CONFLICT DO NOTHING` avoids an identical fixture primary-key insert failure, but its detailed concurrency semantics are assessed in M08, not here.

#### L-06 Timed flow
| Sequence | Type | Minutes |
|---|---|---:|
| Open: why two developers need deterministic setup | Theory | 5 |
| Explain script boundaries, constraint and replay caveats | Theory | 15 |
| Demonstrate execution order and how to read counts | Theory | 10 |
| Guided `01_schema`, `02_seed`, `03_verify` run | Practical | 25 |
| Independent unchanged replay and evidence capture | Practical | 20 |
| Separate FK negative test, repair/recheck | Practical | 10 |
| Exit presentation and feedback | Practical | 5 |
| **Total** | **30T/60P** | **90** |

#### L-07 Explanation of script sequence
1. **Safety identity check:** `SELECT current_database();` should return `erp_m01_lab`; do nothing if it does not.
2. **Schema file:** create schema `m01_training`, parent `company` and child `customer` with PK/FK and uniqueness constraints. `CREATE TABLE IF NOT EXISTS` protects a beginner rerun only for the expected unchanged structure.
3. **Seed file:** insert one fictional company and two fictional customers using fixed IDs, with `ON CONFLICT (id) DO NOTHING` for the training fixture. Actual sample identities are invented and do not represent customers.
4. **Verification file:** show selected DB, expected table list and simple independent counts; expect company **1** and customer **2** on an initially clean fixture.
5. **Replay steps 2–4 unchanged:** expect the same counts, not 2 and 4. If other rows already existed, the result may differ; use a **fresh** assigned database instead of deleting someone else's work.
6. **Separate negative test:** a new customer with `company_id=999` should fail the FK check. Run this file **outside** the normal replay sequence, note its nonzero error outcome, and run verification again to show valid records remain.

#### L-08 Worked example (`EX-01.02.03-01`)

```bash
# shell in directory containing SQL scripts; credentials entered privately
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 01_schema.sql
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 02_seed.sql
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 03_verify.sql
# Rerun those three files in the SAME order without changes.
# Negative test alone (a nonzero exit status is EXPECTED):
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 04_negative_case.sql
# Finally rerun 03_verify.sql and inspect unchanged counts.
```

Do not paste the terminal `psql -f` commands into a SQL editor; use pgAdmin's Query Tool to open and execute **contents** of files 01/02/03 if using GUI. In `psql`, `-v ON_ERROR_STOP=1` exits on a real SQL error so that a training report can distinguish success from failure. For the standalone negative test, an FK failure is **expected**, not a successful normal script run.

**Expected (NOT EXECUTED):** `SELECT COUNT(*) FROM m01_training.company;` → 1 and `SELECT COUNT(*) FROM m01_training.customer;` → 2 after first and second run; `04_negative_case.sql` returns a foreign key violation, typically SQLSTATE `23503`; afterward counts remain 1/2. This package does not claim empirical execution.

#### L-09 Guided + independent exercise
**Guided (`LAB-01.02.03-01`, 25m):** execute first run and annotate output. **Independent (`LAB-01.02.03-02`, 20m):** rerun all three in order and compare counts side by side with timestamps. **Error drill (10m):** execute file 04 by itself; copy only the relevant redacted error line, describe FK safety and run verification once more.

#### L-10 Checks for learning
Why is an `IF NOT EXISTS` table not equivalent to a real schema migration? Why does an insert with a nonexistent parent ID fail? Why isn't the negative SQL file embedded in normal replay? If company count changes from 1 to 2, what should you inspect *before* resetting data?

#### L-11 Acceptance
`PC-01.02.3`: the same unchanged three files are run twice with recorded 1/2 row counts after both rounds. `PC-01.02.4`: independent FK error recorded and valid counts remain 1/2. Learner includes actual commands, log excerpts, DB identity and environment version. Any production connection or missing integrity negative test is a critical failure.

#### L-12 Expected vs observed results
Expected: `CREATE SCHEMA`, `CREATE TABLE`, first inserts create fixture, repeat inserts find conflicts and do not add rows, `SELECT` counts stable at 1 and 2; child insert with parent 999 fails (`23503` if PG reports FK violation). **Observed column remains blank until learner executes the lab**. Do not change expected labels to observed based solely on the written lesson.

#### L-13 Common mistakes
- Runs seed before schema; relation missing. **Fix:** 01→02→03 and inspect first error.
- Executes wrong DB or forgets schema-qualified names. **Fix:** inspect `current_database()` and `m01_training.company` names.
- Runs `04_negative_case.sql` with the normal suite; ON_ERROR_STOP stops batch. **Fix:** separate negative test by design.
- Treats `ON CONFLICT DO NOTHING` as durable enterprise idempotency. **Fix:** here it only avoids duplicate *fixture IDs*; advanced workflow correctness is in M08.

#### L-14 Troubleshooting and safety
On unexpected SQL failure, **stop**; record first error, verify DB identity and execution order; do not drop tables to 'fix' the issue. Instructor handles corrupted *disposable* fixtures through supervised recovery only. The course contains no permission to change real data. Avoid using `psql -W` passwords in scripts or exposing them in process listings; enter them only at secure local prompts.

#### L-15 Support and extension
**Support:** instructor checks `01_schema.sql` exists in the working directory and supplies an illustrated run-order checklist. **Extension:** discuss why actual production database migrations need version tracking and drift detection; do not implement that in M01.

#### L-16 Materials
`labs/01_schema.sql`, `labs/02_seed.sql`, `labs/03_verify.sql`, `labs/04_negative_case.sql`, `assessments/ASM-01.02-01.md`, evidence table in `resources/M01-Setup-and-Glossary.md`, restricted instructor key.

#### L-17 References
[PostgreSQL 16 tutorial](https://www.postgresql.org/docs/16/tutorial-sql.html), [CREATE TABLE](https://www.postgresql.org/docs/16/sql-createtable.html), [psql documentation](https://www.postgresql.org/docs/16/app-psql.html).

#### L-18 Wrap-up
Submit `EVD-01.02-03` and `EVD-01.02-04`. After the lesson, learners can begin M02 SQL queries because each has a known stable training dataset and two usable clients. **Instructor technical verification and signatures pending.**

---

## Part IV — Learner resource and glossary

_Source: `resources/M01-Setup-and-Glossary.md`_

### M01 Learner Setup Guide, Diagram, Glossary and Evidence Toolkit

**Audience:** learners · **Baseline:** PostgreSQL 16.x, `psql` 16.x, pgAdmin 4 v9.x target · **Revision:** 0.1 / 2026-10-10 · **Status:** DRAFT; no installer or SQL command executed during document authoring.

#### 1. System orientation

```text
OS terminal                              pgAdmin 4 Query Tool
     |                                         |
     | executes psql (client)                   | GUI client
     +------------------+----------------------+
                        |
             localhost:5432 (example)
                        |
                PostgreSQL 16 server
                        |
             database: erp_m01_lab
                        |
              schema: m01_training
                        |
          company (1) --------> customer (many)
```

The port is a sample default, **not a guarantee**. Always record the actual configured port. SQL data and server live in PostgreSQL, not in a `psql` terminal or pgAdmin user interface.

#### 2. Installing or accessing the training environment

1. Obtain PostgreSQL **16** from https://www.postgresql.org/download/ or use an instructor-provided PostgreSQL 16 instance. Before installing, verify no unrelated local PostgreSQL service will be overwritten.
2. Windows: run a trusted PostgreSQL 16 installer; record selected port and keep the generated password private. Check Windows Services for the PostgreSQL service. Use the SQL Shell (psql) or full path to `psql.exe` if the binary is not in `PATH`.
3. Linux: install approved PostgreSQL 16 packages through the platform's package manager; service/cluster commands differ by distro. Ensure service is running using the recommended OS tooling. Do not expose TCP connections outside the permitted lab boundary.
4. macOS: use a PostgreSQL 16 package/approved distribution and verify the server is running; consult its vendor instructions for the service command.
5. Install pgAdmin 4 from https://www.pgadmin.org/download/ or use an institution-approved copy. Target the v9.x user experience and record the **actual** installed version. Different versions may arrange UI fields differently.
6. If installation privileges are unavailable, request an **isolated authorized training DB** from the instructor. Students can still complete both-client connectivity and script tests.
7. The lab uses a disposable DB named `erp_m01_lab`. A trained instructor should provision it or, on an unoccupied local lab instance, use `createdb -h localhost -p 5432 -U postgres erp_m01_lab` in the OS terminal. **Check that the DB does not exist before creating; never drop an existing DB to make room.**

#### 3. Safe run sequence (OS shell)

Place the four `.sql` files in one local folder. From that folder:

```bash
psql --version
psql -h localhost -p 5432 -U postgres -d erp_m01_lab
# Inside interactive psql, type: SELECT current_database();
# Leave interactive psql with \q and run the following in the OS shell.

psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 01_schema.sql
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 02_seed.sql
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 03_verify.sql

# Repeat the SAME three lines above and record unchanged counts.
# Separate negative test (failure expected, not part of normal replay):
psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 04_negative_case.sql
# Rerun 03_verify.sql and document post-error valid counts.
```

**Shell versus SQL:** a line beginning `psql -h` or `createdb` is an OS shell command; `SELECT ...;` is SQL. Backslash commands such as `\q` and `\conninfo` are interactive `psql` commands, not general SQL. In pgAdmin Query Tool, open and execute the contents of files 01, 02 and 03 (not the `psql -f` lines); run file 04 separately.

**Protecting credentials:** prefer secure, locally entered prompts; do not place passwords in shell command options, lab scripts, Git commits or screenshots. A shared test environment may use a per-student restricted role rather than `postgres`. Never run training commands against a real customer environment.

#### 4. Expected results versus evidence

| Stage | Expected (not executed by author) | What student records |
|---|---|---|
| `psql --version` | psql 16.x | Actual output + date |
| SQL `current_database()` | `erp_m01_lab` | Two observed client outputs |
| First setup pass | `company=1; customer=2` | Real 03_verify output |
| Second setup pass | `company=1; customer=2` | Real 03_verify output |
| Invalid child insert | FK failure, usually SQLSTATE `23503` | Real error message/state |
| After failure | `company=1; customer=2` | Real verification output |

Do not substitute this table for a real run log. On an already-used database, results may differ; stop and consult instructor rather than delete existing data.

#### 5. Common error decision tree

```text
Can't connect?
├─ Is the PostgreSQL server service actually running? No → instructor checks service
└─ Yes → is host/port correct? No → correct local endpoint
     └─ Yes → does role exist and authenticate? No → local authorized role reset
          └─ Yes → does erp_m01_lab exist? No → instructor provisions it
               └─ Yes → verify pgAdmin Query Tool and psql target same DB

SQL script failed?
├─ Wrong DB? → stop immediately; change connection only
├─ Relation/schema missing? → run 01_schema.sql before 02_seed.sql
├─ Permission denied? → request instructor-approved lab role
├─ 04_negative_case.sql rejected as FK? → expected; document it
└─ Unexpected schema drift/other rows? → stop, preserve logs, get instructor help
```

#### 6. Quick glossary

| Term | Meaning in this module |
|---|---|
| Database | A named collection of related data hosted by a DBMS instance |
| DBMS | Database-management system |
| RDBMS | Relational DBMS, such as PostgreSQL |
| Server / client | Engine accepting requests / tool sending them |
| Relation/table | Relational data structure / SQL implementation |
| Attribute/column | Named field defining a data property |
| Tuple/row | One record of a table |
| Schema | Namespace for tables and other objects inside a database |
| Primary key | Uniquely identifies a table row, non-null |
| Foreign key | Constraint on a reference to a parent/candidate key |
| Candidate key | A minimal set of attributes able to uniquely identify a row |
| Cardinality | How many rows of one entity may relate to another |
| DDL | Data definition commands, e.g. `CREATE TABLE` |
| DML | Data mutation commands, e.g. `INSERT` |
| DQL | Common teaching label for data retrieval via `SELECT` |
| DCL | Access-control language, e.g. `GRANT` |
| TCL | Transaction control, e.g. `COMMIT`/`ROLLBACK` |
| psql | PostgreSQL command-line client, with non-SQL backslash commands |
| pgAdmin | Graphical administrative/query client |
| Fixture | Disposable known sample data for reproducible practice |
| Replay | Repeating the same ordered scripts without changing their content |
| Expected failure | Deliberate negative test demonstrating a constraint or error path |

#### 7. Classroom worksheet / submission scaffolding

```text
EVD-01.01-01: Conceptual diagram location: ___________________
EVD-01.01-02: 10 classifications, portability notes: __________
EVD-01.02-01: OS, exact versions, server state: _______________
EVD-01.02-02: Both clients' database results: ________________
EVD-01.02-03: First and second replay counts: ________________
EVD-01.02-04: FK error and unaffected row counts: _____________
Observations performed by / date: _____________________________
Sanitization check: no passwords, tokens, real customer names: _
```

#### 8. Resources and accessibility

Use selectable text rather than image-only commands. Provide screen-reader-readable diagram narration (client → server → database → schema → tables), and a high-contrast printed version if useful. Offer a preconfigured environment where installation accessibility or system permissions block learners. Authoritative docs: https://www.postgresql.org/docs/16/ , https://www.pgadmin.org/docs/ .

---

## Part V — SQL laboratory scripts

These scripts target **a disposable, student-owned `erp_m01_lab` database only**. Connect to and verify the correct database first. Execute `01_schema.sql`, then `02_seed.sql`, then `03_verify.sql` in that order. Replay the three scripts unchanged to observe idempotent fixture loading, then run `04_negative_case.sql` separately and record the expected foreign-key error. This is **expected behavior, not executed/verified by the author**.

### LAB-M01-01 — `01_schema.sql`

```sql
-- LAB-01.02.03-01 | M01 PostgreSQL 16.x | version 0.1 (2026-10-10)
-- Only run in the isolated, disposable erp_m01_lab database.
-- Prerequisites: role may CREATE in database; execute file before 02_seed.sql.
-- Execution (shell, from this directory):
-- psql -h localhost -p 5432 -U postgres -d erp_m01_lab -v ON_ERROR_STOP=1 -f 01_schema.sql
-- NOTE: pgAdmin Query Tool can execute the SQL in this file (no psql metacommands).
-- EXPECTED ONLY; no source-author test execution recorded.

-- The following gate fails early if the user connected to the wrong database.
DO $$
BEGIN
    IF current_database() <> 'erp_m01_lab' THEN
        RAISE EXCEPTION 'M01 refuses to run outside erp_m01_lab (current database: %)',
                        current_database();
    END IF;
END $$;

CREATE SCHEMA IF NOT EXISTS m01_training;

CREATE TABLE IF NOT EXISTS m01_training.company (
    company_id INTEGER PRIMARY KEY,
    company_name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE IF NOT EXISTS m01_training.customer (
    customer_id INTEGER PRIMARY KEY,
    company_id INTEGER NOT NULL REFERENCES m01_training.company(company_id),
    customer_name VARCHAR(100) NOT NULL,
    customer_email VARCHAR(255) NOT NULL,
    CONSTRAINT uq_m01_customer_email_per_company
        UNIQUE (company_id, customer_email)
);

-- If a pre-existing table has a different structure, IF NOT EXISTS will not fix it.
-- STOP and ask the instructor: do not delete live or shared objects.
```

### LAB-M01-02 — `02_seed.sql`

```sql
-- LAB-01.02.03-01 | Fictional ERP fixtures | PostgreSQL 16.x | DRAFT
-- Execute ONLY after 01_schema.sql and ONLY against erp_m01_lab.
-- These are deliberately fake sample records, not real customer data.
-- Run file twice to demonstrate stable primary-key fixture counts.

DO $$
BEGIN
    IF current_database() <> 'erp_m01_lab' THEN
        RAISE EXCEPTION 'M01 refuses to run outside erp_m01_lab (current database: %)',
                        current_database();
    END IF;
END $$;

BEGIN;
INSERT INTO m01_training.company(company_id, company_name)
VALUES (1, 'Demo Trading Ltd')
ON CONFLICT (company_id) DO NOTHING;

INSERT INTO m01_training.customer(customer_id, company_id, customer_name, customer_email)
VALUES
    (101, 1, 'Sample Customer One', 'customer101@example.invalid'),
    (102, 1, 'Sample Customer Two', 'customer102@example.invalid')
ON CONFLICT (customer_id) DO NOTHING;
COMMIT;

-- Simplified replay behavior for fixed training IDs; ON CONFLICT details are
-- part of later modules. This does NOT prove end-to-end business idempotency.
```

### LAB-M01-03 — `03_verify.sql`

```sql
-- LAB-01.02.03-01 | Observe database identity, tables, and stable row counts.
-- Only run in erp_m01_lab AFTER 01_schema.sql and 02_seed.sql.
-- EXPECTED on a clean assigned environment: company_count=1, customer_count=2.

DO $$
BEGIN
    IF current_database() <> 'erp_m01_lab' THEN
        RAISE EXCEPTION 'M01 refuses to run outside erp_m01_lab (current database: %)',
                        current_database();
    END IF;
END $$;

SELECT current_database() AS database_name, current_user AS connected_role;
SHOW server_version;

SELECT schemaname, tablename
FROM pg_catalog.pg_tables
WHERE schemaname = 'm01_training'
ORDER BY tablename;

SELECT COUNT(*) AS company_count FROM m01_training.company;
SELECT COUNT(*) AS customer_count FROM m01_training.customer;

SELECT company_id, company_name
FROM m01_training.company
ORDER BY company_id;

SELECT customer_id, company_id, customer_name
FROM m01_training.customer
ORDER BY customer_id;

-- Record observed values separately; never invent execution results.
```

### LAB-M01-04 — `04_negative_case.sql`

```sql
-- LAB-01.02.03-02 | EXPECTED FAILURE / run separately from success suite.
-- PostgreSQL 16.x only in disposable erp_m01_lab, after schema and seed.
-- Expected SQLSTATE: 23503 (foreign_key_violation).
-- psql -v ON_ERROR_STOP=1 will return a NONZERO exit code as intended.

DO $$
BEGIN
    IF current_database() <> 'erp_m01_lab' THEN
        RAISE EXCEPTION 'M01 refuses to run outside erp_m01_lab (current database: %)',
                        current_database();
    END IF;
END $$;

-- No company row 999 exists in the clean fixture.
INSERT INTO m01_training.customer
    (customer_id, company_id, customer_name, customer_email)
VALUES (999, 999, 'Invalid Sample Customer', 'invalid999@example.invalid');

-- After recording the failure, run 03_verify.sql independently.
-- Valid counts must remain 1 company and 2 customers.
```


---

## Part VI — Assessment ASM-01.01-01

_Source: `assessments/ASM-01.01-01.md`_

### ASM-01.01-01 — Conceptual Diagram and SQL Classification (Learner Copy)

**Module / unit:** M01 / U01.01 (provisional) · **Version:** 0.1 · **Duration:** included in U01.01's 180 guided minutes · **Marks:** 30 · **Tools:** paper/digital diagram, text editor · **Privacy:** fake names only.

#### Assessment conditions
Individual work after lessons `L01.01.01` and `L01.01.02`. Learners may use the course glossary, but answers must be their own. No database access required. Submit `EVD-01.01-01` and `EVD-01.01-02`.

#### Task A — Draw and explain (16 marks)
Draw a simple environment sketch containing a PostgreSQL server, database `erp_m01_lab`, schema `m01_training`, company and customer tables, rows and columns. Add client arrows for psql and pgAdmin. Model one company to many customers. Label `company.company_id` as PK, `customer.customer_id` as PK, and `customer.company_id` as FK referencing its parent. Below the diagram, explain in three sentences: (1) client versus server, (2) database versus schema, (3) what the FK prevents.

#### Task B — Statement classifier (10 marks)
For each numbered sample, write one teaching category **DDL / DML / DQL / DCL / TCL** and a one-sentence explanation. **Do not execute these commands**.

| No. | Example | Your category | Purpose |
|---|---|---|---|
| 1 | `CREATE TABLE demo (id INT);` | | |
| 2 | `INSERT INTO demo (id) VALUES (1);` | | |
| 3 | `SELECT id FROM demo;` | | |
| 4 | `UPDATE demo SET id=2 WHERE id=1;` | | |
| 5 | `GRANT SELECT ON demo TO report_role;` | | |
| 6 | `BEGIN;` | | |
| 7 | `ROLLBACK;` | | |
| 8 | `ALTER TABLE demo ADD COLUMN note TEXT;` | | |
| 9 | `DELETE FROM demo WHERE id=2;` | | |
| 10 | `REVOKE SELECT ON demo FROM report_role;` | | |

For this course, **SELECT is DQL**. The categories are pedagogical and not universally separate standards.

#### Task C — Portability notes (4 marks)
Write **two** concrete differences or limitations when running SQL/PostgreSQL/psql commands with other tools or DBMSs. Each note must name a feature/command and why a code change or client change may be needed.

#### Submission, criteria and negative case
| Evidence | Related PC | Weight | Pass condition |
|---|---|---:|---|
| Diagram, labels, relationship | `PC-01.01.1`, `PC-01.01.2` | 16 | six of seven labels correct **and** PK/FK direction correct |
| Classifier worksheet | `PC-01.01.3` | 10 | ≥8/10 classified correctly |
| Two portability notes | `PC-01.01.4` | 4 | two substantive caveats |
| **Total** | | **30** | **≥24/30 plus key/relationship gate** |

**Invalid-case prompt:** Would a customer referencing company 999 succeed if no company 999 exists and the FK is enforced? Explain without executing SQL.

If the score/critical gate fails, review the appropriate lesson, correct the diagram or classification, then complete an equivalent instructor-provided reassessment. **Learner copy contains no model answers.**

---

## Part VI — Assessment ASM-01.02-01

_Source: `assessments/ASM-01.02-01.md`_

### ASM-01.02-01 — PostgreSQL Environment and Repeatable ERP Setup (Learner Copy)

**Module / unit:** M01 / U01.02 (provisional) · **Version:** 0.1 · **Marks:** 70 · **Timing:** practical performance inside U01.02's 300 minutes (not extra hours) · **Platform:** PostgreSQL 16.x, psql 16.x, pgAdmin 4 v9.x target.

#### Scenario and conditions
Your team needs a minimal reproducible database workspace for a fictional ERP. Use only `erp_m01_lab` in your own disposable environment; never use real accounts or customer data. Student produces observed evidence while the instructor checks context and outputs.

#### Task 1 — Environment report (15 marks)
Create `EVD-01.02-01`: OS/provisioning route; exact `psql --version`, actual server version, actual pgAdmin About version; local host and port, database name, active role (no password). Write one paragraph distinguishing server and clients. Include service status and observations rather than assumed defaults.

#### Task 2 — Dual-tool connection (15 marks)
Create `EVD-01.02-02`: connect using `psql` and pgAdmin Query Tool and execute in both:

```sql
SELECT current_database() AS database_name, current_user AS connected_role;
```

Show that both returned `erp_m01_lab`. Provide sanitized timestamps and one safe troubleshooting note for a wrong database or port.

#### Task 3 — Repeatable scripts (25 marks)
Create `EVD-01.02-03`: on a fresh assigned DB, execute `01_schema.sql`, `02_seed.sql`, `03_verify.sql` in that exact order using psql or Query Tool. Capture the first row counts and table names. Run the **same** three files again unchanged. Capture the second counts, compare them and explain their meaning. Include scripts or links to unmodified originals, command order and exit status.

#### Task 4 — Negative case and recovery (15 marks)
Create `EVD-01.02-04`: execute `04_negative_case.sql` alone against the same DB and record the actual FK error (failure is expected). Rerun `03_verify.sql` after the error; record counts. Explain which constraint blocks the orphan customer and why the intentional failure must be separate from the success sequence.

#### Scoring and critical gates
| Task | Marks | Mapped PC | Critical requirement |
|---|---:|---|---|
| 1 | 15 | `PC-01.02.1` | observed version + database identity |
| 2 | 15 | `PC-01.02.2` | **both** clients connect to `erp_m01_lab` |
| 3 | 25 | `PC-01.02.3` | **both** run counts: 1 company, 2 customers |
| 4 | 15 | `PC-01.02.4` | FK rejection; valid rows unchanged |
| **Total** | **70** | | **≥56/70 + ALL critical gates** |

No live data or credentials allowed; violating this safety requirement fails the task regardless of numerical score. If unable to install due to limited access, use approved pre-provisioned training DB and document accommodation. Missing real log evidence is not a pass. Remediation is a witnessed rerun with the correct safe environment and resubmitted PC evidence.

#### Learner evidence template

```text
Student alias / date: ___________________________
OS and chosen installation route: _______________
Server 16.x observed? ____ / psql 16.x? ____ / pgAdmin version: ____
Host: localhost  Port: ____  DB: erp_m01_lab  Role (not password): ____
psql current_database result: __________________
pgAdmin current_database result: ________________
First pass counts: company ____ / customer ____
Second pass counts: company ____ / customer ____
Negative test observed SQLSTATE/message: ________
After failure counts: company ____ / customer ____
Redacted evidence paths: ________________________
Reflection: _____________________________________
```

**Keep blank until you have real observations; expected output is not evidence of execution.**

---

## Part VII — QA, traceability and change log

_Source: `qa/M01-Traceability-QA-and-Change-Log.md`_

### M01 — Traceability, Hour Validation, Release Gates and Change Log

**Standard:** SQL-EDU-STD-001 v1.0 · **Syllabus:** v1.1 2026 Edition · **Version/date:** 0.1 / 2026-10-10 · **Current gate:** DRAFT / NOT APPROVED · **Source SQL tests:** NOT EXECUTED.

#### 1. Unconfirmed master-register alignment

The available official *course syllabus draft* fixes Module 01's title and 8h = 4T + 4P, but does not include the 53-unit ID/name register. `U01.01`, `U01.02` and associated lesson IDs are **provisional authored subdivisions**, not evidence of an already-frozen approved unit list. **Before release:** curriculum lead must compare IDs and titles against the authoritative register and either approve them unchanged or coordinate a versioned re-ID/reallocation under GOV-01/03. Do not modify overall M01 hours without a separately approved change.

#### 2. Exact duration arithmetic

| Unit / lesson | Theory min | Practical min | Total min |
|---|---:|---:|---:|
| L01.01.01 | 60 | 30 | 90 |
| L01.01.02 | 60 | 30 | 90 |
| **U01.01** | **120** | **60** | **180** |
| L01.02.01 | 60 | 60 | 120 |
| L01.02.02 | 30 | 60 | 90 |
| L01.02.03 | 30 | 60 | 90 |
| **U01.02** | **120** | **180** | **300** |
| **M01** | **240 = 4h** | **240 = 4h** | **480 = 8h** |

Lessons' phase-by-phase flow arithmetic must be rechecked in instructional QA before publication.

#### 3. Full CLO→MLO→ULO→LLO→PC→assessment→evidence trace

| CLO | MLO | ULO | Lesson outcome | PC | Assessment | Evidence |
|---|---|---|---|---|---|---|
| CLO-01 | MLO-01.1 | ULO-01.01.1 | LLO-01.01.01.1 | PC-01.01.1 | ASM-01.01-01 Task A | EVD-01.01-01 |
| CLO-01 | MLO-01.1 | ULO-01.01.3 | LLO-01.01.01.2 | PC-01.01.2 | ASM-01.01-01 Task A | EVD-01.01-01 |
| CLO-01/02 | MLO-01.2 | ULO-01.01.2 | LLO-01.01.02.1 | PC-01.01.3 | ASM-01.01-01 Task B | EVD-01.01-02 |
| CLO-01/02 | MLO-01.2 | ULO-01.01.2 | LLO-01.01.02.2 | PC-01.01.4 | ASM-01.01-01 Task C | EVD-01.01-02 |
| CLO-01 | MLO-01.3 | ULO-01.02.1 | LLO-01.02.01.1 / .2 | PC-01.02.1 | ASM-01.02-01 Tasks 1,2 | EVD-01.02-01 |
| CLO-01 | MLO-01.3 | ULO-01.02.2 | LLO-01.02.02.1 | PC-01.02.2 | ASM-01.02-01 Task 2 | EVD-01.02-02 |
| CLO-01 | MLO-01.3 | ULO-01.02.1 | LLO-01.02.02.2 | PC-01.02.1 | ASM-01.02-01 Task 2 | EVD-01.02-01 |
| CLO-01/02 | MLO-01.4 | ULO-01.02.3 | LLO-01.02.03.1 | PC-01.02.3 | ASM-01.02-01 Task 3 | EVD-01.02-03 |
| CLO-01/02 | MLO-01.4 | ULO-01.02.3 | LLO-01.02.03.2 | PC-01.02.4 | ASM-01.02-01 Task 4 | EVD-01.02-04 |

#### 4. Checklist, deviations and QA reviewers

| Control | Draft check | Evidence / remaining action |
|---|---|---|
| GOV-01 IDs / frozen 53-unit map | **BLOCKED** | Master unit register not supplied; obtain and reconcile provisional IDs |
| GOV-02 M01 duration 4T/4P | **DRAFT CHECK OK** | File arithmetic totals 240T/240P; reviewer must sign |
| GOV-03 essential topics unchanged | **DRAFT CHECK OK** | Follows baseline Module 01 list; scripts preview later topics without assessing them |
| GOV-04 hierarchy | **DRAFT CHECK OK** | 2 unit records, 5 lesson files nested by ID |
| GOV-05 complete mapping | **DRAFT CHECK OK** | Table above; assessor to confirm observed evidence coverage |
| GOV-06 reviewer approvals | **BLOCKED** | Technical, instructional and editorial signatures missing |
| GOV-07 tools/revisions/authors | **PARTIAL** | PG16/psql16/pgAdmin4 v9.x target named; exact installed versions and named reviewers pending |
| GOV-08 fictional disposable data | **DRAFT CHECK OK** | `.invalid` mail addresses, guarded DB name; runtime safety review pending |
| GOV-09 instructor answers separated | **DRAFT CHECK OK** | Only `instructor/INSTRUCTOR-KEY-M01.md` contains marked answers |
| GOV-10 observed claims | **DRAFT CHECK OK** | All runtime claims labeled expected/unverified |
| SQL-01…12 | **PARTIAL** | Manual review pending; destructive reset instructor-only; script exercise hasn't been run |
| Lesson L-01…L-18 | **DRAFT CHECK OK** | 5 lessons have explicit headings; technical validation pending |
| Unit U-01…U-17 | **DRAFT CHECK OK** | 2 units have explicit headings; approved IDs pending |
| Module M-01…M-17 | **DRAFT CHECK OK** | Module guide has explicit headings; approvals pending |
| Accessibility and editorial proof | **PENDING** | Reviewer checks diagrams, screen readers, localized steps and links |

**Status must remain NOT APPROVED if any critical item remains unchecked.** Do not label draft checks as formal sign-off.

#### 5. Runnable verification record (to be completed by a human with PG16)

| Field | To record |
|---|---|
| Tester and date/time | **NOT RUN** |
| OS/hardware/PG server and client exact versions | **NOT RUN** |
| Host/port/DB and effective permissions | **NOT RUN** |
| First pass `01_schema.sql`, `02_seed.sql`, `03_verify.sql` exit codes | **NOT RUN** |
| Repeat pass identical script checksum and counts | **NOT RUN** |
| Separate `04_negative_case.sql` expected FK error/SQLSTATE | **NOT RUN** |
| Post-error row counts | **NOT RUN** |
| pgAdmin SQL execution check | **NOT RUN** |
| Logs/screenshots (sanitized) | **NOT PROVIDED** |
| Approval decision | **BLOCKED** |

#### 6. Review sign-off

| Review | Reviewer | Date | Decision |
|---|---|---|---|
| Technical | TBD | — | NOT REVIEWED |
| Instructional | TBD | — | NOT REVIEWED |
| Editorial/accessibility | TBD | — | NOT REVIEWED |
| Curriculum lead / frozen unit register | TBD | — | NOT REVIEWED |

#### 7. Change log

| Date | Version | Change | Decision |
|---|---|---|---|
| 2026-10-10 | 0.1 | Initial lesson-, unit- and module-level M01 materials; learner assessments; scripts; separate instructor key; QA traceability. | Authored; **not approved** |

#### 8. Publication gate

Technical test logs + 3 approvals + approved unit-ID registry + lesson run-order observed + accessibility review are mandatory. **Until then: DRAFT / NOT APPROVED.**

---

## Distribution and release notes

- This Markdown contains the module guide, both draft unit guides, all five lessons, glossary/setup resource, all four SQL scripts, both learner assessments and QA documentation.
- Instructor-only `INSTRUCTOR-KEY-M01.md` is **not embedded**, in accordance with GOV-09 and SQL-12. It remains separately available within `M01_Database_Fundamentals_2026_Package.zip`.
- Before release: verify IDs against the approved 53-unit register; run scripts in PostgreSQL 16 and retain logs; complete technical, instructional and editorial reviews; record the curriculum-lead approval.
- Outcome hours: U01.01 = 3h (2T + 1P); U01.02 = 5h (2T + 3P); M01 = **8h (4T + 4P)**. Assessment minutes are included in those hours, not additional.
