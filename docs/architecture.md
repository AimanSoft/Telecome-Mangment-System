# System Architecture — TCMS

> Status: Draft — Based on aim45an diagrams
> ⚠️ TEAM DECISION — Pending Doctor approval
> The team proposes Microservices + Event-Driven. Doctor has not yet approved.

## 1. Architectural Style

**Proposed:** Microservices + Event-Driven
**Alternative (not decided):** Modular Monolith

## 2. Technology Stack (Proposed)

| Layer | Technology |
|-------|-----------|
| Frontend | Angular (SPA) |
| API Gateway | NestJS :3000 |
| Services | Node.js 20 (Alpine) |
| Database | PostgreSQL 16 |
| Message Broker | RabbitMQ 3 |
| Cache | Redis 7 |
| Deployment | Docker Compose |
| Repo Structure | Monorepo (npm workspaces) |

## 3. Components (12 Services)

M1-M12 — see use-case-scenario.md

## 4. Layers

### Presentation Layer
- Web Portal (Angular) — بوابة المشتركين
- Employee Console — وحدة موظف خدمة العملاء
- Admin Dashboard — لوحة الإدارة والتقارير
- Mobile App (Mock)

### API Layer
- API Gateway (NestJS :3000)
- JWT Guard + Rate Limit
- Request Logging + Proxy
- Auth Middleware (JWT + RBAC)
- Health / Circuit Breaker

### Services Layer (12 Microservices)
M1-M12 as described

### Integration Layer (Mock Adapters)
- Identity Adapter (timeout 3000ms + circuit breaker)
- Payment Adapter (HMAC signature + idempotency)
- SMS / Email Adapter (Queue-based retry)
- Network Adapter (BSS / OSS Mock)

### Data + Event Layer
- RabbitMQ 3 (Topic Exchange events.*)
- PostgreSQL 16 (customers, invoices, support_tickets)
- Redis 7 (Cache + Session + Rate Limit)
- Audit Log Store

## 5. External Systems (Mock)
- Identity System
- Payment Gateway
- SMS / Email Provider
- Monitoring (Prometheus + Grafana Mock)

## 6. Deployment (Docker Compose)

- api-gateway :3000
- customer-service :4001
- billing-service :4002
- support-service :4003
- postgres :5432
- rabbitmq :5672 / :15672
- redis :6379

Network: tcms_net (internal)

## 7. Open Architectural Decisions

- [ ] Doctor approval of Microservices vs Monolith
- [ ] Doctor approval of specific stack
- [ ] Cloud deployment target
- [ ] Database per service vs shared

## Diagram source

- `docs/diagrams/18-component-diagram.drawio`
- `docs/diagrams/19-deployment-diagram.drawio`
- `docs/diagrams/16-class-diagram-domain-model.drawio`
- `docs/diagrams/17-erd-database-schema.drawio`
- `docs/diagrams/20-package-diagram.drawio`
