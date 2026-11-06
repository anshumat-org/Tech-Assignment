# Assignment 03 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Dataset (synthetic)

- Candidate generates or is given a small synthetic subscription or retail dataset: customers, orders or subscriptions, and a monthly finance summary.
- The finance summary holds one **known figure** (for example, total net revenue for a quarter) used for reconciliation.
- Ids are opaque. No personal data. Include some mess: duplicates, NULLs, cancelled rows, a backfilled month.

### B. KPI definitions (`kpis.md`)

| KPI | Must state |
|---|---|
| 4–6 KPIs, for example net revenue, active customers, conversion rate, churn rate, average order value | Definition, numerator, denominator, grain, time window, owner, known limits |

### C. Dashboard
- At least 4 KPI tiles with period-over-period change and 3 charts.
- One filter (date range or segment). Show the "as of" date and data source on the page.
- Handle empty and small-sample states without misleading values.
- Charts: zero baseline for bars, labelled axes and units, no dual-axis tricks, no truncated scales without a note.

### D. Reconciliation
- Reconcile the dashboard total to the known figure.
- Show the difference, its cause and whether it is acceptable. Do not force the numbers to match.

### E. Insight report (1–2 pages)

| Section | Content |
|---|---|
| Question | The decision or question the data addresses |
| Findings | 3 findings, each with number, comparison and chart reference |
| Caveats | Data limits, sample size, correlation vs causation |
| Recommendations | Actions, each tied to a finding, plus what to verify next |

### F. Scenarios to address (README)
- **Late-arriving data:** last month is incomplete at report time. How is it shown?
- **Duplicates:** how many were removed and what effect on each KPI?
- **Nulls:** how do missing segments appear (an "Unknown" bucket, excluded, flagged)?
- **Definition change:** churn is redefined from 30 to 60 days inactive. What changes and how do you tell readers?

### G. Live follow-up
The interviewer may ask you to change one KPI definition or add a segment filter. Update the definition once, show which tiles move, and explain whether the trend story still holds.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Define every KPI with its denominator before charting | Show a ratio with no stated base |
| Reconcile to the known figure and report the gap | Adjust data until the totals match |
| State caveats next to the claim they affect | Hide limits in an appendix |
| Use honest scales, labels and units | Truncate axes, use dual axes or 3D to exaggerate |
| Mark incomplete periods clearly | Present a partial month as a drop |
| Keep metric SQL in one place and reuse it | Recompute the same KPI differently per chart |
| Separate observation from interpretation | Claim causes the data cannot show |
| Disclose AI-generated content and verify it | Let AI write conclusions you did not check |

### Deliverables

| Item | Format |
|---|---|
| Git repo with setup instructions | Reproducible from raw inputs |
| Dashboard | Running locally, or screenshots plus exported files |
| `kpis.md` | Definition table from section B |
| SQL for each KPI | Shared views or models, no duplicated logic |
| Reconciliation note | Figures, difference, explanation |
| Insight report | 1–2 pages, PDF or Markdown |
| README with assumptions, trade-offs and answers to scenarios in F | Short bullets |

### Constraints
- Any BI tool or language. SQL required for metrics.
- PostgreSQL, DuckDB or SQLite acceptable.
- No mandatory paid tool or cloud service.
- Synthetic data only. No personal data.

### Technical discussion (30–45 min)
Walk through one KPI from raw rows to tile, show the reconciliation, point out the caveat that matters most, and defend one chart choice. Expect a live definition change.
