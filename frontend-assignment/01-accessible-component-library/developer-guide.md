# Assignment 01 — Developer Guide & Checklists

**v1.0 — 2026-11-23** · Read after [README.md](README.md) and [requirements-and-directives.md](requirements-and-directives.md)

| WH | Answer |
|---|---|
| What | A step-by-step path and three checklists (before you start, while developing, after you finish) |
| Why | So you spend the 4–6 hours on keyboard behaviour, tokens and tests, not on guessing scope |
| Who | The candidate |
| When | Open it now. Tick boxes as you go. Re-check the last list before submitting |

## 1. Suggested build order

| Step | Build | Done when | Time |
|---|---|---|---|
| 1 | Setup, design tokens (colour, spacing, radius, type, focus ring), light and dark themes | Swapping the theme changes the demo by tokens only. No hex values in components | 0.5 h |
| 2 | Button, Input, Checkbox or Radio group | All states render. Input error and hint linked by `aria-describedby`. Loading Button blocks double submit | 1 h |
| 3 | Select (native or custom) and Tabs | Tabs: arrows, Home / End, roving tabindex. Custom Select: full listbox keys. Choice documented | 1 h |
| 4 | Modal dialog and Toast | Focus trap, Esc, focus returns to trigger, scroll lock. Toast announced via live region, pausable | 1 h |
| 5 | Demo page with every component in every state and a theme toggle | Reviewer can see each state without editing code | 0.5 h |
| 6 | Tests (8+) and an axe check | Keyboard, ARIA and focus tests pass. axe reports no violations on the demo | 0.5 h |
| 7 | README scenario answers, `docs/design-system.md`, video or screenshots | Checklist C is complete | 0.5 h |

Total about 5 h (brief: 4–6 h). Build behaviour first. Visual polish is secondary.

## 2. Directions

| Topic | Direction |
|---|---|
| Scope | Build 6–8 components from the brief. Tooltip or Badge is optional |
| Semantics | Semantic HTML first. ARIA only to fill gaps. No ARIA that repeats native roles |
| Tokens | Colour, spacing, radius, type and focus ring defined once. Components only read them |
| Theming | Light and dark work by swapping tokens only. Start from [../../shared/design-system/README.md](../../shared/design-system/README.md) or document your own |
| API | Small consistent props (variant, size, disabled). No prop for every one-off need |
| Refs and attributes | Forward refs and native attributes so consumers can reach the element |
| Polymorphism | Decide how Button renders as a link and say so in the README |
| Keyboard | Every interactive element works by keyboard with a visible focus ring |
| Contrast and motion | Body text at least 4.5:1. Meaning never by colour alone. Respect `prefers-reduced-motion` |
| Size | Usable at 320 px width and at 200% zoom |
| Libraries | No large UI kit. Headless libraries only if you can explain what they do for you |
| Data | No mock API needed. Any sample data is synthetic |
| Live follow-up | Be ready to add a Combobox with async suggestions or a destructive confirm Modal by reusing parts |
| Scope | If you skip something, list it under limitations in your README |

## 3. Checklist A — Before you start

- [ ] Read [README.md](README.md), [requirements-and-directives.md](requirements-and-directives.md), [resources.md](resources.md), [../frontend-instructions.md](../frontend-instructions.md) and [../../SUBMISSION_FORMATS.md](../../SUBMISSION_FORMATS.md)
- [ ] Confirm you are doing Assignment 01 (not another one)
- [ ] Pick your 6–8 components
- [ ] Choose framework (TypeScript preferred) and test tools. Note any unusual choice and why
- [ ] Verify Node (or runtime), package manager and a test runner work locally
- [ ] Create a new git repo with a README skeleton and `.gitignore`
- [ ] Decide native vs custom Select and write down why
- [ ] Sketch the token structure (names for colour, spacing, radius, type, focus ring)
- [ ] Draft the keyboard model for Tabs, Modal and Select
- [ ] Plan the 7 steps above against your available hours
- [ ] Decide the 8+ tests you will write (keyboard, ARIA, focus)

## 4. Checklist B — While developing

### Tokens and theming
- [ ] No hard-coded colours or sizes inside components (search the code for `#` and `px`)
- [ ] Light and dark both work by swapping tokens only
- [ ] Focus ring comes from a token

### Components and states
- [ ] Button has primary, secondary, danger, ghost, and default, hover, focus, disabled, loading
- [ ] Input label, hint and error are linked by `aria-describedby`
- [ ] Modal traps focus, closes on Esc, returns focus to the trigger and locks scroll
- [ ] Tabs support arrows, Home / End, roving tabindex and correct roles
- [ ] Toast uses a live region, is dismissible and auto-dismiss can be paused
- [ ] Checkbox or Radio group has a group label, checked and disabled states
- [ ] Two tab panels of different height do not cause layout jump

### Accessibility
- [ ] Tab through every component using only the keyboard
- [ ] Contrast of body text is at least 4.5:1 in both themes
- [ ] No meaning carried by colour alone (errors, badges, status)
- [ ] `prefers-reduced-motion` respected
- [ ] Checked at 320 px width and 200% zoom

### Habits
- [ ] Commit small and often with meaningful messages
- [ ] Run tests before each commit
- [ ] Keep a running list of assumptions and trade-offs for the README
- [ ] Record any AI tool usage and reused code as you go. Verify it and be able to explain it

## 5. Checklist C — After developing (before you submit)

### Run and verify
- [ ] Clean clone: follow your own README exactly. Install, run demo, test. All work
- [ ] At least 8 meaningful tests pass, including keyboard interaction, ARIA attributes and focus management
- [ ] At least one automated accessibility check (for example axe) runs on the demo or components
- [ ] Demo page shows every component in every state with a theme toggle

### Deliverables
- [ ] Git repo with setup instructions and meaningful commits (SUBMISSION_FORMATS.md Section 7)
- [ ] Demo page or Storybook, plus short video or screenshots (Section 8)
- [ ] `docs/design-system.md` (Section 5)
- [ ] Short README with assumptions and trade-offs
- [ ] README answers all five scenarios: modal focus and Esc, toast during typing, tab panel height, Button as link, double submit on loading Button

### Hygiene
- [ ] No secrets or `.env` in git history
- [ ] No dead code, stray debug logs or TODOs that hide gaps
- [ ] AI-generated or reused code is marked and verified
- [ ] Submit via the form linked in the root README within 3 calendar days

### Prepare for the discussion (about 30 min)
- [ ] Can walk through one component's keyboard model
- [ ] Can explain your token structure
- [ ] Can describe one accessibility bug you found and fixed
- [ ] Can say which files change to add a new variant
- [ ] Ready for a small live change (Combobox with async suggestions or destructive confirm Modal)

## 6. Common mistakes

| ❌ Mistake | ✅ Fix |
|---|---|
| Hex values or pixel sizes inside components | Read from tokens |
| ARIA roles on elements that already have the semantics | Use semantic HTML first |
| Modal without focus return to the trigger | Store the trigger and restore focus on close |
| Toast that is only visual | Use a live region |
| Tabs with every tab in the tab order | Roving tabindex plus arrow keys |
| Error shown only in red | Add text and an icon, link with `aria-describedby` |
| Loading Button still clickable | Block the action while loading |
| Wrapper hides the native element | Forward refs and native attributes |
| Only visual checks and snapshots | Test keyboard, ARIA and focus |
| Pulling in a big UI kit | Build it, or justify a headless library |
