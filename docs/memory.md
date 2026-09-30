# memory.md — TCMS Project Memory

Purpose: single source of truth for what is **confirmed**, what is **open**, and what is
**pending**. Assumptions are never stored here as confirmed decisions.

Last updated: 2026-09-30 (Session 2 — Git repo fact added)

---

## 1. Confirmed decisions

| ID | Decision | Source |
|---|---|---|
| D-01 | Project root is `C:\Telecome` | User brief |
| D-02 | `_incoming/` is read-only reference material; never modify or delete | User brief |
| D-03 | Project name: Telecom Management System (TCMS) / نظام إدارة شركات الاتصالات | User brief |
| D-04 | Course context: System Integration / System Architecture | User brief |
| D-05 | Documentation lives in `docs/`; per-phase todos live in `phases/phase-N/todo.md` | User brief |
| D-06 | Status markers are only `[ ]` Not Started, `[~]` In Progress, `[x]` Completed | User brief |
| D-07 | `[x]` only when the work exists and is reviewable | User brief |
| D-08 | No Backend/Frontend/DB-schema/API/Auth/stack decision before the phases allow it | User brief |
| D-09 | Doctor's instructions outrank reference repositories in `_incoming/` | User brief |

---

## 2. Important project facts

- `C:\Telecome` was **empty** (except `_incoming/`) when the project started:
  no `docs/`, no `phases/`, no doctor files, no prior Todo.
- Git repository initialized 2026-09-30 04:59 (after Session 1): branch `main`, **0 commits**,
  no remote; `docs/`, `phases/`, `_incoming/` untracked. Nothing has been committed.
- `_incoming/` contains 3 zips: `delegate-skills`, `pro-skills-senior-full-stack-software-engineer`,
  `senior-implementation-rules`. They were extracted to a temp folder for reading only;
  the zips inside `_incoming/` are untouched.
- Reference rules are applied selectively; see `docs/implement-plan.md` §7 for the
  adopted / not-adopted lists.

---

## 3. Open questions

| ID | Question | Blocks |
|---|---|---|
| OQ-01 | Where are the doctor's materials (lectures, PDF, notes)? None exist in the project. | Phase 1 confirmation, phase split validation |
| OQ-02 | Does the doctor use the 7-phase split in `implement-plan.md` §3, or a different one? | Phase plan approval |
| OQ-03 | Is the required documentation file list complete (13 files), or does the doctor add more? | docs/ structure approval |
| OQ-04 | Is TCMS a real-world-style system for a telecom operator, or an academic exercise scope? | Scope, modules, boundaries |
| OQ-05 | Git repo now exists (0 commits): should the documentation be committed, and with what commit policy? | Review history |
| OQ-06 | Which actors are in scope (admin, customer service, billing, sales, subscriber, technician…)? | Use cases (Phase 2) |
| OQ-07 | Does the system include network/field-operations domains, or only business/support domains? | Modules, boundaries |
| OQ-08 | Are there non-functional requirements stated by the doctor (users count, response time, security)? | Architecture, NFRs |

---

## 4. Pending decisions

| ID | Decision needed | Owner |
|---|---|---|
| PD-01 | Approve or replace the 7-phase split | User / Doctor |
| PD-02 | Approve or replace the initial module list (`use-case-scenario.md` §3) | User / Doctor |
| PD-03 | Approve or replace the initial actor list | User / Doctor |
| PD-04 | Technology stack — **not to be decided before Phase 5/6** | User / Doctor |
| PD-05 | Architecture style (monolith / modular / services / event-driven) — **not decided** | User / Doctor |

---

## 5. Important notes

- Nothing in `docs/` is a Confirmed Requirement unless it is listed in §1 or explicitly
  confirmed by the user/doctor.
- Draft artifacts (`use-case-*`, `flow-*`, `data-flow`, `website-structure`,
  `ui-ux-specification`, `architecture`) are **Initial Drafts** intended to be revised
  after Phase 2 fixes the use cases.
- Reference-repository rules must never create requirements that the doctor did not ask for.
