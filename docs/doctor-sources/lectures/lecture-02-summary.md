# Lecture 02 — Summary (Conceptual)

Status: Conceptual summary of `lecture-02-fundamentals-systems-architecture-integration.md`.
Course: System Architecture & Integration · IT Dept, 4th Level · Eng. Salah Alssayani · 2024–2025.

---

## 1. System — definition and its four elements

A **system** is a collection of components that work together to achieve a common purpose.
In computing it includes **hardware, software, data, people, and processes**, all coordinated
to deliver a specific function.

Key ideas from systems theory (von Bertalanffy, 1968):

- **Wholeness / emergence:** the whole is greater than the sum of its parts — *emergent
  properties* arise from component interactions that no single component possesses alone.

**The four elements of a system (lecture slide):**

1. **Components** — hardware, software, data, people, processes; each has a defined role.
2. **Interactions** — components communicate via *interfaces*; interactions produce the
   emergent behavior.
3. **Purpose** — every system has a goal; without purpose it is merely a collection of parts.
4. **Boundary** — what is inside (the system) vs. outside (the environment).

> Architecture defines *how* the parts interact — not just what the parts are.
> Definition used in the lecture: *"Architecture is the set of decisions whose cost-of-change
> grows over time."*

---

## 2. The six core architectural principles

| # | Principle | Meaning | Why it matters |
|---|---|---|---|
| 1 | **Separation of Concerns** | Each module addresses one concern (Dijkstra, 1974) | Independent evolution; changes stay local |
| 2 | **Trade-off Analysis** | Every decision optimizes some quality attribute *at the cost of another* (latency vs. cost, consistency vs. availability, security vs. convenience) | The architect's job is to make trade-offs explicit and defensible; ATAM (BCK) provides the structured method |
| 3 | **Abstraction** | Hide complexity behind simple interfaces | Consumers see the *contract*, not the implementation |
| 4 | **Loose Coupling** | Minimize dependencies between components | A change in one component does not ripple to others |
| 5 | **High Cohesion** | All code in a module serves one purpose; related functionality stays together | Modules are understandable and change safely |
| 6 | **Least Privilege** | Grant the minimum access needed | Applies to users, modules, and service boundaries |

How they work together: *separation + abstraction* enable *loose coupling*; *high cohesion*
keeps each concern intact; *least privilege* bounds who/what can act; *trade-off analysis*
is the method for choosing among competing architectures.

---

## 3. The three levels of architecture

| Dimension | System Architecture | Enterprise Architecture (EA) | Software Architecture |
|---|---|---|---|
| **Scope** | One system end-to-end (hardware + software + network) | Whole organization (business + IT + data + processes) | Software only (components, modules, services) |
| **Time horizon** | Years (system lifetime) | Years to decades (org lifetime) | Months to years (release cycles) |
| **Stakeholders** | System owners, ops, users | C-suite, business units, all IT | Developers, architects, product owners |
| **Concerns** | Hardware, deployment, network, HA | Business capabilities, data domains, vendor strategy | Code structure, patterns, frameworks, module boundaries |
| **Frameworks** | BCK, Richards & Ford | TOGAF, Zachman, ArchiMate | GoF, SOLID, DDD, EIP |
| **Position** | Bridges software and infrastructure | Highest level; aligns IT with business | Narrowest; code-level decisions |

---

## 4. Architectural views, stakeholders & concerns

No single diagram can represent a complex system.

**BCK — three structure categories:**

1. **Module view** — *How is code organized?* Packages, layers, components → for developers.
2. **Component-and-Connector (C&C) view** — *How does it run?* Services, processes, queues → for ops/SREs.
3. **Allocation view** — *Where does it live?* Servers, regions, teams → for devops/finance.

**Kruchten 4+1 View Model (1995):** Logical, Process, Development, Physical views **+ Scenarios**.

Rule of thumb: each view answers a different question for different stakeholders —
*"missing a view means missing a conversation."* The architect must choose which view serves
which conversation.

---

## 5. System integration — concept and the four levels

**Definition:** the discipline of connecting *independent* systems — each with its own data
model, protocols, and lifecycle — so they cooperate **as if they were one coherent system**.
Linthicum (1999): bringing together component subsystems into a whole.

| Level | What moves | Typical techniques |
|---|---|---|
| **Data-level** | Moving *bytes* between systems | Shared databases, file transfer, ETL pipelines, CDC |
| **Application-level** | Coordinating *behavior* across services | APIs, RPC, messaging brokers |
| **Process-level** | Coordinating *business workflows* | BPM, saga orchestration |
| **UI-level** | Unifying the *user experience* | Portals, mashups, SSO |

**Why it matters (business value):** cost reduction (no manual re-entry), single source of
truth (Customer 360), faster processes (order-to-cash in minutes), agility (swap vendors
without rewriting), M&A integration, compliance (end-to-end data lineage).
Without integration each app is a data silo — *integration is the bridge from data to insight.*

---

## 6. Integration vs. Migration

Two related but distinct disciplines; confusing them causes project failures.

