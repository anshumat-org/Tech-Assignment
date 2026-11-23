# Assignment 03 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 5–7 hours on schema, autosave and failure handling, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Schema (one source) and data-driven step config for 4 steps | Types and validators derive from the schema. Adding a step is a small change | 1 h |
| 2 | Mock API: `GET /drafts/{id}`, `PUT /drafts/{id}`, `POST /submissions` | Mock simulates latency, 500, timeout, 409, 422 and offline | 1 h |
| 3 | Form UI: steps, progress, Back and jump to completed step, repeating group | Back never loses data. Inline errors on blur, step errors on Next, all errors on submit | 1 h |
| 4 | Autosave state machine and resume | Status shows Saving, Saved, Failed, Offline. Saved appears only after server confirms. Reopening restores draft and last step | 1.5 h |
| 5 | Conflict, retry and submit handling | 409 handled. Saves retried with backoff. Submit has an idempotency key. 422 maps to the right field, even on an earlier step | 1 h |
| 6 | Accessibility pass | Error summary gets focus on failed Next or submit. Step change moves focus to the heading. Status in a polite live region | 0.5 h |
| 7 | Review step and success with reference id | Review lists all answers with edit links | 0.5 h |
| 8 | Tests (6+), README scenario answers, API note, video or screenshots | Checklist C is complete | 0.5 h |

Total about 7 h (brief: 5–7 h, so cut the optional polish first). Build the schema and save flow before styling.

## 2. Directions

| Topic | Direction |
|---|---|
| Schema | Define once (for example Zod). Derive types and validators. Field, step and submit checks share it |
| Steps | Suggested: Personal, Contact, Details (repeating group), Review and submit. Synthetic fields only. Make steps data-driven |
| Separation | Form state, persistence and presentation are separate. No API calls inside field components |
| Autosave | Debounced. Honest status: Saving, Saved, Failed, Offline. Never show Saved before the server confirms |
| Versioning | Use the draft `version`. 409 on mismatch must not overwrite blindly |
| Retry | Queue and retry saves with backoff |
| Submit | Use an idempotency key. No double submit. Handle a lost response |
| Server errors | Map 422 to fields, focus the first one, send the user to the right step. Unknown-field messages go in a form-level summary |
| Resume | Restore draft and last step on reopen. Say how an old draft schema loads |
| Accessibility | Label, hint and error linked by `aria-describedby`. Error summary with links. Step changes announced. No colour-only meaning |
| Sensitive data | Decide what lives in memory, storage and logs. Nothing sensitive in logs or URLs. No secrets in client code |
| Width and keyboard | Works by keyboard and at 360 px |
| Live follow-up | Be ready to add a conditional step or a file-upload field with retry. Validation, autosave, review and tests should adapt |
| Scope | List known gaps in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [../frontend-instructions.md](../frontend-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 03 (not another one)
- [ ] Choose framework (TypeScript preferred), schema library (for example Zod) and mock tool (MSW or json-server). Note any unusual choice and why
- [ ] Verify Node (or runtime), package manager and a test runner work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Write down the API contract, versioning and assumptions
- [ ] Sketch the autosave state machine (states, events, transitions)
- [ ] List the fields per step and which ones are sensitive
- [ ] Choose tokens from [../../shared/design-system/README.md](../../shared/design-system/README.md) or document your own
- [ ] Plan the 8 steps above against your available hours
- [ ] Decide the 6+ tests you will write (422 mapping, 409 conflict and offline are required)

## 4. Checklist B — While developing

### Schema and form
- [ ] One schema drives field, step and final validation
- [ ] Steps come from config, not hard-coded logic spread across components
- [ ] Progress indicator works. Back keeps data. Jump to a completed step works
- [ ] Repeating group can add and remove items
- [ ] Inline errors on blur, step-level errors on Next, all errors on submit
- [ ] Review lists all answers with edit links. Submit shows a reference id

### Autosave and resume
- [ ] Autosave is debounced and shows Saving, Saved, Failed, Offline
- [ ] Saved is shown only after the server confirms
- [ ] Failed saves are retried with backoff. Offline recovery is tested (returns after about 30 seconds)
- [ ] 409 conflict is handled. The second tab does not silently overwrite
- [ ] Closing with unsaved changes is protected
- [ ] Reopening restores the draft and the last step
- [ ] Old draft schema loads as you documented

### Server errors and submit
- [ ] 422 field errors map to the right field, even on an earlier step, and focus goes there
- [ ] Unknown-field server messages appear in a form-level summary
- [ ] Submit uses an idempotency key. No duplicate when the response is lost
- [ ] 500 and timeout show a clear message and a retry path

### Accessibility
- [ ] Every field has label, hint and error linked by `aria-describedby`
- [ ] Failed Next or submit moves focus to an error summary with links to fields
- [ ] Step change is announced and focus moves to the step heading
- [ ] Autosave status is in a polite live region. No colour-only meaning
- [ ] Works by keyboard and at 360 px

### Security and data
- [ ] No sensitive values in logs, URLs or needless storage
- [ ] No secrets in client code. Synthetic data only

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and gaps for the README
- [ ] Record any AI tool usage and reused code as you go. Verify it and be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, start, test. All work
- [ ] At least 6 meaningful tests pass, including 422 mapping, 409 conflict and offline
- [ ] Failure paths are tested, not mocked away
- [ ] Walk the scenarios in the app: network drop mid-save, two tabs, tab close, lost submit response

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits (SUBMISSION_FORMATS.md Section 7)
- [ ] Working app with mock API, plus demo video or screenshots that include a failure (Section 8)
- [ ] Short note on API contract, versioning and assumptions (Section 1)
- [ ] Short README with trade-offs and a list of known gaps
- [ ] README answers all six scenarios: network drop, two tabs, tab close, lost submit response, draft schema change, sensitive data location

### Hygiene
- [ ] No secrets or `.env` in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] AI-generated or reused code is marked and verified
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (30–45 min)
- [ ] Can show the schema and where it is used
- [ ] Can explain the save state machine
- [ ] Can walk one network failure end to end
- [ ] Can explain your accessibility choices for errors
- [ ] Ready for a live change such as a new conditional step or file-upload field with retry

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Validation rules repeated per field, step and submit | One schema, shared |
| API calls inside field components | Separate form state, persistence and presentation |
| "Saved" shown before the server replies | Show Saved only after confirmation |
| Blind draft overwrite | Version check and 409 handling |
| Double submit after a lost response | Idempotency key |
| Generic "Something went wrong" | Map 422 to fields and focus the first one |
| 422 for an earlier step ignored | Navigate to that step and focus the field |
| Step logic hard-coded in many places | Data-driven steps |
| Only happy path tested | Test 422, 409, offline and timeout |
| Sensitive values in logs or URLs | Keep out of logs, URLs and needless storage |
