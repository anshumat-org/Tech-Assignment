# Assignment 02 — Developer Guide & Checklists

**v0.1 DRAFT — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step design path and three checklists (before you start, while designing, after you finish) |
| Why | So you spend the 6–8 hours on token architecture, full component states and contrast checks, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Review [../../shared/design-system/README.md](../../shared/design-system/README.md). Decide extend or replace. Write consumer assumptions | Decision and reason written. Assumed consumers labelled as assumptions | 0.5 h |
| 2 | Raw tokens: colour, type scale, spacing (4px grid suggested), radius, elevation, motion | Every raw value defined once in a table or file (CSS or JSON) | 1 h |
| 3 | Semantic tokens with light and dark values. Naming rules. "How to add a token" | Every semantic colour has a light and a dark value. Components can be built from semantic tokens only | 0.75 h |
| 4 | Components: 8–10 from the brief list (or justified alternatives), every required state, both themes | Each component sheet shows all states from the brief table, in light and dark. No hard-coded values | 2.25 h |
| 5 | Accessibility rules and verification: contrast table for all text and UI tokens in both themes, focus ring, keyboard per component, target size, reduced motion | Contrast table has measured ratios and pass/fail per theme | 1 h |
| 6 | Usage guidance per component and one composed example screen (form with a table or dialog) | Each component has when to use, when not to, content rules, do and don't. Example uses only system parts | 1 h |
| 7 | Scenario answers, rationale doc, exports | Checklist C is complete | 0.5 h |

Total about 7 h (brief: 6–8 h). Tokens first, then components. Keep the set small and complete.

## 2. Directions

| Topic | Direction |
|---|---|
| Token layers | Two layers: raw values, then semantic tokens (for example `text-primary`, `surface`, `border-focus`). Components reference semantic tokens only |
| Naming | Semantic names that survive theming. No hue names (for example `blue-500`) inside components |
| Theming | Light and dark values for every semantic colour. A theme change swaps semantic values, never component specs |
| Component count | 8–10. Fewer complete components beat many half-finished ones |
| States | Show every required state in the brief table, not just default and hover |
| Contrast | Verify in both themes. Do not assume dark passes because light passes |
| Focus | One focus ring spec, reused by every interactive component |
| Keyboard | Write keyboard behaviour per component (for example Dialog: focus trap, Esc to close) |
| Meaning | No colour-only meaning. Badges and errors carry text or an icon |
| Motion | Define motion tokens and a reduced-motion rule |
| Guidance | Write when-not-to-use for every component |
| Live change ready | Structure so a **warning** variant or a new semantic token can be added in both themes and the docs without side effects |
| AI use | Allowed. Disclose AI-generated assets and copy. Review and own them |
| Content | Synthetic only. No real brands. Freely licensed fonts and icons |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [../design-instructions.md](../design-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md) (Section 5 where it applies)
- [ ] Read [product-brief.md](product-brief.md) and [../../shared/design-system/README.md](../../shared/design-system/README.md)
- [ ] Confirm you are doing Assignment 02 (not another one)
- [ ] Pick a design tool. Confirm you can share a view-access link or export PDF/PNG
- [ ] Pick a contrast checker you will use for every ratio
- [ ] Choose freely licensed fonts and icons. Note their licences
- [ ] Pick your 8–10 components and note any justified alternative
- [ ] Draft the token naming pattern before drawing any component
- [ ] Plan the 7 steps above against your available hours
- [ ] Start a running list for assumptions, rejected decisions and AI use

## 4. Checklist B — While working

### Tokens
- [ ] Colour, type scale, spacing, radius, elevation and motion defined
- [ ] Raw and semantic layers separate
- [ ] Every semantic colour has light and dark values
- [ ] Naming rules written. "How to add a token" written
- [ ] No hue-named tokens used inside components

### Components
- [ ] 8–10 components chosen, alternatives justified
- [ ] Every required state shown per component (check against the brief table)
- [ ] Every component shown in light and dark
- [ ] Components reference semantic tokens only. No hard-coded colours or sizes
- [ ] Dialog: confirm, destructive, focus trap, Esc to close
- [ ] Toast or banner: info, success, error, announced

### Accessibility
- [ ] Contrast measured for all text and UI tokens, both themes
- [ ] Focus ring spec defined and reused
- [ ] Keyboard behaviour written per component
- [ ] Target size stated
- [ ] Labels, text alternatives and error association defined
- [ ] No colour-only meaning. Reduced motion respected

### Guidance
- [ ] Each component: when to use, when not to, content rules, do and don't
- [ ] Composed example screen (form with a table or dialog) built only from the system

### Habits
- [ ] Name pages and frames so a reviewer can navigate
- [ ] Log decisions you rejected and why
- [ ] Record AI tool use as you go (you must disclose it)

## 5. Checklist C — After (before you submit)

### Verify
- [ ] Every requirement section A–E has a visible answer in the file or rationale doc
- [ ] Swap theme on the composed screen: only semantic token values change
- [ ] Contrast table complete with pass/fail for both themes
- [ ] Scenario answers written: label doubles in length, brand colour fails in dark, one-off card variant request
- [ ] Live-change rehearsal: add a **warning** variant or a new semantic token, update docs and both themes

### Deliverables
- [ ] Design file: Figma link with view access, or exported PDF/PNG set
- [ ] Token table or file (CSS, JSON or table)
- [ ] Component sheets with states, light and dark
- [ ] Accessibility verification table
- [ ] Usage guidance and composed example screen
- [ ] Rationale doc (1–2 pages): decisions, trade-offs, assumptions, AI use, sources cited

### Hygiene
- [ ] Synthetic content only. No real brands
- [ ] Fonts and icons freely licensed
- [ ] Link opens without a login request (test in a private window), or exports are complete
- [ ] Submitted within the 3-calendar-day window

### Prepare for the discussion (30–45 min)
- [ ] Can walk through the token layers
- [ ] Can show one component and all its states
- [ ] Can explain one contrast fix
- [ ] Can explain one decision you rejected
- [ ] Can say which assets were AI-assisted and how you verified them
- [ ] Ready to add a variant or token live

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Hex values inside component specs | Reference semantic tokens only |
| `blue-500` used in a component | Map it to a semantic token (for example `action-primary`) |
| Only default and hover states | Show every state in the brief table |
| Dark mode assumed to pass | Measure contrast in both themes |
| Many half-finished components | 8–10 complete ones |
| No when-not-to-use guidance | Write it for every component |
| Fixing a dark-mode contrast issue inside a component | Fix the semantic token's dark value |
| Example screen with one-off parts | Build it only from the system |
| Unreviewed AI output | Review, edit and disclose |
