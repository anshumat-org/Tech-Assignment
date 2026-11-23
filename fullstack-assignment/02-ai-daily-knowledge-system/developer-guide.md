# Assignment 02 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 8–12 hours on the node model, local-first sync and safe AI review, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

Steps total 10 h, inside the 8–12 h window. Trim step 7 first if you run short.

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Data model: ER diagram, schema, indexes, constraints (nodes, tags, ai_jobs, ai_outputs, sync_operations, devices) | Migrations run from clean. Hierarchy, ordering and deletion rules written down | 1.5 h |
| 2 | Local store (IndexedDB) and daily page, outliner: create, edit, delete, indent, outdent, reorder. Client-generated stable IDs | Data survives refresh and browser restart, offline | 2 h |
| 3 | Node types and tags | Each node has type, content, parent and order. Tags work | 0.5 h |
| 4 | Backend API and remote storage: daily notes, nodes, search with date, type and tag filters | Filters run in the database | 1.5 h |
| 5 | Sync: queue, push, pull with cursor or version, idempotent retries, status badge | Offline edits reach a second browser after reconnect. Replay does not duplicate | 2 h |
| 6 | AI service: provider interface, mock provider, schema validation, review panel | At least three of summarize, extract, classify work. Nothing applies without review | 1.5 h |
| 7 | Tests, docs, sitemap, demo | Checklist C is complete | 1 h |

Write locally first. Sync and AI are layers on top.

## 2. Directions

| Topic | Direction |
|---|---|
| Local first | Write to IndexedDB first, then sync. Never block editing on a network call |
| IDs | Generate node IDs on the client so offline creates are stable |
| Hierarchy and order | State how parent-child and sibling order are stored, and how deletes cascade |
| Sync ops | Each operation has an ID so a replay is ignored. Retry with backoff |
| Pull | Use a cursor or version. Do not re-download everything |
| Conflicts | A clear basic strategy for simultaneous edits and delete conflicts. A full CRDT is not required |
| AI interface | Implement the `AIProvider` interface: `summarize`, `extractStructuredData`, `classify`. A documented mock provider is acceptable |
| AI output | Validate against a schema. Handle failure and timeout. Keep it separate from the original note |
| AI review | Suggestions are editable with Accept and Dismiss. "Apply selected" is explicit. Label "Suggested by AI. Review before applying." |
| AI keys | Server side only. Never in the frontend or the repo |
| AI provenance | Store input, provider and output in `ai_jobs` and `ai_outputs`. Avoid duplicate processing where practical |
| Offline | Core note-taking works offline. AI may need internet |
| UI | Keyboard first: Enter, Tab, Shift+Tab, Alt+Up/Down. Online/offline and sync status always visible |
| Scope | If you skip something, list it under "Limitations" in your README. Semantic search is a bonus |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [design-system/README.md](design-system/README.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Look at [samples/](samples/)
- [ ] Confirm you are doing Assignment 02 (not another one)
- [ ] Write down assumptions: conflict rule, delete behaviour, ID scheme, which three AI features, mock vs real provider
- [ ] Choose stack: React or Next.js PWA, IndexedDB, Node.js API, PostgreSQL. Note any change and why
- [ ] Verify runtime, database and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Draft the ER diagram (nine entities in the brief) and a one-page HLD (Mermaid is fine)
- [ ] Sketch the sitemap of screens
- [ ] Plan the 7 steps above against your available hours
- [ ] Plan synthetic seed notes: several days, mixed node types, one long note for summarizing

## 4. Checklist B — While developing

### Local-first and sync
- [ ] Create, edit, delete and browse work with the network off
- [ ] Data survives refresh and browser restart
- [ ] Pending changes are queued and pushed on reconnect
- [ ] The same operation applied twice has no effect
- [ ] Pull uses a cursor or version
- [ ] Second browser or device shows the updates
- [ ] Simultaneous edit and delete conflicts behave as you documented
- [ ] Online/offline and sync state (synced, pending count, syncing, error) are always visible

### Data model
- [ ] Nodes have stable ID, parent, type, content and order
- [ ] Hierarchy, ordering and deletion rules implemented as documented
- [ ] Indexes support the search and filter queries
- [ ] AI output is stored with provenance and linked to the source note

### AI
- [ ] At least three of summarization, structured extraction, tagging and classification work
- [ ] Output is validated against a schema. Bad output is rejected, not trusted
- [ ] Timeout and provider failure show an inline message with Retry. Notes stay usable
- [ ] Original text is never overwritten
- [ ] Nothing is applied until the user accepts
- [ ] Keys are server side only

### Search and API
- [ ] Keyword search with date, node type and tag filters
- [ ] Routes validate input and return consistent errors
- [ ] No secrets or real personal data in code, logs or seed data

### UI
- [ ] Node types shown by chip or icon, not colour alone
- [ ] Tasks have a checkbox and a done state with strike-through and text
- [ ] AI panel shows original and suggestions side by side
- [ ] Offline banner uses the brief's wording. Empty day has one clear first action

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, migrate, seed, start, test. All work
- [ ] One command runs all tests
- [ ] Tests include failure paths: duplicate sync operation, invalid AI output, provider timeout, conflict case
- [ ] Rehearse the demo: edit offline, refresh, reconnect, see it in a second browser

### Deliverables
- [ ] HLD diagram ([SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 1)
- [ ] ER diagram, schema, indexes, constraints, sample queries (Section 2)
- [ ] API documentation and AI integration notes (Section 4)
- [ ] Sitemap of screens (Section 11)
- [ ] `docs/testing.md` and local setup (Sections 6 and 7)
- [ ] Demo of offline edit and sync. Show data persisting after refresh and restart (Section 8)
- [ ] README explains: hierarchy and ordering, deletion, AI provenance, local/remote sync, conflict handling, retry, duplicate operations, cursor or version
- [ ] README contains: overview, quick start, assumptions, trade-offs, limitations, future work, AI usage disclosure (Section 7)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can demo offline edit then reconnect
- [ ] Can explain conflict handling
- [ ] Can walk through the AI review flow
- [ ] Can explain what changes before production
- [ ] Can identify AI-generated code and explain it

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Waiting for the server before saving a note | Write locally first, sync after |
| Server-assigned IDs for offline creates | Client-generated stable IDs |
| Replaying a sync op creates a duplicate | Operation IDs and idempotent apply |
| Full re-download on every pull | Cursor or version |
| AI output replaces the user's text | Store separately, apply only after review |
| Trusting raw model output | Schema validation, reject invalid |
| AI key in the frontend | Server-side provider only |
| Conflict strategy left undefined | Write down the rule for edits and deletes |
| Sync failure shown nowhere | Visible status badge with error and retry |
