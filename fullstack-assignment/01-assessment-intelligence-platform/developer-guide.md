# Assignment 01 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 8–12 hours on the data model and allocation engine, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

Steps total 10 h, inside the 8–12 h window. Trim step 7 first if you run short.

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Data model: ER diagram, schema, keys, constraints, indexes, seed data | Migrations run from clean. Seed loads. Normalization note drafted | 2 h |
| 2 | Question bank: create, edit, archive, retrieve (objective and psychometric, dimension mappings, reverse-scored items) | Archived questions are excluded from new blueprints. Mappings saved | 1 h |
| 3 | Assessment and blueprint config with pre-publish check | Publish is blocked when the bank has too few eligible questions | 1 h |
| 4 | Allocation engine | Same pool gives different sets. No duplicates. Set is persisted and survives refresh | 1.5 h |
| 5 | Attempt API: start, save, resume, submit (idempotent) | Duplicate start or submit returns the same result. Snapshot of text, options, marks stored | 1.5 h |
| 6 | Scoring: objective, negative marking, section totals, dimension scores with reverse scoring | Hand-calculated results match | 1 h |
| 7 | Candidate UI and admin screens | Timer, navigator, save indicator, review and confirm submit work. Answer keys never reach the browser | 1 h |
| 8 | Five SQL queries, tests, docs, demo | Checklist C is complete | 1 h |

Design the data model first. UI comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Model first | Draw the ER diagram and review it before writing endpoints |
| Allocation | Document the method: random, weighted random or seeded deterministic. Say why |
| Persistence | Write the allocated set to `attempt_questions` at start. Never regenerate on refresh or resume |
| Snapshot | Store what the candidate saw (text, options, marks) so archive or edit later does not change a past attempt |
| Idempotency | Start and submit must be safe to repeat. Enforce with constraints and server checks, not only the UI |
| Answer keys | Candidate-facing responses carry no `is_correct`, marks or scoring rules |
| Reverse scoring | Direction lives in `question_dimension_mappings`. One item can map to several dimensions |
| Psychometric output | Label "Illustrative summary. Not a clinical or diagnostic result." No right or wrong framing |
| Errors | Validate every input. Consistent error shape. No raw database errors |
| SQL | Five queries, at least one with a CTE or window function. Explain expected indexes and trade-offs |
| API | The endpoint list in the brief is adjustable if you document the change |
| Structure | Keep presentation, business logic, data access and integrations separate |
| Scope | If you skip something, list it under "Limitations" in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [design-system/README.md](design-system/README.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Look at [samples/](samples/)
- [ ] Confirm you are doing Assignment 01 (not another one)
- [ ] Write down assumptions: allocation method, negative marking rule, timer expiry behaviour, what happens to an archived question
- [ ] Choose stack: TypeScript, Node.js, PostgreSQL (SQLite acceptable), React or Next.js. Note any change and why
- [ ] Verify runtime, database and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Draft the ER diagram covering the 11 mandatory entities, and a one-page HLD (Mermaid is fine)
- [ ] Plan the 8 steps above against your available hours
- [ ] List a test for each of the six engineering scenarios in the brief
- [ ] Plan synthetic seed data: both assessment types, enough questions per category and difficulty to fill a blueprint

## 4. Checklist B — While developing

### Data model and SQL
- [ ] All 11 mandatory entities exist with keys, constraints and justified indexes
- [ ] Unique constraints prevent duplicate questions in an attempt and duplicate attempts for one start
- [ ] Five SQL queries written and run against seed data (category and difficulty, blueprint selection without duplicates, section score, dimension scores with reverse scoring, performance summary)
- [ ] Seed script can be re-run without failing

### Allocation and attempts
- [ ] Blueprint quotas checked against eligible questions before publish
- [ ] No duplicate question within an attempt
- [ ] Question and option order randomized where appropriate
- [ ] Refresh or reconnect returns the same persisted set
- [ ] Submit twice does not score twice
- [ ] Archiving a question after an attempt starts does not change that attempt

### Scoring
- [ ] Objective scoring and section totals correct, negative marking applied only where configured
- [ ] Reverse-scored and multi-dimension items scored correctly
- [ ] Psychometric result labelled illustrative

### API and security
- [ ] Routes validate input with a schema and return consistent errors
- [ ] Candidate responses never include answer keys, marks or scoring rules
- [ ] Candidate can only read their own attempt and result
- [ ] No secrets or real personal data in code, logs or seed data

### UI
- [ ] Timer always visible, with a text warning at 5 minutes, not colour alone
- [ ] Navigator chips show unanswered, answered, flagged, current
- [ ] "Saved" indicator, and a visible state if a save fails
- [ ] Submit goes through a review screen and a confirm dialog with the unanswered count
- [ ] Blueprint editor shows available vs required per row, with a text cue when short
- [ ] Dimension bars have no good/bad colouring

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, migrate, seed, start, test. All work
- [ ] One command runs all tests
- [ ] Tests cover all six engineering scenarios: too few eligible questions, refresh or reconnect, duplicate start or submit, randomized sets from one pool, reverse-scored or multi-dimension item, question archived mid-attempt
- [ ] Failure-path tests exist, not only the happy path
- [ ] Inspect a candidate API response and confirm no answer key leaks

### Deliverables
- [ ] HLD diagram ([SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 1)
- [ ] ER diagram, schema, keys, constraints, indexes with justification, cardinality, seed data, normalization note (Section 2)
- [ ] Five SQL queries with index and trade-off notes and tests (Sections 3 and 6)
- [ ] API documentation (Section 4)
- [ ] Allocation algorithm and scoring explanation in README or `docs/`
- [ ] `docs/testing.md` with what is not tested and why (Section 6)
- [ ] Demo video or screenshots: setup, main flow, a failure case, a design decision. Show data surviving refresh and restart (Section 8)
- [ ] README contains: overview, quick start, assumptions, trade-offs, limitations, future work, AI usage disclosure (Section 7)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days. One submission only

### Prepare for the discussion (30–45 min)
- [ ] Can walk through architecture, schema and key queries
- [ ] Can demo one end-to-end flow: blueprint, allocation, attempt, submit, result
- [ ] Can explain each failure scenario and what changes before production
- [ ] Can identify AI-generated code and explain it

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Starting with the UI, schema later | ER diagram and schema first |
| Regenerating questions on refresh | Persist the set in `attempt_questions` |
| Reading live question rows after edit or archive | Snapshot text, options and marks at allocation |
| Returning `is_correct` to the browser | Strip answer keys in a candidate-facing response type |
| Double scoring on retried submit | Idempotent submit with a status guard |
| Blueprint publish with a short bank | Check eligible counts before publish |
| Reverse scoring done in the UI | Score on the server from mapping direction |
| Psychometric result shown as right or wrong | Dimension summary, labelled illustrative |
| Happy-path tests only | One test per engineering scenario |
