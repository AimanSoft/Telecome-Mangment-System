# Flow of Action — TCMS

> Status: Draft — Based on aim45an diagrams (Team Decision, Pending Doctor)
> Source: Activity Diagrams in docs/diagrams/

## UC-05: Create Customer (onboarding flow)

**Actor:** Customer Service Employee
**Trigger:** Customer visits branch with national ID
**Precondition:** Employee logged in (UC-01)

### Main Flow:
1. Employee enters national ID + phone + name
2. System calls Identity System (Mock) to verify national ID
3. IF VERIFIED (200 OK):
   3.1 System creates customer record with status=ACTIVE
   3.2 System publishes CustomerCreated event
   3.3 System returns 201 Created with Customer_ID
   3.4 Employee proceeds to UC-11 (Activate SIM)
4. ELSE (NOT_FOUND / TIMEOUT):
   4.1 System logs failure in Audit Log
   4.2 System returns 400/408 error
   4.3 Employee must retry or escalate

### Postcondition:
- Customer record exists with verified national ID
- Audit log entry created

## UC-11 + UC-14 + UC-19: SIM Activation & Subscription

**Actor:** Customer Service Employee
**Trigger:** Customer approved, ready for SIM assignment

### Main Flow:
1. Employee posts SIM + MSISDN assignment
2. SIM Service checks iccid availability
3. SIM assigned → SIM_Status_History updated
4. Employee creates subscription with package
5. System validates package, price, quota
6. Subscription created (PENDING_PAYMENT)
7. Event SubscriptionCreated published → Notification Service notified

## UC-28: Process Payment

**Actor:** Customer
**Trigger:** Customer selects unpaid invoice

### Main Flow (Success):
1. Customer POST /api/v1/payments (invoiceId, amount, idempotencyKey)
2. Payment Service validates invoice status
3. Payment Gateway charges (with HMAC signature)
4. Payment recorded SUCCESS
5. Invoice marked PAID
6. Event PaymentCompleted published
7. Notification sent

### Alternate Flow 1 (REJECTED):
- Gateway returns 402 (INSUFFICIENT_FUNDS)
- Payment status = FAILED
- Customer notified of failure

### Alternate Flow 2 (TIMEOUT):
- Gateway doesn't respond in 3000ms
- Payment status = PENDING_RECONCILIATION
- Ticket created for manual reconciliation
- Reconciliation runs later

## UC-35 + UC-36 + UC-38: Incident Report & Ticket

**Actor:** Network Engineer / Customer
**Trigger:** Tower/network failure detected

### Main Flow:
1. Network Engineer POST /api/v1/incidents (description, towerId)
2. Incident Service verifies tower exists
3. Incident created (OPEN)
4. Event IncidentReported published
5. IF customer-initiated: Support Service creates ticket
6. Ticket assigned to Support Agent with SLA priority

## UC-38 → UC-41: Support Ticket Lifecycle

**Actor:** Customer / Support Agent

### Main Flow:
1. Customer creates ticket (subject + category)
2. System classifies + assigns priority (P0-P3)
3. IF P0/P1 → SLA 4 hours
   IF P2/P3 → SLA 24 hours
4. Support Agent assigned
5. Agent investigates, replies (UC-40)
6. IF resolved → Ticket RESOLVED → CLOSED
   IF need transfer → UC-41 → reassign

(Add similar flows for each UC or UC group)

## Diagram source

- `docs/diagrams/phase-3-flows/04-activity-customer-onboarding.drawio`
- `docs/diagrams/phase-3-flows/05-activity-payment-processing.drawio`
- `docs/diagrams/phase-3-flows/06-activity-support-ticket.drawio`
- `docs/diagrams/phase-3-flows/25-business-process-flow.drawio`
