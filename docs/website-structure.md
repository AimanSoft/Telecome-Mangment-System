# website-structure.md — TCMS Website Structure

Status: **Initial Structure (Draft).** No frontend implementation is started from this
file. Structure is provisional until the doctor's requirements and the confirmed actor
list exist.

Assumption behind this file: TCMS is a web application (the brief names it "Website
Structure"). This is marked **Assumption** pending confirmation.

---

## 1. Site map (Draft)

```
/ (Public)
├── /login                        Sign in
├── /forgot-password              Password recovery (Assumption)
│
/app (Authenticated — role-based)
├── /dashboard                    Overview / KPIs
│
├── /subscribers                  Subscriber list + search
│   ├── /subscribers/new          Registration (UC-01)
│   └── /subscribers/:id          Subscriber detail
│       ├── /subscribers/:id/packages   Package assignment (UC-02)
│       └── /subscribers/:id/invoices   Invoices of subscriber
│
├── /packages                     Package list (UC-02 support)
│   └── /packages/new | /packages/:id
│
├── /billing
│   ├── /billing/invoices         Invoice list (UC-03)
│   ├── /billing/invoices/:id     Invoice detail
│   └── /billing/payments         Payments (UC-04)
│
├── /support
│   ├── /support/complaints       Complaint list (UC-05/06)
│   └── /support/complaints/:id   Complaint detail
│
├── /reports                      Reports (UC-09)
│
└── /admin
    ├── /admin/users              Users & roles (UC-08)
    ├── /admin/roles              Roles & permissions
    └── /admin/settings           System settings (Assumption)
```

---

## 2. Navigation rules (Draft)

- Top-level navigation reflects modules M-1…M-9 of `use-case-scenario.md` §3.
- Items are shown/hidden by role (server-side authorization is mandatory when
  implemented — senior-rules SEC-02; not yet applicable).
- Subscriber self-service portal (`/portal` for A-5) is **excluded for now** —
  assumption, pending OQ-04.

---

## 3. Page inventory (Draft, minimal)

| Route | Purpose | Primary actor |
|---|---|---|
| /login | Authenticate | all |
| /dashboard | Summary indicators | all (role-filtered) |
| /subscribers* | Subscriber management | Sales, CS, Admin |
| /packages* | Package management | Sales, Admin |
| /billing/* | Invoices & payments | Billing |
| /support/* | Complaints | CS |
| /reports | Reports | Admin, Billing |
| /admin/* | Users, roles, settings | Admin |

---

## 4. Not included (explicit)

- No HTML/CSS/JS code, no framework choice, no component library.
- No responsive/visual design — that belongs to `ui-ux-specification.md`.
- No URL/route contract treated as final.

## 5. Open questions

- Is there a customer-facing portal? (OQ-04)
- Is a mobile app part of the project? (unknown)
- Does the doctor prescribe a specific site-structure format (e.g., sitemap diagram)? (OQ-01)
