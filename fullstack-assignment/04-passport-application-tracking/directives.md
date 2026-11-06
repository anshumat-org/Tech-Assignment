# Assignment 04 — Directives

**v1.0 — 2026-11-06**

| ✅ Do | ❌ Don't |
|---|---|
| Put DigiLocker and tracking behind adapter interfaces | Call a provider directly from business logic |
| Label mock and simulated data in the UI and README | Present simulated status as real Passport Seva data |
| Enforce transitions in one state machine, server-side | Trust the client to send a valid next status |
| Sign and expire the callback state/nonce. Make the callback idempotent | Accept a replayed or unsigned callback |
| Record consent, document access, review decisions and status changes in the audit trail | Log document contents, identity numbers or tokens |
| Check ownership and role on every document and application query | Rely on hidden UI buttons for access control |
| Store the minimum: references and metadata | Keep document copies or identity numbers you do not need |
| Offer another permitted upload route when the provider is down | Block the applicant completely |
| Use synthetic data only | Use real personal data or real credentials |
| Never scrape government portals or ask for DigiLocker passwords or OTPs | Handle user authentication secrets in any form |

## Deliverables

| Item | Format reference |
|---|---|
| Working app and GitHub repo | Meaningful commit history |
| HLD diagram | [SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) Section 1 |
| ER diagram, schema, indexes, seed data | Section 2 |
| API documentation | Section 4 |
| State machine diagram with roles per transition | In README or `docs/` |
| Consent, retention and deletion explanation | In README or `docs/` |
| Tests: invalid transitions, duplicate callbacks, provider failure, access control | Section 6 |
| README with setup, assumptions, trade-offs | Section 7 |
| Demo video or screenshots | Section 8 |

## Constraints
- TypeScript preferred. PostgreSQL preferred.
- Mock provider is acceptable and expected if no authorised credentials are supplied.
- Separate presentation, business logic, data access, external integrations.
- Runs locally.

## Technical discussion (30–45 min)
Walk through the state machine, consent capture and revocation, adapter replacement, what you chose not to persist, and how you tested callbacks, failures and access boundaries.
