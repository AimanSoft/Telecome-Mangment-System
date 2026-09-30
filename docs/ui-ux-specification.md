# ui-ux-specification.md — TCMS UI/UX Specification

Status: **Initial Specification (Draft).** Not a design document: no wireframes,
mockups, colors, or components are finalized, and no frontend code is written.

Reference hygiene applied: senior-rules UI-01..UI-04 (HCI metrics, WCAG 2.1 AA,
i18n/RTL readiness, responsive breakpoints) are recorded here as **expectations for later
phases**, not as confirmed project requirements.

---

## 1. Users of the interface (from `use-case-scenario.md`, Draft)

| Actor | Usage pattern | Proficiency expectation |
|---|---|---|
| Administrator | Frequent, full system | Power user |
| Customer Service | Frequent, complaint/subscriber screens | High-frequency data entry |
| Billing Officer | Periodic batches (billing runs) | Accuracy-critical |
| Sales Agent | Frequent registration flows | Speed-critical, guided forms |
| Subscriber | (Assumption) own data only | Non-expert |

---

## 2. Interaction principles (Draft)

1. Every screen supports the flow defined in `flow-of-action.md` — no dead controls.
2. Destructive actions (deactivate, delete, close) require an explicit confirmation
   step (no browser `alert()`/`confirm()` when implemented — senior-rules IMP-04).
3. Every operation displays: success / validation error / server error / network error.
4. Lists support search + filter + pagination (Assumption for scale).
5. Role determines visible actions; server-side checks remain authoritative.

---

## 3. Screen-level requirements (Initial, minimal)

| Screen | Must show | Must allow |
|---|---|---|
| Login | error messages | sign in, recovery (if in scope) |
| Dashboard | key counts/indicators (TBD) | navigate to modules |
| Subscriber list | status, search results | create, open, deactivate |
| Subscriber detail | identity, packages, invoices, complaints | edit, assign package |
| Invoice list/detail | status, amount, period | generate, review, record payment |
| Complaint list/detail | status, category, notes | lodge, update, resolve |
| Reports | parameters, results | run, view (export: Open Question) |
| Admin users | accounts, roles | create, edit, assign roles |

Indicator definitions (which KPIs on the dashboard) are **Open Questions** — not invented here.

---

## 4. Quality expectations (Draft, for later phases)

| Attribute | Expectation | Status |
|---|---|---|
| Accessibility | WCAG 2.1 AA (keyboard, focus, contrast, ARIA) | Reference rule — confirm if required |
| Internationalization | Arabic/English + RTL readiness | **Assumption** — confirm (OQ-08/NFR) |
| Responsiveness | Define breakpoints later | Pending |
| Usability heuristics | Review per phase | Planned in Phase 4/7 |
| Performance | Page load targets unknown | Open Question |

---

## 5. Explicitly out of scope now

- No visual design, style guide, color palette, typography, or component library.
- No frontend framework decision.
- No implementation of any screen.

## 6. Open questions

- Doctor's prescribed UI/UX format (wireframes? storyboard? HCI metrics table?) — OQ-01
- Required language(s) and RTL — OQ-08
- Required NFRs (concurrent users, response time) — OQ-08
