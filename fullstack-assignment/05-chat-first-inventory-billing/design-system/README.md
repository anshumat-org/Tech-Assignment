# Assignment 05 — Design System Notes

**v1.0 — 2026-11-06** · Extends [../../../shared/design-system/README.md](../../../shared/design-system/README.md)

| Area | Guidance |
|---|---|
| Layout | Chat on one side, structured preview or report on the other. Works on a phone |
| Language | Visible Hindi / English toggle. Every label, error, confirmation and export follows it. Devanagari renders correctly |
| Preview card | Items, quantities, unit price, discount, tax, total, stock impact. Explicit Confirm and Cancel |
| Confirmation | Never auto-confirm. Show what will change (order, invoice, payment, stock) before the button |
| Clarification | Short question with tappable choices when several products or customers match |
| Reports | Readable tables in chat, with date, category and product filters and an export action |
| Low stock | Marked with text and an icon, not colour alone |
| Errors | Plain language in the active language. Offer a next step |
| Voice or typing | Typed input is required. Voice is optional |

## Component additions

| Component | States |
|---|---|
| Message bubble | user, assistant, system |
| Pending action card | proposed, confirmed, cancelled, expired, failed |
| Choice chips | default, selected |
| Report table | loading, empty, ready, exported |
| Language toggle | Hindi, English |

## Wording
- Confirmation: "Confirm order for Rahul? Total ₹X. Stock will be reduced." / "राहुल का ऑर्डर कन्फ़र्म करें? कुल ₹X। स्टॉक कम होगा।"
