# Assignment 02 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on repeatable, safe pipeline behaviour, not on tooling choices |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Seeded generator: daily customers, orders, events files for 10–14 days, with seeded bad data | Same seed gives the same files. Bad data covers duplicates, NULLs, malformed dates, negative amounts, unknown currency, orphans | 1 h |
| 2 | DDL for raw, staging, model, rejects and run log | Schema builds from clean. Keys and constraints noted | 1 h |
| 3 | Raw load with source file name and load timestamp | Files load as-is. Raw is never edited | 0.75 h |
| 4 | Staging and rejects: type, clean, dedupe, reason codes | Every bad row lands in rejects with reason and source file | 1.25 h |
| 5 | Model tables (for example dim_customer, fact_orders) with upsert or merge, inside a transaction | Running a day twice gives identical tables. A forced failure leaves the model unchanged | 1.25 h |
| 6 | Incremental run, full rebuild, run log | New day touches only new or changed data. Run log has rows read, loaded, rejected, status | 0.75 h |
| 7 | Data-quality tests, blocking vs warning | Passing and failing demonstration is automated | 0.5 h |
| 8 | Lineage note, README, rerun proof, rehearse live rule change | Checklist C is complete | 0.5 h |

Total 7 h (range 6–8 h). Correct reruns first, extras last.

## 2. Directions

| Topic | Direction |
|---|---|
| Layers | raw (as-is, with file name and load time), staging (typed, cleaned, deduplicated), model (dimensions and facts), rejects |
| Idempotency | Use keys and upserts or merge. Running the same file or day twice gives the same final tables |
| Incremental and rebuild | A new day processes only new or changed data. A full rebuild must also work |
| Atomicity | Wrap model updates in a transaction. A failed run leaves model tables unchanged |
| Bad rows | Send to rejects with a reason code and source file. Do not drop silently or crash on the first one |
| Raw data | Keep untouched and replayable. Never hand-edit files |
| Reuse | Keep rules and transforms in one place. No cleaning logic duplicated per source |
| Run log | Run id, start, end, rows read, loaded, rejected, status. Report counts, not just success |
| Tests | Uniqueness, not null, referential, range / domain, volume / freshness. State which block the run and which warn, and why |
| Scenarios | Decide and document: late file, conflicting duplicate (which wins), NULL required field, renamed status or mandatory currency, extra column |
| Tooling | Any language. SQL for transforms. PostgreSQL, DuckDB or SQLite. Orchestrator optional, a script or Makefile is fine |
| Scope | No streaming, no Kubernetes, no paid cloud. Synthetic data only. If you skip something, say so in the README |
| AI | Allowed if disclosed. You must explain and verify all generated code |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../data-instructions.md](../data-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 02 (not another one)
- [ ] Choose language, engine (PostgreSQL, DuckDB or SQLite) and run method (script or Makefile). Check they work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Write down your rules: which duplicate wins, reject vs default vs quarantine for NULLs, what counts as a late file
- [ ] Decide which tests block the run and which only warn
- [ ] Sketch the layer diagram and the table list (customers, orders, events through to model and rejects)
- [ ] Plan the 8 steps above against your available hours

## 4. Checklist B — While developing

### Data and layers
- [ ] Generator is seeded and writes daily files for 10–14 days
- [ ] Bad data is seeded: duplicate keys, NULLs, malformed dates, negative amounts, unknown currency, orphan customer ids
- [ ] Raw keeps source file name and load timestamp, and is never modified
- [ ] Staging types, cleans and deduplicates
- [ ] Rejects hold the row, reason code and source file

### Pipeline behaviour
- [ ] Rerun of the same file or day gives identical final tables
- [ ] Incremental run touches only new or changed data
- [ ] Full rebuild works and matches the incremental result
- [ ] Model update runs in one transaction. A forced failure leaves the model unchanged (try it)
- [ ] Late file for day 3 arriving after day 5 is handled as documented
- [ ] Conflicting duplicate across two files follows your stated winner rule
- [ ] Schema drift (extra column) does not break the run silently

### Data-quality tests
- [ ] Uniqueness: order_id unique in fact_orders
- [ ] Not null: customer_id, order_ts
- [ ] Referential: each order maps to a customer or goes to rejects
- [ ] Range / domain: amount >= 0, status in the allowed list
- [ ] Volume / freshness: row-count band and latest file date
- [ ] Blocking vs warning is stated for each test
- [ ] A failing test is demonstrated, with what the pipeline does next

### Habits
- [ ] Rules and transforms live in one place and are reused
- [ ] Run log records rows read, loaded and rejected for every run
- [ ] Commit small and often with meaningful messages
- [ ] Record any AI tool usage as you go (you must disclose it)
- [ ] No personal data or secrets anywhere

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README in one or two commands. Generate, load, test. All work
- [ ] Rerun proof: output shows identical results after a second run
- [ ] All data-quality tests pass on clean data and fail as expected on bad data
- [ ] Live-change rehearsal: add a rule (for example reject orders older than 90 days) or a new source column, with a test. Unrelated tables and rows are unchanged

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits
- [ ] Seeded data generator and sample raw files (synthetic only)
- [ ] Pipeline code and SQL transforms, layers as raw, staging, model, rejects
- [ ] Schema or DDL for all layers, including rejects and run log, with keys and constraints noted
- [ ] Automated data-quality tests with passing and failing demonstration
- [ ] Lineage note (table or Mermaid): source file to raw, staging, model, and which transform touches which column
- [ ] README with assumptions, trade-offs and short-bullet answers to the 5 scenarios: late data, duplicates, nulls, definition change, schema drift
- [ ] AI usage disclosure and sources cited, per [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the layers
- [ ] Can show a rerun and a late file
- [ ] Can explain one rejected row end to end
- [ ] Can say which test catches the most likely failure and what you would monitor
- [ ] Ready for the live rule change

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Append-only load that assumes one run | Keys and upsert or merge |
| Editing raw files by hand | Keep raw untouched, fix in staging |
| Dropping bad rows or crashing on the first | Rejects table with reason code |
| Model tables half-loaded after a failure | One transaction around model updates |
| Cleaning logic copied per source | One shared rule set |
| "Success" with no counts | Run log with rows read, loaded, rejected |
| Incremental run never compared to a full rebuild | Compare them and show the result |
| Every test blocks, or none do | State and justify blocking vs warning |
| Scope creep into streaming or orchestration | Plain script or Makefile, correct reruns first |
