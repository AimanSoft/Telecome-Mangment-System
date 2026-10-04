# Use Case Actions — TCMS

> Status: Draft — Based on aim45an diagrams (Team Decision, Pending Doctor)
> Format: Actor → Action → System Response → Result
> Source: docs/diagrams/ (use-case, activity, sequence diagrams)

## Actions per Use Case (Extracted from Diagrams)

| UC ID | Actor | Action | Result |
|-------|-------|--------|--------|
| UC-01 | All | login(username, password) | Token issued |
| UC-02 | All (logged-in) | logout(token) | Token invalidated |
| UC-03 | Super Admin | registerUser(username, role) | User created |
| UC-04 | All (logged-in) | refreshToken(token) | New token issued |
| UC-05 | Customer Service | createCustomer(nationalId, phone, name) | Customer created + audit log |
| UC-06 | Customer Service | updateCustomer(customerId, data) | Customer record updated |
| UC-07 | Super Admin | deleteCustomer(customerId) | Customer record removed |
| UC-08 | Customer Service | listCustomers(filter) | Customer list returned |
| UC-09 | Customer | viewCustomerDetails(customerId) | Own details returned |
| UC-01V | Customer Service | verifyNationalId(nationalId) → Identity System (Mock) | VERIFIED (200 OK) / NOT_FOUND / TIMEOUT |
| UC-10 | Customer Service | createSim(iccid) | SIM record created |
| UC-11 | Customer Service | activateSim(iccid, msisdn) | SIM ASSIGNED + status history |
| UC-12 | Customer Service | suspendSim(iccid) | SIM SUSPENDED |
| UC-13 | Super Admin | blockSim(iccid) | SIM BLOCKED |
| UC-14 | Customer Service | assignPhoneNumber(msisdn, iccid) | Number assigned (200 OK {iccid, msisdn, status: ASSIGNED}) |
| UC-15 | Company Admin | createPackage(name, price, quota) | Package created |
| UC-16 | Company Admin | updatePackage(packageId, data) | Package updated |
| UC-17 | Company Admin | deletePackage(packageId) | Package removed |
| UC-18 | Customer | listPackages() | Packages listed |
| UC-19 | Customer Service | createSubscription(customerId, iccid, packageId) | Subscription PENDING_PAYMENT |
| UC-20 | Customer Service | renewSubscription(subscriptionId) | Subscription renewed |
| UC-21 | Customer Service | cancelSubscription(subscriptionId) | Subscription cancelled |
| UC-22 | System (CDR, automatic) | recordCall(from, to, duration) | Usage record created |
| UC-23 | System (SMS, automatic) | recordMessage(from, to) | Usage record created |
| UC-24 | System (internet, automatic) | recordInternetUsage(subscriptionId, bytes) | Usage record created |
| UC-25 | System (scheduled) | generateInvoice(subscriptionId) | Invoice UNPAID |
| UC-26 | Accountant | calculateAmounts(invoiceId) | Amounts recalculated |
| UC-27 | Accountant | updatePaymentStatus(invoiceId, status) | Invoice status updated |
| UC-28 | Customer | processPayment(invoiceId, amount, idempotencyKey) | Payment SUCCESS/FAILED |
| UC-29 | Customer | rechargeBalance(msisdn, amount) | Balance recharged |
| UC-30 | Accountant | checkTransactionStatus(reference) | Status returned (SUCCESS / PENDING_RECONCILIATION / FAILED) |
| UC-31 | Network Engineer | manageTowers(towerId, data) | Tower record maintained |
| UC-32 | Network Engineer | manageStations(stationId, data) | Station record maintained |
| UC-33 | Network Engineer | manageDevices(deviceId, data) | Device record maintained |
| UC-34 | Network Engineer | manageCoverageAreas(areaId, data) | Coverage area maintained |
| UC-35 | Network Engineer | reportIncident(description, towerId) | Incident OPEN + ticket created |
| UC-36 | Network Engineer | assignIncidentToTower(incidentId, towerId) | Incident linked to tower |
| UC-37 | Support Agent / Customer | trackIncident(incidentId) | Incident status returned |
| UC-38 | Customer | createTicket(subject, category) | Ticket OPEN + assigned |
| UC-39 | Support Agent | assignTicket(ticketId, agentId) | Ticket assigned |
| UC-40 | Support Agent | replyToTicket(ticketId, message) | Reply sent |
| UC-41 | Support Agent | transferTicket(ticketId, targetAgentId) | Ticket transferred |
| UC-42 | Customer Service | fullCustomerLifecycle(customerId) | UC-05 → UC-11 → UC-14 → UC-19 → UC-25 → UC-28 executed |

## Diagram evidence

- Actor ↔ Use Case links: `docs/diagrams/01-use-case-overview.drawio`, `03-use-case-network-support.drawio`
- Request/response details: sequence diagrams `07`–`10`
- Automatic system actors (UC-22…UC-24): note in `01-use-case-overview.drawio`
  (usage UCs are system-generated; no human actor)

## Notes

- كل Actions مستخرجة من Activity + Sequence Diagrams
- كل Use Case له Actor Action واحد على الأقل
- Status: Draft — Team Decision, Pending Doctor
