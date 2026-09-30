# memory.md — TCMS Project Memory

Purpose: single source of truth for what is **confirmed**, what is **open**, and what is
**pending**. Assumptions are never stored here as confirmed decisions.

Last updated: 2026-09-30 (Session 6 — doctor sources fully processed: whiteboard transcribed, OQ-01/02/03 resolved)

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
- Git: root commit `687b8a6` on `main` (2026-09-30) covering docs/, phases/, .gitignore;
  `_incoming/*.zip` gitignored; no remote. Nothing pushed, no reset/clean/branch ops.
- `_incoming/` contains 3 zips: `delegate-skills`, `pro-skills-senior-full-stack-software-engineer`,
  `senior-implementation-rules`. They were extracted to a temp folder for reading only;
  the zips inside `_incoming/` are untouched.
- Reference rules are applied selectively; see `docs/implement-plan.md` §7 for the
  adopted / not-adopted lists.
- **Doctor sources arrived** and live in `docs/doctor-sources/` (index: its `README.md`);
  originals stay untouched in `C:\Telecome/uploads/`.
- **Doctor's projects list saved** → `doctor-sources/projects/projects-list.txt` (verbatim):
  26 proposed projects — **TCMS = #16 نظام إدارة شركات الاتصالات**; groups ≤10 students;
  idea + initial analysis due before next lecture's session; non-project students graded by
  exam only; the engineer helps with per-phase plans.
- **Both lectures are available as text:** `lectures/lecture-01-text.md` (51 pages) and
  `lectures/lecture-02-text.md` (21 pages); Lecture 02 also has `lecture-02-summary.md`
  (conceptual summary). Duplicate extraction of L2 was removed as junk (Session 5).
- **Lecture 01 original PDF** in `lectures/` was originally scanned (AnyScanner) and is kept
  unchanged; the failed extraction stub was removed as junk (Session 5) — the readable text
  now lives in `lecture-01-text.md`.
- **Core course concepts:** *System* (4 elements: components, interactions, purpose,
  boundary) · *Architecture levels* (System / Enterprise / Software; views: Module, C&C,
  Allocation, 4+1; principles: separation of concerns, trade-off analysis, abstraction,
  loose coupling, high cohesion, least privilege) · *Integration levels* (data, application,
  process, UI; integration vs migration) · *Coupling* (direct/tight vs decoupled/loose) ·
  *Heterogeneous systems* (interoperability, legacy, silos).
- **Course roadmap:** 11 further lectures (L2 → L14).
  **Lecture 3 = Foundational Architectural Styles** (Monolithic, Client-Server, Layered,
  N-Tier, MVC).

---

## 3. Open questions

| ID | Question | Blocks |
|---|---|---|
| OQ-01 | Doctor's materials (lectures + projects list + whiteboard) | **Resolved** — all 3 sources documented under `docs/doctor-sources/` (lectures 01/02 text, `projects/projects-list.txt`, `whiteboard/whiteboard-notes.md`) |
| OQ-02 | Does the doctor use the 7-phase split in `implement-plan.md` §3, or a different one? | **Resolved** — whiteboard names Phase 1/2/3 explicitly + "Phases المتبقية" (→ 4–7) + "اكتب phase في ملف منفصل" = our structure |
| OQ-03 | Is the required documentation file list complete (13 files), or does the doctor add more? | **Resolved** — whiteboard lists 9 core docs + mindmap/Audit/memory + "Todo for each Phase" + "all other required md file" = 13/13 |
| OQ-04 | Is TCMS a real-world-style system for a telecom operator, or an academic exercise scope? | Scope, modules, boundaries |
| OQ-05 | Commit policy for *future* commits (initial commit `687b8a6` already made on request) | Change tracking |
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

## 4A. Session 3 — Doctor Sources Fully Processed

- **Projects list preserved** — `doctor-sources/projects/projects-list.txt` (26 projects; **#16 = TCMS**).
- **Whiteboard transcribed** — `doctor-sources/whiteboard/whiteboard-notes.md`, with per-item
  confidence markers `[مؤكد]` / `[غير واضح]`.
- **Phase 1 / Phase 2 / Phase 3 confirmed by name** on the doctor's whiteboard.
- **"اكتب phase في ملف منفصل"** (write each phase in a separate file) = our
  `phases/phase-N/todo.md` structure — confirmed.
- **Discoveries:** `SEO`, `Home/About`, `house plan / home page` appear on the whiteboard →
  handled in **Phase 4** (Website Structure); no structure change needed.

---

## Team (Confirmed)

- Size: 8 members (within Doctor's limit ≤10 ✅)
- Source: docs/doctor-sources/team.md
- Repo Owner: AimanSoft
- Confirmed usernames: 5/8 (aim45an, AimanSoft, wwwyhye00-dev, almorady55, alhareth447)
- Pending usernames: عمار، أسامة، خليل أمين
- Roles: Not yet assigned

---

## 5. Important notes

- Nothing in `docs/` is a Confirmed Requirement unless it is listed in §1 or explicitly
  confirmed by the user/doctor.
- Draft artifacts (`use-case-*`, `flow-*`, `data-flow`, `website-structure`,
  `ui-ux-specification`, `architecture`) are **Initial Drafts** intended to be revised
  after Phase 2 fixes the use cases.
- Reference-repository rules must never create requirements that the doctor did not ask for.
