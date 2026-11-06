# Assignment 05 — Requirements

**v1.0 — 2026-11-06**

## A. Core workflows

| Workflow | Requirement | Example |
|---|---|---|
| Product setup | Add products with SKU, unit, purchase and selling price, tax setting, opening stock. Update price or stock by chat | "Amul butter ke 20 packet add karo, rate 58 rupaye rakho" / "Add 20 packets of Amul butter at ₹58 each" |
| Create order | Walk-in or named customer, multiple products and quantities, stock check, discount and tax, preview | "Rahul ke naam se order banao: 2 rice bags aur 1 oil bottle" |
| Confirm and bill | Human confirmation before confirming an order, issuing an invoice, recording payment or deducting stock. Unique order and invoice numbers. Cash, UPI, card, credit | |
| Customers | Find or create. Keep only necessary contact details. Order and payment history. Optional outstanding credit | |
| Stock operations | Purchases, sales, returns, damage, manual adjustments with reason. Auditable ledger | |
| Daily stock report | Opening, inward, sold, returns, adjustments, closing, low-stock alerts. Filter by date, category, product | "Aaj ka stock report dikhao" |
| Daily sales report | Gross sales, discounts, tax, net sales, order count, average order value, top products, payment split, refunds, outstanding dues | "Show today's sales report" |
| Export / share | Readable tables in chat. Hindi or English CSV/PDF summary | "Kal ke sales ka report English mein bhejo" |

## B. Bilingual requirements

| Capability | Expected behaviour |
|---|---|
| Language preference | Choose Hindi or English. Remember per user or shop |
| Understanding | Hindi, English and common Hinglish, including in one sentence |
| Responses | Reply in selected or detected language. Support "Hindi mein batao" and "Tell me in English" |
| Numbers and units | Digits and spoken-style numbers (for example "pachaas"), kg, litre, packet, piece, dozen, rupees. Clarify ambiguity |
| Reports | Headings, labels, filters, status messages and exports in both languages |
| Fallback | Focused clarification in the same language. Never guess product, customer or quantity |

## C. Chat-to-action pipeline

| Step | Expected behaviour |
|---|---|
| 1 Understand | Detect language and intent: order, product update, stock query, report, customer lookup, return |
| 2 Extract | Convert the message to typed fields. Preserve units, quantities, dates, language |
| 3 Resolve | Match product or customer. Ask the user to choose when several match |
| 4 Validate | Check permissions, required fields, stock, prices, tax, business rules server-side |
| 5 Preview | Items, quantities, totals, stock impact, report date range, in the chosen language |
| 6 Confirm | Explicit approval before order confirmation, invoice, payment or stock mutation |
| 7 Execute | Deterministic business services in DB transactions. Retries are idempotent |
| 8 Report | Return persisted order or invoice references, or database-backed report results |

## D. Database (suggested)

| Entity | Purpose |
|---|---|
| shops / users | Tenancy, roles, language preference, timezone, settings |
| products | SKU, name, local-language aliases, unit, prices, tax category, reorder level |
| customers | Name, phone or address only when needed, preferred language |
| orders / order_items | Number, customer, status, product snapshot, quantity, price, discount, tax, totals |
| invoices / payments | Invoice number and status. Method, amount, reference, payment status |
| inventory_movements | Product, type, signed quantity, source, reason, actor, timestamp |
| inventory_balances | Available quantity, kept consistent with movements |
| chat_sessions / messages | Role, text, language, timestamp, action correlation ID |
| pending_actions | Parsed intent, typed payload, validation and confirmation state, expiry |
| audit_events | Actor, action, entity, before/after reference, timestamp |

## E. API scope (adjustable if documented)

| Method | Endpoint |
|---|---|
| POST | /chat/sessions · /chat/sessions/{id}/messages |
| POST | /actions/{id}/confirm · /orders/drafts · /orders/{id}/confirm |
| GET | /orders/{id} · /customers?query=... |
| POST / PATCH | /products · /products/{id} |
| POST | /inventory/movements |
| GET | /reports/stock/daily · /reports/sales/daily |
| GET | /reports/{id}/export?format=csv\|pdf |

## F. Reporting logic
- Closing stock = opening + inward + returns-in − sold − returns-to-supplier − damage and other outward adjustments.
- Define gross sales, discounts, tax, net sales, refunds, collected amount and outstanding credit separately.
- Use the shop timezone and an explicit business-day boundary.
- Calculate from persisted orders, payments and inventory movements, not the chat transcript or LLM arithmetic.
- Explain live reports versus end-of-day snapshots, and how late corrections and refunds affect reports.

## G. Engineering scenarios to address
- Two products have similar Hindi or English names. How do you avoid the wrong SKU?
- A customer orders 5 units but only 3 are available. What does the order flow do?
- The user says "pachaas" or "50" but the parser extracts 15. How is it caught before saving?
- An order confirmation is retried after a timeout. How do you prevent duplicate orders, invoices or stock deductions?
- A return is processed after the daily report is generated. How are reports and the audit trail corrected?
- A shop has two branches. How do you scope stock and reports by branch?
- The AI provider is unavailable. Do structured product search, order entry and reports still work?

## H. Live follow-up
Add a return or refund flow so the order, payment adjustment, inventory restock and daily reports stay consistent and auditable. Switch the same conversation from Hindi to English without losing context.
