# M02 — SQL Programming Fundamentals

## Course publication notice

This is a full **learner-ready draft**, not a claim of NTVQF accreditation, runtime verification, or final course-team approval. The author's expected outputs are labeled **EXPECTED (NOT EXECUTED)**. Instructor answer keys MUST NOT be included in learner distribution. A complete technical, instructional and editorial sign-off is still required by SQL-EDU-STD-001.

**Programme:** Professional SQL Programming & Enterprise Database Engineering — 2026 Edition  
**Syllabus:** `Professional_SQL_Enterprise_Database_Engineering_Syllabus_2026.md`, v1.1 (9 October 2026)  
**Authoring standard:** `SQL_Curriculum_Authoring_Standard_v1.0.md`, SQL-EDU-STD-001 v1.0  
**Revision:** v0.1, 10 October 2026  
**Delivery status:** **DRAFT — NOT APPROVED; PostgreSQL scripts NOT EXECUTED during authoring**  
**Author:** Curriculum development team (named author/signature pending)  
**Technical reviewer / instructional reviewer / editorial reviewer:** Not appointed; signatures pending  
**Environment:** PostgreSQL 16.x, `psql` 16.x; pgAdmin 4 v9.x target or equivalent PostgreSQL 16-compatible client; no extensions required  
**Training data:** Disposable ERP dataset only; all names/email addresses fictional (.test domain).  
**ID control:** Unit IDs `U02.01–U02.04` and lesson IDs `L02.xx.xx` are **PROVISIONAL** until checked against the separately approved 53-unit master register. M02 identifier and **18h (6T/12P)** are syllabus-fixed.  
**Distribution:** Learner-facing content; instructor solutions are stored **separately**, not embedded here.  


## Contents

1. Module specification M-01 through M-17, 18-hour hour ledger and outcome map.
2. Four instructional unit guides U-01 through U-17 with elements and performance criteria.
3. Twelve detailed learner lessons L-01 through L-18, each 90 minutes.
4. Five separate reusable PostgreSQL lab scripts, reproduced in code-block appendices.
5. Four assessment briefs, evidence, remediation and rubric.
6. Traceability, technical/QA status, instructor review form and change log.

---

# Part I — Module specification (M-01 to M-17)

## M-01. Identity and control

| Field | Value |
|---|---|
| Module | **M02 — SQL Programming Fundamentals** |
| Programme | Professional SQL Programming & Enterprise Database Engineering, 2026 |
| Governing syllabus | v1.1, 9 October 2026 |
| Authoring standard | SQL-EDU-STD-001 v1.0 |
| Version / revised | v0.1 / 10 October 2026 |
| Hours | **18 guided h: 6 theory + 12 practical** |
| Supported lab | PostgreSQL 16.x, matching `psql` client, pgAdmin 4 target v9.x |
| Author / reviewer | Author pending; technical, instructional, editorial reviewers pending |
| Status | **DRAFT — not approved, runtime unverified** |

## M-02. Workplace rationale

A sales administrator must list customers, edit a single record, identify unsold items, join orders to products, and calculate sales totals without accidentally changing many customers or double-counting money. Correct SQL is not only syntax: it requires explicit predicates, data-type and NULL reasoning, grouping semantics, relationship cardinality, and secure value binding when data arrives from a web application. This module establishes those reliable daily skills on a fictional ERP customer, supplier, product, sales-order and order-line dataset.

## M-03. Prerequisites

- Complete `M01`: server versus database/schema, primary/foreign keys, pgAdmin/psql connection, script execution and safe disposal of fixture data.
- Have access to an **isolated**, writable PostgreSQL 16 lab database named `erp_m02_lab` (or an instructor-provisioned equivalent with the same safety validation); never connect this module's reset script to other databases.
- Know where to save `.sql` and `.md` files and how to record actual command output without credentials.

## M-04. Scope / exclusions

**In scope (syllabus-mandated):** `SELECT`, `INSERT`, `UPDATE`, `DELETE`; Boolean `WHERE`, `IN`, `BETWEEN`, `DISTINCT`, `ORDER BY`, `LIMIT/OFFSET`; `NULL`, `CASE`, `COALESCE`; numeric/text/date functions; `INNER JOIN`, `LEFT JOIN`; `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`, `GROUP BY`, `HAVING`; `IN`, `EXISTS`, correlated and noncorrelated subqueries; `UNION`, `INTERSECT`, `EXCEPT`; parameterized input; safe row-changing operations and edge-case tests.

**Out of scope:** relational normalization, index/schema design and migrations (`M03`), window functions/CTEs/keyset paging (`M04`), procedures (`M05`), transaction isolation (`M06`), idempotency (`M08`), query-plan tuning (`M10`), tenant security policies (`M12`), and full Spring Boot integration (`M15`). Basic schema declarations and `BEGIN/ROLLBACK` are *provided scaffolding/safe practice*, not independently assessed mastery of later topics.

## M-05. Observable module learning outcomes (MLO) and CLO map

| MLO | Learner can, given PostgreSQL 16 and supplied ERP fixtures… | Course alignment | Evidence / pass condition |
|---|---|---|---|
| `MLO-02.1` | Write SELECT/INSERT/UPDATE/DELETE commands targeting exact records, correctly scoped and verified. | `CLO-02` | CRUD workbook with bounded write previews and no unintended persistent change |
| `MLO-02.2` | Predict and handle at least two integrity/safety failure modes in basic DML. | `CLO-01`, `CLO-02` | Duplicate PK/FK notes, before/after counts and recovery explanation |
| `MLO-02.3` | Return correctly filtered, deterministic and NULL-aware query results using expressions and set/subquery operators. | `CLO-02` | Correct results for all unit benchmark cases |
| `MLO-02.4` | Join and aggregate order/customer/product data, retaining unmatched records and reconciling paid sales **13500.00**. | `CLO-02` | Join cardinality proof and aggregate reconciliation |
| `MLO-02.5` | Use a bound parameter in a query and explain why concatenated external values are unsafe. | `CLO-02`, `CLO-09` (introductory only) | Prepared query evidence and input-safety explanation |

## M-06. Frozen hour ledger: 18 h = 6T + 12P

| Unit (PROVISIONAL IDs) | Theory (h) | Practice (h) | Total (h) | Lessons |
|---|---:|---:|---:|---:|
| `U02.01` Core CRUD and Safe Mutations | 1.5 | 3 | 4.5 | L02.01.01–03 |
| `U02.02` Filtering, NULL and Scalar Expressions | 1.5 | 3 | 4.5 | L02.02.01–03 |
| `U02.03` Joins and Grouped Reporting | 1.5 | 3 | 4.5 | L02.03.01–03 |
| `U02.04` Subqueries, Set Operations and Parameterization | 1.5 | 3 | 4.5 | L02.04.01–03 |
| **MODULE TOTAL** | **6** | **12** | **18** | **12 × 90 min** |

Each lesson allocates **30 theory + 60 practice** minutes (90 total). Theory covers instructor explanation and demonstration; practical time includes guided lab, individual tasks, feedback and assessment. Breaks are outside these guided hours.

## M-07. Unit sequence and dependency map

| Sequence | Unit | Prior skills | Primary products | MLO |
|---|---|---|---|---|
| 1 | `U02.01` | M01 baseline | Safe CRUD commands and replay proof | 02.1, 02.2 |
| 2 | `U02.02` | L02.01.01 | Deterministic filtered customer/product views | 02.1, 02.3 |
| 3 | `U02.03` | Relational keys + SELECT | Order/line join and paid-sales report | 02.4 |
| 4 | `U02.04` | Filtering, joins | Customer/product existence queries, city sets and parameterized workbook | 02.3, 02.5 |

## M-08. Teaching strategy

Every 90-minute lesson follows **5 min scenario + 15 min explanation + 10 min annotated demonstration (30T); 25 min guided practice + 25 min independent application + 10 min checked evidence and feedback (60P)**. Use: (a) prediction before running SQL; (b) execution in disposable DB; (c) comparison of expected versus observed; (d) peer/instructor explanation of NULL and cardinality traps; (e) correction and reassessment of any failed criterion. Learners without local install privileges use the instructor-managed training DB but record the same SQL client/server version evidence.

## M-09. Materials and versioned resource inventory

- `labs/01_schema.sql`: guarded reset and supplied relational tables; scaffold, not assessed design.
- `labs/02_seed.sql`: fictional ERP fixture, to run only after guarded reset.
- `labs/03_verify.sql`: sanity checks and paid-total baseline.
- `labs/04_assignment_starter.sql`: learner prompts only, no answer key.
- `labs/05_negative_cases.sql`: standalone expected-failure demonstrations; run one statement at a time.
- `M02-SQL-Programming-Fundamentals-Complete.md`: the entire module specification, units, lessons, lab SQL and assessment briefs (this file).
- `M02-INSTRUCTOR-KEY.md`: restricted instructor-only solutions (separate distribution).
- Teaching aids to be prepared before delivery: accessible schema diagram, plain-text sample result sheets and OS-specific client screenshots.
- Reference documents: official PostgreSQL 16 SQL command and function manual, Oracle Java SE 17 JDBC PreparedStatement documentation (see M-15).

## M-10. Integrated workplace case, fixture and test oracle

**Case:** A small ERP sales team serves Alpha Retail (`C001`), Beta Traders (`C002`) and Gamma Clinic (`C003`). Suppliers offer five catalog products. Four orders contain six order lines. Gamma has **no orders**. Sticker (`P-STICK`) has **no order lines**. Of the four orders, **two are PAID**, one PENDING and one CANCELLED. For this toy scenario, report only PAID order lines in the paid-sales subtotal.

| Entity / invariant | EXPECTED value (NOT EXECUTED) |
|---|---|
| Customers, suppliers, products | 3, 2, 5 |
| Orders, order items | 4, 6 |
| Missing customer email addresses | 2 (C002, C003) |
| Orders for C001, C002, C003 | 2, 2, 0 |
| PAID order subtotal 1001 | 700.00 |
| PAID order subtotal 1003 | 12800.00 |
| **Total PAID order lines** | **13500.00** |
| NEVER sold product | product 105 / P-STICK |
| Distinct customer/supplier city UNION / INTERSECT / EXCEPT | 3 / 1 / 1 |

**Runbook:** Create disposable DB `erp_m02_lab`; run `01_schema.sql` with ON_ERROR_STOP enabled and review the RESET warning; then `02_seed.sql`, `03_verify.sql`. Preserve sanitized output. The learner's CRUD edits should use BEGIN/ROLLBACK to return the fixture to its original state; if it drifts, rerun setup and seed ONLY on the disposable DB. `05_negative_cases.sql` is not a batch migration; run its failing statements individually.

## M-11. Assessment blueprint

| Assessment | Type | Unit / mapped MLO | Marks | Critical criteria |
|---|---|---|---:|---|
| `ASM-02.01-01` | CRUD practical + code explanation | U02.01 / MLO-02.1,02.2 | 25 | Scoped writes, before/after, rollback, no unscoped DML |
| `ASM-02.02-01` | Query exercises + NULL edge cases | U02.02 / MLO-02.3 | 25 | NULL and ordering right, no stored data altered |
| `ASM-02.03-01` | Report/reconciliation pack | U02.03 / MLO-02.4 | 25 | Gamma present as zero; paid total exactly 13500.00 |
| `ASM-02.04-01` | Existence/set/binding capstone | U02.04 / MLO-02.3,02.5 | 25 | Valid bound parameter; no input concatenation |
| **Total** | | | **100** | **80/100 minimum AND all critical criteria** |

Assessment timing is included inside lesson practical minutes. An invalid result that exposes a write without a scoped key, loses Gamma in required outer-join report, includes nonpaid orders in paid total, or concatenates externally supplied SQL parameters is a **critical fail even at 80+ points**. Remediate with one targeted corrective exercise and independently resubmit its evidence.

## M-12. Named learner evidence

`EVD-02.01-01`: CRUD SQL and before/after/rollback output; `EVD-02.01-02`: observed negative-case notes; `EVD-02.02-01`: filtered/NULL/function SQL outputs; `EVD-02.03-01`: inner/outer join tables and grouped paid-total reconciliation; `EVD-02.04-01`: EXISTS/sets queries and explained results; `EVD-02.04-02`: bound-value SQL and full workbook. Include database identity (`SELECT current_database()`), actual PostgreSQL version, timestamps and reviewer comments in `evidence.md`. Never submit passwords or secrets.

## M-13. Integrity, safety and security

1. Use an **isolated** training database named `erp_m02_lab`; the reset script contains a database-name guard and an intentionally destructive `DROP SCHEMA` which must **never** run elsewhere.
2. For updates/deletes, preview with SELECT and predicate, verify affected IDs/rows with RETURNING, and ROLLBACK when exploring. Never teach unscoped DELETE/UPDATE as acceptable business operations.
3. Preserve foreign-key and CHECK constraint behaviour. Negative tests are executed individually and documented as observed errors, not recorded as pre-passed.
4. Keep PENDING and CANCELLED out of the PAID subtotal; count any unmatched LEFT JOIN rows correctly.
5. Use bound values in application-originated SQL; parameter binding is necessary but not sufficient for access-control and tenancy protection, which are deeper M12/M15 topics.
6. Training names and addresses are fictional; `.test` is reserved for examples. Do not store real personal information or credentials.

## M-14. Instructor preparation and adaptations

- Check each learner can connect to the designated training DB with PostgreSQL 16; note precise patch level and `psql`/pgAdmin versions.
- Create/read the five scaffold scripts and ensure instructor-only solution file is not distributed to students.
- Demonstrate a deliberate join-cardinality error and a corrected LEFT JOIN using the tiny dataset. Record that the demonstration is an observed test only once actually run.
- Rehearse rollback as protection against unintentional mutations; explain that it is not the production recovery strategy.
- Support: supply the five-row fixture diagram and column dictionary, pair syntax-first learners with concept-first peers, avoid requiring a specific operating system.
- Extend: ask advanced students to contrast anti-joins, pagination anomalies or outer-join predicates, without adding mandatory delivery hours or changing frozen outcomes.
- Accessibility: include non-color-only output clues, text descriptions of diagrams, clear tabular output and keyboard-accessible editor instructions.

## M-15. References and edition anchors

- PostgreSQL Global Development Group, **PostgreSQL 16 Documentation**, SQL Commands (`SELECT`, `INSERT`, `UPDATE`, `DELETE`, `PREPARE`), Functions/Operators and table expressions, https://www.postgresql.org/docs/16/ (target major version 16).
- PostgreSQL 16 Tutorial, Queries/Joins/Aggregate Functions, https://www.postgresql.org/docs/16/tutorial.html .
- PostgreSQL 16, Subquery Expressions, https://www.postgresql.org/docs/16/functions-subquery.html .
- PostgreSQL 16, Combining Queries (`UNION`, `INTERSECT`, `EXCEPT`), https://www.postgresql.org/docs/16/queries-union.html .
- Java SE 17, JDBC `PreparedStatement` reference, https://docs.oracle.com/en/java/javase/17/docs/api/java.sql/java/sql/PreparedStatement.html .
- Local governing references: 2026 syllabus v1.1 and SQL-EDU-STD-001 v1.0. **Textbook section assignments intentionally await edition verification** rather than inventing chapter citations.

