# Assignment 03 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Context and assumptions
- Invent a fictional service and 3–4 data categories it asks for (e.g. contact details, an ID document, location, usage data). Label everything as synthetic.
- State the user assumptions and open questions. Do not cite real laws or products as fact.

### B. Onboarding flow
- Flow map: welcome, account basics, consent choices, review, confirmation.
- Each data category has its own consent card. No bundled or pre-ticked consent.
- Skipping an optional category must keep the user moving.

### C. Consent cards
Each card answers, in plain language:

| Question | Requirement |
|---|---|
| What is asked? | Specific data, named plainly |
| Why? | The purpose in one sentence |
| Who sees it? | Named recipients |
| For how long? | Retention or expiry |
| What if I say no? | Honest consequence |
| How do I change my mind? | Link to withdrawal |

Provide accept and decline with equal visual weight. Short copy, target reading level stated.

### D. Error and recovery
- Network failure on submit, expired session, invalid input, upload rejected, back button mid-flow.
- Progress is preserved. Errors say what happened and what to do next.

### E. Withdrawal of consent
- Findable settings screen listing each consent, its status and date.
- Withdraw one consent in two steps or fewer, with a clear outcome message.
- Show the effect on the service and what happens to existing data.
- Confirmation and a receipt state. Re-granting is possible.

### F. Accessibility and content
- Contrast, keyboard path, focus order, screen-reader labels, error announcements.
- Content guide: tone, banned jargon, label list, one translated or longer-text stress test.
- Sensitive screens avoid showing full data by default.

### G. Scenarios to address
- A user declines the required consent. What happens next?
- A user withdraws consent while a request is in progress.
- A user returns after a month and does not remember agreeing.

### H. Live follow-up
The interviewer may ask you to add a new data category with a consent card, including the withdrawal and error states, and show how copy and components stay consistent.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Use plain, specific language | Use legal jargon or vague phrases like "improve your experience" |
| Give accept and decline equal weight | Use dark patterns, pre-ticked boxes or guilt copy |
| Make withdrawal as easy as granting | Hide withdrawal in deep menus |
| Design error and recovery states | Lose user input on failure |
| Label assumptions and synthetic data | Claim legal compliance or cite real users |
| Reuse shared components and tokens | Create one-off consent styles |
| Disclose AI-generated copy and assets, and review them | Submit unreviewed AI copy |

### Deliverables

| Item | Format |
|---|---|
| Design file | Candidate's choice: Figma link (view access) or exported PDF/PNG set |
| Flow map, consent cards, error and withdrawal screens | Inside the file or exports |
| Content guide and full copy deck | Rationale doc or file |
| Accessibility check summary | Rationale doc |
| Rationale doc (1–2 pages) | Markdown or PDF: decisions, trade-offs, assumptions, AI use |

### Constraints
- Fictional service. Synthetic data only. No real brands.
- Mobile first plus one desktop layout. Light and dark for consent cards.
- Freely licensed fonts and icons.
- Design exercise only. Not legal advice.

### Design discussion (30–45 min)
Walk through one consent card word by word, the withdrawal path, one error state you refined, an accessibility decision, which copy was AI-assisted and how you verified it, and the live new-category change.
