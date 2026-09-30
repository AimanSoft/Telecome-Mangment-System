# Implement Plan — Telecom Management System (TCMS)

- Project: نظام إدارة شركات الاتصالات / Telecom Management System (TCMS)
- Course: System Integration / System Architecture
- Plan status: **DRAFT — Pending Confirmation of doctor's requirements**
- Project root: `C:\Telecome`
- Git: repository initialized 2026-09-30 04:59, branch `main`, **0 commits** (all files untracked) — see §9

---

## 1. Purpose of this document

This is the master implementation plan for TCMS. It defines the phase breakdown, the
documentation set, the status system, and the rules adopted from the reference
repositories in `_incoming/`.

It does **not** authorize implementation. No Backend, Frontend, database schema, APIs,
authentication, or technology stack is decided in this plan.

---

## 2. Source hierarchy (precedence)

| Rank | Source | Status |
|---|---|---|
| 1 | Doctor's instructions (lectures, PDFs, notes, project files) | **NOT YET AVAILABLE in project** — see §10 |
| 2 | This plan + `docs/*` + `phases/*/todo.md` | Draft, pending doctor confirmation |
| 3 | `_incoming/senior-implementation-rules` | Applied selectively (see §7) |
| 4 | `_incoming/pro-skills-senior-full-stack-software-engineer` | Applied selectively (see §7) |
| 5 | `_incoming/delegate-skills` | Available; used only for non-decision work (see §7) |

Rule: a reference rule is **never** applied if it contradicts items 1–2. No requirement
is ever invented from a reference repository.

---

## 3. Phase plan (draft)

| Phase | Name | Focus |
|---|---|---|
| Phase 1 | Project Planning & Initial Analysis | Idea, scope, objective, actors, modules, operations, data, boundaries |
| Phase 2 | Use Case Analysis | Use case scenario, use case actions |
| Phase 3 | System Flows & Data Flow | Flow of action, flow of event, data flow |
| Phase 4 | Website Structure & UI/UX | Site map, UI/UX specification |
| Phase 5 | System Architecture & Integration | Architecture, integration points, boundaries |
| Phase 6 | Implementation | Build (blocked until Phases 1–5 accepted) |
| Phase 7 | Testing, Audit & Final Review | Test plan, Audit, final consistency review |

**Status of this breakdown: DRAFT — Pending Confirmation.**
No source in the project currently defines the doctor's phase split, so this split cannot
be compared against the doctor's version yet. When the doctor's materials arrive:

- if the doctor uses a different split → the doctor's split is adopted;
- this file must then be updated and the difference explained in this section (not hidden).

**Difference already found in reference sources (declared openly):**
`_incoming/senior-implementation-rules` defines a different documentation model
(`docs/phases/<phase-slug>/` with 16 artifacts per phase, plus a canonical entry set:
`ENTRY.md`, `mind_map.md`, `development_phases_entry.md`, `all_in_one_track.md`,
`session_track.md`, `CHANGELOG.md`). That structure is **not adopted**, because the
project's required structure is `docs/` + `phases/phase-N/todo.md` with the file names
listed in §5. Only the *content* rules of the reference set are adopted (§7).

---

## 4. Work breakdown

| Task ID | Task | Depends on | Status |
|---|---|---|---|
| T-1-01 | Locate and read all doctor source materials | — | BLOCKED — no doctor files found in project |
| T-1-02 | Confirm project idea with the user/doctor | T-1-01 | [ ] Not Started |
| T-1-03 | Define initial scope, objective, boundaries | T-1-02 | [~] In Progress (draft written) |
| T-1-04 | Identify actors, modules, operations, data | T-1-03 | [~] In Progress (draft written) |
| T-1-05 | Create documentation skeleton (`docs/`, `phases/`) | — | [x] Completed |
| T-1-06 | Write initial analysis (`docs/initial-status.md`, `docs/memory.md`) | T-1-03, T-1-04 | [x] Completed (draft content, unconfirmed) |
| T-1-07 | Draft use-case / flow / structure / UI / architecture files | T-1-04 | [x] Completed (Initial Draft only) |
| T-1-08 | Phase 1 completion review against doctor requirements | T-1-01…T-1-07 | [ ] Not Started |
| T-2-01 | Use Case Analysis (Phase 2) | Phase 1 accepted | [ ] Not Started |
| T-3-01 | Flows & Data Flow finalized (Phase 3) | Phase 2 accepted | [ ] Not Started |
| T-4-01 | Website structure & UI/UX (Phase 4) | Phase 3 accepted | [ ] Not Started |
| T-5-01 | Architecture & integration (Phase 5) | Phase 4 accepted | [ ] Not Started |
| T-6-01 | Implementation (Phase 6) | Phases 1–5 accepted + stack decision | [ ] Not Started |
| T-7-01 | Testing, audit, final review (Phase 7) | Phase 6 | [ ] Not Started |

---

## 5. Documentation structure

