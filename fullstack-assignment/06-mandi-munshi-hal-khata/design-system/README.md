# Assignment 06 — Design System Notes

**v1.0 — 2026-11-23** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Users | A munshi entering many entries quickly, often on a phone or a shared counter PC. Large touch targets, minimal typing, keyboard-friendly |
| Language | Visible Hindi / English toggle. Every label, error, report and print follows it. Devanagari renders correctly |
| Entry form | One screen per entry type. Remembers last party, crop and date. Amount and quantity fields with units shown |
| Preview before post | Show the journal lines (Dr / Cr), the party's balance before and after. Explicit Post and Cancel |
| Statement view | Date, narration, Dr, Cr, running balance. Sticky header. Reversed entries marked with text and an icon, not colour alone |
| Settlement slip | Sale lines, each deduction with rate and base, advances, net payable. Printable in both languages |
| Corrections | "Correct this entry" opens reverse-and-repost with a required reason. Never an edit-in-place |
| Outstanding | Ageing buckets, oldest first, tap a party to open its khata |
| Money display | Rupees with Indian digit grouping (₹1,23,456.00). Dr and Cr labelled in text |
| Errors | Plain language in the active language. Offer a next step |
| Offline | If you add any offline behaviour, show queued vs posted state clearly |

## Component additions

| Component | States |
|---|---|
| Entry preview card | draft, ready, posted, failed |
| Ledger row | normal, reversed, reversal |
| Settlement slip | draft, posted, reversed |
| Ageing table | loading, empty, ready, exported |
| Language toggle | Hindi, English |

## Wording
- Confirm: "Post settlement for Ramesh? Net payable ₹X." / "रमेश का हिसाब पोस्ट करें? देय राशि ₹X।"
- Reversal: "Reverse this entry? Reason is required." / "यह एंट्री उलटें? कारण ज़रूरी है।"
