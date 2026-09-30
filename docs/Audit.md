# Audit — TCMS Project Review Checklist

Purpose: review gate before any phase is declared closed (from senior-rules AUD-01/AUD-04
and the project brief). Nothing is checked `[x]` unless the reviewed artifact exists and
has been read in its current state.

Status legend: `[ ]` Not Started · `[~]` In Progress · `[x]` Completed · `[!]` Blocked

Last updated: 2026-09-30 (Session 2 — root commit `687b8a6`; F-02 fixed)

---

## 1. Doctor requirements coverage

- [!] Implement Plan — drafted in `docs/implement-plan.md`, **not confirmed** (doctor sources missing)
- [!] Use Case Scenario — Initial Draft present (`docs/use-case-scenario.md`)
- [!] Use Case Action — Initial Draft present (`docs/use-case-action.md`)
- [!] Flow of Action — Initial Draft present (`docs/flow-of-action.md`)
- [!] Flow of Event — Initial Draft present (`docs/flow-of-event.md`)
- [!] Data Flow — Initial Draft present (`docs/data-flow.md`)
- [!] Website Structure — Initial Draft present (`docs/website-structure.md`)
- [!] UI/UX Specification — Initial Specification present (`docs/ui-ux-specification.md`)
- [!] Architecture — Initial Draft present (`docs/architecture.md`)
- [!] Todo file for each Phase — present (`phases/phase-1..7/todo.md`)
- [!] mindmap.md — present (`docs/mindmap.md`)
- [!] Audit.md — this file
- [!] memory.md — present (`docs/memory.md`)
- [ ] Any additional file required by the doctor's sources — **unknown, sources missing**

All items above are `[!]` because coverage cannot be confirmed without the doctor's
original materials (see `docs/initial-status.md` → Missing Information).

---

## 2. Content review checklist

- [ ] Project idea confirmed
- [ ] Project scope reviewed
- [ ] Objective reviewed
- [ ] Actors reviewed
- [ ] Modules reviewed
- [ ] Use Cases reviewed
- [ ] Actions reviewed
- [ ] Events reviewed
- [ ] Data Flow reviewed
- [ ] Website Structure reviewed
- [ ] UI/UX reviewed
- [ ] Architecture reviewed
- [ ] Phase Todos reviewed
- [ ] Doctor requirements reviewed
- [ ] Final project consistency reviewed

---

## 3. Consistency rules checked in every audit pass

| # | Check | Status |
|---|---|---|
| C-1 | No file claims a status its content does not support | [x] pass done in Session 1 |
| C-2 | No requirement invented without a source (brief / doctor / confirmed by user) | [x] pass done in Session 1 |
| C-3 | Draft / Assumption / Open Question labels used wherever unconfirmed | [x] applied in Session 1 |
| C-4 | No contradiction between `docs/*` files | [x] first pass done in Session 1 (IDs OQ-01…08, UC-01…09, M-1…9, PD/AD all consistent; statuses aligned) |
| C-5 | No code, schema, API, auth, or stack decision present | [x] verified in Session 1 (none exist) |
| C-6 | `_incoming/` unmodified | [x] verified in Session 1 |
| C-7 | Every Phase has a `todo.md` | [x] created in Session 1 |
| C-8 | Status markers limited to `[ ]` / `[~]` / `[x]` (plus `[!]` Blocked in this file) | [x] applied in Session 1 |

---

## 4. Findings register (Session 1)

| ID | Severity | Finding | Status | Action |
|---|---|---|---|---|
| F-01 | HIGH | No doctor source materials in the project → all requirements unverified | OPEN | Ask user for the materials |
| F-02 | LOW | Review history was missing; resolved by root commit `687b8a6` (2026-09-30) | FIXED | Future commit policy = OQ-05 |
| F-03 | MEDIUM | Phase split unverified against the doctor's split | OPEN | Resolve OQ-02 |
| F-04 | LOW | Status marker `[!]` added to this file beyond the three standard markers | ACCEPTED | Documented in §3 C-8 |

---

## 5. Report — Done / Remaining / Next

- **Done (Session 1):** reference repositories read; project inspected; documentation
  skeleton (`docs/`, `phases/phase-1..7`) created; initial drafts written; this audit file created.
- **Remaining:** confirm doctor requirements; confirm idea/scope/actors/modules;
  re-run C-1…C-4 after any change; close F-01 and F-03.
- **Next:** obtain the doctor's materials and answer OQ-01…OQ-03, then re-audit §1 and §2.
