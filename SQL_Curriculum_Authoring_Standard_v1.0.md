# SQL Curriculum Authoring & Quality Assurance Standard

**Standard ID:** SQL-EDU-STD-001  
**Version:** 1.0 (proposed internal standard)  
**Date:** 9 October 2026  
**Applies to:** Professional SQL Programming & Enterprise Database Engineering — 2026 Edition  
**Programme baseline:** 16 modules | 53 instructional units | 240 guided hours (84 theory + 156 practical)  
**Status:** Ready for course-team adoption; not an official accreditation or NTVQF standard  
**Owner:** Curriculum Lead  
**Review cycle:** Before each teaching cohort and whenever the supported technology baseline changes

---

## 1. Purpose and authority

This standard defines the **minimum required content, structure, traceability, technical verification and approval process** for every **module**, **unit** and **lesson** in the 240-hour SQL curriculum. It ensures materials are consistent, competency-based, teachable, reproducible and assessable.

**Normative language**
- **MUST / SHALL:** mandatory. Failure blocks publication or delivery approval.
- **MUST NOT:** prohibited.
- **SHOULD:** recommended; omission requires a recorded explanation.
- **MAY:** optional enhancement.

This is an **internal curriculum authoring standard**. Course *instructional units* are **not automatically formal Units of Competency** under Bangladesh's NTVQF. Official qualification alignment requires a separate mapping and validation against the applicable approved competency standard.

## 2. Frozen curriculum constraints

| Rule ID | Mandatory rule | Verification |
|---|---|---|
| GOV-01 | Preserve the **16 approved module IDs**, **53 instructional unit IDs** and **240 total hours** unless a versioned curriculum change is approved. | Master register comparison |
| GOV-02 | Preserve **84 theory and 156 practical hours** in the programme. Module and unit hour breakdowns MUST reconcile exactly. | Hour ledger sums |
| GOV-03 | Topic additions MUST fit an existing approved outcome; scope expansions require change control. | Change log + CLO map |
| GOV-04 | Every unit MUST belong to one module; every lesson MUST belong to one unit. | Hierarchy validation |
| GOV-05 | Every assessable outcome MUST be linked to teaching material, practice and at least one assessment item. | Traceability matrix |
| GOV-06 | No learning material is published without technical, instructional and editorial QA approval. | Signed QA record |
| GOV-07 | Material MUST name its PostgreSQL/tool version, prerequisites, author/reviewer and revision date. | Metadata check |
| GOV-08 | Training examples MUST use disposable/sample data; real personal or production credentials/data are prohibited. | Safety review |
| GOV-09 | Learner-facing material and instructor-only answers MUST be distributed separately. | Repository review |
| GOV-10 | Claims of standards compliance, accreditation or test success MUST have documented evidence; otherwise label them as proposed/unverified. | Evidence inspection |

**Master source of truth:** the versioned course syllabus and unit register. This standard controls **how** content is authored; it does not silently override the approved syllabus.

## 3. Naming, numbering and folder rules

| Artifact | ID format | Example |
|---|---|---|
| Module | `MNN` | `M08` |
| Instructional unit | `UNN.UU` | `U08.02` |
| Lesson | `LNN.UU.LL` | `L08.02.02` |
| Learning outcome | `CLO-NN`, `MLO-NN.N`, `ULO-NN.UU.N`, `LLO-NN.UU.LL.N` | `LLO-08.02.02.1` |
| Unit element | `EC-NN.UU.N` | `EC-08.02.1` |
| Performance criterion | `PC-NN.UU.N` | `PC-08.02.3` |
| Worked example | `EX-NN.UU.LL-NN` | `EX-08.02.02-01` |
| Practical/lab | `LAB-NN.UU.LL-NN` | `LAB-08.02.02-01` |
| Assessment | `ASM-NN.UU-NN` | `ASM-08.02-01` |
| Evidence record | `EVD-NN.UU-NN` | `EVD-08.02-01` |

