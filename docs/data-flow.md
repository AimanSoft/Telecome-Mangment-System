# Data Flow — TCMS

> Status: Draft — Based on aim45an DFD diagrams (Team Decision, Pending Doctor)
> Source: docs/diagrams/phase-3-flows/21-dfd-level-0-context.drawio, docs/diagrams/phase-3-flows/22-dfd-level-1.drawio

## Level 0 — Context Diagram

External Entities:
- Customer (العميل)
- Employee / Staff (موظف خدمة العملاء)
- Network / Support (مهندس شبكة / موظف دعم)

External Systems (Mock):
- External Identity System
- External Payment Gateway
- SMS / Email Provider

Central Process: TCMS System
(handles: Customer, SIM, Subscription, Usage, Billing, Payment, Network, Support)

## Level 1 — Main Processes (6)

| # | Process | Arabic |
|---|---------|--------|
| 1.0 | Customer & Identity | إدارة العملاء والتحقق |
| 2.0 | SIM & Subscription | الشرائح والاشتراكات |
| 3.0 | Usage Tracking | تسجيل الاستهلاك |
| 4.0 | Billing & Invoicing | الفوترة والاحصاء |
| 5.0 | Payment Processing | معالجة المدفوعات |
| 6.0 | Network & Support | الشبكة والأعطال والدعم |

## Data Stores (8)

| ID | Store | Arabic | Tables |
|----|-------|--------|--------|
| D1 | Customers | العملاء | customers, addresses, contacts |
| D2 | SIMs & Numbers | الشرائح والأرقام | sim_cards, phone_numbers |
| D3 | Subscriptions | الاشتراكات | subscriptions |
| D4 | Usage Records | الاستهلاك | usage_records |
| D5 | Invoices | الفواتير | invoices, invoice_items |
| D6 | Payments | المدفوعات | payments |
| D7 | Network & Tickets | الأعطال والتذاكر | incidents, support_tickets |
| D8 | Audit Log | التدقيق | audit_log |

## Notes

- Database-per-Service: لا وحدات مباشرة بين D1-D8، كل خدمة تملك قواعدها
- D5 و D6 مشتركة كتحويلات (لا كتابة مباشرة)
- D8 يُسجّل من كل عمليات تعديل حالة (Audit Trail)
- Status: Draft — Team Decision, Pending Doctor
