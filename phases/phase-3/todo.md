# Phase 3

## Objective

System Flows & Data Flow: finalize `flow-of-action.md`, `flow-of-event.md`, and
`data-flow.md` from the Phase 2 use cases, with consistent diagrams and no schema design.

## Tasks

- [ ] 1. Derive flow of action for every confirmed use case
- [ ] 2. Derive flow of event (domain events + state changes)
- [ ] 3. Build Level-0 / Level-1 data flow diagrams
- [ ] 4. List data entities and conceptual relations (no schema)
- [ ] 5. Cross-check flows ↔ use cases ↔ actions for consistency
- [ ] 6. Review `docs/Audit.md` items "Events reviewed", "Data Flow reviewed"
- [ ] 7. Phase 3 completion review

## Deliverables

- [ ] `docs/flow-of-action.md` — final
- [ ] `docs/flow-of-event.md` — final
- [ ] `docs/data-flow.md` — final (conceptual, still no schema)
- [ ] Updated `docs/Audit.md`, `docs/memory.md`

## Completion Criteria

- [ ] Every confirmed use case has an action flow and event flow
- [ ] Every data flow references only entities defined in `data-flow.md`
- [ ] No database schema or storage technology introduced
- [ ] Consistency check against Phase 2 artifacts passes

## Dependencies

- Phase 2 completion

## Open Questions

- Doctor's required flow notation (OQ-01)
- Billing model drives the data flow (OQ-08)
