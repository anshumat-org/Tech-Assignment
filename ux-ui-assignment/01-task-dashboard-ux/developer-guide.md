# Assignment 01 — Developer Guide & Checklists

**v0.1 DRAFT — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step design path and three checklists (before you start, while designing, after you finish) |
| Why | So you spend the 6–8 hours on framing, flows and full state coverage, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Research notes: 2 personas labelled **Assumption**, 5–8 user needs or jobs-to-be-done, open questions | Each need is numbered so screens can point back to it. No invented statistics or quotes | 0.75 h |
| 2 | User flows: create a task, triage my day, review team workload, recover from failure | Each flow shows what the brief lists (entry, validation, success, cancel, filter, sort, bulk, reassign, offline, undo delete) | 1 h |
| 3 | IA: navigation model and screen inventory. Low-fi wireframes for dashboard, task detail, create/edit, filters | Every screen names the need it serves. Layout choices explained against section A | 1.25 h |
| 4 | Set up from [../../shared/design-system/README.md](../../shared/design-system/README.md): tokens, core components, light and dark | Screens use shared tokens and components only. Any extension or replacement noted with a reason | 0.5 h |
| 5 | Hi-fi: dashboard, task detail, create/edit, empty first-run, filtered-no-results. Dashboard in light and dark, plus one small-screen dashboard | All required hi-fi screens exist. Status and priority use text or icon, not colour alone | 1.5 h |
| 6 | States: default, loading, empty, error, success, disabled on every key screen. Delete confirmation or undo | A reviewer can find every state for every key screen without asking | 1 h |
| 7 | Accessibility: contrast results, keyboard path for create and complete, focus, text alternatives, headings, announced toasts | Check summary written with results, not just intentions | 0.5 h |
| 8 | Scenario answers (300 overdue, 200-char title, two editors), rationale doc, exports | Checklist C is complete | 0.5 h |

Total about 7 h (brief: 6–8 h). Framing, flows and states first. Visual polish last.

## 2. Directions

| Topic | Direction |
|---|---|
| Research | Personas and needs are assumptions. Label them. Write open questions instead of guessing |
| Traceability | Give each need an ID (for example N1–N8) and tag screens and flows with it |
| Scope | No screen or feature without a stated need. Note "what I would do next" instead of overrunning |
| System reuse | Start from the shared design system. Reuse tokens and components. No one-off styles per screen |
| Status and priority | Text label plus icon or shape. Colour is a support, never the only signal |
| Destructive actions | Delete uses a deliberate confirmation or an undo. State which and why |
| States | Design default, loading, empty, error, success and disabled. Failure and empty are not optional |
| Theming | Light and dark for the dashboard at minimum. Both from the same semantic tokens |
| Small screen | One usable small-screen dashboard layout. Show what collapses or moves |
| Long content | Decide truncation, wrapping and full-text access for long titles in list and detail |
| Conflicts | Decide what the second editor sees when two people edit one task, and design that state |
| Live change ready | Build so a new **Blocked** status with a reason field can be added by reusing the status chip, filter and detail components |
| AI use | Allowed. Disclose AI-generated assets, copy and layouts. Review and own them |
| Content | Synthetic only. No real brands or user data. Freely licensed fonts and icons |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../design-instructions.md](../design-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) (where it applies)
- [ ] Read [product-brief.md](product-brief.md) and [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [ ] Confirm you are doing Assignment 01 (not another one)
- [ ] Pick a design tool. Confirm you can share a view-access link or export PDF/PNG
- [ ] Choose freely licensed fonts and icons. Note their licences
- [ ] Decide: use the shared design system as-is, extend it, or replace it (with a reason)
- [ ] Write down your first assumptions about users, team size and task fields
- [ ] Plan the 8 steps above against your available hours
- [ ] Start a running list for assumptions, open questions and AI use

## 4. Checklist B — While working

### Framing and flows
- [ ] Both personas labelled **Assumption**, with goals, pain points and context of use
- [ ] 5–8 needs written, each with an ID
- [ ] Open questions listed for validation with real users
- [ ] Create-task flow shows entry points, validation, success and cancel
- [ ] Triage flow shows filter, sort, change status and bulk action
- [ ] Team workload flow shows assignee view, overdue and reassign
- [ ] Recovery flow shows save failure, offline and undo delete

### Structure and screens
- [ ] Navigation model and screen inventory done
- [ ] Wireframes for dashboard, task detail, create/edit and filters
- [ ] Each screen tagged with the need(s) it serves
- [ ] Hi-fi: dashboard, task detail, create/edit, empty first-run, filtered-no-results
- [ ] Dashboard in light and dark. One small-screen dashboard layout

### States and scenarios
- [ ] Every key screen: default, loading, empty, error, success, disabled
- [ ] Delete has a confirmation or undo
- [ ] 300 overdue tasks: what the dashboard shows first is decided, designed and explained
- [ ] 200-character title: behaviour defined in list and in detail
- [ ] Two editors: second person's view designed (conflict, warning or merge)

### Accessibility and system
- [ ] Status and priority never colour-only
- [ ] Contrast checked for text and key UI, both themes
- [ ] Keyboard path for create and complete a task, with visible focus
- [ ] Text alternatives, heading structure, toasts announced
- [ ] Tokens and components reused. No hard-coded one-off styles

### Habits
- [ ] Name frames and pages clearly so a reviewer can navigate
- [ ] Keep a running list of assumptions, trade-offs and shortcuts
- [ ] Record AI tool use as you go (you must disclose it)

## 5. Checklist C — After (before you submit)

### Verify
- [ ] Every requirement section A–G has a visible answer in the file or rationale doc
- [ ] Every screen traces to a need. No screen without one
- [ ] All six states present on every key screen
- [ ] Contrast and keyboard checks recorded with results
- [ ] Live-change rehearsal: add **Blocked** with a reason field to the dashboard, filters, detail and states using existing components

### Deliverables
- [ ] Design file: Figma link with view access, or exported PDF/PNG set
- [ ] Research notes, personas (labelled assumptions) and flows
- [ ] Wireframes and hi-fi screens with all states
- [ ] Accessibility check summary
- [ ] Rationale doc (1–2 pages): decisions, trade-offs, assumptions, AI use, what you would do next, sources cited

### Hygiene
- [ ] Synthetic content only. No real brands, people or user data
- [ ] Fonts and icons freely licensed
- [ ] Link opens without a login request (test in a private window), or exports are complete
- [ ] Submitted within the 3-calendar-day window

### Prepare for the discussion (30–45 min)
- [ ] Can walk the main flow and the need behind it
- [ ] Can name one state you almost missed
- [ ] Can explain one accessibility decision
- [ ] Can say which assets were AI-assisted and how you verified them
- [ ] Ready to add the Blocked status live

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Personas presented as real research | Label them **Assumption**. Add open questions |
| Happy path only | Design loading, empty, error, success and disabled |
| Red text as the only overdue signal | Add a label, count or icon |
| Screens with no stated need | Tie each screen to a need ID, or cut it |
| One-off colours per screen | Use semantic tokens from the design system |
| Dark mode as an afterthought | Build both themes from the same tokens and check contrast in each |
| Delete with no safety net | Confirmation or undo |
| Long title breaks the row | Define truncation and full-text access |
| Unreviewed AI layouts or copy | Review, edit and disclose |
| Overrunning the effort range | Stop at 8 h and list next steps |