| Dimension | Integration | Migration |
|---|---|---|
| Goal | Make independent systems cooperate as one | Move from old system to new system |
| Systems | Stay in place — connected, not replaced | Old system retired — replaced |
| Risk | Data inconsistency, coupling, performance | Data loss, downtime, user disruption |
| Approach | APIs, messaging, ETL, ESB, iPaaS | Data conversion, parallel runs, cutover |
| Timeline | **Continuous** — integration is never done | **Finite** — ends at cutover |
| Identity | Systems retain identity and ownership | Old system loses identity entirely |
| Key metric | End-to-end process latency | Cutover success rate, data integrity |

> **Key distinction:** integration connects systems that *coexist*; migration *replaces* one
> system with another. Many failures occur when teams treat integration as a one-time
> migration project — it never ends.

---

## 7. Direct (tight) coupling vs. Decoupled (loose) integration

The fundamental architectural choice: **synchronous and tight, or asynchronous and loose?**

| Dimension | Direct (Tight) | Decoupled (Loose) |
|---|---|---|
| Communication | Synchronous request-response (REST, gRPC) | Asynchronous events (Kafka, RabbitMQ, pub/sub) |
| Coupling | Caller knows callee | Producer does not know consumer |
| Failure mode | Cascading failures | Broker buffers; consumer catches up |
| Latency | Low (sub-ms → seconds) | Higher (seconds → minutes) |
| Consistency | Strong (immediate) | Eventual (converges) |
| Scalability | Limited by callee capacity | High — add consumers freely |
| Debugging | Easy — single call stack | Hard — distributed tracing required |
| Best for | Reads, queries, RPC commands (caller cannot proceed without the answer) | Writes, side effects, fan-out, audit (success can return before downstream completes) |

---

## 8. Heterogeneous systems & complexity

A **heterogeneous environment** = systems differ in hardware, OS, programming languages,
data models, network protocols, and ownership. It is the **default state of enterprise IT** —
not a problem to fix, but a reality to manage.

**Why heterogeneity exists:** historical accumulation (each team bought what was best at the
time), M&A legacy, technology evolution (REST/JSON vs SOAP/XML coexisting), legacy
persistence (mainframes, COBOL, AS/400 still run critical processes).

**Four diversity dimensions:** hardware · OS/runtime · data models (schema mapping is the
*hardest* part of data integration) · network protocols — plus language and deployment diversity.

**Core challenges:**

| Challenge | Impact | Mitigation |
|---|---|---|
| Interoperability | Manual re-entry, delays, errors | Protocol bridges (ESB, API gateway), canonical data models, adapters |
| Legacy systems | Cannot expose REST APIs; lock-in | Anti-corruption layer, screen scraping, progressive modernization |
| Siloed architectures | Duplication, no single source of truth | iPaaS, master data management, API-led connectivity |
| Data inconsistency | No Customer 360; compliance violations | MDM, event-driven sync, conflict resolution |
| Vendor lock-in | High switching cost | Open standards, abstraction layers |
| Skills gap | Multi-disciplinary teams required | Cross-training, low-code iPaaS, center of excellence |

**Cross-cutting concerns:** data consistency (ACID vs BASE, 2PC vs Sagas, LWW/CRDTs),
security & compliance (SSO/SAML/OIDC, Zero Trust, TLS 1.3, AES-256, Vault),
observability (OpenTelemetry, distributed tracing), governance (MDM, data catalog, RBAC/ABAC, OPA).

> **Key insight:** these challenges are why **integration is harder than building** — you
> inherit every constraint (protocols, data models, vendor APIs, team skills) and must
> compose them into a coherent whole.

---

## 9. Course roadmap (what comes next)

The lecture established the vocabulary; **11 more lectures (L2 → L14)** follow:

| Block | Lectures | Content |
|---|---|---|
| Foundations | L3–L4 | Architectural styles + distributed systems |
| Integration | L5–L8 | EAI, middleware, web services, SOA |
| Event-driven | L9–L11 | EDA, streaming, Kafka |
| Data | L10 | Database integration, ETL, CDC, consistency |
| Cloud & Security | L12–L13 | Cloud integration, auth, API security |
| Quality | L14 | Performance, scalability, observability |

**Recommended reading:** BCK *Software Architecture in Practice* 4/e Ch.1–3 · Linthicum
*Enterprise Application Integration* (1999) Ch.1–2 · Kleppmann *Designing Data-Intensive
Applications* Ch.1 · Hohpe & Woolf *Enterprise Integration Patterns* (skim Ch.1) ·
Tanenbaum & Van Steen *Distributed Systems* 3/e · ISO/IEC/IEEE 42010:2022.

**Next in the lecture series:** Lecture 3 — Foundational Architectural Styles
(Monolithic, Client-Server, Layered, N-Tier, MVC).

---

*Relation to TCMS: this lecture supplies the vocabulary used later in the course (coupling,
integration levels, views). It does not add project requirements — TCMS requirements still
come from the doctor's project instructions (see `docs/doctor-sources/`).*
