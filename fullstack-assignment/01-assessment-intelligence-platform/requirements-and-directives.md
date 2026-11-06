# Assignment 01 — Requirements & Directives

**v1.0 — 2026-11-06**

## Part 1 — Requirements

### A. Question bank
- Create, edit, archive, retrieve questions.
- Types, categories, topics, skills, difficulty, marks, status.
- Answer options and correct answers for objective questions.
- Psychometric questions map to one or more scoring dimensions; reverse-scored items supported.

### B. Assessment configuration
- Name, type, duration, sections, scoring rules.
- Total question count with category-wise and difficulty-wise allocation.
- Negative marking for applicable technical questions.
- Validate the bank has enough eligible questions before publishing.

**Example blueprint (illustrative)**

| Category | Difficulty | Questions |
|---|---|---|
| SQL | Easy | 5 |
| SQL | Medium | 5 |
| SQL | Hard | 2 |
| Data Modeling | Medium | 4 |
| Analytical Thinking | Mixed | 4 |
| **Total** | | **20** |

### C. Question allocation engine
- Select eligible questions using the blueprint.
- Randomize question order and, where appropriate, option order.
- No duplicate questions within an attempt.
- Persist the generated set so refresh or resume does not regenerate it.
- Document the selection method: random, weighted random, or seeded deterministic.

### D. Candidate experience
- Instructions, sections, questions, navigation, timer.
- Save answers and resume the attempt.
- Single-choice, multiple-choice, Likert responses.
- Deliberate submit flow; prevent duplicate submission.

### E. Evaluation
- Auto-score objective questions; section totals.
- Psychometric dimension scores, including reverse scoring.
- Dimension summaries without right or wrong framing.
- Label psychometric output as **illustrative**. No clinical validity or diagnosis claims.

### Database (mandatory)

| Entity | Purpose |
|---|---|
| users / candidates | Accounts and profiles |
| questions / question_options | Question bank and options |
| question_categories | Topics, skills, categories |
| assessments / assessment_sections | Definitions and sections |
| assessment_blueprints | Allocation rules and quotas |
| assessment_attempts | Attempts and lifecycle |
| attempt_questions | Persisted allocation and order |
| candidate_responses | Submitted answers |
| scoring_dimensions | Psychometric dimensions |
| question_dimension_mappings | Weights and direction |
| assessment_results | Calculated results |

Deliverables: ER diagram, schema, keys, constraints, indexes with justification, cardinality, seed data, normalization note.

### SQL challenge (mandatory)
Five queries, at least one using a CTE or window function:
1. Questions by category and difficulty.
2. Blueprint selection without duplicates.
3. Section-wise candidate score.
4. Psychometric dimension scores with reverse scoring.
5. Candidate performance summary.

Explain expected indexes and trade-offs.

### API scope (adjustable if documented)

| Method | Endpoint | Purpose |
|---|---|---|
| POST | /api/questions | Create question |
| PATCH | /api/questions/:id | Update question |
| POST | /api/assessments | Create assessment |
| POST | /api/assessments/:id/attempts | Start attempt, allocate |
| GET | /api/attempts/:id | Retrieve attempt |
| PUT | /api/attempts/:id/responses | Save responses |
| POST | /api/attempts/:id/submit | Submit and evaluate |
| GET | /api/attempts/:id/result | Retrieve result |

Protect answer keys and scoring logic from candidate-facing responses.

### Engineering scenarios to address
- Fewer eligible questions than the blueprint needs.
- Refresh or reconnect during an active attempt.
- Same start or submit request received more than once.
- Two candidates get randomized sets from the same pool.
- Reverse-scored item, or item mapped to multiple dimensions.
- Question archived after an attempt has started.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Design the data model before coding | Start with the UI and bolt a schema on later |
| Persist the allocated question set | Regenerate questions on refresh |
| Make start and submit idempotent | Allow double attempts or double scoring |
| Hide answer keys and marks from candidate responses | Return `is_correct` or scoring rules to the browser |
| Snapshot what the candidate saw (text, options, marks) | Rely on live question rows after archive or edit |
| Validate every input and return consistent errors | Return raw database errors |
| Label psychometric output illustrative | Claim clinical validity or diagnosis |
| Test the six engineering scenarios | Test only the happy path |
| Document assumptions and trade-offs | Hide limitations |

### Deliverables

| Item | Format reference |
|---|---|
| Working app and GitHub repo | Meaningful commit history |
| ER diagram, schema, indexes, seed data | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 2 |
| HLD diagram | Section 1 |
| API documentation | Section 4 |
| Allocation algorithm and scoring explanation | In README or `docs/` |
| Five SQL queries and tests | Section 3 and 6 |
| README with setup, assumptions, trade-offs | Section 7 |
| Demo video or screenshots | Section 8 |

### Constraints
- TypeScript where practical. Justify major technology choices.
- Separate presentation, business logic, data access, external integrations.
- Runs locally. Docker optional.
- Synthetic data only.

### Technical discussion (30–45 min)
Expect to walk through architecture, schema and key queries, demo one end-to-end flow, discuss failure scenarios, and explain what changes before production.
