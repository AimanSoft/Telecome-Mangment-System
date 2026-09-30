# Phase 5

## Objective

System Architecture & Integration: choose and document the architecture, system
boundaries, integration points, and communication approach — **after** the doctor's
requirements and NFRs are known. This phase decides; it does not implement.

## Tasks

- [ ] 1. Collect NFRs, constraints, and external systems from the doctor's sources (OQ-08)
- [ ] 2. Evaluate architecture style options (AD-1) and record the decision + rationale
- [ ] 3. Select technology stack (AD-2 / PD-04) — requires user approval
- [ ] 4. Define system boundaries and integration contracts (AD-4)
- [ ] 5. Define authentication/authorization approach (AD-5)
- [ ] 6. Update `docs/architecture.md` from Initial Draft to approved architecture
- [ ] 7. Add security considerations required by the doctor
- [ ] 8. Review `docs/Audit.md` item "Architecture reviewed"
- [ ] 9. Phase 5 completion review

## Deliverables

- [ ] `docs/architecture.md` — approved version (replaces Initial Draft)
- [ ] Updated `docs/memory.md` (PD-04, PD-05 resolved)
- [ ] Updated `docs/Audit.md`

## Completion Criteria

- [ ] Architecture decision documented with rationale and alternatives considered
- [ ] All open architectural decisions AD-1…AD-6 closed or explicitly deferred
- [ ] Integration points either confirmed or explicitly declared out of scope
- [ ] User approval recorded for stack and architecture (PD-04, PD-05)

## Dependencies

- Phase 4 completion
- Doctor's NFR/security requirements (missing → OQ-01, OQ-08)

## Open Questions

- Which architecture style suits the course expectations? (PD-05)
- Is any real external integration required, or simulated? (OQ-08)