- IDs MUST remain stable across revisions; deleted IDs MUST NOT be reassigned to new content.
- Filenames MUST include their artifact ID, e.g. `L08.02.02-UPSERT-and-Conflict-Handling.md`.
- Cross-references MUST use IDs rather than ambiguous phrases such as “the next topic.”
- A release MUST include a change log; changes affecting outcomes, hours or assessment require approval.

## 4. Required learning hierarchy

`Course outcome (CLO) → Module outcome (MLO) → Unit outcome (ULO) + Elements/Performance Criteria → Lesson outcome (LLO) → Activity → Assessment → Evidence`

Each outcome MUST use an observable verb and specify **what the learner can produce or demonstrate**, the **conditions/tools**, and an **objective success criterion** where practical.

**Avoid:** “Understand idempotency.”  
**Use:** “Given two concurrent payment requests sharing a tenant and idempotency key, implement a PostgreSQL uniqueness strategy that persists no more than one request record and document the observed database response.”

## 5. MODULE standard — mandatory fields (M-01 through M-17)

Every module MUST include:

1. **M-01 Identity:** ID, title, edition, author, reviewer, status and last revision.
2. **M-02 Rationale:** why the module matters in an enterprise application.
3. **M-03 Prerequisites:** required prior modules, SQL skills and environment.
4. **M-04 Scope:** in-scope and out-of-scope topics; connection to the approved syllabus.
5. **M-05 Outcomes:** 3–6 measurable module learning outcomes linked to CLOs.
6. **M-06 Hour ledger:** total, theory, practical and hours of each constituent unit.
7. **M-07 Unit map:** sequence, unit IDs, unit names, dependency order and outcomes.
8. **M-08 Teaching strategy:** explanation, demonstration, guided practice, independent work and feedback.
9. **M-09 Learning resources:** textbook chapters/sections, SQL scripts, diagrams, slides and glossary.
10. **M-10 Practical case:** at least one realistic ERP, finance, e-commerce or SaaS scenario.
11. **M-11 Assessment blueprint:** formative/summative methods, assessed outcomes, criteria and weight/decision rule.
12. **M-12 Evidence:** named learner deliverables and expected artefacts.
13. **M-13 Integrity and safety:** relevant data-integrity, tenancy, security or transaction risks.
14. **M-14 Instructor guidance:** preparation, environment, timing, common misconceptions and differentiation.
15. **M-15 References:** accurate bibliography and official documentation links/versions where relevant.
16. **M-16 Review checklist:** technical, instructional, accessibility and editorial sign-off.
17. **M-17 Completion criterion:** explicitly verifiable conditions for module completion.

**Module release gate:** all units present, all hours balanced, outcomes mapped and assessments available.

## 6. UNIT standard — mandatory fields (U-01 through U-17)

Every unit MUST include:

1. **U-01 Identity:** unit ID/title, owning module, version and author/reviewer.
2. **U-02 Purpose and context:** realistic workplace task and why it is needed.
3. **U-03 Prerequisites:** knowledge, software and input data.
4. **U-04 Unit outcomes:** 2–5 measurable ULOs linked to MLOs.
5. **U-05 Elements of competency:** 2–5 functional elements (internal pedagogical mapping).
6. **U-06 Performance criteria:** observable pass conditions for each element; no vague verbs alone.
7. **U-07 Boundaries:** what is and is not covered in this unit.
8. **U-08 Hour allocation:** total/theory/practical, with exact lesson sums.
9. **U-09 Lesson map:** ordered lesson IDs, titles, durations and dependencies.
10. **U-10 Theory:** definitions, principles, stepwise explanations and misconceptions.
11. **U-11 Examples:** at least one annotated, technically valid worked example.
12. **U-12 Application:** at least one guided lab and one independent task, or documented equivalent if unsuitable.
13. **U-13 Assessment:** questions, task, criteria, marking approach and remediation path.
14. **U-14 Evidence guide:** files, SQL outputs, screenshots/logs where justified, and test observations to retain.
15. **U-15 Error/failure coverage:** expected failure modes, troubleshooting and negative cases relevant to the skill.
16. **U-16 Resource list:** reusable scripts, seed data, glossary, references and instructor key.
17. **U-17 Review status:** content accuracy, alignment, runnable examples and accessibility checked.