## M-16. Required QA and sign-off (not completed)

| Review | Required check | State | Reviewer / date |
|---|---|---|---|
| Technical | SQL parses/runs under actual PostgreSQL 16; tests captured; safe reset and row counts verified | **NOT EXECUTED** | Pending |
| Instructional | Unit/lesson prerequisites, outcomes, practical time, assessment load and accessibility | **NOT REVIEWED** | Pending |
| Editorial | IDs, terms, spelling, links, evidence paths, learner/instructor separation | **NOT REVIEWED** | Pending |
| Curriculum lead | Provisional unit IDs mapped to frozen master register and approved | **NOT APPROVED** | Pending |

Publication is blocked until all mandatory gate items and reviewer signatures are completed.

## M-17. Module completion criteria

Learner must attend/complete the documented 18 guided hours (6T+12P), submit all four assessed evidence bundles, earn **≥80/100**, meet all critical safety/correctness gates, demonstrate correct database/version context and explain error recovery. Passing the module is not an NTVQF or other external qualification claim. Remediation is allowed through observed retest of failed PCs.

---

# Part II — Instructional units (U-01 to U-17 each)

## U02.01 — Core CRUD and Safe Mutations

### U-01. Identity and metadata

**Owning module:** M02. **Version:** v0.1 / 10 October 2026. **Author/reviewer:** Curriculum team (name pending) / appointed reviewers pending. **Status:** DRAFT, SQL NOT EXECUTED, IDs PROVISIONAL. **Platform:** PostgreSQL 16.x with seed dataset from lab scripts.

### U-02. Purpose and workplace task

Maintain the customer directory safely and prove every change is scoped and recoverable in a disposable ERP lab.

### U-03. Preconditions

Complete relevant preceding lesson(s); have `erp_m02_lab` connected, seed script loaded, a local SQL editor and permission to read training schema. Students must know the sample row counts and practice `SELECT` before any scoped DML.

### U-04. Unit learning outcomes / MLO traceability

| ULO | Observable outcome | MLO | Direct evidence |
|---|---|---|---|
| `ULO-02.01.1` | Select required columns and rows with an explicit, reproducible order; projected result matches seed. | `MLO-02.1` | `EVD-02.01-01` and lesson output |
| `ULO-02.01.2` | Insert and update exactly one intended test customer, show RETURNING, and restore the starting row count. | `MLO-02.2` | `EVD-02.01-01` and lesson output |
| `ULO-02.01.3` | Preview target keys and delete only a bounded disposable record; demonstrate rollback and describe FK protection. | `MLO-02.2` | `EVD-02.01-01` and lesson output |

### U-05–U-06. Elements of Competency / Performance Criteria

These are **internal educational elements**, not formal NTVQF Units of Competency. Each element has an observable performance criterion and an evidence target.

| Element | PC (assessable pass threshold) | Evidence / lesson |
|---|---|---|
| `EC-02.01.1` — SELECT, Projection and First Predicates | `PC-02.01.1` — Select required columns and rows with an explicit, reproducible order; projected result matches seed. | `L02.01.01`; `EVD-02.01-01` |
| `EC-02.01.2` — INSERT and UPDATE with Scoped Keys | `PC-02.01.2` — Insert and update exactly one intended test customer, show RETURNING, and restore the starting row count. | `L02.01.02`; `EVD-02.01-01` |
| `EC-02.01.3` — Safe DELETE, Constraints and CRUD Verification | `PC-02.01.3` — Preview target keys and delete only a bounded disposable record; demonstrate rollback and describe FK protection. | `L02.01.03`; `EVD-02.01-01` |

### U-07. Scope and exclusions

DQL projection and basic CRUD; no normalization design (M03), full transaction internals (M06) or server RBAC (M12).

### U-08. Unit hour ledger

**270 minutes = 90 theory + 180 practical = 4h 30m**. Each of three lessons is **90m (30T/60P)**; no extra hour is assigned for assessments.

### U-09. Lesson sequence and dependencies

| Order | Lesson | Core task | Theory | Practical | Total |
|---|---|---|---:|---:|---:|
| 1 | `L02.01.01` | SELECT, Projection and First Predicates | 30m | 60m | 90m |
| 2 | `L02.01.02` | INSERT and UPDATE with Scoped Keys | 30m | 60m | 90m |
| 3 | `L02.01.03` | Safe DELETE, Constraints and CRUD Verification | 30m | 60m | 90m |
| **TOTAL** | | | **90m** | **180m** | **270m** |

### U-10. Detailed theoretical foundation

**SELECT, Projection and First Predicates:** A `SELECT` query returns a result set; it does not alter the stored rows. The projection list selects columns, while `FROM` identifies the relation(s) and `WHERE` decides which rows qualify. A SQL result has no guaranteed order unless an `ORDER BY` is present. `SELECT *` is convenient during discovery but couples a report to every table column; explicit columns make interfaces predictable. Rows in a result are not automatically unique: two different customers can share a city. Evaluate Boolean expressions carefully: `AND` binds more tightly than `OR`, so use parentheses to express the business decision. The product catalog and customer list belong to a sales administrator; start with a read-only view before issuing write commands.

**INSERT and UPDATE with Scoped Keys:** `INSERT` creates rows subject to constraints. Always name columns explicitly so a table-column reorder does not silently corrupt meaning. A row-changing `UPDATE` selects existing rows through `WHERE`; omitting that condition touches every row (unless prevented by other controls). Affected-row counts matter: `UPDATE 0` can indicate a nonexistent key even when SQL reports no error. PostgreSQL `RETURNING` exposes the changed rows and is useful for verification. The training exercise uses a transaction preview: `BEGIN`, change one disposable training row, inspect `RETURNING`, then `ROLLBACK` to restore the fixture; transaction semantics are fully examined in M06.

**Safe DELETE, Constraints and CRUD Verification:** `DELETE` removes rows; a predicate is mandatory for safe training practice. Deleting parents referenced by children can violate foreign-key integrity; a failed statement is useful evidence that data relationships are enforced. Preview exact target keys with SELECT and run changes inside a disposable transaction with ROLLBACK. SQL commands are not a replacement for business approval. In particular, a DELETE without WHERE is unscoped. Practice recovery by discarding a transaction; do not practice removing production rows. Distinguish a constraint error from `DELETE 0`, which succeeds without matching rows.

### U-11. Annotated unit worked example

Use the example from L02.01.01:

```sql
SELECT customer_code, customer_name, city
FROM training_m02.customer
WHERE status = 'ACTIVE'
ORDER BY customer_code;

SELECT product_name, list_price
FROM training_m02.product
WHERE active = TRUE AND list_price < 1000
ORDER BY list_price DESC, product_name;
```

**EXPECTED (NOT EXECUTED):** First query returns C001 Alpha Retail, C002 Beta Traders (2 rows). Second returns Keyboard 800, Mouse 400, Notebook 150 (3 rows); Sticker is inactive.

### U-12. Guided and independent application

- `L02.01.01` guided: Inspect all customer rows, run both examples, change the second predicate to `list_price >= 400`, and explain why `ORDER BY` is essential for deterministic presentation. Independent: Write a read-only query returning only active products under 500, ordered by SKU. Explain why an unsorted result must not be used as a positional API contract.
- `L02.01.02` guided: Run the transaction and copy the RETURNING lines. Query C004 after rollback; it must be absent. Independent: Within BEGIN/ROLLBACK, update Beta Traders by customer_id=2 to an alternate city, inspect row count, and confirm original value is restored. Record an `UPDATE 0` for an invalid ID.
- `L02.01.03` guided: Use a SELECT preview and rollback before/after count. Capture command output and explain why customer 1 is protected by order references. Independent: Prepare a safe DELETE for an ephemeral customer you created in the same transaction; demonstrate its `RETURNING` output. Never execute an unscoped deletion.


### U-13. Assessment, marking and remediation

**Assessment:** `ASM-02.01-01` (25 marks), completed within unit practical time. Allocate 15 marks to correctness against the three PCs (5 each), 5 to negative/edge-case handling and 5 to reproducible SQL/evidence/commentary. Any safety-critical failure overrides the percentage. Instructor provides targeted feedback and rechecks the failed PC against a new but equivalent sample input.

**Oral/written questions:** Which clause chooses columns, which removes rows, and which guarantees output order? Interpret `A OR B AND C` using parentheses. What is the difference between `UPDATE 0` and an error? Why include a predicate and RETURNING? Why is DELETE without WHERE prohibited? How do rollback and FK constraints protect different things?

### U-14. Evidence retention and acceptance

`EVD-02.01-01` must contain a `.sql` file and sanitized actual result tables/error observations, database identity/version, timestamp, and a short statement explaining how each `EC-02.01.1`–`EC-02.01.3` condition was shown. The expected results printed here are predictions, **not** execution evidence.

### U-15. Common failure modes and safe recovery

- Assuming implicit row order; using SELECT * as a stable report contract; misreading AND/OR precedence.
- Updating by nonunique name instead of stable ID; omitting a key predicate; forgetting to rollback the training modification.
- Deleting a parent with dependents; assuming DELETE 0 is a database fault; forgetting to log target IDs.
- If rows drift, restore ONLY the disposable training schema using guarded `01_schema.sql` then `02_seed.sql`. Use targeted `ROLLBACK` for preview edits. Never reset production data.

### U-16. Resources

Use `labs/01_schema.sql`, `02_seed.sql`, `03_verify.sql`, learner `04_assignment_starter.sql` and separate negative-case file as relevant. Unit-specific documentation links are included in its three lesson references. Instructor-only solution reference: `M02-INSTRUCTOR-KEY.md` (restricted; do not share in learner handout).

### U-17. Review status

**DRAFT / NOT APPROVED**: outcome and timing arithmetic authored, PostgreSQL scripts **not executed**; technical evidence, independent instructional check, editorial/accessibility review and approved-register unit ID validation pending.

---

## U02.02 — Filtering, NULL and Scalar Expressions

### U-01. Identity and metadata

**Owning module:** M02. **Version:** v0.1 / 10 October 2026. **Author/reviewer:** Curriculum team (name pending) / appointed reviewers pending. **Status:** DRAFT, SQL NOT EXECUTED, IDs PROVISIONAL. **Platform:** PostgreSQL 16.x with seed dataset from lab scripts.

### U-02. Purpose and workplace task

Produce stable filtered catalog/customer views, explicitly handle unknown values and calculate display expressions.

### U-03. Preconditions

Complete relevant preceding lesson(s); have `erp_m02_lab` connected, seed script loaded, a local SQL editor and permission to read training schema. Students must know the sample row counts and practice `SELECT` before any scoped DML.

### U-04. Unit learning outcomes / MLO traceability

| ULO | Observable outcome | MLO | Direct evidence |
|---|---|---|---|
| `ULO-02.02.1` | Return a correctly filtered, distinctly projected and deterministically paginated result with tie-breaker. | `MLO-02.1` | `EVD-02.02-01` and lesson output |
| `ULO-02.02.2` | Use IS NULL, CASE and COALESCE correctly; find exactly two missing-email customers without changing stored NULLs. | `MLO-02.3` | `EVD-02.02-01` and lesson output |
| `ULO-02.02.3` | Compute accurate numeric/text/date expressions with documented interpretation and no catalog mutation. | `MLO-02.3` | `EVD-02.02-01` and lesson output |

### U-05–U-06. Elements of Competency / Performance Criteria

These are **internal educational elements**, not formal NTVQF Units of Competency. Each element has an observable performance criterion and an evidence target.

| Element | PC (assessable pass threshold) | Evidence / lesson |
|---|---|---|
| `EC-02.02.1` — WHERE, DISTINCT, ORDER BY and Pagination | `PC-02.02.1` — Return a correctly filtered, distinctly projected and deterministically paginated result with tie-breaker. | `L02.02.01`; `EVD-02.02-01` |
| `EC-02.02.2` — NULL, Three-Valued Logic, CASE and COALESCE | `PC-02.02.2` — Use IS NULL, CASE and COALESCE correctly; find exactly two missing-email customers without changing stored NULLs. | `L02.02.02`; `EVD-02.02-01` |
| `EC-02.02.3` — Numeric, Text and Date Expressions | `PC-02.02.3` — Compute accurate numeric/text/date expressions with documented interpretation and no catalog mutation. | `L02.02.03`; `EVD-02.02-01` |

### U-07. Scope and exclusions

SELECT filtering and scalar expressions only; window analytics and keyset pagination are M04.

### U-08. Unit hour ledger

**270 minutes = 90 theory + 180 practical = 4h 30m**. Each of three lessons is **90m (30T/60P)**; no extra hour is assigned for assessments.

### U-09. Lesson sequence and dependencies

| Order | Lesson | Core task | Theory | Practical | Total |
|---|---|---|---:|---:|---:|
| 1 | `L02.02.01` | WHERE, DISTINCT, ORDER BY and Pagination | 30m | 60m | 90m |
| 2 | `L02.02.02` | NULL, Three-Valued Logic, CASE and COALESCE | 30m | 60m | 90m |
| 3 | `L02.02.03` | Numeric, Text and Date Expressions | 30m | 60m | 90m |
| **TOTAL** | | | **90m** | **180m** | **270m** |

### U-10. Detailed theoretical foundation

**WHERE, DISTINCT, ORDER BY and Pagination:** Filtering changes the membership of the result. `LIKE` supports simple patterns; `BETWEEN` includes its endpoints for non-NULL values; `IN` tests membership. `DISTINCT` removes duplicates only across the full projection, so `DISTINCT city` is not equivalent to `DISTINCT customer_code, city`. `ORDER BY` establishes presentation sequence. `LIMIT` reduces rows and `OFFSET` skips earlier ordered rows, but paging without a unique tie-breaker may return unstable pages, and new writes between requests can shift offsets. More advanced keyset pagination belongs in M04.

**NULL, Three-Valued Logic, CASE and COALESCE:** SQL `NULL` indicates missing/unknown, not an empty string or zero. Ordinary comparisons to NULL evaluate to UNKNOWN, so `email = NULL` is never a correct way to select missing emails. Use `IS NULL` or `IS NOT NULL`. A `WHERE` retains only rows where its expression is TRUE, not FALSE or UNKNOWN. `COALESCE` chooses the first non-NULL argument; it is appropriate for display fallback but may hide missing source information. `CASE` selects an expression based on ordered conditions; use it to label states without changing stored values. Avoid substituting zero for unknown money unless the business rule explicitly allows it.

**Numeric, Text and Date Expressions:** Built-in scalar functions transform values within query results. Numeric `ROUND` requires considering scale and rounding policy; money examples should use NUMERIC, not floating point display approximations. Text `LOWER`, `UPPER`, `TRIM`, `CHAR_LENGTH` help clean labels for reports without overwriting original strings. PostgreSQL can add integers to DATE values and use EXTRACT to derive calendar parts. Arithmetic involving NULL usually yields NULL, so treat missing operands explicitly. Date/time handling should distinguish DATE from TIMESTAMPTZ; timezone-heavy reporting is beyond M02.

