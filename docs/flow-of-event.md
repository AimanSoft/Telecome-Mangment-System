# Flow of Event — TCMS

> Status: Draft — Based on aim45an diagrams (Team Decision, Pending Doctor)
> Source: Sequence + Event Flow Diagrams (docs/diagrams/phase-3-flows/ — 07-10, 28)

## Event-Driven Architecture

**Broker:** RabbitMQ 3 (Topic Exchange)
**Exchange:** events.*
**Pattern:** Publish/Subscribe + Commands

### Commands (Actors → System)
| Command | Issuer | Handler |
|---------|--------|---------|
| CreateCustomer | Customer Service | Customer Service |
| AssignSim | Customer Service | SIM & Number Service |
| CreateSubscription | Customer Service | Subscription Service |
| ProcessPayment | Customer | Payment Service |
| ReportIncident | Network Engineer | Incident Service |

### Events (System → Subscribers)

| Event | Publisher | Subscribers | Payload |
|-------|-----------|-------------|---------|
| CustomerCreated | Customer Service | Billing, Notification, Audit | C-101 |
| SimAssigned | SIM & Number Service | Subscription, Notification | iccid |
| SubscriptionCreated | Subscription Service | Billing, Notification | SUB-501 |
| InvoiceGenerated | Billing Service | Payment, Notification | INV-901 |
| PaymentCompleted | Payment Service | Billing, Notification | ref |
| InvoicePaid | Billing Service | Notification, Usage | INV-901 |
| IncidentReported | Incident Service | Support, Notification | INC-204 |
| TicketCreated | Support Service | Notification | TKT-000931 |

### Event Flow Example: Payment (UC-28)

### Message Policies
- **Idempotency:** Payment uses idempotencyKey (UNIQUE)
- **Retry:** 5 attempts then Dead Letter Queue
- **Idempotent Consumer:** 24h cache window
- **Partitioning:** partitionKey = aggregateId
- **Command vs Event:** Command = imperative (do X), Event = past tense (X happened)

## Diagram source

- `docs/diagrams/phase-3-flows/07-sequence-identity-verification.drawio`
- `docs/diagrams/phase-3-flows/08-sequence-payment-invoice.drawio`
- `docs/diagrams/phase-3-flows/09-sequence-sim-subscription.drawio`
- `docs/diagrams/phase-3-flows/10-sequence-incident-ticket.drawio`
- `docs/diagrams/phase-3-flows/28-event-flow-diagram.drawio`