```
C:\Telecome
│
├── docs/
│   ├── implement-plan.md
│   ├── use-case-scenario.md
│   ├── use-case-action.md
│   ├── flow-of-action.md
│   ├── flow-of-event.md
│   ├── data-flow.md
│   ├── website-structure.md
│   ├── ui-ux-specification.md
│   ├── architecture.md
│   ├── mindmap.md
│   ├── memory.md
│   ├── Audit.md
│   └── initial-status.md
│
├── phases/
│   ├── phase-1/todo.md … phase-7/todo.md
│
└── _incoming/          (reference repos — read-only, never modified)
```

If the doctor's sources specify different file names, the doctor's names win and this
section is updated with the reason.

---

## 6. Status system (project-wide)

| Marker | Meaning |
|---|---|
| `[ ]` | Not Started |
| `[~]` | In Progress |
| `[x]` | Completed — work exists and is reviewable |

Distinction that must never be blurred:
**Confirmed Requirement · Draft · Assumption · Open Question · Decision Needed · Completed.**
Anything not confirmed by the doctor/user is marked `Draft`, `Pending Confirmation`,
`Assumption`, or `Open Question`.

---

## 7. Rules adopted from the reference repositories

Adopted (content rules only):

| Rule | Source | Meaning in TCMS |
|---|---|---|
| GEN-02/GEN-03 | senior-rules | Implement completely; **never claim completion that is not verifiable** |
| GEN-04 | senior-rules | Claims backed by evidence (file exists, output pasted) |
| DOC-02/DOC-03 | senior-rules | Every phase has its own todo file, produced from a consistent template |
| DOC-04 | senior-rules | Documents interlink; no orphan docs |
| AUD-01/AUD-04 | senior-rules | `docs/Audit.md` checklist + Done/Remaining/Next reporting |
| COM-01/COM-02 | senior-rules | Ambiguity → ask before acting; questions batched in Open Questions |
| DOD-10 | senior-rules | A task failing any gate is reported as incomplete, never as done |
| SDLC/charter/RACI elements | pro-skills 01 | Used as a checklist for scope/objective/stakeholder completeness |
| Requirements engineering hygiene | pro-skills 14 | Confirmed vs draft vs assumption separation |

Explicitly **not** adopted (conflicts with project structure / premature):

- senior-rules canonical entry file set (`ENTRY.md`, `session_track.md`, `RULES.md`,
  `CHANGELOG.md`, `mind_map.md`, …) — project structure in §5 governs.
- senior-rules `docs/phases/<slug>/` 16-artifact set — project structure in §5 governs.
- senior-rules DOD numeric build/test/lint gates — not applicable until Phase 6.
- senior-rules VCS commit/push gates — the repo exists but has **0 commits**; commit policy
  awaits an explicit user instruction (OQ-05). Nothing is committed without being asked.
- delegate-skills multi-agent orchestration — not used for any decision that belongs to
  the user; delegation is limited to reading/searching/exploration.

---

## 8. Gates before Phase 2 starts

- [ ] Doctor source materials read (currently missing)
- [ ] Project idea confirmed
- [ ] Scope, objective, boundaries confirmed
- [ ] Actors, modules, operations, data reviewed
- [ ] `docs/initial-status.md` reflects the real state
- [ ] Open Questions answered or explicitly deferred by the user
- [ ] No Phase 6 work started (no code, no schema, no stack decision)

---

## 9. Repository / safety

- `C:\Telecome` **is** a Git repository since 2026-09-30 04:59 (`git init`, branch `main`,
  0 commits, no remote). Local config has no `user.name`/`user.email` (global `AimanSoft` used).
  Current status: `docs/`, `phases/`, `_incoming/` are **untracked**.
  Open: should the initial documentation be committed, and with what policy? (OQ-05)
- No commit, push, reset, clean, or branch operation was performed by this session.
- `_incoming/` is read-only reference material: never modified, never deleted.
- No existing work was deleted in creating this plan (project contained no prior files).

---

## 10. Missing information (blocking)

- **No doctor materials found** in `C:\Telecome` (no lectures, PDFs, TXT, MD notes,
  Project Knowledge, or prior `docs/`). Everything in §3–§8 is therefore Draft until
  those materials are provided.
- The requirement list used here (Implement Plan, Use Case Scenario, Use Case Action,
  Flow of Action, Flow of Event, Data Flow, Website Structure, UI/UX Specification,
  Architecture, Phase Todo, mindmap.md, Audit.md, memory.md) is taken from the project
  brief and **must be verified** against the doctor's own list.

---

## 11. Risks

| Risk | Severity | Mitigation |
|---|---|---|
| Doctor requirements differ from this draft | HIGH | All files marked Draft; nothing treated as confirmed |
| Scope invented beyond doctor's intent | HIGH | No requirement written without source; gaps listed as Open Questions |
| Premature implementation | HIGH | Phase 6 blocked by gate in §8 |
| Reference rules overriding the doctor | MEDIUM | Precedence table in §2; non-adopted rules listed in §7 |