### U-11. Annotated unit worked example

Use the example from L02.02.01:

```sql
SELECT DISTINCT city FROM training_m02.customer ORDER BY city;
SELECT customer_code, customer_name
FROM training_m02.customer
WHERE city IN ('Dhaka', 'Khulna') AND status = 'ACTIVE'
ORDER BY customer_code LIMIT 2 OFFSET 0;
SELECT product_id, product_name, list_price
FROM training_m02.product
WHERE list_price BETWEEN 150 AND 800
ORDER BY list_price DESC, product_id
LIMIT 2 OFFSET 1;
```

**EXPECTED (NOT EXECUTED):** Distinct cities: Chattogram, Dhaka (2). Active customers in chosen cities: C001 (1). Last query: Mouse 400 then Notebook 150 (2), given prices 800,400,150 before offset.

### U-12. Guided and independent application

- `L02.02.01` guided: Run all filters, predict outputs before execution, and compare ordered full result with paged result. Independent: Find product names containing `o` case-insensitively using ILIKE (PostgreSQL-specific); return 2nd page of 2 products sorted by product_id, after filtering only active products.
- `L02.02.02` guided: Test `email IS NULL`, `email IS NOT NULL` and `email = NULL` separately; record why third query finds no rows. Independent: Use searched CASE to display Premium when list_price >=1000, Standard when >=100, and Budget otherwise; explain branch order and boundary conditions.
- `L02.02.03` guided: Run expression examples; compare original columns and displayed transformed values. Verify all monetary output remains NUMERIC scale 2. Independent: Write a SKU/name display expression using CONCAT or `||`; calculate 10% discount preview with ROUND without updating catalog prices.


### U-13. Assessment, marking and remediation

**Assessment:** `ASM-02.02-01` (25 marks), completed within unit practical time. Allocate 15 marks to correctness against the three PCs (5 each), 5 to negative/edge-case handling and 5 to reproducible SQL/evidence/commentary. Any safety-critical failure overrides the percentage. Instructor provides targeted feedback and rechecks the failed PC against a new but equivalent sample input.

**Oral/written questions:** What makes OFFSET paging nondeterministic? What column can break ties? Contrast DISTINCT and GROUP BY. Why does email = NULL not find C002? Does COALESCE write default values to the database? Do scalar functions affect stored values? Why use NUMERIC for monetary demonstrations? What is the follow-up date for 1003?

### U-14. Evidence retention and acceptance

`EVD-02.02-01` must contain a `.sql` file and sanitized actual result tables/error observations, database identity/version, timestamp, and a short statement explaining how each `EC-02.02.1`–`EC-02.02.3` condition was shown. The expected results printed here are predictions, **not** execution evidence.

### U-15. Common failure modes and safe recovery

- Putting ORDER BY after LIMIT; forgetting tie-breaker; assuming DISTINCT considers only the first selected column.
- Treating NULL as empty string; trusting `= NULL`; using COALESCE to silently change meaning of missing values.
- Rounding too early in a sum; treating calculated display as stored amount; mixing DATE and timestamp assumptions.
- If rows drift, restore ONLY the disposable training schema using guarded `01_schema.sql` then `02_seed.sql`. Use targeted `ROLLBACK` for preview edits. Never reset production data.

### U-16. Resources

Use `labs/01_schema.sql`, `02_seed.sql`, `03_verify.sql`, learner `04_assignment_starter.sql` and separate negative-case file as relevant. Unit-specific documentation links are included in its three lesson references. Instructor-only solution reference: `M02-INSTRUCTOR-KEY.md` (restricted; do not share in learner handout).

### U-17. Review status

**DRAFT / NOT APPROVED**: outcome and timing arithmetic authored, PostgreSQL scripts **not executed**; technical evidence, independent instructional check, editorial/accessibility review and approved-register unit ID validation pending.

---

## U02.03 — Joins and Grouped Reporting

### U-01. Identity and metadata

**Owning module:** M02. **Version:** v0.1 / 10 October 2026. **Author/reviewer:** Curriculum team (name pending) / appointed reviewers pending. **Status:** DRAFT, SQL NOT EXECUTED, IDs PROVISIONAL. **Platform:** PostgreSQL 16.x with seed dataset from lab scripts.

### U-02. Purpose and workplace task

Produce operational sales reports that retain missing master records, correctly join relations and reconcile paid totals.

### U-03. Preconditions

Complete relevant preceding lesson(s); have `erp_m02_lab` connected, seed script loaded, a local SQL editor and permission to read training schema. Students must know the sample row counts and practice `SELECT` before any scoped DML.

### U-04. Unit learning outcomes / MLO traceability

| ULO | Observable outcome | MLO | Direct evidence |
|---|---|---|---|
| `ULO-02.03.1` | Join keys correctly; produce four order headers and order 1001 two lines totaling 700.00. | `MLO-02.4` | `EVD-02.03-01` and lesson output |
| `ULO-02.03.2` | Preserve all three customers under LEFT JOIN with paid counts 1,1,0. | `MLO-02.4` | `EVD-02.03-01` and lesson output |
| `ULO-02.03.3` | Produce paid only aggregate 13500.00 and distinguish WHERE versus HAVING with matching evidence. | `MLO-02.4` | `EVD-02.03-01` and lesson output |

### U-05–U-06. Elements of Competency / Performance Criteria

These are **internal educational elements**, not formal NTVQF Units of Competency. Each element has an observable performance criterion and an evidence target.

| Element | PC (assessable pass threshold) | Evidence / lesson |
|---|---|---|
| `EC-02.03.1` — INNER JOIN and Related Data | `PC-02.03.1` — Join keys correctly; produce four order headers and order 1001 two lines totaling 700.00. | `L02.03.01`; `EVD-02.03-01` |
| `EC-02.03.2` — LEFT JOIN and Missing-Row Reporting | `PC-02.03.2` — Preserve all three customers under LEFT JOIN with paid counts 1,1,0. | `L02.03.02`; `EVD-02.03-01` |
| `EC-02.03.3` — GROUP BY, HAVING and Sales Totals | `PC-02.03.3` — Produce paid only aggregate 13500.00 and distinguish WHERE versus HAVING with matching evidence. | `L02.03.03`; `EVD-02.03-01` |

### U-07. Scope and exclusions

Ordinary equijoins, LEFT joins, GROUP BY and HAVING; multi-table performance tuning is M10.

### U-08. Unit hour ledger

**270 minutes = 90 theory + 180 practical = 4h 30m**. Each of three lessons is **90m (30T/60P)**; no extra hour is assigned for assessments.

### U-09. Lesson sequence and dependencies

| Order | Lesson | Core task | Theory | Practical | Total |
|---|---|---|---:|---:|---:|
| 1 | `L02.03.01` | INNER JOIN and Related Data | 30m | 60m | 90m |
| 2 | `L02.03.02` | LEFT JOIN and Missing-Row Reporting | 30m | 60m | 90m |
| 3 | `L02.03.03` | GROUP BY, HAVING and Sales Totals | 30m | 60m | 90m |
| **TOTAL** | | | **90m** | **180m** | **270m** |

### U-10. Detailed theoretical foundation

**INNER JOIN and Related Data:** A join combines rows through an explicit relationship. A sales order refers to one customer using customer_id, and each order item refers to an order and a product. Always specify key-based ON predicates rather than cross-joining by mistake. One order may have multiple order_item rows, so joining orders to items changes row cardinality; a row per order is no longer guaranteed. Use meaningful table aliases, qualify ambiguous column names and preserve item unit_price as historical transaction price, not current product list_price.

**LEFT JOIN and Missing-Row Reporting:** An inner join omits a left-side row with no match. A LEFT JOIN preserves all left-side rows and supplies NULL values for unmatched right-side columns. Business reports such as a complete customer directory should retain customers without sales; a careless `WHERE o.status='PAID'` after LEFT JOIN removes the unmatched NULL rows and effectively changes the outcome. Put right-table restrictions in the ON condition if you intend to keep the unmatched left-side entities. `COUNT(o.order_id)` reports zero for unmatched customers, while COUNT(*) counts the null-extended row as one. Use this distinction deliberately.

**GROUP BY, HAVING and Sales Totals:** Aggregates summarize sets of rows: COUNT, SUM, AVG, MIN and MAX. `GROUP BY` makes one output row per distinct group. A grouped SELECT can contain grouping columns or aggregate expressions, subject to PostgreSQL rules. `WHERE` filters input rows before grouping; `HAVING` filters groups afterward. Financially meaningful sales reporting needs an explicit recognized-status rule. Here only `PAID` counts as paid sales; `PENDING` and `CANCELLED` are excluded. Avoid multiplying totals by joining unrelated one-to-many tables. Use line-level unit_price captured on the order item and a NUMERIC multiplication.

### U-11. Annotated unit worked example

Use the example from L02.03.01:

```sql
SELECT o.order_id, c.customer_name, o.order_status
FROM training_m02.sales_order AS o
JOIN training_m02.customer AS c ON c.customer_id=o.customer_id
ORDER BY o.order_id;
SELECT o.order_id, p.product_name, oi.qty, oi.unit_price,
       oi.qty * oi.unit_price AS line_total
FROM training_m02.sales_order AS o
JOIN training_m02.order_item AS oi ON oi.order_id=o.order_id
JOIN training_m02.product AS p ON p.product_id=oi.product_id
WHERE o.order_id=1001
ORDER BY oi.order_item_id;
```

**EXPECTED (NOT EXECUTED):** First query returns 4 orders with Alpha Retail on 1001/1002, Beta Traders on 1003/1004. Second returns Notebook 300.00 and Mouse 400.00; order 1001 total 700.00.

### U-12. Guided and independent application

- `L02.03.01` guided: Draw one-to-many arrows, run joins in steps, compare row counts before and after the order_item join. Independent: List all PAID order lines with customer, product, quantity and line total sorted by order_id, order_item_id; predict 4 rows.
- `L02.03.02` guided: Run ON-filter example, then relocate order_status condition into WHERE and observe missing customer. Compare COUNT(*) vs COUNT(order_id). Independent: List every product and any order_item match, including unsold Sticker. Select explicit columns and order by product_id, order_item_id.
- `L02.03.03` guided: Recalculate totals manually from line rows; execute the queries; check 700+12800=13500. Use a WHERE vs HAVING experiment. Independent: Produce per-status order counts and amounts (including pending/cancelled clearly labeled as not paid), then produce a paid-only customer summary.


### U-13. Assessment, marking and remediation

**Assessment:** `ASM-02.03-01` (25 marks), completed within unit practical time. Allocate 15 marks to correctness against the three PCs (5 each), 5 to negative/edge-case handling and 5 to reproducible SQL/evidence/commentary. Any safety-critical failure overrides the percentage. Instructor provides targeted feedback and rechecks the failed PC against a new but equivalent sample input.

**Oral/written questions:** Why can an order appear twice after joining its lines? Which unit_price belongs in historical sales reporting? Where must a right-side status filter go to preserve customers with no orders? Why does COUNT(*) return 1 for unmatched left row? Which clause filters groups? What happens to a sum when duplicate rows arise from a bad join?

### U-14. Evidence retention and acceptance

`EVD-02.03-01` must contain a `.sql` file and sanitized actual result tables/error observations, database identity/version, timestamp, and a short statement explaining how each `EC-02.03.1`–`EC-02.03.3` condition was shown. The expected results printed here are predictions, **not** execution evidence.

### U-15. Common failure modes and safe recovery

- Missing ON clause causing cross product; joining on display names; using current price instead of sale price.
- Treating LEFT JOIN as INNER JOIN; counting * instead of a nullable matched key; placing right-side filter in WHERE.
- Using HAVING for simple row filters; accidentally counting cancelled orders as revenue; COUNT(*) after outer join.
- If rows drift, restore ONLY the disposable training schema using guarded `01_schema.sql` then `02_seed.sql`. Use targeted `ROLLBACK` for preview edits. Never reset production data.

### U-16. Resources

Use `labs/01_schema.sql`, `02_seed.sql`, `03_verify.sql`, learner `04_assignment_starter.sql` and separate negative-case file as relevant. Unit-specific documentation links are included in its three lesson references. Instructor-only solution reference: `M02-INSTRUCTOR-KEY.md` (restricted; do not share in learner handout).

### U-17. Review status

**DRAFT / NOT APPROVED**: outcome and timing arithmetic authored, PostgreSQL scripts **not executed**; technical evidence, independent instructional check, editorial/accessibility review and approved-register unit ID validation pending.

---

## U02.04 — Subqueries, Set Operations and Parameterization

### U-01. Identity and metadata

**Owning module:** M02. **Version:** v0.1 / 10 October 2026. **Author/reviewer:** Curriculum team (name pending) / appointed reviewers pending. **Status:** DRAFT, SQL NOT EXECUTED, IDs PROVISIONAL. **Platform:** PostgreSQL 16.x with seed dataset from lab scripts.

### U-02. Purpose and workplace task

Answer existence and set-membership questions and implement safe externally supplied SQL values.

### U-03. Preconditions

Complete relevant preceding lesson(s); have `erp_m02_lab` connected, seed script loaded, a local SQL editor and permission to read training schema. Students must know the sample row counts and practice `SELECT` before any scoped DML.

### U-04. Unit learning outcomes / MLO traceability

| ULO | Observable outcome | MLO | Direct evidence |
|---|---|---|---|
| `ULO-02.04.1` | Use EXISTS/IN and NOT EXISTS to identify two paid customers and unsold product 105; explain NOT IN/NULL. | `MLO-02.3` | `EVD-02.04-01` and lesson output |
| `ULO-02.04.2` | Produce accurate UNION (3), INTERSECT (1), EXCEPT (1) city results using compatible projections. | `MLO-02.5` | `EVD-02.04-01` and lesson output |
| `ULO-02.04.3` | Demonstrate actual bound-value SQL with PREPARE or JDBC and submit complete, safe, annotated final workbook. | `MLO-02.5` | `EVD-02.04-01` and lesson output |

### U-05–U-06. Elements of Competency / Performance Criteria

These are **internal educational elements**, not formal NTVQF Units of Competency. Each element has an observable performance criterion and an evidence target.

| Element | PC (assessable pass threshold) | Evidence / lesson |
|---|---|---|
| `EC-02.04.1` — IN, EXISTS and Subqueries | `PC-02.04.1` — Use EXISTS/IN and NOT EXISTS to identify two paid customers and unsold product 105; explain NOT IN/NULL. | `L02.04.01`; `EVD-02.04-01` |
| `EC-02.04.2` — UNION, INTERSECT and EXCEPT | `PC-02.04.2` — Produce accurate UNION (3), INTERSECT (1), EXCEPT (1) city results using compatible projections. | `L02.04.02`; `EVD-02.04-01` |
| `EC-02.04.3` — Parameterized SQL and Integrated Workbook | `PC-02.04.3` — Demonstrate actual bound-value SQL with PREPARE or JDBC and submit complete, safe, annotated final workbook. | `L02.04.03`; `EVD-02.04-01` |

