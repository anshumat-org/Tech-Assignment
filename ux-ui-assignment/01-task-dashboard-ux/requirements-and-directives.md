# Assignment 01 — Requirements & Directives

**v0.1 DRAFT — 2026-11-06**

## Part 1 — Requirements

### A. Research notes (assumption-based)
- Write 2 personas, each labelled **Assumption**. Include goals, pain points, context of use.
- List 5–8 user needs or jobs-to-be-done and the open questions you would validate with real users.
- Note any AI assistance used. Do not invent statistics or quotes.

### B. User flows
Provide flow diagrams (any format) for at least:

| Flow | Must show |
|---|---|
| Create a task | Entry points, validation, success, cancel |
| Triage my day | Filter, sort, change status, bulk action |
| Review team workload | Assignee view, overdue, reassign |
| Recover from failure | Save failure, offline, undo delete |

### C. Information architecture and wireframes
- Navigation model and screen inventory.
- Low-fidelity wireframes for dashboard, task detail, create/edit, filters.
- Explain layout choices against the needs in section A.

### D. Hi-fi screens
- Dashboard, task detail, create/edit, empty first-run, filtered-no-results.
- Light and dark theme for the dashboard at minimum.
- Desktop plus one small-screen layout of the dashboard.

### E. States
- Every key screen shows: default, loading, empty, error, success, disabled.
- Destructive actions (delete) use a deliberate confirmation or undo.
- Status and priority never rely on colour alone.

### F. Accessibility
- Contrast check results for text and key UI.
- Keyboard path for creating and completing a task, with visible focus.
- Text alternatives, heading structure, announced toasts.

### G. Scenarios to address
- A user has 300 overdue tasks. What does the dashboard show first?
- A task title is 200 characters long. How does it behave in list and detail?
- Two people edit the same task. What does the second person see?

### H. Live follow-up
The interviewer may ask you to add a **Blocked** status, with a reason field, and update the dashboard, filters, detail view and states live. Show which shared components and tokens you reuse so the change stays consistent.

## Part 2 — Directives

| ✅ Do | ❌ Don't |
|---|---|
| Label personas and research as assumptions | Present invented research or metrics as fact |
| Tie every screen to a stated need | Add screens or features with no user need |
| Reuse tokens and components | Make one-off styles per screen |
| Design failure, empty and loading states | Show only the happy path |
| Check contrast and keyboard path | Rely on colour alone for status |
| Disclose AI-generated assets, copy and layouts, and review them | Submit unreviewed AI output |
| Record open questions | Guess silently on ambiguity |

### Deliverables

| Item | Format |
|---|---|
| Design file | Candidate's choice: Figma link (view access) or exported PDF/PNG set |
| Research notes, personas (labelled assumptions), flows | Inside the file or in the rationale doc |
| Wireframes and hi-fi screens with all states | Inside the file or exports |
| Accessibility check summary | Rationale doc |
| Rationale doc (1–2 pages) | Markdown or PDF: decisions, trade-offs, assumptions, AI use |

### Constraints
- Any design tool. Fonts and icons must be freely licensed.
- Synthetic content only. No real brands or user data.
- Light and dark theme for the dashboard.
- Do not exceed the effort range. Note what you would do next.

### Design discussion (30–45 min)
Walk through the main flow and the need behind it, one state you almost missed, one accessibility decision, which assets were AI-assisted and how you verified them, and the live Blocked-status change.
