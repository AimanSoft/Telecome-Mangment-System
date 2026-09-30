# architecture.md — TCMS Architecture

Status: **Architecture Initial Draft — NOT a final architecture.**
No style (monolith / modular monolith / microservices / event-driven), no technology
stack, and no infrastructure is decided here. Such decisions are `Pending Decision`
(PD-04, PD-05 in `docs/memory.md`).

---

## 1. Purpose & scope of this draft

- Describe the initial components the system will need.
- Mark system boundaries and integration points.
- Record open architectural decisions.

Out of scope: deployment topology, vendor selection, stack selection, capacity planning.

---

## 2. System boundary

**Inside the boundary (assumed):** web application for internal telecom-operator workflows
(subscribers, packages, billing, payments, complaints, sales, inventory?, reports, admin).

**Outside the boundary (candidates — unconfirmed):**

| External system | Why it may be needed | Status |
|---|---|---|
| Payment channel / bank | settling payments | Assumption (OQ-08) |
| Usage/CDR source | usage-based billing | Assumption (OQ-08) |
| Notification gateway (SMS/email) | complaints, invoices, reminders | Assumption |
| Identity provider (SSO/LDAP) | user authentication | Assumption — likely simple auth first |
| Reporting/BI tool | advanced analytics | Assumption |

No external integration is confirmed by the doctor's sources (not available).

---

## 3. Initial components (Draft)

```
[ Web UI (browser) ]
        │
        │  (protocol TBD)
        ▼
[ Application layer ]
  ├── Authentication & authorization
  ├── Subscriber management
  ├── Packages & subscriptions
  ├── Billing & payments
  ├── Complaints & support
  ├── Sales/orders
  ├── Inventory (?)            — Assumption
  ├── Reporting
  └── Audit & activity logging
        │
        ▼
[ Data store ]   (technology TBD — not decided)
        │
        ▼
[ Integration layer ]  → external systems (if confirmed)
```

Component list derives from modules M-1…M-9 (`use-case-scenario.md` §3).

---

## 4. Communication considerations (options, not decisions)

| Concern | Options seen | Status |
|---|---|---|
| Client–server protocol | Server-rendered pages / REST API + SPA / hybrid | Open decision |
| Internal component communication | in-process calls / messages | Open decision |
| Async work (billing runs, notifications) | background jobs / queue / synchronous | Open decision |
| Data consistency for billing & payments | single transaction vs eventual | Open decision |

---

## 5. Open architectural decisions (must not be decided prematurely)

| ID | Decision | Candidate options | When to decide |
|---|---|---|---|
| AD-1 | Architectural style | Modular monolith / microservices / event-driven / layered | Phase 5 |
| AD-2 | Technology stack (language, framework, DB) | — | Phase 5–6 (PD-04) |
| AD-3 | Deployment environment | On-prem / cloud / course-provided | Phase 5 |
| AD-4 | Integration approach with external systems | Point-to-point / API gateway / messaging | Phase 5 |
| AD-5 | AuthN approach | Simple credentials / SSO / directory | Phase 5 |
| AD-6 | Reporting approach | In-app queries / separate store / export | Phase 5 |

---

## 6. Constraints & quality drivers (unknown → Open Questions)

- Expected user count, availability, retention, and regulatory constraints are unknown
  (OQ-08). Architecture cannot be finalized without them.
- Security baseline (senior-rules SEC) is treated as good practice but the doctor's
  required security scope is unknown.

---

## 7. Explicit statements

- This file does **not** approve any architecture.
- Nothing in `implementation/`, no code, no schema exists or may be created from this
  draft before Phase 5/6 gates are passed.