### U-07. Scope and exclusions

Basic subqueries, set operators and parameterized input; no stored procedures (M05), advanced query plans (M10) or application-service implementation (M15).

### U-08. Unit hour ledger

**270 minutes = 90 theory + 180 practical = 4h 30m**. Each of three lessons is **90m (30T/60P)**; no extra hour is assigned for assessments.

### U-09. Lesson sequence and dependencies

| Order | Lesson | Core task | Theory | Practical | Total |
|---|---|---|---:|---:|---:|
| 1 | `L02.04.01` | IN, EXISTS and Subqueries | 30m | 60m | 90m |
| 2 | `L02.04.02` | UNION, INTERSECT and EXCEPT | 30m | 60m | 90m |
| 3 | `L02.04.03` | Parameterized SQL and Integrated Workbook | 30m | 60m | 90m |
| **TOTAL** | | | **90m** | **180m** | **270m** |

### U-10. Detailed theoretical foundation

**IN, EXISTS and Subqueries:** A subquery is a query nested inside another SQL statement. `IN` compares a value with members of a set; `EXISTS` checks whether a correlated subquery returns any row. Correlation means the inner query refers to a value from the outer query; for each candidate, the logical test asks whether a qualifying match exists. Do not assume physical evaluation order. `NOT EXISTS` is reliable for no-match cases. `NOT IN` can surprise learners when the subquery includes NULL, because comparisons become UNKNOWN rather than TRUE; prefer NOT EXISTS for anti-matches unless null semantics are proven.

**UNION, INTERSECT and EXCEPT:** Set operators combine compatible query outputs: `UNION` returns distinct combined rows, `INTERSECT` returns rows common to both inputs, and `EXCEPT` removes rows found in the right input from the left. `UNION ALL` retains duplicates, often important for append-only lists; ordinary UNION removes them. Inputs require the same number of columns and compatible types, and a final ORDER BY must follow the combined query. The relative direction of EXCEPT matters. Use customer and supplier cities to tell a meaningful master-data story.

**Parameterized SQL and Integrated Workbook:** User-supplied input must be passed as a bound parameter, never concatenated into SQL source text. PostgreSQL server-side `PREPARE` supports positional `$1` parameters for teaching; application code typically uses JDBC `?` or its driver binding API. A parameter is data, not part of SQL syntax; the server can distinguish the two. Query structure, identifiers and sort directions generally cannot be supplied as ordinary value parameters; those require fixed allowlisted choices if dynamic construction is unavoidable. Perform a final customer/order workbook with a bound customer_code, a safe scoped mutation preview, a JOIN report, an aggregate and negative tests on disposable data.

### U-11. Annotated unit worked example

Use the example from L02.04.01:

```sql
SELECT customer_code, customer_name
FROM training_m02.customer AS c
WHERE EXISTS (
  SELECT 1 FROM training_m02.sales_order AS o
  WHERE o.customer_id=c.customer_id AND o.order_status='PAID'
) ORDER BY customer_code;
SELECT product_id, product_name
FROM training_m02.product AS p
WHERE NOT EXISTS (
  SELECT 1 FROM training_m02.order_item AS oi
  WHERE oi.product_id=p.product_id
) ORDER BY product_id;
```

**EXPECTED (NOT EXECUTED):** Customers with PAID orders: C001 and C002. Never-sold product: P-STICK Sticker (product 105). Expected, not executed.

### U-12. Guided and independent application

- `L02.04.01` guided: Rewrite the first query with `IN (SELECT customer_id ...)`; compare result sets. Use NOT EXISTS for unsold products. Independent: Find customers with NO orders of any status. Explain why a LEFT JOIN/IS NULL rewrite requires care around match predicates.
- `L02.04.02` guided: Run each operator, compare UNION to UNION ALL row counts, and explain why repeated Dhaka values do not appear twice under UNION. Independent: Find supplier cities with no customer using supplier EXCEPT customer; interpret why changing side changes the answer.
- `L02.04.03` guided: Run PREPARE/EXECUTE and discuss why an input containing a quote remains a string value with parameter binding, not executable SQL. Independent: Complete 04_assignment_starter.sql and submit result evidence, bounded CRUD preview, supplier/product join, paid-total proof and input-binding explanation.


### U-13. Assessment, marking and remediation

**Assessment:** `ASM-02.04-01` (25 marks), completed within unit practical time. Allocate 15 marks to correctness against the three PCs (5 each), 5 to negative/edge-case handling and 5 to reproducible SQL/evidence/commentary. Any safety-critical failure overrides the percentage. Instructor provides targeted feedback and rechecks the failed PC against a new but equivalent sample input.

**Oral/written questions:** Why can NOT IN behave strangely if an inner expression is NULL? When does EXISTS disregard selected columns? What is the role of ALL? Why must column types be compatible? Does EXCEPT have direction? Show safe and unsafe examples conceptually: which uses values rather than concatenation? What does a parameter NOT allow dynamically?

### U-14. Evidence retention and acceptance

`EVD-02.04-01` must contain a `.sql` file and sanitized actual result tables/error observations, database identity/version, timestamp, and a short statement explaining how each `EC-02.04.1`–`EC-02.04.3` condition was shown. The expected results printed here are predictions, **not** execution evidence.

### U-15. Common failure modes and safe recovery

- Assuming NOT IN and NOT EXISTS are always interchangeable; selecting join columns from the wrong level; forgetting correlation.
- Confusing JOIN with set operation; ordering one input instead of final output; assuming EXCEPT symmetric.
- Escaping by ad-hoc string replacement; concatenating external input into WHERE; trying to parameterize table identifiers as values.
- If rows drift, restore ONLY the disposable training schema using guarded `01_schema.sql` then `02_seed.sql`. Use targeted `ROLLBACK` for preview edits. Never reset production data.

### U-16. Resources

Use `labs/01_schema.sql`, `02_seed.sql`, `03_verify.sql`, learner `04_assignment_starter.sql` and separate negative-case file as relevant. Unit-specific documentation links are included in its three lesson references. Instructor-only solution reference: `M02-INSTRUCTOR-KEY.md` (restricted; do not share in learner handout).

### U-17. Review status

**DRAFT / NOT APPROVED**: outcome and timing arithmetic authored, PostgreSQL scripts **not executed**; technical evidence, independent instructional check, editorial/accessibility review and approved-register unit ID validation pending.

---

# Part III — Complete timed learner lessons (L-01 to L-18 each)

## L02.01.01 — SELECT, Projection and First Predicates

### L-01. Identity

**Lesson:** `L02.01.01`, unit `U02.01` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.01` hour allocation.

### L-03. Prerequisites

Complete `M01.02.03 (M01 prerequisite)`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.01.01.1` → `ULO-02.01.1` and `PC-02.01.1`: Select required columns and rows with an explicit, reproducible order; projected result matches seed.
- `LLO-02.01.01.2` → `ULO-02.01.1` and `PC-02.01.1`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

A `SELECT` query returns a result set; it does not alter the stored rows. The projection list selects columns, while `FROM` identifies the relation(s) and `WHERE` decides which rows qualify. A SQL result has no guaranteed order unless an `ORDER BY` is present. `SELECT *` is convenient during discovery but couples a report to every table column; explicit columns make interfaces predictable. Rows in a result are not automatically unique: two different customers can share a city. Evaluate Boolean expressions carefully: `AND` binds more tightly than `OR`, so use parentheses to express the business decision. The product catalog and customer list belong to a sales administrator; start with a read-only view before issuing write commands.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

A `SELECT` query returns a result set; it does not alter the stored rows. The projection list selects columns, while `FROM` identifies the relation(s) and `WHERE` decides which rows qualify. A SQL result has no guaranteed order unless an `ORDER BY` is present. `SELECT *` is convenient during discovery but couples a report to every table column; explicit columns make interfaces predictable. Rows in a result are not automatically unique: two different customers can share a city. Evaluate Boolean expressions carefully: `AND` binds more tightly than `OR`, so use parentheses to express the business decision. The product catalog and customer list belong to a sales administrator; start with a read-only view before issuing write commands.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.01.01-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT customer_code, customer_name, city
FROM training_m02.customer
WHERE status = 'ACTIVE'
ORDER BY customer_code;

SELECT product_name, list_price
FROM training_m02.product
WHERE active = TRUE AND list_price < 1000
ORDER BY list_price DESC, product_name;
```

**Interpretation and expected observations:** First query returns C001 Alpha Retail, C002 Beta Traders (2 rows). Second returns Keyboard 800, Mouse 400, Notebook 150 (3 rows); Sticker is inactive.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.01.01-01`. Inspect all customer rows, run both examples, change the second predicate to `list_price >= 400`, and explain why `ORDER BY` is essential for deterministic presentation.

**Independent task:** Write a read-only query returning only active products under 500, ordered by SKU. Explain why an unsorted result must not be used as a positional API contract.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Which clause chooses columns, which removes rows, and which guarantees output order? Interpret `A OR B AND C` using parentheses.

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.01.01-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.01.1`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** First query returns C001 Alpha Retail, C002 Beta Traders (2 rows). Second returns Keyboard 800, Mouse 400, Notebook 150 (3 rows); Sticker is inactive.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Assuming implicit row order
- using SELECT * as a stable report contract
- misreading AND/OR precedence.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

No writes needed. If schema missing, rerun lab setup on `erp_m02_lab` only; confirm database before any setup reset.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Draw three labeled boxes: projection, filter and order, and place SELECT, WHERE and ORDER BY into them.

**Extension:** Use an explicit alias and compute a derived `list_price * 2` display column without changing data.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL 16 `SELECT` reference: https://www.postgresql.org/docs/16/sql-select.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.01.01.md`. This lesson feeds directly into `L02.01.02`. Feedback must mark `PC-02.01.1` achieved or revision-required. **Reviewer approval pending.**

---

## L02.01.02 — INSERT and UPDATE with Scoped Keys

### L-01. Identity

**Lesson:** `L02.01.02`, unit `U02.01` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.01` hour allocation.

### L-03. Prerequisites

Complete `L02.01.01`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.01.02.1` → `ULO-02.01.2` and `PC-02.01.2`: Insert and update exactly one intended test customer, show RETURNING, and restore the starting row count.
- `LLO-02.01.02.2` → `ULO-02.01.2` and `PC-02.01.2`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

`INSERT` creates rows subject to constraints. Always name columns explicitly so a table-column reorder does not silently corrupt meaning. A row-changing `UPDATE` selects existing rows through `WHERE`; omitting that condition touches every row (unless prevented by other controls). Affected-row counts matter: `UPDATE 0` can indicate a nonexistent key even when SQL reports no error. PostgreSQL `RETURNING` exposes the changed rows and is useful for verification. The training exercise uses a transaction preview: `BEGIN`, change one disposable training row, inspect `RETURNING`, then `ROLLBACK` to restore the fixture; transaction semantics are fully examined in M06.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

`INSERT` creates rows subject to constraints. Always name columns explicitly so a table-column reorder does not silently corrupt meaning. A row-changing `UPDATE` selects existing rows through `WHERE`; omitting that condition touches every row (unless prevented by other controls). Affected-row counts matter: `UPDATE 0` can indicate a nonexistent key even when SQL reports no error. PostgreSQL `RETURNING` exposes the changed rows and is useful for verification. The training exercise uses a transaction preview: `BEGIN`, change one disposable training row, inspect `RETURNING`, then `ROLLBACK` to restore the fixture; transaction semantics are fully examined in M06.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.01.02-01`. **Expected only (NOT EXECUTED):**

```sql
BEGIN;
INSERT INTO training_m02.customer
  (customer_id, customer_code, customer_name, city, email, status)
VALUES (4, 'C004', 'Demo Store', 'Dhaka', NULL, 'ACTIVE')
RETURNING customer_code, status;
UPDATE training_m02.customer
SET city = 'Sylhet'
WHERE customer_id = 4
RETURNING customer_code, city;
ROLLBACK;
SELECT count(*) FROM training_m02.customer;
```

**Interpretation and expected observations:** Inserted row C004, then updated city Sylhet, then `ROLLBACK` leaves customer count 3. SQL has NOT been executed in authoring.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.01.02-01`. Run the transaction and copy the RETURNING lines. Query C004 after rollback; it must be absent.

**Independent task:** Within BEGIN/ROLLBACK, update Beta Traders by customer_id=2 to an alternate city, inspect row count, and confirm original value is restored. Record an `UPDATE 0` for an invalid ID.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

What is the difference between `UPDATE 0` and an error? Why include a predicate and RETURNING?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.01.02-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.01.2`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Inserted row C004, then updated city Sylhet, then `ROLLBACK` leaves customer count 3. SQL has NOT been executed in authoring.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Updating by nonunique name instead of stable ID
- omitting a key predicate
- forgetting to rollback the training modification.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Run on disposable DB only; reset fixture using 01_schema and 02_seed if necessary. Do not use training patterns in production.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Write SELECT first using the same WHERE predicate to preview targets.

**Extension:** Insert and update using a `RETURNING` projection of changed keys and statuses; explain why only one target is expected.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL 16 INSERT/UPDATE docs: https://www.postgresql.org/docs/16/sql-insert.html and https://www.postgresql.org/docs/16/sql-update.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.01.02.md`. This lesson feeds directly into `L02.01.03`. Feedback must mark `PC-02.01.2` achieved or revision-required. **Reviewer approval pending.**

---

## L02.01.03 — Safe DELETE, Constraints and CRUD Verification

### L-01. Identity

**Lesson:** `L02.01.03`, unit `U02.01` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.01` hour allocation.

### L-03. Prerequisites

Complete `L02.01.02`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.01.03.1` → `ULO-02.01.3` and `PC-02.01.3`: Preview target keys and delete only a bounded disposable record; demonstrate rollback and describe FK protection.
- `LLO-02.01.03.2` → `ULO-02.01.3` and `PC-02.01.3`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

`DELETE` removes rows; a predicate is mandatory for safe training practice. Deleting parents referenced by children can violate foreign-key integrity; a failed statement is useful evidence that data relationships are enforced. Preview exact target keys with SELECT and run changes inside a disposable transaction with ROLLBACK. SQL commands are not a replacement for business approval. In particular, a DELETE without WHERE is unscoped. Practice recovery by discarding a transaction; do not practice removing production rows. Distinguish a constraint error from `DELETE 0`, which succeeds without matching rows.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

