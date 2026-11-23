# Assignment 03 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on defensible numbers and honest messages, not on visual polish |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Synthetic dataset: customers, orders or subscriptions, monthly finance summary with one known figure, plus mess (duplicates, NULLs, cancelled rows, a backfilled month) | Clean checkout builds the data. Known figure is identifiable | 1 h |
| 2 | `kpis.md`: 4–6 KPIs with definition, numerator, denominator, grain, window, owner, limits | Every KPI has a stated base before any chart | 1 h |
| 3 | Metric SQL in shared views or models | One place per KPI. No duplicated logic | 1.25 h |
| 4 | Reconciliation to the known figure | Difference, cause and acceptability are written. Numbers are not forced to match | 0.75 h |
| 5 | Dashboard: 4+ KPI tiles with period change, 3 charts, one filter, "as of" date and source | Runs locally or exports. Empty and small-sample states do not mislead | 1.5 h |
| 6 | Insight report (1–2 pages): question, 3 findings, caveats, recommendations | Each finding has number, comparison and chart reference. Each recommendation ties to a finding | 1 h |
| 7 | README, scenarios F, rehearse live definition change | Checklist C is complete | 0.5 h |

Total 7 h (range 6–8 h). Definitions and reconciliation first, polish last.

## 2. Directions

| Topic | Direction |
|---|---|
| Definitions first | Define each KPI with its denominator in `kpis.md` before charting |
| Tooling | Any BI tool or code (Streamlit, Metabase, Superset, notebook, static HTML). SQL for all metrics. PostgreSQL, DuckDB or SQLite. No paid tool required |
| Data | Synthetic only. Opaque ids. Include duplicates, NULLs, cancelled rows, a backfilled month |
| One source of metric logic | Keep KPI SQL in shared views or models. Do not recompute a KPI differently per chart |
| Reconciliation | Reconcile to the known figure and report the gap and its cause. Never adjust data to match |
| Dashboard | 4+ KPI tiles with period-over-period change, 3 charts, one filter, "as of" date and data source on the page |
| Honest charts | Zero baseline for bars, labelled axes and units. No dual axes, 3D or truncated scales without a note |
| States | Handle empty and small-sample states. Mark incomplete periods clearly. Never show a partial month as a drop |
| Caveats | Put each caveat next to the claim it affects, not in an appendix |
| Insight | Separate observation from interpretation. Do not claim causes the data cannot show |
| Report | 1–2 pages, PDF or Markdown: question, 3 findings, caveats, recommendations |
| AI | Allowed if disclosed. You must verify every conclusion it drafts |
| Scope | If you skip something, say so in the README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../data-instructions.md](../data-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 03 (not another one)
- [ ] Choose the dataset theme (subscription or retail), the engine and the dashboard tool. Check they run locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Pick the 4–6 KPIs and the one known figure for reconciliation (for example quarterly net revenue)
- [ ] Write down open assumptions: churn window, how incomplete months show, how missing segments appear
- [ ] Decide the one filter (date range or segment)
- [ ] Plan the 7 steps above against your available hours

## 4. Checklist B — While developing

### Data and KPIs
- [ ] Data is synthetic with opaque ids. Mess is seeded: duplicates, NULLs, cancelled rows, a backfilled month
- [ ] Finance summary holds the known figure
- [ ] Each KPI states definition, numerator, denominator, grain, time window, owner and known limits
- [ ] KPI SQL lives in shared views or models and is reused by every tile and chart
- [ ] Duplicates removed are counted, with the effect on each KPI

### Reconciliation
- [ ] Dashboard total compared to the known figure
- [ ] Difference shown with cause and whether it is acceptable
- [ ] No data adjusted to force a match

### Dashboard
- [ ] 4+ KPI tiles with period-over-period change
- [ ] 3 charts with labelled axes and units. Bars start at zero
- [ ] No dual axes, 3D or unexplained truncated scales
- [ ] One filter works (date range or segment)
- [ ] "As of" date and data source shown on the page
- [ ] Empty and small-sample states do not show misleading values
- [ ] Incomplete last month is marked as incomplete
- [ ] Missing segments appear as stated (Unknown bucket, excluded or flagged)

### Insight report
- [ ] States the question or decision it addresses
- [ ] 3 findings, each with number, comparison and chart reference
- [ ] Caveats sit next to the claims they affect (limits, sample size, correlation vs causation)
- [ ] Each recommendation is tied to a finding, plus what to verify next
- [ ] Observation and interpretation are kept separate

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Record any AI tool usage as you go (you must disclose it)
- [ ] No personal data or secrets anywhere

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Build data, run SQL, open the dashboard. All work
- [ ] Every tile matches its SQL. Re-run one KPI by hand from raw rows
- [ ] Reconciliation figures match the note
- [ ] Live-change rehearsal: change one KPI definition (for example churn 30 to 60 days) or add a segment filter. Update it once, show which tiles move and say whether the trend story still holds

### Deliverables
- [ ] Git repo with setup instructions, reproducible from raw inputs
- [ ] Dashboard running locally, or screenshots plus exported files
- [ ] `kpis.md` with the definition table
- [ ] SQL for each KPI, in shared views or models
- [ ] Reconciliation note: figures, difference, explanation
- [ ] Insight report, 1–2 pages, PDF or Markdown
- [ ] README with assumptions, trade-offs and short-bullet answers to the 4 scenarios: late-arriving data, duplicates, nulls, definition change
- [ ] AI usage disclosure and sources cited, per [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead queries, stray debug output or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk one KPI from raw rows to tile
- [ ] Can show the reconciliation
- [ ] Can name the caveat that matters most
- [ ] Can defend one chart choice
- [ ] Ready for the live definition change

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Ratio shown with no stated base | Denominator in `kpis.md` and on the tile |
| Adjusting data until totals match | Report the gap and its cause |
| Same KPI computed differently per chart | One shared view per KPI |
| Partial month shown as a drop | Mark it incomplete or exclude it with a note |
| Truncated axis, dual axis or 3D | Zero baseline, labelled axes and units, one scale per chart |
| Caveats in an appendix | Put each next to its claim |
| Claiming a cause the data cannot show | State the observation, label interpretation as such |
| Polished visuals, weak definitions | Definitions and reconciliation first |
| Unchecked AI-written conclusions | Verify against the data, disclose use |