**Unit release gate:** each criterion has matching evidence; all lessons sum to the unit's total and theory/practical hours.

## 7. LESSON standard — mandatory fields (L-01 through L-18)

Every lesson MUST include:

1. **L-01 Identity:** lesson ID, title, unit, version, author/reviewer.
2. **L-02 Duration:** total and theory/practical minutes.
3. **L-03 Prerequisites:** what students must already know and have installed.
4. **L-04 Outcomes:** 1–3 observable LLOs linked to a ULO and performance criterion.
5. **L-05 Essential concepts:** precise terms and minimal background.
6. **L-06 Lesson flow:** timed opening, explanation, demonstration, guided activity, independent application and closing assessment/feedback.
7. **L-07 Core explanation:** logically sequenced teaching content, not slides alone.
8. **L-08 Worked example:** code/diagram with narrative explanation and expected behaviour.
9. **L-09 Practice:** at least one student action or application check with instructions.
10. **L-10 Checks for learning:** question, mini-quiz, code review or direct observation.
11. **L-11 Acceptance criteria:** specific conditions showing the lesson outcome was achieved.
12. **L-12 Expected results:** expected rows/errors/performance interpretation, distinguished from actually executed results.
13. **L-13 Common mistakes:** at least two credible misconceptions/errors, with corrections.
14. **L-14 Troubleshooting/safety:** warnings and safe recovery procedure where applicable.
15. **L-15 Differentiation:** a support hint and an extension challenge.
16. **L-16 Materials:** learner handout, sample data/scripts and instructor notes.
17. **L-17 References:** traceable sources appropriate to the lesson.
18. **L-18 Wrap-up:** key takeaway, next lesson dependency and evidence location.

**Lesson release gate:** total minutes reconcile, code/examples are validated or clearly labeled unverified, and every LLO is assessed.

## 8. Mandatory technical rules for SQL/PostgreSQL material

| Rule | Requirement |
|---|---|
| SQL-01 | State supported PostgreSQL version and any extension requirements; avoid implying features are portable without qualification. |
| SQL-02 | Runnable examples MUST include prerequisites, schema/seed dependencies, execution steps and expected outcomes. |
| SQL-03 | Never claim code was executed or a test passed unless actual logs/evidence exist. Mark unrun scripts as **Expected (not executed)**. |
| SQL-04 | Any `DROP`, unscoped `DELETE`, destructive migration or configuration change MUST be clearly restricted to an isolated training database and include a reset/recovery plan. |
| SQL-05 | Parameterization is mandatory for application-originated SQL. Never teach unsafe string-concatenated SQL as a solution. |
| SQL-06 | Race-condition demonstrations MUST identify separate sessions, transaction boundaries, interleaving and expected terminal state. |
| SQL-07 | Transactions MUST state success, rollback and error paths; retryable failures and idempotency must not be conflated. |
| SQL-08 | Avoid real credentials, personal data and production endpoints. Use test fixtures. |
| SQL-09 | Finance examples MUST show integrity checks (e.g. balanced postings); tenancy examples MUST include unauthorized-access tests. |
| SQL-10 | Performance examples MUST report hardware/data conditions, methodology, measured baseline and measured comparison; no invented performance gains. |
| SQL-11 | Generated AI SQL MUST use database-side least privilege and execution restrictions; prompts are not security controls. |
| SQL-12 | Instructor answer keys MUST be separated from learner exercise files. |

## 9. Required assessment design

For each ULO and PC, authors MUST identify:

| Field | Question |
|---|---|
| Target | What competency is being assessed? |
| Conditions | Which database version, data set, tools and time constraints apply? |
| Task | What must the learner do? |
| Expected output | Which files, SQL result sets, logs or explanation are produced? |
| Pass condition | What observable minimum is required? |
| Negative case | What incorrect/unsafe outcome must be prevented? |
| Feedback/remediation | How will failed criteria be taught and reassessed? |

A completion percentage alone MUST NOT replace critical correctness checks. A payment lab fails if duplicate postings occur; a multi-tenant lab fails if another tenant's data can be read.

## 10. Authoring workflow and approval rules

