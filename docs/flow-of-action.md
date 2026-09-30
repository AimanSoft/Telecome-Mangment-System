# flow-of-action.md — TCMS Flow of Action

Status: **Initial Draft.** Explicitly provisional: these flows are re-derived after the
use cases are fixed in Phase 2 (`use-case-scenario.md`, `use-case-action.md`).

Scope: a representative flow per main operation. Not exhaustive.

---

## 1. Flow of action — Subscriber registration (UC-01, Draft)

```mermaid
flowchart TD
    A[Start: sales agent opens registration] --> B{Duplicate search}
    B -- existing found --> C[Update existing record]
    B -- none found --> D[Enter subscriber data]
    D --> E{Validation}
    E -- invalid --> D
    E -- valid --> F[Save subscriber]
    F --> G[End: subscriber active]
    C --> G
```

---

## 2. Flow of action — Package assignment (UC-02, Draft)

```mermaid
flowchart TD
    A[Open subscriber record] --> B[List available packages]
    B --> C[Select package]
    C --> D{Validation / eligibility}
    D -- fails --> B
    D -- ok --> E[Save subscription]
    E --> F[End]
```

---

## 3. Flow of action — Invoice generation (UC-03, Draft)

```mermaid
flowchart TD
    A[Select billing period] --> B[Compute charges]
    B --> C[Review invoice]
    C -- corrections needed --> B
    C -- ok --> D[Issue invoice]
    D --> E[End: invoice available]
```

Open: automatic vs manual trigger (OQ-08).

---

## 4. Flow of action — Payment recording (UC-04, Draft)

```mermaid
flowchart TD
    A[Open invoice] --> B[Enter payment]
    B --> C{Amount valid?}
    C -- no --> B
    C -- yes --> D[Save payment]
    D --> E[Update invoice status]
    E --> F[End]
```

---

## 5. Flow of action — Complaint handling (UC-05/UC-06, Draft)

```mermaid
flowchart TD
    A[Lodge complaint] --> B[Complaint open]
    B --> C[Investigate / record notes]
    C --> D{Resolved?}
    D -- no --> C
    D -- yes --> E[Close complaint]
    E --> F[End]
```

---

## 6. Flow of action — User & role management (UC-08, Draft)

```mermaid
flowchart TD
    A[Administrator opens users] --> B[Create or edit account]
    B --> C[Assign role]
    C --> D[Save]
    D --> E[Audit log entry]
    E --> F[End]
```

---

## 7. Revision note

- All flows assume a web application with server-side validation — this is an
  **Assumption**, not a decided architecture (see `docs/architecture.md`).
- Flows will be reviewed against Phase 2 use cases and against the doctor's flow
  requirements (there may be a prescribed flow format — Open Question OQ-01).
