# Assignment 04 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 6–8 hours on the state machine, consent and access control, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

Steps total 7 h, inside the 6–8 h window.

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema: profiles, applications, requirements, documents, connections, consent, reviews, status events, notifications, audit | Migrations run from clean. Seed has synthetic applicants and an operator | 1 h |
| 2 | Status state machine, one server-side place, with roles per transition | Invalid transitions are rejected and audited. Every change writes a status event | 1 h |
| 3 | Auth, roles and ownership checks | Applicant A cannot read applicant B's application or documents | 1 h |
| 4 | Adapter interfaces and mocks: DigiLocker, notifications, tracking | Swapping the mock needs no change to business logic | 1 h |
| 5 | Consent-led DigiLocker flow: signed expiring state, idempotent callback, document discovery and link, withdraw | Duplicate callback is safe. Withdrawal blocks access. Provider-down shows an upload route | 1.25 h |
| 6 | Checklist and operator review, notifications | Reject needs a reason. Applicant is notified when action is needed | 0.75 h |
| 7 | UI, tests, docs, demo | Checklist C is complete | 1 h |

Security and the state machine first. UI last.

## 2. Directions

| Topic | Direction |
|---|---|
| Boundary | Not the official passport system. Label mock and simulated data in the UI and README. Never scrape portals or ask for DigiLocker passwords or OTPs |
| Adapters | DigiLocker, notifications and tracking sit behind interfaces. Mock now, authorised sandbox later without rewriting logic |
| State machine | Draft, Documents Pending, Ready for Review, Under Review, Correction Required, Submitted (simulated), Closed. Enforce in one place, server-side. State roles per transition |
| Callback | Signed, expiring state/nonce. Validate it. Make the callback idempotent. Reject replay and unsigned requests |
| Consent | Purpose-specific, visible, revocable and audited. Explain retention and deletion |
| Minimum data | Store references and metadata. No document copies or identity numbers you do not need |
| Logs and URLs | No tokens, identity numbers or document contents in URLs, analytics or logs. Redact |
| Access control | Check ownership and role on every document and application query. Hidden buttons are not access control |
| Provider down | Applicant can use another permitted upload route |
| Audit | Record consent events, document access, checklist decisions and status changes with a correlation ID |
| Data | Synthetic only. No real credentials |
| Scope | If you skip something, list it under "Limitations" in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [design-system/README.md](design-system/README.md), [../developer-instructions.md](../developer-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 04 (not another one)
- [ ] Re-read the "Important boundary" table in the README
- [ ] Write down assumptions: roles, allowed transitions, retention, what withdrawal makes inaccessible, fallback upload route
- [ ] Choose stack: TypeScript and PostgreSQL preferred. Note any change and why
- [ ] Verify runtime, database and package manager work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore` (no secrets, no `.env` committed)
- [ ] Draw the state machine with roles per transition
- [ ] Draft the ER diagram and a one-page HLD covering applicant UI, operator dashboard, API, database, adapters (Mermaid is fine)
- [ ] Decide what sensitive data you will deliberately not persist
- [ ] Plan the 7 steps above against your available hours
- [ ] Plan tests for: invalid transitions, duplicate callbacks, provider failure, access control
- [ ] Plan synthetic seed data: applicants, an operator, requirement sets for fresh and re-issue

## 4. Checklist B — While developing

### State machine and workflow
- [ ] All transitions go through one function
- [ ] Invalid transition is rejected server-side and audited
- [ ] Each transition checks the actor's role
- [ ] Each status change stores previous, new, actor, reason and time
- [ ] Checklist items support missing, pending, verified and rejected, with a reason on reject
- [ ] Requirements are configurable by application type and scenario

### DigiLocker adapter and consent
- [ ] Flow covers connect, authorise or callback, discover, select, retrieve
- [ ] State/nonce is signed and expires. Bad or replayed state is refused
- [ ] Duplicate callback leaves one connection and one set of documents
- [ ] Consent records purpose, scopes, grant and withdrawal times
- [ ] Withdrawal makes linked documents inaccessible and the application shows it
- [ ] Provider-unavailable state offers "upload instead"
- [ ] A document that fails a checklist rule explains why to the applicant

### Security and privacy
- [ ] Ownership and role checked on every application and document query
- [ ] Applicant cannot see another applicant's data. Operator access follows least privilege
- [ ] Identity numbers masked. Metadata shown, not contents
- [ ] No tokens, identity numbers or document contents in URLs or logs
- [ ] Secrets come from environment, not code
- [ ] Audit events for consent, document access, review decisions and status changes

### API and UI
- [ ] Endpoints in the brief work (or documented adjustments). Input validated, consistent errors
- [ ] Persistent badge "Simulated. Not the official passport system" on submission and tracking views
- [ ] Timeline shows status, actor, time and reason, with the current step highlighted
- [ ] Operator can accept or reject each item with a required reason, and request corrections
- [ ] In-app notifications with unread state
- [ ] Loading, empty, error, provider unavailable and consent withdrawn states designed

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and shortcuts for the README
- [ ] Record any AI tool usage as you go (you must disclose it)

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, migrate, seed, start, test. All work
- [ ] One command runs all tests
- [ ] Tests cover invalid transitions, duplicate callbacks, provider failure and access-control boundaries
- [ ] Tests or demo cover the seven engineering scenarios: consent withdrawal, duplicate callback, failed checklist rule, invalid operator transition, second device, provider down, cross-user access
- [ ] Grep logs and URLs for tokens, identity numbers and document contents. None found
- [ ] Prove the mock adapter can be replaced by showing the interface boundary

### Deliverables
- [ ] HLD diagram ([SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 1)
- [ ] ER diagram, schema, indexes, seed data (Section 2)
- [ ] API documentation (Section 4)
- [ ] State machine diagram with roles per transition, in README or `docs/`
- [ ] Consent, retention and deletion explanation, in README or `docs/`
- [ ] `docs/testing.md` (Section 6)
- [ ] Demo video or screenshots, simulation labels visible (Section 8)
- [ ] README contains: overview, quick start, assumptions, trade-offs, limitations, future work, AI usage disclosure, what you chose not to persist (Section 7)

### Hygiene
- [ ] No secrets, `.env` or real data in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] Commit history is meaningful
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the state machine and how invalid moves are blocked
- [ ] Can show consent capture, check and revocation
- [ ] Can show how the mock adapter is swapped for an authorised provider
- [ ] Can name what sensitive data you chose not to persist
- [ ] Can show how you tested duplicate callbacks, provider failures and access boundaries

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Client sends the next status and the server accepts it | One server-side state machine with role checks |
| Unsigned or replayable callback | Signed, expiring state and idempotent handling |
| Provider called straight from business logic | Adapter interface with a mock |
| Simulated status shown as real | Persistent "Simulated" label in UI and README |
| Access control only by hiding buttons | Ownership and role check in every query |
| Document contents or ID numbers in logs | Store references, redact logs |
| Consent withdrawal changes nothing | Revoke access and reflect it on the application |
| Provider outage blocks the applicant | Offer another permitted upload route |
| Audit only on success | Audit rejected transitions too |
