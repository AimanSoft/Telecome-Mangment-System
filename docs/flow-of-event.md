# flow-of-event.md — TCMS Flow of Event

Status: **Initial Draft.** Events listed here are business-level occurrences (things that
happen in the domain and cause a state change), not technical message-broker events.
Whether the system uses technical events/queues is an **open architectural decision**
(`docs/architecture.md` §5) and is not decided.

Revised after Phase 2 fixes the use cases.

---

## 1. Event catalogue (Draft)

| EV ID | Event | Trigger | Source | Effect (Draft) | State change |
|---|---|---|---|---|---|
| EV-01 | SubscriberRegistered | Sales agent completes registration | M-1/M-6 | Subscriber record created | none → Active |
| EV-02 | PackageAssigned | Subscription saved | M-2 | Subscriber bound to package | Active + plan |
| EV-03 | InvoiceIssued | Invoice confirmed | M-3 | Invoice available for payment | none → Open |
| EV-04 | PaymentReceived | Payment saved | M-4 | Invoice balance reduced/closed | Open → Paid / Partial |
| EV-05 | ComplaintLodged | Complaint saved | M-5 | Support ticket exists | none → Open |
| EV-06 | ComplaintClosed | Resolution saved | M-5 | Complaint resolved | Open → Closed |
| EV-07 | SubscriberDeactivated | Administrator confirms | M-1 | Subscriber no longer active | Active → Inactive |
| EV-08 | UserAccountChanged | Administrator saves user/role | M-9 | Access rights changed + audit entry | — |
| EV-09 | ReportGenerated | Report executed | M-8 | Result produced (transient) | — |

---

## 2. Representative event flows (Draft)

### EV-03 InvoiceIssued
```
Billing period selected
  → charges computed
    → invoice reviewed
      → EVENT: InvoiceIssued
        → invoice status = Open
        → (possible downstream) payment reminder / notification — Assumption
```

### EV-04 PaymentReceived
```
Payment entered
  → amount validated against invoice
    → EVENT: PaymentReceived
      → invoice balance updated
        → invoice status = Paid (or Partial)
          → (possible downstream) receipt generated — Assumption
```

### EV-05 → EV-06 Complaint lifecycle
```
Complaint created       → EVENT: ComplaintLodged (status Open)
Handling notes recorded → status In Progress (Assumption)
Resolution saved        → EVENT: ComplaintClosed (status Closed)
```

---

## 3. Notification / automation events — Assumptions

These are **not confirmed**; they are candidates only:

- Payment overdue reminder (needs due-date rules — OQ-08)
- Complaint SLA breach alert (needs SLA definition — OQ-08)
- Subscriber deactivation due to non-payment

---

## 4. Open questions

- Does the doctor expect "events" as UML/system events, message events, or domain events?
  (OQ-01)
- Which events are observable/integrated with external systems? (`docs/architecture.md`)
- Retention/audit requirements for events (senior-rules LOG-01 suggests full activity
  logging — not confirmed as a project requirement).