`DELETE` removes rows; a predicate is mandatory for safe training practice. Deleting parents referenced by children can violate foreign-key integrity; a failed statement is useful evidence that data relationships are enforced. Preview exact target keys with SELECT and run changes inside a disposable transaction with ROLLBACK. SQL commands are not a replacement for business approval. In particular, a DELETE without WHERE is unscoped. Practice recovery by discarding a transaction; do not practice removing production rows. Distinguish a constraint error from `DELETE 0`, which succeeds without matching rows.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.01.03-01`. **Expected only (NOT EXECUTED):**

```sql
BEGIN;
SELECT customer_id, customer_code
FROM training_m02.customer WHERE customer_id = 3;
DELETE FROM training_m02.customer
WHERE customer_id = 3
RETURNING customer_id;
ROLLBACK;
SELECT count(*) FROM training_m02.customer;
-- Separately: attempting to delete customer 1 should fail because orders reference it.

```

**Interpretation and expected observations:** Preview C003, temporary deletion of one unreferenced customer, post-rollback customer count 3. Attempting referenced customer 1 raises a foreign-key violation (if attempted separately); exact error text varies.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.01.03-01`. Use a SELECT preview and rollback before/after count. Capture command output and explain why customer 1 is protected by order references.

**Independent task:** Prepare a safe DELETE for an ephemeral customer you created in the same transaction; demonstrate its `RETURNING` output. Never execute an unscoped deletion.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Why is DELETE without WHERE prohibited? How do rollback and FK constraints protect different things?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.01.03-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.01.3`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Preview C003, temporary deletion of one unreferenced customer, post-rollback customer count 3. Attempting referenced customer 1 raises a foreign-key violation (if attempted separately); exact error text varies.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Deleting a parent with dependents
- assuming DELETE 0 is a database fault
- forgetting to log target IDs.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Use transactions only in the isolated training database; ROLLBACK is the recovery path. To fully reset, rerun guarded 01_schema and seed.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Before a DELETE, run `SELECT ... WHERE customer_id=...` and inspect the count.

**Extension:** Explain the business difference between hard deletion and status deactivation without implementing a new retention policy.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL 16 DELETE and FK references: https://www.postgresql.org/docs/16/sql-delete.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.01.03.md`. This lesson feeds directly into `L02.02.01`. Feedback must mark `PC-02.01.3` achieved or revision-required. **Reviewer approval pending.**

---

## L02.02.01 — WHERE, DISTINCT, ORDER BY and Pagination

### L-01. Identity

**Lesson:** `L02.02.01`, unit `U02.02` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.02` hour allocation.

### L-03. Prerequisites

Complete `L02.01.03`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.02.01.1` → `ULO-02.02.1` and `PC-02.02.1`: Return a correctly filtered, distinctly projected and deterministically paginated result with tie-breaker.
- `LLO-02.02.01.2` → `ULO-02.02.1` and `PC-02.02.1`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

Filtering changes the membership of the result. `LIKE` supports simple patterns; `BETWEEN` includes its endpoints for non-NULL values; `IN` tests membership. `DISTINCT` removes duplicates only across the full projection, so `DISTINCT city` is not equivalent to `DISTINCT customer_code, city`. `ORDER BY` establishes presentation sequence. `LIMIT` reduces rows and `OFFSET` skips earlier ordered rows, but paging without a unique tie-breaker may return unstable pages, and new writes between requests can shift offsets. More advanced keyset pagination belongs in M04.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

Filtering changes the membership of the result. `LIKE` supports simple patterns; `BETWEEN` includes its endpoints for non-NULL values; `IN` tests membership. `DISTINCT` removes duplicates only across the full projection, so `DISTINCT city` is not equivalent to `DISTINCT customer_code, city`. `ORDER BY` establishes presentation sequence. `LIMIT` reduces rows and `OFFSET` skips earlier ordered rows, but paging without a unique tie-breaker may return unstable pages, and new writes between requests can shift offsets. More advanced keyset pagination belongs in M04.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.02.01-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT DISTINCT city FROM training_m02.customer ORDER BY city;
SELECT customer_code, customer_name
FROM training_m02.customer
WHERE city IN ('Dhaka', 'Khulna') AND status = 'ACTIVE'
ORDER BY customer_code LIMIT 2 OFFSET 0;
SELECT product_id, product_name, list_price
FROM training_m02.product
WHERE list_price BETWEEN 150 AND 800
ORDER BY list_price DESC, product_id
LIMIT 2 OFFSET 1;
```

**Interpretation and expected observations:** Distinct cities: Chattogram, Dhaka (2). Active customers in chosen cities: C001 (1). Last query: Mouse 400 then Notebook 150 (2), given prices 800,400,150 before offset.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.02.01-01`. Run all filters, predict outputs before execution, and compare ordered full result with paged result.

**Independent task:** Find product names containing `o` case-insensitively using ILIKE (PostgreSQL-specific); return 2nd page of 2 products sorted by product_id, after filtering only active products.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

What makes OFFSET paging nondeterministic? What column can break ties? Contrast DISTINCT and GROUP BY.

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.02.01-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.02.1`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Distinct cities: Chattogram, Dhaka (2). Active customers in chosen cities: C001 (1). Last query: Mouse 400 then Notebook 150 (2), given prices 800,400,150 before offset.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Putting ORDER BY after LIMIT
- forgetting tie-breaker
- assuming DISTINCT considers only the first selected column.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

This lesson is read-only. `ILIKE` is PostgreSQL-specific, not portable to every SQL vendor.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Show the unsliced ordered query first, then add LIMIT and OFFSET.

**Extension:** Discuss why modified tables between page requests can cause skip/duplicate observations even with ordering.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL SELECT reference: https://www.postgresql.org/docs/16/sql-select.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.02.01.md`. This lesson feeds directly into `L02.02.02`. Feedback must mark `PC-02.02.1` achieved or revision-required. **Reviewer approval pending.**

---

## L02.02.02 — NULL, Three-Valued Logic, CASE and COALESCE

### L-01. Identity

**Lesson:** `L02.02.02`, unit `U02.02` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.02` hour allocation.

### L-03. Prerequisites

Complete `L02.02.01`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.02.02.1` → `ULO-02.02.2` and `PC-02.02.2`: Use IS NULL, CASE and COALESCE correctly; find exactly two missing-email customers without changing stored NULLs.
- `LLO-02.02.02.2` → `ULO-02.02.2` and `PC-02.02.2`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

SQL `NULL` indicates missing/unknown, not an empty string or zero. Ordinary comparisons to NULL evaluate to UNKNOWN, so `email = NULL` is never a correct way to select missing emails. Use `IS NULL` or `IS NOT NULL`. A `WHERE` retains only rows where its expression is TRUE, not FALSE or UNKNOWN. `COALESCE` chooses the first non-NULL argument; it is appropriate for display fallback but may hide missing source information. `CASE` selects an expression based on ordered conditions; use it to label states without changing stored values. Avoid substituting zero for unknown money unless the business rule explicitly allows it.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

SQL `NULL` indicates missing/unknown, not an empty string or zero. Ordinary comparisons to NULL evaluate to UNKNOWN, so `email = NULL` is never a correct way to select missing emails. Use `IS NULL` or `IS NOT NULL`. A `WHERE` retains only rows where its expression is TRUE, not FALSE or UNKNOWN. `COALESCE` chooses the first non-NULL argument; it is appropriate for display fallback but may hide missing source information. `CASE` selects an expression based on ordered conditions; use it to label states without changing stored values. Avoid substituting zero for unknown money unless the business rule explicitly allows it.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.02.02-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT customer_code, email,
       COALESCE(email, '(not supplied)') AS display_email
FROM training_m02.customer ORDER BY customer_code;
SELECT customer_code FROM training_m02.customer
WHERE email IS NULL ORDER BY customer_code;
SELECT order_id, CASE order_status
  WHEN 'PAID' THEN 'Completed'
  WHEN 'PENDING' THEN 'Awaiting payment'
  ELSE 'Not billable' END AS display_status
FROM training_m02.sales_order ORDER BY order_id;
```

**Interpretation and expected observations:** Missing email customers: C002 and C003 (2). CASE maps 1001/1003 to Completed, 1002 to Awaiting payment, 1004 to Not billable. Display fallback does not change table values.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.02.02-01`. Test `email IS NULL`, `email IS NOT NULL` and `email = NULL` separately; record why third query finds no rows.

**Independent task:** Use searched CASE to display Premium when list_price >=1000, Standard when >=100, and Budget otherwise; explain branch order and boundary conditions.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Why does email = NULL not find C002? Does COALESCE write default values to the database?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.02.02-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.02.2`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Missing email customers: C002 and C003 (2). CASE maps 1001/1003 to Completed, 1002 to Awaiting payment, 1004 to Not billable. Display fallback does not change table values.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Treating NULL as empty string
- trusting `= NULL`
- using COALESCE to silently change meaning of missing values.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

No data modifications. Avoid making unsupported assumptions about missing customer personal information.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Build a three-row truth table showing TRUE/FALSE/UNKNOWN for comparisons involving NULL.

**Extension:** Compare `IS DISTINCT FROM` to ordinary equality and describe where PostgreSQL-specific null-safe comparisons help.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL conditional expressions: https://www.postgresql.org/docs/16/functions-conditional.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.02.02.md`. This lesson feeds directly into `L02.02.03`. Feedback must mark `PC-02.02.2` achieved or revision-required. **Reviewer approval pending.**

---

## L02.02.03 — Numeric, Text and Date Expressions

### L-01. Identity

**Lesson:** `L02.02.03`, unit `U02.02` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.02` hour allocation.

### L-03. Prerequisites

Complete `L02.02.02`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.02.03.1` → `ULO-02.02.3` and `PC-02.02.3`: Compute accurate numeric/text/date expressions with documented interpretation and no catalog mutation.
- `LLO-02.02.03.2` → `ULO-02.02.3` and `PC-02.02.3`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

Built-in scalar functions transform values within query results. Numeric `ROUND` requires considering scale and rounding policy; money examples should use NUMERIC, not floating point display approximations. Text `LOWER`, `UPPER`, `TRIM`, `CHAR_LENGTH` help clean labels for reports without overwriting original strings. PostgreSQL can add integers to DATE values and use EXTRACT to derive calendar parts. Arithmetic involving NULL usually yields NULL, so treat missing operands explicitly. Date/time handling should distinguish DATE from TIMESTAMPTZ; timezone-heavy reporting is beyond M02.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

Built-in scalar functions transform values within query results. Numeric `ROUND` requires considering scale and rounding policy; money examples should use NUMERIC, not floating point display approximations. Text `LOWER`, `UPPER`, `TRIM`, `CHAR_LENGTH` help clean labels for reports without overwriting original strings. PostgreSQL can add integers to DATE values and use EXTRACT to derive calendar parts. Arithmetic involving NULL usually yields NULL, so treat missing operands explicitly. Date/time handling should distinguish DATE from TIMESTAMPTZ; timezone-heavy reporting is beyond M02.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.02.03-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT product_name, list_price,
       ROUND(list_price * 1.15, 2) AS illustrative_price_with_15pct
FROM training_m02.product ORDER BY product_id;
SELECT customer_code,
       UPPER(TRIM(customer_name)) AS upper_name,
       CHAR_LENGTH(customer_name) AS name_length
FROM training_m02.customer ORDER BY customer_code;
SELECT order_id, order_date, order_date + 7 AS followup_date,
       EXTRACT(MONTH FROM order_date) AS month_number
FROM training_m02.sales_order ORDER BY order_id;
```

**Interpretation and expected observations:** Notebook illustrative price 172.50; Mouse 460.00. Order 1001 followup date 2026-01-22 and month 1. This is an example calculation, not a real tax/price policy.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.02.03-01`. Run expression examples; compare original columns and displayed transformed values. Verify all monetary output remains NUMERIC scale 2.

**Independent task:** Write a SKU/name display expression using CONCAT or `||`; calculate 10% discount preview with ROUND without updating catalog prices.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Do scalar functions affect stored values? Why use NUMERIC for monetary demonstrations? What is the follow-up date for 1003?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.02.03-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.02.3`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Notebook illustrative price 172.50; Mouse 460.00. Order 1001 followup date 2026-01-22 and month 1. This is an example calculation, not a real tax/price policy.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Rounding too early in a sum
- treating calculated display as stored amount
- mixing DATE and timestamp assumptions.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

No DML. 15% is an illustrative calculation only and must not be described as statutory tax.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Evaluate one simple scalar expression (`SELECT round(150::numeric * 1.15, 2)`) before applying to a table.

**Extension:** Compare ROUND with TRUNC and explain why a business requirement must define rounding rules.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL math/string/date-time: https://www.postgresql.org/docs/16/functions-math.html ; https://www.postgresql.org/docs/16/functions-string.html ; https://www.postgresql.org/docs/16/functions-datetime.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.02.03.md`. This lesson feeds directly into `L02.03.01`. Feedback must mark `PC-02.02.3` achieved or revision-required. **Reviewer approval pending.**

---

## L02.03.01 — INNER JOIN and Related Data

### L-01. Identity

**Lesson:** `L02.03.01`, unit `U02.03` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.03` hour allocation.

### L-03. Prerequisites

Complete `L02.02.03`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.03.01.1` → `ULO-02.03.1` and `PC-02.03.1`: Join keys correctly; produce four order headers and order 1001 two lines totaling 700.00.
- `LLO-02.03.01.2` → `ULO-02.03.1` and `PC-02.03.1`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

A join combines rows through an explicit relationship. A sales order refers to one customer using customer_id, and each order item refers to an order and a product. Always specify key-based ON predicates rather than cross-joining by mistake. One order may have multiple order_item rows, so joining orders to items changes row cardinality; a row per order is no longer guaranteed. Use meaningful table aliases, qualify ambiguous column names and preserve item unit_price as historical transaction price, not current product list_price.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

A join combines rows through an explicit relationship. A sales order refers to one customer using customer_id, and each order item refers to an order and a product. Always specify key-based ON predicates rather than cross-joining by mistake. One order may have multiple order_item rows, so joining orders to items changes row cardinality; a row per order is no longer guaranteed. Use meaningful table aliases, qualify ambiguous column names and preserve item unit_price as historical transaction price, not current product list_price.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.03.01-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT o.order_id, c.customer_name, o.order_status
FROM training_m02.sales_order AS o
JOIN training_m02.customer AS c ON c.customer_id=o.customer_id
ORDER BY o.order_id;
SELECT o.order_id, p.product_name, oi.qty, oi.unit_price,
       oi.qty * oi.unit_price AS line_total
FROM training_m02.sales_order AS o
JOIN training_m02.order_item AS oi ON oi.order_id=o.order_id
JOIN training_m02.product AS p ON p.product_id=oi.product_id
WHERE o.order_id=1001
ORDER BY oi.order_item_id;
```

**Interpretation and expected observations:** First query returns 4 orders with Alpha Retail on 1001/1002, Beta Traders on 1003/1004. Second returns Notebook 300.00 and Mouse 400.00; order 1001 total 700.00.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.03.01-01`. Draw one-to-many arrows, run joins in steps, compare row counts before and after the order_item join.

