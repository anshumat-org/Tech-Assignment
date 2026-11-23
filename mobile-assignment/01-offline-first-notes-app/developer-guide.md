# Assignment 01 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on correct, explainable sync behaviour, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order (about 7 h)

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Local store and note model (id, title, body, updated_at, sync_status, version) | Notes survive an app restart. UI reads only from the local DB | 1 h |
| 2 | Notes UI: create, view, edit, delete, list, local search or filter | All actions work in airplane mode. UI never blocks on the network | 1 h |
| 3 | Outbox: write the change and its queue entry in one transaction | Killing the app between save and sync loses nothing | 1 h |
| 4 | Mock backend with latency and failure switches, idempotent on operation id | Repeating an operation id creates no duplicate | 1 h |
| 5 | Sync engine: ordered send, backoff with cap and jitter, Sync now, auto sync on reconnect | Pending becomes Synced. 5xx ends as Failed after the limit and stays visible | 1.5 h |
| 6 | Conflict policy and delete-while-pending-create handling | Edited-elsewhere note is resolved per your policy and shown to the user | 1 h |
| 7 | Tests, README, demo video | Checklist C is complete | 0.5 h |

Local store and queue first. UI polish comes last.

## 2. Directions

| Topic | Direction |
|---|---|
| Source of truth | The local database drives the UI. Never render straight from network responses |
| Atomic write | A note change and its queue entry commit in one transaction |
| IDs | Client-generated note id and operation id. Do not wait for the server to assign ids |
| Retry | Exponential backoff with a cap and jitter. No tight loops. Failed items stay visible |
| Idempotency | Mock server ignores a repeated operation id |
| Conflict policy | Choose one: last-write-wins, version check with keep mine / keep theirs, or field-level merge. Document what is lost |
| Sync states | Show Pending / Synced / Failed / Conflict per note |
| Structure | Keep UI, logic, storage and networking separate. No DB or HTTP calls in UI components |
| Permissions and libraries | Request none you do not need. No analytics, ads or extra libraries |
| Live change | Keep the code ready to add a `pinned` flag (or tags) through model, queue, mock API, conflict handling and tests |
| Scope | Record assumptions and known gaps in the README. Mark AI-assisted code |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../mobile-instructions.md](../mobile-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 01 (the one selected for you)
- [ ] Choose React Native, Flutter, Kotlin or Swift. Note why
- [ ] Verify the toolchain and an emulator (or device) run a hello-world locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets)
- [ ] Pick the local store (SQLite, Room, Core Data, Realm or equivalent)
- [ ] Choose the conflict policy and write down what it can lose
- [ ] Sketch the queue lifecycle: create, update, delete, retry, fail
- [ ] Decide the 5 or more tests (queue, retry, conflict, restart recovery, one error case)
- [ ] Plan the 7 steps above against your available hours

## 4. Checklist B — While developing

### Offline and data
- [ ] Every action works with no connection, with no blocking spinner
- [ ] Note change and queue entry are written in one transaction
- [ ] Notes use client-generated ids and operation ids
- [ ] Search or filter runs on local data
- [ ] Per-note state (Pending / Synced / Failed / Conflict) is visible

### Sync and conflicts
- [ ] Retry uses backoff, cap and jitter. Failed items remain visible with a manual retry
- [ ] Repeated operation id creates no duplicate (test it)
- [ ] Kill the app mid-sync, reopen: queue resumes, nothing lost or duplicated
- [ ] Delete while create is pending collapses or orders correctly
- [ ] Same note edited elsewhere: policy applied and shown to the user
- [ ] Double submit is prevented on slow networks. Timeouts are set
- [ ] Sync on reconnect does not hammer the battery

### Mobile and security
- [ ] Airplane-mode test done on an emulator or device
- [ ] Only needed permissions requested. Likely none for this brief
- [ ] You know what is stored locally, whether it is sensitive and whether it is encrypted
- [ ] No secrets in the app bundle. Synthetic data only
- [ ] Layout works on at least two screen sizes and at large text. Screen reader labels present

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record AI tool usage as you go. You must be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, start mock backend, run app, test. All work
- [ ] At least 5 meaningful tests pass: queue, retry, conflict, restart recovery, one error case
- [ ] Rehearse the scenarios: offline, app killed mid-sync, slow network, 5xx, edited elsewhere, delete while pending create
- [ ] Live-change rehearsal: add `pinned` through model, queue, mock API, conflict handling and tests

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits
- [ ] Demo video on emulator or device: offline edit, kill app, reopen, reconnect, sync
- [ ] Mocked backend runs locally with failure and latency switches
- [ ] README: stack choice and why, conflict policy and its data-loss cases, trade-offs, known gaps
- [ ] README answers the depth checks: local data and encryption, atomic write, retry and battery, small screen and large text
- [ ] AI usage disclosed

### Hygiene
- [ ] No secrets or real data in git history
- [ ] No dead code, stray debug logs or hidden TODOs
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the data model and queue lifecycle
- [ ] Can explain the conflict policy and what it loses
- [ ] Can name the most likely failure mode and how you tested restart recovery
- [ ] Can identify and explain AI-generated code
- [ ] Ready for the live change from section F

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Save note, then enqueue in a separate write | One transaction for both |
| UI reads from the network response | UI reads from the local DB |
| Waiting for server-assigned ids | Client-generated ids and operation ids |
| Tight retry loop | Backoff with cap and jitter |
| Retries create duplicates | Idempotency by operation id on the mock server |
| Failed items silently dropped | Keep them visible with retry |
| Queue held only in memory | Persist it and test kill and reopen |
| Conflict policy undocumented | State it and what is lost |
| Perfect UI, thin sync tests | Queue, retry and recovery first |
