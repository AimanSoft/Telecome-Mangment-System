# use-case-scenario.md — TCMS Use Case Scenarios

Status: **Initial Draft — not a final use case analysis.**
This file will be revised in **Phase 2 (Use Case Analysis)**, once the doctor's
requirements and the confirmed module/actor lists exist.

Source of content: project brief only (Telecom Management System). No doctor materials
were available → every line below is `Draft`.

---

## 1. How to read this file

| Marker | Meaning |
|---|---|
| Draft | Proposed, not confirmed |
| Assumption | Reasonable inference, no source yet |
| Open Question | Needs the user/doctor |

---

## 2. Actors (Draft — pending confirmation, OQ-06)

| ID | Actor | Description |
|---|---|---|
| A-1 | Administrator | Manages users, roles, and system configuration |
| A-2 | Customer Service Agent | Handles subscriber inquiries and complaints |
| A-3 | Billing Officer | Manages invoices, payments, adjustments |
| A-4 | Sales Agent | Registers subscribers and sells packages |
| A-5 | Subscriber (End customer) | Views own account/invoice (if self-service is in scope — Assumption) |
| A-6 | Technician / Field engineer | Network/field tasks (Assumption — may be out of scope, OQ-07) |

---

## 3. Modules (Draft — pending confirmation, PD-02)

| ID | Module | Purpose (Draft) |
|---|---|---|
| M-1 | Subscriber Management | Create, search, update, deactivate subscribers |
| M-2 | Packages & Offers | Maintain plans/offers; assign to subscribers |
| M-3 | Billing & Invoicing | Generate invoices from usage/plans |
| M-4 | Payments | Record and reconcile payments |
| M-5 | Complaints & Support | Raise, assign, resolve complaints |
| M-6 | Sales & Orders | Handle subscription orders |
| M-7 | Inventory (SIM / Devices) | Track SIMs and devices (Assumption) |
| M-8 | Reporting & Dashboards | Operational and management reports |
| M-9 | Administration & Roles | Users, roles, permissions, audit logs |

---

## 4. Use cases (Initial Draft — deliberately small set)

> Only a minimal set is listed. Dozens of use cases are **not** invented here; the full
> set is a Phase 2 deliverable.

| UC ID | Name | Primary actor | Related module | Notes |
|---|---|---|---|---|
| UC-01 | Register a new subscriber | Sales Agent | M-1, M-6 | Draft |
| UC-02 | Assign package to subscriber | Sales Agent | M-2, M-1 | Draft |
| UC-03 | Generate monthly invoice | Billing Officer (system-assisted) | M-3 | Draft — trigger/automation unclear (OQ-08) |
| UC-04 | Record a payment | Billing Officer | M-4 | Draft |
| UC-05 | Lodge a complaint | Customer Service Agent | M-5 | Draft |
| UC-06 | Resolve a complaint | Customer Service Agent | M-5 | Draft |
| UC-07 | Deactivate subscriber | Administrator | M-1 | Draft |
| UC-08 | Manage user accounts & roles | Administrator | M-9 | Draft |
| UC-09 | View operational report | Administrator / Billing Officer | M-8 | Draft |

Scenario descriptions (short form):

### UC-01 Register a new subscriber — Draft
- Preconditions: actor authenticated and authorized (Draft).
- Main flow: search for duplicates → enter subscriber data → validate → save → subscriber active.
- Alternate: existing subscriber found → update record instead.
- Exception: validation fails → correct and retry.
- Postcondition: subscriber record exists.
- Data: subscriber, contact details, identification (Assumption about fields).

### UC-03 Generate monthly invoice — Draft
- Preconditions: subscriber active, billing period open.
- Main flow: select period → system computes charges → review → confirm → invoice created.
- Open: is generation automatic or manual? Which inputs (plan, usage, taxes)? (OQ-08)

### UC-05 Lodge a complaint — Draft
- Preconditions: subscriber exists.
- Main flow: identify subscriber → select complaint type → describe → save → complaint open with reference.
- Postcondition: complaint record exists and is trackable.

(Other use cases expand in Phase 2 with full dressed format.)

---

## 5. Open questions for this file

- OQ-06: confirm the actor list.
- OQ-07: is the network/field domain in scope?
- OQ-08: billing inputs and automation rules.
- Are there use cases imposed by the doctor's materials not visible here? (OQ-01)