**Independent task:** List all PAID order lines with customer, product, quantity and line total sorted by order_id, order_item_id; predict 4 rows.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Why can an order appear twice after joining its lines? Which unit_price belongs in historical sales reporting?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.03.01-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.03.1`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** First query returns 4 orders with Alpha Retail on 1001/1002, Beta Traders on 1003/1004. Second returns Notebook 300.00 and Mouse 400.00; order 1001 total 700.00.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Missing ON clause causing cross product
- joining on display names
- using current price instead of sale price.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Read-only. Compare original row counts to detect join cardinality errors.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Start with a two-table join and inspect one parent row before adding order_item.

**Extension:** Draw the cardinality shape for customer-to-order-to-line and explain possible duplicates.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL tutorial joins: https://www.postgresql.org/docs/16/tutorial-join.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.03.01.md`. This lesson feeds directly into `L02.03.02`. Feedback must mark `PC-02.03.1` achieved or revision-required. **Reviewer approval pending.**

---

## L02.03.02 — LEFT JOIN and Missing-Row Reporting

### L-01. Identity

**Lesson:** `L02.03.02`, unit `U02.03` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.03` hour allocation.

### L-03. Prerequisites

Complete `L02.03.01`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.03.02.1` → `ULO-02.03.2` and `PC-02.03.2`: Preserve all three customers under LEFT JOIN with paid counts 1,1,0.
- `LLO-02.03.02.2` → `ULO-02.03.2` and `PC-02.03.2`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

An inner join omits a left-side row with no match. A LEFT JOIN preserves all left-side rows and supplies NULL values for unmatched right-side columns. Business reports such as a complete customer directory should retain customers without sales; a careless `WHERE o.status='PAID'` after LEFT JOIN removes the unmatched NULL rows and effectively changes the outcome. Put right-table restrictions in the ON condition if you intend to keep the unmatched left-side entities. `COUNT(o.order_id)` reports zero for unmatched customers, while COUNT(*) counts the null-extended row as one. Use this distinction deliberately.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

An inner join omits a left-side row with no match. A LEFT JOIN preserves all left-side rows and supplies NULL values for unmatched right-side columns. Business reports such as a complete customer directory should retain customers without sales; a careless `WHERE o.status='PAID'` after LEFT JOIN removes the unmatched NULL rows and effectively changes the outcome. Put right-table restrictions in the ON condition if you intend to keep the unmatched left-side entities. `COUNT(o.order_id)` reports zero for unmatched customers, while COUNT(*) counts the null-extended row as one. Use this distinction deliberately.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.03.02-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT c.customer_code, c.customer_name,
       COUNT(o.order_id) AS paid_order_count
FROM training_m02.customer AS c
LEFT JOIN training_m02.sales_order AS o
  ON o.customer_id=c.customer_id AND o.order_status='PAID'
GROUP BY c.customer_id, c.customer_code, c.customer_name
ORDER BY c.customer_code;
-- Contrast: WHERE o.order_status='PAID' after LEFT JOIN removes C003.
```

**Interpretation and expected observations:** Expected C001=1, C002=1, C003=0; all three customers remain. A post-join WHERE predicate drops C003.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.03.02-01`. Run ON-filter example, then relocate order_status condition into WHERE and observe missing customer. Compare COUNT(*) vs COUNT(order_id).

**Independent task:** List every product and any order_item match, including unsold Sticker. Select explicit columns and order by product_id, order_item_id.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Where must a right-side status filter go to preserve customers with no orders? Why does COUNT(*) return 1 for unmatched left row?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.03.02-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.03.2`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Expected C001=1, C002=1, C003=0; all three customers remain. A post-join WHERE predicate drops C003.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Treating LEFT JOIN as INNER JOIN
- counting * instead of a nullable matched key
- placing right-side filter in WHERE.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Read-only. Expected results depend on untouched seed; reset safely if prior examples were not rolled back.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Sketch Gamma Clinic on the left and NULL order on the right before writing SQL.

**Extension:** Contrast LEFT JOIN + `IS NULL` with NOT EXISTS to identify unsold products.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL table expressions joins: https://www.postgresql.org/docs/16/queries-table-expressions.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.03.02.md`. This lesson feeds directly into `L02.03.03`. Feedback must mark `PC-02.03.2` achieved or revision-required. **Reviewer approval pending.**

---

## L02.03.03 — GROUP BY, HAVING and Sales Totals

### L-01. Identity

**Lesson:** `L02.03.03`, unit `U02.03` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.03` hour allocation.

### L-03. Prerequisites

Complete `L02.03.02`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.03.03.1` → `ULO-02.03.3` and `PC-02.03.3`: Produce paid only aggregate 13500.00 and distinguish WHERE versus HAVING with matching evidence.
- `LLO-02.03.03.2` → `ULO-02.03.3` and `PC-02.03.3`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

Aggregates summarize sets of rows: COUNT, SUM, AVG, MIN and MAX. `GROUP BY` makes one output row per distinct group. A grouped SELECT can contain grouping columns or aggregate expressions, subject to PostgreSQL rules. `WHERE` filters input rows before grouping; `HAVING` filters groups afterward. Financially meaningful sales reporting needs an explicit recognized-status rule. Here only `PAID` counts as paid sales; `PENDING` and `CANCELLED` are excluded. Avoid multiplying totals by joining unrelated one-to-many tables. Use line-level unit_price captured on the order item and a NUMERIC multiplication.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

Aggregates summarize sets of rows: COUNT, SUM, AVG, MIN and MAX. `GROUP BY` makes one output row per distinct group. A grouped SELECT can contain grouping columns or aggregate expressions, subject to PostgreSQL rules. `WHERE` filters input rows before grouping; `HAVING` filters groups afterward. Financially meaningful sales reporting needs an explicit recognized-status rule. Here only `PAID` counts as paid sales; `PENDING` and `CANCELLED` are excluded. Avoid multiplying totals by joining unrelated one-to-many tables. Use line-level unit_price captured on the order item and a NUMERIC multiplication.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.03.03-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT c.customer_code,
       SUM(oi.qty * oi.unit_price) AS paid_sales
FROM training_m02.customer AS c
JOIN training_m02.sales_order AS o ON o.customer_id=c.customer_id
JOIN training_m02.order_item AS oi ON oi.order_id=o.order_id
WHERE o.order_status='PAID'
GROUP BY c.customer_code
HAVING SUM(oi.qty * oi.unit_price) >= 1000
ORDER BY c.customer_code;
SELECT SUM(oi.qty * oi.unit_price) AS paid_total
FROM training_m02.sales_order AS o
JOIN training_m02.order_item AS oi ON oi.order_id=o.order_id
WHERE o.order_status='PAID';
```

**Interpretation and expected observations:** HAVING result C002=12800.00 only; C001=700.00 excluded. Overall paid total is 13500.00. Pending 800.00 and cancelled 150.00 are excluded from paid total.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.03.03-01`. Recalculate totals manually from line rows; execute the queries; check 700+12800=13500. Use a WHERE vs HAVING experiment.

**Independent task:** Produce per-status order counts and amounts (including pending/cancelled clearly labeled as not paid), then produce a paid-only customer summary.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Which clause filters groups? What happens to a sum when duplicate rows arise from a bad join?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.03.03-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.03.3`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** HAVING result C002=12800.00 only; C001=700.00 excluded. Overall paid total is 13500.00. Pending 800.00 and cancelled 150.00 are excluded from paid total.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Using HAVING for simple row filters
- accidentally counting cancelled orders as revenue
- COUNT(*) after outer join.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

This is a toy training sales calculation, not recognized accounting revenue. No real finance data or posting occurs.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** First compute per-line extended price, then aggregate it and explain the filter before writing HAVING.

**Extension:** Include zero-paid customers using LEFT JOIN and COALESCE, ensuring no false matched rows are counted.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL aggregation tutorial: https://www.postgresql.org/docs/16/tutorial-agg.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.03.03.md`. This lesson feeds directly into `L02.04.01`. Feedback must mark `PC-02.03.3` achieved or revision-required. **Reviewer approval pending.**

---

## L02.04.01 — IN, EXISTS and Subqueries

### L-01. Identity

**Lesson:** `L02.04.01`, unit `U02.04` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.04` hour allocation.

### L-03. Prerequisites

Complete `L02.03.03`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.04.01.1` → `ULO-02.04.1` and `PC-02.04.1`: Use EXISTS/IN and NOT EXISTS to identify two paid customers and unsold product 105; explain NOT IN/NULL.
- `LLO-02.04.01.2` → `ULO-02.04.1` and `PC-02.04.1`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

A subquery is a query nested inside another SQL statement. `IN` compares a value with members of a set; `EXISTS` checks whether a correlated subquery returns any row. Correlation means the inner query refers to a value from the outer query; for each candidate, the logical test asks whether a qualifying match exists. Do not assume physical evaluation order. `NOT EXISTS` is reliable for no-match cases. `NOT IN` can surprise learners when the subquery includes NULL, because comparisons become UNKNOWN rather than TRUE; prefer NOT EXISTS for anti-matches unless null semantics are proven.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

A subquery is a query nested inside another SQL statement. `IN` compares a value with members of a set; `EXISTS` checks whether a correlated subquery returns any row. Correlation means the inner query refers to a value from the outer query; for each candidate, the logical test asks whether a qualifying match exists. Do not assume physical evaluation order. `NOT EXISTS` is reliable for no-match cases. `NOT IN` can surprise learners when the subquery includes NULL, because comparisons become UNKNOWN rather than TRUE; prefer NOT EXISTS for anti-matches unless null semantics are proven.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.04.01-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT customer_code, customer_name
FROM training_m02.customer AS c
WHERE EXISTS (
  SELECT 1 FROM training_m02.sales_order AS o
  WHERE o.customer_id=c.customer_id AND o.order_status='PAID'
) ORDER BY customer_code;
SELECT product_id, product_name
FROM training_m02.product AS p
WHERE NOT EXISTS (
  SELECT 1 FROM training_m02.order_item AS oi
  WHERE oi.product_id=p.product_id
) ORDER BY product_id;
```

**Interpretation and expected observations:** Customers with PAID orders: C001 and C002. Never-sold product: P-STICK Sticker (product 105). Expected, not executed.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.04.01-01`. Rewrite the first query with `IN (SELECT customer_id ...)`; compare result sets. Use NOT EXISTS for unsold products.

**Independent task:** Find customers with NO orders of any status. Explain why a LEFT JOIN/IS NULL rewrite requires care around match predicates.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Why can NOT IN behave strangely if an inner expression is NULL? When does EXISTS disregard selected columns?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.04.01-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.04.1`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** Customers with PAID orders: C001 and C002. Never-sold product: P-STICK Sticker (product 105). Expected, not executed.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Assuming NOT IN and NOT EXISTS are always interchangeable
- selecting join columns from the wrong level
- forgetting correlation.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Read-only; maintain null-aware semantics. Verify that the seed product 105 has no lines.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Run the subquery alone to inspect its candidate keys before embedding it.

**Extension:** Use a correlated EXISTS for customers with at least one order containing Mouse, avoiding duplicate customer rows.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL subquery expressions: https://www.postgresql.org/docs/16/functions-subquery.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.04.01.md`. This lesson feeds directly into `L02.04.02`. Feedback must mark `PC-02.04.1` achieved or revision-required. **Reviewer approval pending.**

---

## L02.04.02 — UNION, INTERSECT and EXCEPT

### L-01. Identity

**Lesson:** `L02.04.02`, unit `U02.04` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.04` hour allocation.

### L-03. Prerequisites

Complete `L02.04.01`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.04.02.1` → `ULO-02.04.2` and `PC-02.04.2`: Produce accurate UNION (3), INTERSECT (1), EXCEPT (1) city results using compatible projections.
- `LLO-02.04.02.2` → `ULO-02.04.2` and `PC-02.04.2`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

Set operators combine compatible query outputs: `UNION` returns distinct combined rows, `INTERSECT` returns rows common to both inputs, and `EXCEPT` removes rows found in the right input from the left. `UNION ALL` retains duplicates, often important for append-only lists; ordinary UNION removes them. Inputs require the same number of columns and compatible types, and a final ORDER BY must follow the combined query. The relative direction of EXCEPT matters. Use customer and supplier cities to tell a meaningful master-data story.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

Set operators combine compatible query outputs: `UNION` returns distinct combined rows, `INTERSECT` returns rows common to both inputs, and `EXCEPT` removes rows found in the right input from the left. `UNION ALL` retains duplicates, often important for append-only lists; ordinary UNION removes them. Inputs require the same number of columns and compatible types, and a final ORDER BY must follow the combined query. The relative direction of EXCEPT matters. Use customer and supplier cities to tell a meaningful master-data story.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.04.02-01`. **Expected only (NOT EXECUTED):**

```sql
SELECT city FROM training_m02.customer
UNION
SELECT city FROM training_m02.supplier
ORDER BY city;
SELECT city FROM training_m02.customer
INTERSECT
SELECT city FROM training_m02.supplier
ORDER BY city;
SELECT city FROM training_m02.customer
EXCEPT
SELECT city FROM training_m02.supplier
ORDER BY city;
```

**Interpretation and expected observations:** UNION: Chattogram, Dhaka, Khulna (3). INTERSECT: Dhaka (1). EXCEPT (customer - supplier): Chattogram (1).

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.04.02-01`. Run each operator, compare UNION to UNION ALL row counts, and explain why repeated Dhaka values do not appear twice under UNION.

**Independent task:** Find supplier cities with no customer using supplier EXCEPT customer; interpret why changing side changes the answer.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

What is the role of ALL? Why must column types be compatible? Does EXCEPT have direction?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.04.02-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.04.2`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** UNION: Chattogram, Dhaka, Khulna (3). INTERSECT: Dhaka (1). EXCEPT (customer - supplier): Chattogram (1).

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Confusing JOIN with set operation
- ordering one input instead of final output
- assuming EXCEPT symmetric.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Read-only. Do not mistake distinct city counts for distinct customer or supplier counts.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Start from the two city lists written on paper and calculate set results manually.

**Extension:** Repeat with two-column projections and explain why distinctness now applies to entire pairs.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL SELECT set operations: https://www.postgresql.org/docs/16/queries-union.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.04.02.md`. This lesson feeds directly into `L02.04.03`. Feedback must mark `PC-02.04.2` achieved or revision-required. **Reviewer approval pending.**

---

## L02.04.03 — Parameterized SQL and Integrated Workbook

### L-01. Identity

**Lesson:** `L02.04.03`, unit `U02.04` / module `M02`; **v0.1**, revised 10 October 2026; author and reviewers pending. **Status:** DRAFT / technical execution not recorded. **Tools:** PostgreSQL 16.x, psql 16.x or pgAdmin 4 client.

### L-02. Duration

**90 minutes = 30 theory + 60 practical**, included in `U02.04` hour allocation.

### L-03. Prerequisites

Complete `L02.04.02`, open authorized disposable `erp_m02_lab`, run `01_schema.sql` followed by `02_seed.sql` if this is a new exercise session, and verify expected counts with `03_verify.sql`. Use an SQL editor and retain actual observed result notes.

### L-04. Measurable learning outcomes / mappings

