# Assignment 03 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Functional requirements
- 4 steps (suggested: Personal, Contact, Details with a repeating group, Review and submit). Synthetic fields only.
- Step navigation with progress indicator. Back never loses data. Jumping to a completed step is allowed.
- Validation from one schema, shared by field, step and final submit checks.
- Autosave draft after edits (debounced) with visible status: Saving, Saved, Failed, Offline.
- Resume: reopening the app restores the draft and the last step.
- Review step lists all answers with edit links. Submit shows success with a reference id.

### B. Mocked API (suggested, adjustable if documented)

| Method | Endpoint | Purpose |
|---|---|---|
| GET | /drafts/{id} | Load draft with `version` |
| PUT | /drafts/{id} | Save draft. Returns new `version`, 409 on version mismatch |
| POST | /submissions | Final submit. May return 422 with field errors |

- Mock must simulate latency, 500s, timeouts, 409 conflicts, 422 field errors and offline.

### C. Validation and server errors
- Inline errors on blur, step-level errors on Next, all errors on submit.
- Map 422 field errors from the server to the right field, even on an earlier step, and send the user there.
- Server message for an unknown field is shown in a form-level summary, never swallowed.

### D. Accessibility
- Every field has a label, hint and error linked by `aria-describedby`.
- On failed Next or submit, focus moves to an error summary with links to fields.
- Step changes are announced and focus moves to the step heading.
- Autosave status is in a polite live region. No colour-only meaning. Works at 360 px.

### E. Scenarios to address (answer in README)
- The network drops mid-save and returns 30 seconds later. What does the user see, and what is retried?
- The same draft is open in two tabs and one saves first (409). What happens to the other?
- The user closes the tab with unsaved changes. What is protected?
- Submit succeeds on the server but the response is lost. How do you avoid a duplicate?
- Draft schema changes between releases. How does an old draft load?
- Where does sensitive data live (memory, storage, logs)? What do you avoid persisting?

### F. Live follow-up
The interviewer may ask you to add a **conditional step** (shown only for some answers) or a **file-upload field with retry**. Validation, autosave, review and tests must adapt with a small change.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Define the schema once and derive types and validators from it | Repeat rules in each field, step and submit handler |
| Keep form state, persistence and presentation separate | Mix API calls into field components |
| Use version checks and idempotency keys for saves and submit | Overwrite drafts blindly or allow double submit |
| Queue and retry saves with backoff, and show honest status | Show "Saved" before the server confirms |
| Map server errors to fields and focus the first one | Show a generic "Something went wrong" only |
| Make steps data-driven so adding one is small | Hard-code step logic across components |
| Test failure paths, not only the happy path | Mock away the failures you were asked to handle |
| Mark AI-generated or reused code and verify it | Submit code you cannot explain |

### Deliverables

| Item | Format reference |
|---|---|
| Git repo with setup instructions and meaningful commits | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 7 |
| Working app with mock API, plus demo video or screenshots including a failure | Section 8 |
| Short note on API contract, versioning and assumptions | Section 1 |
| At least six meaningful tests, including 422 mapping, 409 conflict and offline | Section 6 |
| Short README with trade-offs and a list of known gaps | Section 7 |

### Constraints
- Any framework. TypeScript preferred.
- Mock API only (MSW, json-server or similar). Synthetic data only.
- No secrets in client code. Do not store sensitive values in logs or URLs.
- Works by keyboard and at 360 px width.
- Follow [../frontend-instructions.md](../frontend-instructions.md).

### Technical discussion (30–45 min)
Walk through the schema and where it is used, the save state machine, one network failure end to end, and your accessibility choices for errors. Expect a live change such as a new conditional step.
