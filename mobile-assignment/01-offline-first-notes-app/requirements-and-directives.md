# Assignment 01 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Functional requirements
- Create, view, edit and delete a note. Fields: id, title, body, updated_at, sync_status, version.
- All actions work with no connection. The UI never blocks on the network.
- Show per-note sync state (Pending / Synced / Failed / Conflict).
- Search or filter the list locally.
- Manual "Sync now" action plus automatic sync when connectivity returns.

### B. Local data and sync queue (suggested)

| Part | Suggested design |
|---|---|
| Local store | SQLite, Room, Core Data, Realm or equivalent. Notes are the source of truth for the UI |
| Outbox / queue | Ordered operations: create, update, delete, with client-generated id and operation id |
| Retry | Exponential backoff with a cap and jitter. Failed items stay visible |
| Idempotency | Mock server ignores a repeated operation id, so retries cannot duplicate |
| Mock backend | Local server or in-app fake with configurable latency and failure rate |

### C. Conflict policy (choose one, document it)
- Last-write-wins by server timestamp, or
- Version check with a user-visible resolution (keep mine / keep theirs), or
- Field-level merge.

Explain what is lost under your policy and why that is acceptable.

### D. Scenarios to address

| Scenario | Expected behaviour |
|---|---|
| Offline | Edits saved locally, queued, visible as Pending |
| App killed mid-sync | On reopen the queue resumes; no lost or duplicated notes |
| Slow network | Non-blocking UI, timeouts, retry, no double submit |
| Server error (5xx) | Retry with backoff; item shows Failed after the limit |
| Same note edited elsewhere | Conflict policy applied and shown to the user |
| Delete while pending create | Operations collapse or order correctly |

### E. Engineering depth checks (answer in README)
- What is stored locally, and is any of it sensitive? Is it encrypted?
- How do you guarantee a local write and its queue entry commit together?
- How do you avoid battery drain from aggressive retries?
- How does the UI behave on a small screen and at large text size?

### F. Live follow-up
The interviewer may ask you to add a **pinned** flag (or a tags field) and carry it through the model, queue, mock API, conflict handling and tests, or to change the conflict policy. Structure the code so this is a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Treat the local database as the UI's source of truth | Read UI state straight from network responses |
| Write the change and its queue entry in one transaction | Save a note and enqueue it as two unrelated writes |
| Use client-generated ids and operation ids for idempotency | Rely on the server to assign ids before showing a note |
| Cap and back off retries | Retry in a tight loop |
| Keep UI, logic, storage and networking separate | Call the database or HTTP from UI components |
| Request no permissions you do not need | Add analytics, ads or extra libraries |
| Record assumptions and mark AI-assisted code | Hide limitations |

### Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Demo video on emulator or device: offline edit, kill app, reopen, reconnect, sync | Section 8 |
| Mocked backend, runnable locally, with failure and latency switches | Section 7 |
| At least five meaningful tests (queue, retry, conflict, restart recovery, one error case) | Section 6 |
| Short README: stack choice and why, conflict policy, trade-offs, known gaps | Section 7 |

### Constraints
- React Native, Flutter, Kotlin or Swift. State the choice and why.
- Mocked backend only. No real accounts or paid services.
- Synthetic data only.
- Follow [../mobile-instructions.md](../mobile-instructions.md).
- Works on at least two screen sizes.

### Technical discussion (30–45 min)
Walk through the data model, the queue lifecycle, the conflict policy and its data-loss cases, the most likely failure mode, and how you tested restart recovery. Identify AI-generated code and explain it. Expect a live change from section F.
