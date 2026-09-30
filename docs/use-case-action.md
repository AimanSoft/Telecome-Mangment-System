# use-case-action.md — TCMS Use Case Actions

Status: **Initial Draft.** Actions are derived from `use-case-scenario.md` (itself Draft).
This file must be re-derived after Phase 2 confirms the use cases.

Format per use case: the elementary actions of the main flow, in order, with the actor
and the data touched. Alternate/exception flows are added in Phase 2.

---

## UC-01 Register a new subscriber (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Open subscriber registration form | Sales Agent | — |
| 2 | Search existing subscribers (duplicate check) | Sales Agent | subscriber |
| 3 | Enter subscriber data | Sales Agent | subscriber, contact |
| 4 | Validate entered data | System | subscriber |
| 5 | Save subscriber record | System | subscriber |
| 6 | Confirm registration result | Sales Agent | — |

---

## UC-02 Assign package to subscriber (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Open subscriber record | Sales Agent | subscriber |
| 2 | List available packages | System | package |
| 3 | Select package | Sales Agent | subscription |
| 4 | Save subscription assignment | System | subscription, subscriber |

---

## UC-03 Generate monthly invoice (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Select billing period | Billing Officer | billing period |
| 2 | Compute charges for period | System | invoice, subscription, plan |
| 3 | Review computed invoice | Billing Officer | invoice |
| 4 | Confirm and issue invoice | Billing Officer | invoice |

---

## UC-04 Record a payment (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Open invoice | Billing Officer | invoice |
| 2 | Enter payment details | Billing Officer | payment |
| 3 | Validate amount against invoice | System | payment, invoice |
| 4 | Save payment and update invoice status | System | payment, invoice |

---

## UC-05 Lodge a complaint (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Identify subscriber | Customer Service Agent | subscriber |
| 2 | Select complaint category | Customer Service Agent | complaint |
| 3 | Enter description | Customer Service Agent | complaint |
| 4 | Save complaint with reference | System | complaint |

---

## UC-06 Resolve a complaint (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Open complaint | Customer Service Agent | complaint |
| 2 | Record handling steps/notes | Customer Service Agent | complaint |
| 3 | Close complaint with resolution | Customer Service Agent | complaint |

---

## UC-07 Deactivate subscriber (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Open subscriber record | Administrator | subscriber |
| 2 | Confirm deactivation | Administrator | subscriber |
| 3 | Set status to inactive | System | subscriber |

---

## UC-08 Manage user accounts & roles (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Create/update user account | Administrator | user account |
| 2 | Assign role | Administrator | role, user account |
| 3 | Save changes | System | user account, audit log |

---

## UC-09 View operational report (Draft)

| # | Action | Actor | Data touched |
|---|---|---|---|
| 1 | Select report and period | Administrator / Billing Officer | report parameters |
| 2 | Run report | System | reports over subscriber/invoice/payment |
| 3 | View or export result | Actor | — (export scope: Open Question) |

---

## Notes

- Permission per action (role × allowed action) is **not** specified here; it belongs to
  the permissions matrix deliverable (Phase 5/6 per senior-rules IMP-03) and is currently
  a Pending Decision.
- No action here is confirmed by the doctor.
