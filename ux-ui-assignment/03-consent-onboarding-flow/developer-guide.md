# Assignment 03 — Developer Guide & Checklists

**v0.1 DRAFT — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step design path and three checklists (before you start, while designing, after you finish) |
| Why | So you spend the 5–7 hours on plain-language consent, recovery and withdrawal, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Context: fictional service, 3–4 data categories, user assumptions, open questions | Everything labelled synthetic or assumption. No real laws or products cited as fact. Each category marked required or optional | 0.5 h |
| 2 | Flow map: welcome, account basics, consent choices, review, confirmation. Include skip, decline, back and error branches | Each category has its own consent step. Skipping an optional category keeps the user moving | 0.75 h |
| 3 | Content guide and consent copy: tone, banned jargon, label list, reading level. One card per category answering the 6 questions | Every card answers what, why, who sees it, how long, what if I say no, how to change my mind | 1 h |
| 4 | Hi-fi mobile screens for the flow and consent cards. Consent cards in light and dark. One desktop layout | Accept and decline have equal visual weight. Nothing pre-ticked or bundled. Shared tokens and components reused | 1.5 h |
| 5 | Error and recovery: network failure on submit, expired session, invalid input, upload rejected, back button mid-flow | Each error says what happened and what to do next. Progress preserved in every case | 0.75 h |
| 6 | Withdrawal: settings list (status and date), withdraw in two steps or fewer, effect on service and existing data, receipt, re-grant | A user can withdraw one consent in two steps or fewer and see the outcome | 0.75 h |
| 7 | Accessibility and stress test: contrast, keyboard path, focus order, screen-reader labels, error announcements, masked sensitive data, one translated or longer-text test | Check summary written with results | 0.5 h |
| 8 | Scenario answers, full copy deck, rationale doc, exports | Checklist C is complete | 0.25 h |

Total about 6 h (brief: 5–7 h). Copy and flow first. Visual polish last.

## 2. Directions

| Topic | Direction |
|---|---|
| Fiction | Invent the service and its data categories. Label all of it synthetic. No real brands |
| Law | Design exercise only. Do not claim legal compliance or cite real laws as fact |
| One card per category | No bundled consent. No pre-ticked boxes |
| Equal weight | Accept and decline share size, style prominence and position logic. No guilt copy |
| Plain language | Specific data, one-sentence purpose, named recipients, stated retention. State your target reading level |
| Banned phrases | Avoid vague lines such as "improve your experience" and legal jargon. List banned terms in the content guide |
| Optional vs required | Skipping an optional category keeps the user moving. Declining a required one has an honest, designed outcome |
| Recovery | Never lose user input. Errors say what happened and what to do next |
| Withdrawal | As easy as granting. Findable settings, two steps or fewer, clear effect on the service and on existing data, receipt, re-grant |
| Sensitive data | Do not show full data by default on sensitive screens (for example mask an ID number) |
| Theming | Light and dark for consent cards at minimum, from shared tokens |
| Live change ready | Make the consent card a reusable component so a new category, with withdrawal and error states, can be added live |
| AI use | Allowed. Disclose AI-generated copy and assets. Review and own them |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../design-instructions.md](../design-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) (where it applies)
- [ ] Read [product-brief.md](product-brief.md) and [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [ ] Confirm you are doing Assignment 03 (not another one)
- [ ] Pick a design tool. Confirm you can share a view-access link or export PDF/PNG
- [ ] Choose freely licensed fonts and icons. Note their licences
- [ ] Name your fictional service and choose 3–4 data categories
- [ ] Decide which category is required and which are optional, and note why
- [ ] Pick a target reading level and how you will check it
- [ ] Plan the 8 steps above against your available hours
- [ ] Start a running list for assumptions, open questions and AI use

## 4. Checklist B — While working

### Flow
- [ ] Welcome, account basics, consent choices, review, confirmation all mapped
- [ ] One consent step per category. No bundling
- [ ] Skip path for optional categories keeps the user moving
- [ ] Decline-required path designed (scenario)

### Consent cards and copy
- [ ] Each card answers all 6 questions in plain language
- [ ] Accept and decline have equal visual weight
- [ ] Nothing pre-ticked. No guilt or dark-pattern copy
- [ ] Target reading level stated
- [ ] Content guide: tone, banned jargon, label list
- [ ] One translated or longer-text stress test done

### Error and recovery
- [ ] Network failure on submit
- [ ] Expired session
- [ ] Invalid input
- [ ] Upload rejected
- [ ] Back button mid-flow
- [ ] Progress preserved in each case. Message says what happened and what to do

### Withdrawal
- [ ] Settings screen is findable and lists each consent with status and date
- [ ] Withdraw one consent in two steps or fewer
- [ ] Effect on the service and on existing data shown
- [ ] Confirmation and receipt state
- [ ] Re-grant possible
- [ ] Withdrawal during an in-progress request designed (scenario)

### Accessibility and system
- [ ] Contrast checked, both themes for consent cards
- [ ] Keyboard path and focus order defined
- [ ] Screen-reader labels and error announcements defined
- [ ] Sensitive screens do not show full data by default
- [ ] Shared tokens and components reused. No one-off consent styles

### Habits
- [ ] Keep a running list of assumptions and open questions
- [ ] Record AI tool use as you go, especially copy (you must disclose it)

## 5. Checklist C — After (before you submit)

### Verify
- [ ] Every requirement section A–G has a visible answer in the file or rationale doc
- [ ] Read every card aloud: specific, short, no jargon, honest consequence
- [ ] Returning-after-a-month scenario designed: the user can see what they agreed to and when
- [ ] Mobile flow complete, plus one desktop layout
- [ ] Live-change rehearsal: add a new data category with consent card, withdrawal and error states, reusing components and copy rules

### Deliverables
- [ ] Design file: Figma link with view access, or exported PDF/PNG set
- [ ] Flow map, consent cards, error and withdrawal screens
- [ ] Content guide and full copy deck
- [ ] Accessibility check summary
- [ ] Rationale doc (1–2 pages): decisions, trade-offs, assumptions, AI use, sources cited

### Hygiene
- [ ] Fictional service, synthetic data. No real brands or people
- [ ] No claim of legal compliance
- [ ] Fonts and icons freely licensed
- [ ] Link opens without a login request (test in a private window), or exports are complete
- [ ] Submitted within the 3-calendar-day window

### Prepare for the discussion (30–45 min)
- [ ] Can walk through one consent card word by word
- [ ] Can walk the withdrawal path
- [ ] Can explain one error state you refined
- [ ] Can explain one accessibility decision
- [ ] Can say which copy was AI-assisted and how you verified it
- [ ] Ready to add a new data category live

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| One "I agree to all" checkbox | One card per category |
| Big Accept, small grey Decline | Equal visual weight |
| "We use your data to improve your experience" | Name the data, purpose, recipients and retention |
| Withdrawal buried in deep menus | Findable settings, two steps or fewer |
| Input lost after a network error | Preserve progress and explain next step |
| Full ID number shown by default | Mask sensitive data by default |
| Claiming the flow is legally compliant | State it is a design exercise |
| Dead end after declining | Design an honest next step |
| Unreviewed AI copy | Review, edit and disclose |
