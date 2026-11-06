# Assignment 04 — Requirements

**v1.0 — 2026-11-06**

## A. Core requirements

| Area | Requirement |
|---|---|
| Applicant profile | Capture minimum required details. User can review and edit before proceeding |
| Application checklist | Configurable document requirements by application type (for example fresh or re-issue) and applicant scenario. Flag missing, pending, verified, rejected |
| DigiLocker connection | Consent-led adapter. Show connect, authorisation/callback, document discovery, user selection and retrieval using an approved sandbox or a labelled mock |
| Document vault | Show document metadata and verification state. Store no more personal data or document copies than the workflow needs |
| Review workflow | Operator reviews a package, requests corrections, accepts or rejects checklist items, adds a reason |
| Application tracking | Timeline: Draft, Documents Pending, Ready for Review, Under Review, Correction Required, Submitted (simulated), Closed. Record who changed status and when |
| Notifications | In-app notification or email mock on status change or when applicant action is required |
| Audit trail | Record consent events, document access/retrieval, checklist decisions, status changes |

## B. Architecture expectations
- HLD showing applicant UI, operator dashboard, backend API, relational database, secure document storage (if used), notification adapter, DigiLocker adapter, simulated passport tracking adapter.
- Provider-specific code behind interfaces so mock and authorised sandbox implementations swap without rewriting application logic.
- Status state machine. Reject invalid transitions. State which roles may perform each transition.
- Signed, expiring state/nonce for the authorisation callback. Validate state and handle retries safely.
- Encryption in transit and at rest, role-based and least-privilege access, secure secret management, redacted logs.
- Consent is purpose-specific, visible, revocable where applicable and auditable. Explain retention and deletion choices.
- No access tokens, identity numbers, document contents or other sensitive values in URLs, analytics events or logs.

## C. Database (suggested)

| Entity | Purpose |
|---|---|
| users / applicant_profiles | Account, profile, contact details. Only necessary fields |
| passport_applications | Type, reference number (simulated if needed), current status, timestamps |
| document_requirements | Type or scenario, required document type, rules and version |
| application_documents | Document type, source, provider reference, metadata, verification state |
| digilocker_connections | Provider subject or reference, state, consent scope, expiry and revocation. Never user password or OTP |
| consent_records | User, purpose, scopes, consent and withdrawal timestamps, provider transaction reference |
| application_reviews | Reviewer, decision, reason, timestamp |
| status_events | Previous status, new status, actor, reason, timestamp |
| notifications | Recipient, event, channel, delivery state, created_at |
| audit_events | Actor, action, resource, timestamp, correlation ID. No document contents or secrets |

## D. API scope (adjustable if documented)

| Method | Endpoint |
|---|---|
| POST | /applications |
| GET | /applications/{id} |
| GET | /applications/{id}/checklist |
| POST | /applications/{id}/digilocker/connect |
| GET | /integrations/digilocker/callback |
| GET | /integrations/digilocker/documents |
| POST | /applications/{id}/documents/link |
| PATCH | /applications/{id}/documents/{documentId}/review |
| POST | /applications/{id}/status-transitions |
| GET | /applications/{id}/timeline |

## E. Engineering scenarios to address
- The user withdraws DigiLocker consent after linking documents. What becomes inaccessible, and how is the application represented?
- The provider callback is received twice. How is the flow idempotent?
- A document is retrieved but fails the checklist rules. How is that communicated?
- An operator attempts an invalid status transition. Where is it rejected and audited?
- A user starts on one device and continues on another. What data is synchronised?
- The provider is unavailable. Can the applicant continue with another permitted upload route?
- How do you prevent one applicant or reviewer from accessing another applicant's documents?

## F. Reviewer prompts
1. How did you model status transitions and prevent invalid ones?
2. Show how consent is captured, checked and revoked.
3. Show how the mock adapter could be replaced by an authorised provider.
4. What sensitive data did you deliberately choose not to persist?
5. Show how you tested duplicate callbacks, provider failures and access-control boundaries.