1. **Freeze and map:** confirm syllabus version, module scope, hours, CLOs and unit register.
2. **Draft module guide:** complete M-01–M-17 and approve the unit map.
3. **Draft unit plans:** complete U-01–U-17 and define performance criteria.
4. **Draft lesson plans:** complete L-01–L-18, with timing and assessed outcomes.
5. **Build reusable examples/labs:** create data fixtures, scripts and independent tasks.
6. **Technical verification:** run SQL in the stated PostgreSQL environment where available; record commands, output, errors and version. If unavailable, retain status **not executed**.
7. **Instructional review:** verify cognitive progression, workload, accessibility and assessment alignment.
8. **Editorial review:** standardize terms, diagrams, IDs, links and bibliography.
9. **Release:** curriculum lead approves package and records version/change log.
10. **Improve:** collect learner issues, fix errata and preserve stable IDs.

**Required approval statuses:** `DRAFT → TECH_REVIEW → INSTRUCTIONAL_REVIEW → APPROVED → PUBLISHED`. `REVISION_REQUIRED` can be assigned at any review gate.

## 11. Worked example: Module → Unit → Lesson

### 11.1 Example module record: M08

| Mandatory field | Filled example |
|---|---|
| ID/title | `M08 — Idempotency and Reliable Transaction Processing` |
| Duration | **16h = 6h theory + 10h practical** |
| Prerequisites | M03 constraints; M06 transactions; M07 concurrency |
| CLO map | CLO-04, CLO-05, CLO-06 |
| MLO-08.1 | Explain when retries can duplicate business effects. |
| MLO-08.2 | Implement duplicate-safe, fingerprint-validated transaction requests. |
| MLO-08.3 | Demonstrate safe retry, Inbox/Outbox and crash recovery behaviour. |
| Units | U08.01 (4h: 2T/2P); U08.02 (4h: 1T/3P); U08.03 (4h: 1T/3P); U08.04 (4h: 2T/2P) |
| Case study | Multi-tenant payment processing |
| Module assessment | Code, concurrent duplicate tests, recovery scenarios, written design explanation |
| Critical pass rule | One business payment MUST NOT create duplicate financial effects under replay. |

### 11.2 Example unit record: U08.02

**Title:** Duplicate Prevention and UPSERT  
**Hours:** 4h = 1h theory + 3h practical  
**Prerequisites:** unique constraints, INSERT, transactions, tenant-scoped keys  
**Unit purpose:** prevent duplicate request records when a payment API is retried or called concurrently.

**Unit outcomes**
- `ULO-08.02.1`: Create a tenant-scoped uniqueness rule for an idempotency key.
- `ULO-08.02.2`: Use `INSERT ... ON CONFLICT` safely and interpret the result of a replay.
- `ULO-08.02.3`: Detect a key reused with a different request fingerprint and describe required application handling.

**Elements and performance criteria**

| Element | Performance criterion (PC) | Evidence |
|---|---|---|
| EC-08.02.1 Define uniqueness | PC-08.02.1: one `(tenant_id, idempotency_key)` pair cannot produce two rows | DDL + uniqueness test |
| EC-08.02.2 Handle replay | PC-08.02.2: conflict insert produces no second record; existing request can be read | SQL output + code |
| EC-08.02.2 Handle replay | PC-08.02.3: changed fingerprint is detected and rejected by service policy | Negative case + explanation |
| EC-08.02.3 Verify contention | PC-08.02.4: competing inserts are documented without duplicate records | Two-session test notes |

**Lessons**

| Lesson | Name | Theory | Practical | Total |
|---|---|---:|---:|---:|
| L08.02.01 | Unique Constraints and Duplicate Prevention | 30m | 30m | 60m |
| L08.02.02 | UPSERT and Conflict Handling | 20m | 40m | 60m |
| L08.02.03 | Payment Request Lab and Concurrent Tests | 10m | 110m | 120m |
| **Total** | | **60m** | **180m** | **240m** |

**Unit summative task:** submit schema and SQL demonstrations proving one row per key, including the replay/mismatch decision logic and a two-session contention report. Record observed behaviour; do not invent test output.

