# Assignment 02 — Directives

**v1.0 — 2026-11-06**

| ✅ Do | ❌ Don't |
|---|---|
| Write locally first, then sync | Block editing on network calls |
| Give every node a stable ID generated on the client | Rely on server-assigned IDs for offline creates |
| Make sync operations idempotent, with retry | Apply the same operation twice |
| Use a cursor or version for pull | Re-download everything every time |
| Keep AI output separate from the original note | Overwrite the user's text with AI output |
| Show AI suggestions for review and edit before applying | Auto-apply extraction |
| Validate AI output against a schema; handle timeout and failure | Trust raw model output |
| Keep AI keys on the server | Put keys in the frontend or the repo |
| Show online/offline and sync state | Fail silently |
| Document the conflict strategy for edits and deletes | Leave conflicts undefined |

## Deliverables

| Item | Format reference |
|---|---|
| Working PWA or web app and GitHub repo | Meaningful commit history |
| HLD diagram | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 1 |
| ER diagram, schema, indexes | Section 2 |
| API documentation and AI integration notes | Section 4 |
| Sitemap of screens | Section 11 |
| Local setup and test cases | Section 6 and 7 |
| Demo of offline edit and sync | Section 8 |

## Constraints
- TypeScript where practical. Justify major choices.
- Separate UI, business logic, local storage, remote storage, AI, sync.
- Runs locally without mandatory paid infrastructure.
- Synthetic data only.

## Technical discussion (30–45 min)
Expect to demo offline edit then reconnect, explain conflict handling, walk through the AI review flow, and explain what changes before production.