- `LLO-02.04.03.1` → `ULO-02.04.3` and `PC-02.04.3`: Demonstrate actual bound-value SQL with PREPARE or JDBC and submit complete, safe, annotated final workbook.
- `LLO-02.04.03.2` → `ULO-02.04.3` and `PC-02.04.3`: Execute and explain this lesson's edge case, verify the expected observation against actual SQL output, and submit reproducible evidence without touching production data.

### L-05. Essential concepts

User-supplied input must be passed as a bound parameter, never concatenated into SQL source text. PostgreSQL server-side `PREPARE` supports positional `$1` parameters for teaching; application code typically uses JDBC `?` or its driver binding API. A parameter is data, not part of SQL syntax; the server can distinguish the two. Query structure, identifiers and sort directions generally cannot be supplied as ordinary value parameters; those require fixed allowlisted choices if dynamic construction is unavoidable. Perform a final customer/order workbook with a bound customer_code, a safe scoped mutation preview, a JOIN report, an aggregate and negative tests on disposable data.

### L-06. Timed learning sequence (all minutes allocated)

| Activity | Category | Minutes | Evidence / method |
|---|---|---:|---|
| Real ERP scenario and prediction question | Theory | 5 | Opening response |
| Explain syntax and relation/NULL/safety semantics | Theory | 15 | Concept map and annotated SQL |
| Demonstrate named example (expected results labeled) | Theory | 10 | Walkthrough and prediction |
| Guided execution and error diagnosis | Practical | 25 | Learner-run commands |
| Independent variation / application | Practical | 25 | Changed query and reasoning |
| Exit check, peer review and instructor feedback | Practical | 10 | Marked output and remediation note |
| **TOTAL** | **30T + 60P** | **90** | **PC assessed** |

### L-07. Learner-ready explanation

User-supplied input must be passed as a bound parameter, never concatenated into SQL source text. PostgreSQL server-side `PREPARE` supports positional `$1` parameters for teaching; application code typically uses JDBC `?` or its driver binding API. A parameter is data, not part of SQL syntax; the server can distinguish the two. Query structure, identifiers and sort directions generally cannot be supplied as ordinary value parameters; those require fixed allowlisted choices if dynamic construction is unavoidable. Perform a final customer/order workbook with a bound customer_code, a safe scoped mutation preview, a JOIN report, an aggregate and negative tests on disposable data.

**How to reason before running:** (1) identify source relations and expected row cardinality; (2) identify which predicate, projection, transformation or change is demanded; (3) predict a small benchmark output from the supplied fixture; (4) execute only on the training database; (5) compare observed result/affected-row count and explain any mismatch. Read the specific SQL clauses carefully rather than relying on query formatting alone.

### L-08. Worked example

**Prerequisites:** guarded `01_schema.sql` + `02_seed.sql` loaded into `erp_m02_lab`. **Example ID:** `EX-02.04.03-01`. **Expected only (NOT EXECUTED):**

```sql
PREPARE lookup_customer(text) AS
  SELECT customer_id, customer_code, customer_name
  FROM training_m02.customer WHERE customer_code=$1;
EXECUTE lookup_customer('C001');
EXECUTE lookup_customer('C002');
DEALLOCATE lookup_customer;
-- Java JDBC analogue (not executable SQL):
-- PreparedStatement ps = c.prepareStatement(
--    "SELECT customer_code FROM training_m02.customer WHERE customer_code = ?");
-- ps.setString(1, customerCode);
```

**Interpretation and expected observations:** C001 resolves Alpha Retail and C002 resolves Beta Traders; parameter changes only value, not SQL structure. No execution claimed.

A learner must record the *actual* server response separately, including PostgreSQL patch version and current database. The example is intended to be technically runnable under the stated fixture; its runtime correctness still awaits lab execution.

### L-09. Guided and independent practice

**Guided lab:** `LAB-02.04.03-01`. Run PREPARE/EXECUTE and discuss why an input containing a quote remains a string value with parameter binding, not executable SQL.

**Independent task:** Complete 04_assignment_starter.sql and submit result evidence, bounded CRUD preview, supplier/product join, paid-total proof and input-binding explanation.

Submit SQL, predictions and observed output; do not modify the original fixture permanently.

### L-10. Checks for learning

Show safe and unsafe examples conceptually: which uses values rather than concatenation? What does a parameter NOT allow dynamically?

### L-11. Acceptance criteria

A pass requires the result/row count or documented error in `EX-02.04.03-01` to match the predicted data-dependent outcomes, a clear explanation of the lesson's rule, completion of the independent task, and evidence for `PC-02.04.3`. No unintended persistent change, unsafe unscoped DML or fabricated runtime results is permitted.

### L-12. Expected versus actual result rule

**EXPECTED (NOT EXECUTED):** C001 resolves Alpha Retail and C002 resolves Beta Traders; parameter changes only value, not SQL structure. No execution claimed.

**ACTUAL observed by learner:** `[paste real psql/pgAdmin result here during delivery]`. If different: record input query, server version, fixture counts and errors, correct the query or reset *only* the disposable schema, then retest.

### L-13. Common errors and corrections

- Escaping by ad-hoc string replacement
- concatenating external input into WHERE
- trying to parameterize table identifiers as values.
- Confusing a predicted output written by an author with the observed database output; obtain a real terminal result and label it.

### L-14. Troubleshooting and safe recovery

Never paste secrets, personal records or production endpoints. Use sample codes and bounded transactions; SQL injection defense requires parameterized app interfaces and least privilege.

If relation does not exist, check `SELECT current_database();`, confirm `training_m02` schema and the setup order; do not test reset scripts in any other database. If a mutation exercise caused drift, `ROLLBACK` while the transaction is open, or deliberately reload the isolated fixture after documenting the issue.

### L-15. Differentiation

**Support:** Use one PREPARE with two different sample codes to see the same query plan shape applied to different values.

**Extension:** Explain why limiting database privileges is necessary even when an application binds parameters correctly.

### L-16. Materials and instructor-only key

Learner file: this guide and `labs/01_schema.sql` + `02_seed.sql`; use `03_verify.sql` for dataset verification and relevant workbook page. Instructor-only key is kept separately as `M02-INSTRUCTOR-KEY.md` and must not appear in the learner deliverable.

### L-17. References

PostgreSQL PREPARE: https://www.postgresql.org/docs/16/sql-prepare.html ; JDBC PreparedStatement: https://docs.oracle.com/en/java/javase/17/docs/api/java.sql/java/sql/PreparedStatement.html

### L-18. Wrap-up, dependency and evidence location

Record a two-sentence rule and the screenshot-free plain-text result in `evidence/L02.04.03.md`. This lesson feeds directly into `M03 Database Objects and Relational Design`. Feedback must mark `PC-02.04.3` achieved or revision-required. **Reviewer approval pending.**

---

# Part IV — Assessment briefs and learner evidence templates

**General conditions:** PostgreSQL 16.x, untouched fixture from `01_schema.sql` + `02_seed.sql`; time is included within the final 10 practical minutes of each lesson plus integrated individual lab time, not additional. Every response must be evidenced by SQL and observed rows/errors, not an author-provided result.

## ASM-02.01-01 — Core CRUD and Safe Mutations

**Weight:** 25/100. **Target:** `MLO-02.1, MLO-02.2`. **Time:** absorbed within the 4.5h unit (primarily independent practice). **Inputs:** fictional ERP seed; access only to named isolated database.

**Tasks:**
1. `PC-02.01.1` — Select required columns and rows with an explicit, reproducible order; projected result matches seed. Submit runnable `.sql`, predicted output and actual observed output or error.
2. `PC-02.01.2` — Insert and update exactly one intended test customer, show RETURNING, and restore the starting row count. Submit runnable `.sql`, predicted output and actual observed output or error.
3. `PC-02.01.3` — Preview target keys and delete only a bounded disposable record; demonstrate rollback and describe FK protection. Submit runnable `.sql`, predicted output and actual observed output or error.

**Negative/unsafe case to explain:** Deleting a parent with dependents; assuming DELETE 0 is a database fault; forgetting to log target IDs. Learners must not intentionally execute an unscoped write against any database.

**Required evidence:** `EVD-02.01-01` containing original query, fixture/version metadata, observed records or errors, interpretation and where relevant safety/recovery details. No screenshots required if command text is accessible and complete.

| Scoring dimension | Points | Objective marking rule |
|---|---:|---|
| Three mapped PCs | 15 | 5 per PC; pass only if output and meaning correct |
| Edge case and safety | 5 | Correct prediction, observed negative evidence where allowed, and safe procedure |
| Reproducibility and explanation | 5 | Self-contained SQL, evidence, version/fixture and explanation |
| **Total** | **25** | Critical integrity/safety failure overrides numerical mark |

**Feedback / remediation:** return precise failed PC code, demonstrated wrong output, and a smaller correction exercise; learner resubmits observed result against an equivalent task. The instructor must record whether `PC` is met or revision is required.

## ASM-02.02-01 — Filtering, NULL and Scalar Expressions

**Weight:** 25/100. **Target:** `MLO-02.1, MLO-02.3`. **Time:** absorbed within the 4.5h unit (primarily independent practice). **Inputs:** fictional ERP seed; access only to named isolated database.

**Tasks:**
1. `PC-02.02.1` — Return a correctly filtered, distinctly projected and deterministically paginated result with tie-breaker. Submit runnable `.sql`, predicted output and actual observed output or error.
2. `PC-02.02.2` — Use IS NULL, CASE and COALESCE correctly; find exactly two missing-email customers without changing stored NULLs. Submit runnable `.sql`, predicted output and actual observed output or error.
3. `PC-02.02.3` — Compute accurate numeric/text/date expressions with documented interpretation and no catalog mutation. Submit runnable `.sql`, predicted output and actual observed output or error.

**Negative/unsafe case to explain:** Rounding too early in a sum; treating calculated display as stored amount; mixing DATE and timestamp assumptions. Learners must not intentionally execute an unscoped write against any database.

**Required evidence:** `EVD-02.02-01` containing original query, fixture/version metadata, observed records or errors, interpretation and where relevant safety/recovery details. No screenshots required if command text is accessible and complete.

| Scoring dimension | Points | Objective marking rule |
|---|---:|---|
| Three mapped PCs | 15 | 5 per PC; pass only if output and meaning correct |
| Edge case and safety | 5 | Correct prediction, observed negative evidence where allowed, and safe procedure |
| Reproducibility and explanation | 5 | Self-contained SQL, evidence, version/fixture and explanation |
| **Total** | **25** | Critical integrity/safety failure overrides numerical mark |

**Feedback / remediation:** return precise failed PC code, demonstrated wrong output, and a smaller correction exercise; learner resubmits observed result against an equivalent task. The instructor must record whether `PC` is met or revision is required.

## ASM-02.03-01 — Joins and Grouped Reporting

**Weight:** 25/100. **Target:** `MLO-02.4`. **Time:** absorbed within the 4.5h unit (primarily independent practice). **Inputs:** fictional ERP seed; access only to named isolated database.

**Tasks:**
1. `PC-02.03.1` — Join keys correctly; produce four order headers and order 1001 two lines totaling 700.00. Submit runnable `.sql`, predicted output and actual observed output or error.
2. `PC-02.03.2` — Preserve all three customers under LEFT JOIN with paid counts 1,1,0. Submit runnable `.sql`, predicted output and actual observed output or error.
3. `PC-02.03.3` — Produce paid only aggregate 13500.00 and distinguish WHERE versus HAVING with matching evidence. Submit runnable `.sql`, predicted output and actual observed output or error.

**Negative/unsafe case to explain:** Using HAVING for simple row filters; accidentally counting cancelled orders as revenue; COUNT(*) after outer join. Learners must not intentionally execute an unscoped write against any database.

**Required evidence:** `EVD-02.03-01` containing original query, fixture/version metadata, observed records or errors, interpretation and where relevant safety/recovery details. No screenshots required if command text is accessible and complete.

| Scoring dimension | Points | Objective marking rule |
|---|---:|---|
| Three mapped PCs | 15 | 5 per PC; pass only if output and meaning correct |
| Edge case and safety | 5 | Correct prediction, observed negative evidence where allowed, and safe procedure |
| Reproducibility and explanation | 5 | Self-contained SQL, evidence, version/fixture and explanation |
| **Total** | **25** | Critical integrity/safety failure overrides numerical mark |

**Feedback / remediation:** return precise failed PC code, demonstrated wrong output, and a smaller correction exercise; learner resubmits observed result against an equivalent task. The instructor must record whether `PC` is met or revision is required.

## ASM-02.04-01 — Subqueries, Set Operations and Parameterization

**Weight:** 25/100. **Target:** `MLO-02.3, MLO-02.5`. **Time:** absorbed within the 4.5h unit (primarily independent practice). **Inputs:** fictional ERP seed; access only to named isolated database.

**Tasks:**
1. `PC-02.04.1` — Use EXISTS/IN and NOT EXISTS to identify two paid customers and unsold product 105; explain NOT IN/NULL. Submit runnable `.sql`, predicted output and actual observed output or error.
2. `PC-02.04.2` — Produce accurate UNION (3), INTERSECT (1), EXCEPT (1) city results using compatible projections. Submit runnable `.sql`, predicted output and actual observed output or error.
3. `PC-02.04.3` — Demonstrate actual bound-value SQL with PREPARE or JDBC and submit complete, safe, annotated final workbook. Submit runnable `.sql`, predicted output and actual observed output or error.

**Negative/unsafe case to explain:** Escaping by ad-hoc string replacement; concatenating external input into WHERE; trying to parameterize table identifiers as values. Learners must not intentionally execute an unscoped write against any database.

**Required evidence:** `EVD-02.04-01` containing original query, fixture/version metadata, observed records or errors, interpretation and where relevant safety/recovery details. No screenshots required if command text is accessible and complete.

| Scoring dimension | Points | Objective marking rule |
|---|---:|---|
| Three mapped PCs | 15 | 5 per PC; pass only if output and meaning correct |
| Edge case and safety | 5 | Correct prediction, observed negative evidence where allowed, and safe procedure |
| Reproducibility and explanation | 5 | Self-contained SQL, evidence, version/fixture and explanation |
| **Total** | **25** | Critical integrity/safety failure overrides numerical mark |

**Feedback / remediation:** return precise failed PC code, demonstrated wrong output, and a smaller correction exercise; learner resubmits observed result against an equivalent task. The instructor must record whether `PC` is met or revision is required.

# Part V — PostgreSQL laboratory resources (separate reusable scripts)

**Safety before execution:** Only use the disposable local PostgreSQL 16 database `erp_m02_lab`. The setup script intentionally deletes `training_m02` schema when rerun; save learners' drafts and evidence before resetting. DO NOT run against any other database. To create the training database, an authorized administrator can run `createdb -U <lab-role> erp_m02_lab` (host/role determined locally), or use pgAdmin's Create → Database in a disposable local PostgreSQL instance. NEVER include passwords in scripts.

**Recommended CLI sequence (run from the directory containing the scripts):**