### 11.3 Example lesson record: L08.02.02

**Title:** UPSERT and Conflict Handling  
**Duration:** 60 minutes (20 theory + 40 practical)  
**Mapped outcomes:** `ULO-08.02.2`, `ULO-08.02.3`; criteria `PC-08.02.2`, `PC-08.02.3`.  
**Prerequisites:** `L08.02.01`, PostgreSQL connection, training schema.

**Lesson outcomes**
- `LLO-08.02.02.1`: Execute an `ON CONFLICT DO NOTHING` insert and correctly interpret an empty `RETURNING` result.
- `LLO-08.02.02.2`: Locate the existing request, compare its fingerprint and explain why the database uniqueness rule does not by itself reject mismatched business payloads.

**Minute-by-minute teaching plan**

| Activity | Minutes | Category |
|---|---:|---|
| Introduce retry and duplicate-payment scenario | 5 | Theory |
| Explain unique conflict targets and fingerprint policy | 10 | Theory |
| Instructor demonstration of SQL and expected outputs | 5 | Theory |
| Guided SQL practical | 15 | Practical |
| Independent replay/mismatch investigation | 15 | Practical |
| Exit assessment, feedback and submission | 10 | Practical |
| **Total** | **60** | **20T / 40P** |

**Worked example — EX-08.02.02-01**

> Run only in a disposable training database. The following results are **expected, not represented as actually executed**.

```sql
CREATE SCHEMA IF NOT EXISTS sql_training;

CREATE TABLE IF NOT EXISTS sql_training.payment_request (
    request_id BIGINT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    tenant_id UUID NOT NULL,
    idempotency_key TEXT NOT NULL,
    request_fingerprint TEXT NOT NULL,
    state TEXT NOT NULL
        CHECK (state IN ('PROCESSING', 'SUCCEEDED', 'FAILED')),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT uq_training_payment_request
        UNIQUE (tenant_id, idempotency_key)
);

-- Reset this one test fixture only, in a disposable training DB.
DELETE FROM sql_training.payment_request
WHERE tenant_id = '00000000-0000-0000-0000-000000000001'
  AND idempotency_key = 'lesson-payment-001';

-- First submission: expect one returned request_id.
INSERT INTO sql_training.payment_request
    (tenant_id, idempotency_key, request_fingerprint, state)
VALUES
    ('00000000-0000-0000-0000-000000000001',
     'lesson-payment-001', 'fingerprint-A', 'PROCESSING')
ON CONFLICT (tenant_id, idempotency_key) DO NOTHING
RETURNING request_id;

-- Exact retry: expect zero returned rows.
INSERT INTO sql_training.payment_request
    (tenant_id, idempotency_key, request_fingerprint, state)
VALUES
    ('00000000-0000-0000-0000-000000000001',
     'lesson-payment-001', 'fingerprint-A', 'PROCESSING')
ON CONFLICT (tenant_id, idempotency_key) DO NOTHING
RETURNING request_id;

-- Load existing request and compare the submitted fingerprint.
SELECT request_id,
       request_fingerprint = 'fingerprint-A' AS matches_request,
       state
FROM sql_training.payment_request
WHERE tenant_id = '00000000-0000-0000-0000-000000000001'
  AND idempotency_key = 'lesson-payment-001';

-- Expect 1 matching row. A different fingerprint must be rejected
-- by transaction/service logic; DO NOTHING alone does not reject it.
SELECT COUNT(*) AS request_count
FROM sql_training.payment_request
WHERE tenant_id = '00000000-0000-0000-0000-000000000001'
  AND idempotency_key = 'lesson-payment-001';
```

**Instructor explanation:** The unique constraint prevents a second stored request with the same `(tenant_id, idempotency_key)`. The `ON CONFLICT` clause makes a conflicting insert harmless at the row-creation level. The application MUST then compare the existing fingerprint with the new payload, respect the request's processing status and persist the business effect plus final response through a properly designed transactional workflow. This example **does not** by itself prove end-to-end payment idempotency.

