# Phase 2 — Use Case Analysis

## Objective

Analyze and document all Use Cases for TCMS based on the confirmed actors and modules from Phase 1. Produce Use Case Scenarios and Use Case Actions in the format approved by the Doctor.

## Pre-conditions (مطلوب قبل البدء)

- [ ] OQ-06 (Actor list) resolved and approved by Doctor/Engineer
- [ ] Use Case template received from Doctor (Cockburn / UML / Tabular)
- [ ] Rubric for grading Use Cases received
- [ ] Confirmation that Phase 1 initial delivery was accepted

## Tasks

### A. Preparation
- [x] Confirm final actor list from Phase 1 initial analysis
- [x] Cross-check actors against Doctor's whiteboard requirements
- [ ] Receive Use Case template (format specification)
- [ ] Set naming conventions (UC-01, UC-02, ...)
- [ ] Confirm level of detail (brief / casual / fully-dressed)

### B. Use Case Identification
- [x] List all candidate Use Cases per actor
- [x] Categorize by module (Subscribers, Services, Billing, Support, Network, Admin)
- [ ] Prioritize (Must-have / Should-have / Could-have)
- [ ] Review with team (7 members)
- [ ] Freeze the Use Case list

### C. Use Case Scenario Writing
- [~] For each Use Case: write Pre-conditions
- [~] For each Use Case: write Main Flow (Happy Path)
- [~] For each Use Case: write Alternate Flows
- [~] For each Use Case: write Exception Flows
- [~] For each Use Case: write Post-conditions
- [ ] Cross-reference with data entities from Phase 1

### D. Use Case Action Writing
- [~] For each Use Case: identify Actor Actions
- [~] For each Use Case: identify System Actions
- [~] Map Action → Trigger → Result
- [ ] Verify coverage (each UC has at least 1 action)

### E. Diagram (if required by Doctor)
- [x] Create Use Case Diagram (UML)
- [x] Show Actors, Use Cases, relationships
- [ ] Include «include» and «extend» where applicable
- [ ] Save as docs/diagrams/use-case-diagram.png or .puml

### F. Consistency & Review
- [ ] All Use Cases consistent with Phase 1 actors
- [ ] All Use Cases consistent with Phase 1 modules
- [ ] All Use Cases reference valid data entities
- [ ] No orphan actions
- [ ] Internal team review
- [ ] Update docs/Audit.md with Phase 2 checklist
- [ ] Update docs/memory.md with Phase 2 decisions

### G. Phase 2 Closure
- [ ] All Phase 2 tasks marked [x]
- [ ] All deliverables present
- [ ] Update docs/initial-status.md
- [ ] Update docs/mindmap.md with Use Cases
- [ ] Commit + push

## Deliverables

- docs/use-case-scenario.md — Complete (not Draft)
- docs/use-case-action.md — Complete (not Draft)
- docs/diagrams/use-case-diagram.* (if required)
- Updated docs/mindmap.md
- Updated docs/memory.md
- Updated docs/Audit.md
- Updated phases/phase-2/todo.md (this file, [x] marked)

## Completion Criteria

- [ ] Every Use Case has: Pre-conditions, Main Flow, Alternate Flows, Post-conditions
- [ ] Every Use Case has at least one Actor Action
- [ ] Every Use Case references valid data entity
- [ ] Use Case diagram covers 100% of Use Cases
- [ ] No Use Case contradicts Phase 1
- [ ] Doctor's template followed exactly
- [ ] Internal peer review passed
- [ ] Git commit signed off

## Dependencies

- ✅ Phase 1 — Completed
- ⏳ OQ-06 (Actor list) — Pending
- ⏳ Use Case template from Doctor — Pending
- ⏳ Phase 1 delivery acceptance — Pending

## Open Questions

- OQ-06: Final actor list?
- OQ-08: Language (AR/EN/Both)? RTL support?
- Use Case template: Cockburn? UML? Tabular?
- Use Case diagram required or optional?
- Number of Use Cases expected: 10? 20? 30?
- Level of detail: brief or fully-dressed?

## Notes

- لا تبدأ كتابة Use Cases فعلية قبل استيفاء Pre-conditions.
- كل بيانات الفريق في docs/doctor-sources/team.md
- Team size: 7 members — يمكن توزيع Use Cases
- Deadline: after Doctor's confirmation