```bash
psql --version
psql -X -U <lab-role> -d erp_m02_lab -v ON_ERROR_STOP=1 -f 01_schema.sql
psql -X -U <lab-role> -d erp_m02_lab -v ON_ERROR_STOP=1 -f 02_seed.sql
psql -X -U <lab-role> -d erp_m02_lab -v ON_ERROR_STOP=1 -f 03_verify.sql
```

In pgAdmin Query Tool, confirm `SELECT current_database()` first, then run the *complete* setup script and seed; keep the same order. Avoid `ON_ERROR_STOP=1` batch execution of negative-case script: each intentional failure should be submitted separately and recorded. **All results cited in this authored material are EXPECTED (NOT EXECUTED).**

## Lab source: `labs/01_schema.sql`

```sql
-- 01_schema.sql | SQL-EDU M02 | PostgreSQL 16.x
-- WARNING: Destructive reset ONLY in a disposable database explicitly named erp_m02_lab.
-- Never point this script at another database. Back up your learning changes first.
-- A transaction keeps every subsequent DDL statement inert if the safety guard errors.
BEGIN;
DO $guard$
BEGIN
  IF current_database() <> 'erp_m02_lab' THEN
    RAISE EXCEPTION 'Safety stop: use disposable erp_m02_lab (connected to %)', current_database();
  END IF;
END
$guard$;

-- The DROP below is safe ONLY after the guard above has succeeded.
-- Execute this whole file using psql -v ON_ERROR_STOP=1 -f 01_schema.sql.
DROP SCHEMA IF EXISTS training_m02 CASCADE;
CREATE SCHEMA training_m02;
CREATE TABLE training_m02.customer (
  customer_id INTEGER PRIMARY KEY,
  customer_code TEXT NOT NULL UNIQUE,
  customer_name TEXT NOT NULL,
  city TEXT NOT NULL,
  email TEXT,
  status TEXT NOT NULL CHECK (status IN ('ACTIVE','INACTIVE'))
);
CREATE TABLE training_m02.supplier (
  supplier_id INTEGER PRIMARY KEY,
  supplier_name TEXT NOT NULL,
  city TEXT NOT NULL
);
CREATE TABLE training_m02.product (
  product_id INTEGER PRIMARY KEY,
  sku TEXT NOT NULL UNIQUE,
  product_name TEXT NOT NULL,
  supplier_id INTEGER NOT NULL REFERENCES training_m02.supplier(supplier_id),
  list_price NUMERIC(12,2) NOT NULL CHECK (list_price >= 0),
  active BOOLEAN NOT NULL
);
CREATE TABLE training_m02.sales_order (
  order_id INTEGER PRIMARY KEY,
  customer_id INTEGER NOT NULL REFERENCES training_m02.customer(customer_id),
  order_date DATE NOT NULL,
  order_status TEXT NOT NULL CHECK (order_status IN ('PENDING','PAID','CANCELLED'))
);
CREATE TABLE training_m02.order_item (
  order_item_id INTEGER PRIMARY KEY,
  order_id INTEGER NOT NULL REFERENCES training_m02.sales_order(order_id),
  product_id INTEGER NOT NULL REFERENCES training_m02.product(product_id),
  qty INTEGER NOT NULL CHECK (qty > 0),
  unit_price NUMERIC(12,2) NOT NULL CHECK (unit_price >= 0)
);
COMMIT;
```

## Lab source: `labs/02_seed.sql`

```sql
-- 02_seed.sql | SQL-EDU M02 | PostgreSQL 16.x
-- Run ONCE after 01_schema.sql (re-run schema first to reset training data).
BEGIN;
INSERT INTO training_m02.customer VALUES
  (1,'C001','Alpha Retail','Dhaka','alpha@example.test','ACTIVE'),
  (2,'C002','Beta Traders','Chattogram',NULL,'ACTIVE'),
  (3,'C003','Gamma Clinic','Dhaka',NULL,'INACTIVE');
INSERT INTO training_m02.supplier VALUES
  (10,'North Supply','Dhaka'),(20,'Delta Supply','Khulna');
INSERT INTO training_m02.product VALUES
  (101,'P-NOTE','Notebook',10,150.00,TRUE),
  (102,'P-MOUSE','Mouse',10,400.00,TRUE),
  (103,'P-KEY','Keyboard',20,800.00,TRUE),
  (104,'P-MON','Monitor',20,12000.00,TRUE),
  (105,'P-STICK','Sticker',10,50.00,FALSE);
INSERT INTO training_m02.sales_order VALUES
  (1001,1,DATE '2026-01-15','PAID'),
  (1002,1,DATE '2026-02-05','PENDING'),
  (1003,2,DATE '2026-02-10','PAID'),
  (1004,2,DATE '2026-02-15','CANCELLED');
INSERT INTO training_m02.order_item VALUES
  (1,1001,101,2,150.00),(2,1001,102,1,400.00),
  (3,1002,103,1,800.00),(4,1003,102,2,400.00),
  (5,1003,104,1,12000.00),(6,1004,101,1,150.00);
COMMIT;
```

## Lab source: `labs/03_verify.sql`

```sql
-- 03_verify.sql | SQL-EDU M02 | Expected, NOT EXECUTED in authoring
SELECT current_database() AS database_name, current_user AS login_role, version();
SELECT 'customer' AS entity, count(*) AS n FROM training_m02.customer
UNION ALL SELECT 'supplier', count(*) FROM training_m02.supplier
UNION ALL SELECT 'product', count(*) FROM training_m02.product
UNION ALL SELECT 'sales_order', count(*) FROM training_m02.sales_order
UNION ALL SELECT 'order_item', count(*) FROM training_m02.order_item
ORDER BY entity;
-- Expected counts: customer=3, supplier=2, product=5, sales_order=4, order_item=6.
SELECT count(*) AS customers_without_email
FROM training_m02.customer WHERE email IS NULL;
-- Expected: 2.
SELECT count(DISTINCT customer_id) AS purchasing_customers
FROM training_m02.sales_order;
-- Expected: 2.
SELECT sum(oi.qty * oi.unit_price) AS paid_sales_total
FROM training_m02.sales_order AS o
JOIN training_m02.order_item AS oi ON oi.order_id=o.order_id
WHERE o.order_status='PAID';
-- Expected: 13500.00, excluding PENDING and CANCELLED.
```

## Lab source: `labs/04_assignment_starter.sql`

```sql
-- 04_assignment_starter.sql | Module 02 | learner submission
-- Use SELECT-only queries outside explicit disposable practice transactions.
-- Include a comment with each query's expected and observed result after running.
-- Q1: Show active customers sorted by code. [PC-02.02.1]
-- Q2: Retrieve customers missing email using proper NULL semantics. [PC-02.02.2]
-- Q3: Show products with supplier names, including products with no sales. [PC-02.03.1]
-- Q4: Show ALL customers and their count of PAID orders, including zero. [PC-02.03.2]
-- Q5: Compute paid sales total by customer; do not include cancelled/pending. [PC-02.03.3]
-- Q6: Retrieve products with no order_item using NOT EXISTS. [PC-02.04.1]
-- Q7: Compare distinct cities from customer and supplier with set operators. [PC-02.04.2]
-- Q8: Document a bound-parameter query in JDBC or your approved client. [PC-02.04.3]
-- Q9: Run a scoped UPDATE inside BEGIN / ROLLBACK; record row count. [PC-02.01.2]
-- Q10: Explain why DELETE without WHERE is prohibited in this training workflow. [PC-02.01.3]
```

## Lab source: `labs/05_negative_cases.sql`

```sql
-- 05_negative_cases.sql | SQL-EDU M02 | Run each section SEPARATELY.
-- EXPECTED FAILURES are documented; do not use psql -v ON_ERROR_STOP=1 -f on this whole file.
-- Connect ONLY to erp_m02_lab. Re-run 01_schema.sql + 02_seed.sql if data differs.
-- (A) Expected duplicate key error; row counts remain unchanged.
INSERT INTO training_m02.customer VALUES
  (1, 'C999', 'Duplicate ID Demo', 'Dhaka', NULL, 'ACTIVE');
-- (B) Expected CHECK violation; product count unchanged.
INSERT INTO training_m02.product VALUES
  (900, 'P-FAIL', 'Invalid Price', 10, -1.00, TRUE);
-- (C) Expected TRUE for NULL, not `email = NULL` (which is UNKNOWN).
SELECT customer_code FROM training_m02.customer WHERE email IS NULL ORDER BY customer_code;
-- (D) In pgAdmin, paste each statement individually and record observed errors.
```

# Part VI — Traceability matrix, validation and controlled release

## Six-level traceability (CLO → MLO → ULO → PC → LLO/Lab → ASM/EVD)

| CLO | MLO | ULO | PC | Lesson & worked lab | Assessment → evidence |
|---|---|---|---|---|---|
| CLO-01, CLO-02 | `MLO-02.1` | `ULO-02.01.1` | `PC-02.01.1` | `LLO-02.01.01.1`, `LLO-02.01.01.2`; `L02.01.01` / `LAB-02.01.01-01` | `ASM-02.01-01` → `EVD-02.01-01` |
| CLO-01, CLO-02 | `MLO-02.2` | `ULO-02.01.2` | `PC-02.01.2` | `LLO-02.01.02.1`, `LLO-02.01.02.2`; `L02.01.02` / `LAB-02.01.02-01` | `ASM-02.01-01` → `EVD-02.01-01` |
| CLO-01, CLO-02 | `MLO-02.2` | `ULO-02.01.3` | `PC-02.01.3` | `LLO-02.01.03.1`, `LLO-02.01.03.2`; `L02.01.03` / `LAB-02.01.03-01` | `ASM-02.01-01` → `EVD-02.01-01` |
| CLO-02 | `MLO-02.1` | `ULO-02.02.1` | `PC-02.02.1` | `LLO-02.02.01.1`, `LLO-02.02.01.2`; `L02.02.01` / `LAB-02.02.01-01` | `ASM-02.02-01` → `EVD-02.02-01` |
| CLO-02 | `MLO-02.3` | `ULO-02.02.2` | `PC-02.02.2` | `LLO-02.02.02.1`, `LLO-02.02.02.2`; `L02.02.02` / `LAB-02.02.02-01` | `ASM-02.02-01` → `EVD-02.02-01` |
| CLO-02 | `MLO-02.3` | `ULO-02.02.3` | `PC-02.02.3` | `LLO-02.02.03.1`, `LLO-02.02.03.2`; `L02.02.03` / `LAB-02.02.03-01` | `ASM-02.02-01` → `EVD-02.02-01` |
| CLO-02 | `MLO-02.4` | `ULO-02.03.1` | `PC-02.03.1` | `LLO-02.03.01.1`, `LLO-02.03.01.2`; `L02.03.01` / `LAB-02.03.01-01` | `ASM-02.03-01` → `EVD-02.03-01` |
| CLO-02 | `MLO-02.4` | `ULO-02.03.2` | `PC-02.03.2` | `LLO-02.03.02.1`, `LLO-02.03.02.2`; `L02.03.02` / `LAB-02.03.02-01` | `ASM-02.03-01` → `EVD-02.03-01` |
| CLO-02 | `MLO-02.4` | `ULO-02.03.3` | `PC-02.03.3` | `LLO-02.03.03.1`, `LLO-02.03.03.2`; `L02.03.03` / `LAB-02.03.03-01` | `ASM-02.03-01` → `EVD-02.03-01` |
| CLO-02 | `MLO-02.3` | `ULO-02.04.1` | `PC-02.04.1` | `LLO-02.04.01.1`, `LLO-02.04.01.2`; `L02.04.01` / `LAB-02.04.01-01` | `ASM-02.04-01` → `EVD-02.04-01` |
| CLO-02 | `MLO-02.5` | `ULO-02.04.2` | `PC-02.04.2` | `LLO-02.04.02.1`, `LLO-02.04.02.2`; `L02.04.02` / `LAB-02.04.02-01` | `ASM-02.04-01` → `EVD-02.04-01` |
| CLO-02, CLO-09 (intro) | `MLO-02.5` | `ULO-02.04.3` | `PC-02.04.3` | `LLO-02.04.03.1`, `LLO-02.04.03.2`; `L02.04.03` / `LAB-02.04.03-01` | `ASM-02.04-01` → `EVD-02.04-01` |

## Timetable reconciliation (no hour inflation)

| Unit | Lessons | Theory minutes | Practical minutes | Total minutes |
|---|---:|---:|---:|---:|
| U02.01 | 3 | 90 | 180 | 270 |
| U02.02 | 3 | 90 | 180 | 270 |
| U02.03 | 3 | 90 | 180 | 270 |
| U02.04 | 3 | 90 | 180 | 270 |
| **TOTAL** | **12** | **360 (6h)** | **720 (12h)** | **1080 (18h)** |

## Editorial and technical release checklist

- [x] M02 syllabus duration preserved (18h = 6T+12P).
- [x] Module fields M-01…M-17 included.
- [x] Four unit records contain U-01…U-17 and three mapped PCs each.
- [x] Twelve lesson records contain L-01…L-18, 90-minute timed plans and separate expected vs actual.
- [x] Four assessments, 12 PC links, distinct learner evidence targets and guided/independent activity included.
- [x] Files use ID-based references and sample data; no real credentials.
- [x] SQL scripts consistently target PostgreSQL 16.x and named disposable database.
- [x] Separate instructor key exists and is not embedded in learner Markdown.
- [ ] Frozen 53-unit register inspected and provisional U02 IDs formally approved; **NOT DONE**.
- [ ] PostgreSQL 16 setup, seed, queries and negative cases executed and results logged; **NOT DONE**.
- [ ] Technical reviewer signs with execution evidence and exact software build; **NOT DONE**.
- [ ] Instructional reviewer verifies assessment load and accessibility; **NOT DONE**.
- [ ] Editorial reviewer verifies cross-references and presentation; **NOT DONE**.
- [ ] Curriculum lead signs off for publication; **NOT DONE**.

**Gate result: DRAFT, NOT APPROVED.** Items lacking evidence block publication; no unsupported compliance, accreditation or test-success statement is made.

## QA evidence record (to be completed during review)

| Evidence | Actual observation / location | Reviewer / date |
|---|---|---|
| PostgreSQL `SELECT version()` | Pending | Pending |
| Fresh setup stdout and relation list | Pending | Pending |
| Seed verification (3/2/5/4/6) | Pending | Pending |
| Paid-total 13500.00 | Pending | Pending |
| NULL and LEFT JOIN negative tests | Pending | Pending |
| Prepared-value / injection-safety demonstration | Pending | Pending |
| Approved unit-register IDs | Pending | Pending |

## Revision and change-control log

| Revision | Date | Scope | Notes | Approval |
|---|---|---|---|---|
| v0.1 | 2026-10-10 | First full M02 draft | M02 fixed syllabus hours/topics; four **provisional** units, twelve lessons, five lab files, four assessments, QA gate pending | Not approved |

**No scope expansion is authorized:** Any change to syllabus module hours, 16 module IDs, total 53 instructional unit IDs, or 240 programme hours requires a versioned curriculum change-control decision.