**Learner tasks**
1. Run the script on a new training database and record the observed first insert, retry result and final count.
2. Change the proposed retry fingerprint to `fingerprint-B`; explain why a unique constraint alone cannot determine a business mismatch.
3. Show how service logic should reject a mismatched fingerprint without creating a new payment.
4. In the next lesson, test competing inserts from two sessions and document the blocking/interleaving behaviour.

**Exit assessment**
- Q1: What does an empty `RETURNING` result mean in this example?
- Q2: Why must tenant ID be part of the uniqueness key?
- Q3: What must the application do if the same key is used with a different fingerprint?

**Lesson pass conditions:** SQL executes in the stated training environment; final request count is exactly one; all three conceptual answers are correct; learner documents observed results, including any errors. Instructor marks criteria against evidence, not learner assertion.

**Common mistakes**
- Treating `ON CONFLICT DO NOTHING` as full end-to-end payment idempotency.
- Failing to compare the existing fingerprint or to enforce tenant context.
- Reading an existing record without considering concurrent state transitions.

**Support hint:** Start with one tenant and one key; verify how the unique constraint behaves before using two sessions.  
**Extension:** Discuss how to return a durable prior response after a successful payment, and how to avoid races around `PROCESSING` and `SUCCEEDED` states.

## 12. Mandatory reusable templates

### 12.1 Module template

```markdown
# MNN — [Module Title]
Metadata: Version | Status | Author | Reviewer | PostgreSQL baseline
Duration: [total] = [theory] + [practical]
Course outcomes (CLO): ...
Prerequisites: ...
Purpose and scope: ...
Module outcomes (MLO): ...
Unit and hour matrix: ...
Case study and core resources: ...
Assessment blueprint, deliverables and completion criteria: ...
Safety/security/integrity considerations: ...
Instructor preparation and references: ...
QA sign-off and change history: ...
```

### 12.2 Unit template

```markdown
# UNN.UU — [Unit Title]
Identity | Purpose | Prerequisites | Boundaries
Duration: [theory] + [practical]
Mapped MLO / Unit outcomes (ULO)
Elements of Competency (EC)
Performance Criteria (PC) + evidence per PC
Lesson plan, hours and learning activities
Theory | Worked examples | Guided lab | Independent practice
Common errors | Negative cases | Assessment | Remediation
Resource files | References | Instructor-only key reference
QA review status
```

### 12.3 Lesson template

```markdown
# LNN.UU.LL — [Lesson Title]
Identity | Duration/minutes (T/P) | Prerequisites | LLO-to-ULO/PC mapping
Learner-ready explanations and key concepts
Timed instructional sequence
Worked example: setup → commands → expected results → explanation
Guided practice, independent application and check for learning
Acceptance criteria, negative tests and evidence
Common mistakes, troubleshooting and safety note
Support hint, extension activity, wrap-up, next lesson
References, assets, answer-key reference, QA status
```

## 13. Mandatory release checklist

- [ ] Module, unit and lesson IDs are unique and stable.
- [ ] Required metadata, version, owner and review status are present.
- [ ] Scope matches the approved syllabus and prerequisite order.
- [ ] Module and unit learning outcomes are measurable and mapped to CLOs.
- [ ] Each unit has explicit elements, performance criteria and evidence.
- [ ] All lesson outcomes are linked to criteria and assessed.
- [ ] Hour totals and theory/practical splits reconcile at every level.
- [ ] All mandatory learning materials and instructor keys are complete.
- [ ] PostgreSQL version and setup/fixtures are stated.
- [ ] Scripts are executed and evidence recorded **or** conspicuously marked unverified.
- [ ] Dangerous operations are restricted to disposable training data.
- [ ] Negative cases and errors are covered where relevant.
- [ ] No invented results, unsupported accreditation claims or unverified citations.
- [ ] All three approvals (technical, instructional, editorial) are recorded.

**Publication rule:** Any unchecked mandatory item = **NOT APPROVED**. An exception requires a written deviation request, owner, risk, mitigation and curriculum-lead approval; deviations cannot bypass data integrity, learner safety or essential assessment evidence.

---

**End of Standard SQL-EDU-STD-001, Version 1.0.**
