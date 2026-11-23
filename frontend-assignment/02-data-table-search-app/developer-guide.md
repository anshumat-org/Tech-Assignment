# Assignment 02 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on URL state, async correctness and performance evidence, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Seed script (5,000+ synthetic rows) and mock API (`/records`, `/records/{id}`, optional `/facets`) | Server-side search, filter, sort and paging work. Latency, random 500s and empty result are simulated | 1.5 h |
| 2 | URL state layer: search, filters, sort, page parsed and validated | Reload and back / forward restore the view. Invalid sort or page falls back safely | 1 h |
| 3 | Data-fetching hook with debounce and stale-response protection | Fast typing sends few requests. A slow response never overwrites a newer one | 1 h |
| 4 | Table UI: semantic markup, sort on 3+ columns, 2+ filters (one multi-select), pagination or virtualization | Keyboard and screen reader can operate it. Choice justified | 1.5 h |
| 5 | Row detail (drawer or page) reachable by link | A detail URL opens directly | 0.5 h |
| 6 | Loading, empty, error and partial-refresh states | Skeleton without layout jump. Empty has clear filters. Error has retry. Old rows stay while fetching | 0.5 h |
| 7 | Performance: one budget, one measured before / after, lazy loading | Finding recorded in README | 0.5 h |
| 8 | Tests (6+), README scenario answers, API note, video or screenshots | Checklist C is complete | 0.5 h |

Total about 7 h (brief: 6–8 h). Get the URL and fetch flow right before styling.

## 2. Directions

| Topic | Direction |
|---|---|
| Source of truth | The URL owns search, filters, sort and page. No duplicate copy in component state |
| Server side | Mock handlers filter, sort and paginate. Not the client |
| API contract | Adjust the suggested endpoints only if you document it in a short note |
| Mock | MSW, json-server or similar. Synthetic data from a seed script. No real endpoints |
| Stale requests | Cancel or ignore stale responses |
| Search | Debounce. Keep the input responsive |
| Separation | Data hooks fetch. Table components only present |
| Markup | Semantic table, labelled controls, live result count for screen readers |
| States | Loading, empty, error, partial refresh. Every failure has a recovery action |
| Performance | State one budget, measure before optimizing, record one before / after finding. No blanket memoization |
| Bundle | Keep initial bundle small. Note what you lazy-loaded |
| Width and keyboard | Works at 360 px and by keyboard |
| Secrets | None in client code |
| Live follow-up | Be ready to add saved view, column toggle or CSV export of the current view. Keep state structured for it |
| Scope | If you skip something, list it under limitations in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [../frontend-instructions.md](../frontend-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 02 (not another one)
- [ ] Choose framework (TypeScript preferred), mock tool (MSW or json-server) and router. Note any unusual choice and why
- [ ] Verify Node (or runtime), package manager and a test runner work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Decide pagination vs virtualization and write down why
- [ ] Define the URL schema (parameter names, defaults, valid values)
- [ ] Write down the API contract and assumptions
- [ ] Choose tokens from [../../shared/design-system/README.md](../../shared/design-system/README.md) or document your own
- [ ] Plan the 8 steps above against your available hours
- [ ] Decide the 6+ tests you will write (URL state and an error case are required)

## 4. Checklist B — While developing

### Data and API
- [ ] Seed script generates 5,000+ synthetic rows (id, name, category, status, owner, amount, updated_at or similar)
- [ ] Handlers filter, sort and paginate on the "server" side and return items plus total
- [ ] Mock simulates latency, random 500 errors and an empty result
- [ ] Stale responses never overwrite newer ones (test it with out-of-order delays)

### URL state
- [ ] Search, filters, sort and page all live in the URL
- [ ] Reload and back / forward restore the view
- [ ] Invalid sort or page in a shared URL is handled, not crashed
- [ ] Page beyond the new total after a filter change lands somewhere sensible
- [ ] Row detail is reachable by link

### UI states and accessibility
- [ ] Loading shows a skeleton or spinner with no layout jump
- [ ] Empty state has a clear-filters action
- [ ] Error state has retry
- [ ] Old rows stay visible during a refresh
- [ ] Table uses semantic markup. Controls are labelled
- [ ] Result count change is announced (live region)
- [ ] Works at 360 px and by keyboard only

### Performance
- [ ] One budget stated (for example interaction under 100 ms) and how you checked it
- [ ] One measured before / after or profiler finding
- [ ] Lazy-loaded parts noted

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and trade-offs for the README
- [ ] Record any AI tool usage and reused code as you go. Verify it and be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, seed, start, test. All work
- [ ] At least 6 meaningful tests pass, including URL state and an error case
- [ ] Walk the scenarios in the app: fast typing, invalid URL, shrinking results on page 9, filter change with a screen reader
- [ ] Try a larger seed (for example 50,000 rows) and note what changes

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits (SUBMISSION_FORMATS.md Section 7)
- [ ] Working app with mock API, plus demo video or screenshots (Section 8)
- [ ] Short note on API contract and assumptions (Section 1)
- [ ] Short README with performance notes and trade-offs
- [ ] README answers all six scenarios: fast typing, invalid URL, results drop on page 9, 50,000 rows, screen reader result count, caching and invalidation

### Hygiene
- [ ] No secrets, real endpoints or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] AI-generated or reused code is marked and verified
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can explain state ownership
- [ ] Can trace a request from URL change to rendered rows
- [ ] Can show one performance decision with evidence
- [ ] Can say what breaks first at 10x data
- [ ] Ready for a live change such as a new filter, saved view, column toggle or CSV export

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Filter state in components and in the URL | URL is the single source of truth |
| A request per keystroke | Debounce |
| Slow response overwrites a newer one | Cancel or ignore stale requests |
| Filtering or sorting in the client | Do it in the mock handlers |
| Fetching inside presentational components | Separate data hooks from the table |
| Table built from unlabelled divs | Semantic table and labelled controls |
| Blank screen on failure | Error state with retry |
| Memoization everywhere | Measure first, record the finding |
| Invalid URL params crash the page | Validate and fall back |
| Result count change is silent for screen readers | Live region |
