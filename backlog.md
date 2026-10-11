# ShiftSwap — Sprint 1 Product Backlog

This ordered backlog is derived from the [Project Charter](./project-charter.md) and [MVP Scope](./scope.md). Items are Sprint 1 candidates; priority indicates implementation order, not effort. No estimates are assigned because team capacity and velocity are not yet known.

## Backlog Items

### PBI-1 — Confirm shift and approval rules
**Priority:** P0 · **Type:** Discovery

As the project team, we need Operations and HR to confirm the minimum shift details, request eligibility, responsible manager, and handling of competing requests so that the MVP reflects the actual workplace process.

**Acceptance criteria**
- Operations and HR agree on the minimum details needed to offer and assess a shift.
- The responsible manager and approval rules are clear for a request.
- The team records how eligibility and multiple requests for one shift are handled; unresolved policy questions are raised before implementing the affected behavior.

### PBI-2 — Provide basic employee and manager access
**Priority:** P0 · **Type:** Enabler

As an employee or manager, I need the appropriate basic app access and role so that I can use only the actions relevant to my part of the workflow.

**Acceptance criteria**
- Employee and manager roles can access the MVP.
- Employee and manager actions are distinguishable in the app.
- The workflow does not depend on SSO or enterprise identity provisioning.

### PBI-3 — Offer a shift for coverage
**Priority:** P1 · **Type:** User story

As a frontline employee, I want to post a shift I cannot work so that coworkers can offer to cover it.

**Acceptance criteria**
- The employee can enter the minimum shift details agreed in PBI-1 and submit the offer.
- A valid offer appears as open and available for coworkers to review.
- Invalid or incomplete required details are identified before the offer is posted.

### PBI-4 — Browse open shifts and request one
**Priority:** P1 · **Type:** User story

As a frontline employee, I want to review open shifts and request one so that I can offer to cover a coworker’s shift.

**Acceptance criteria**
- The employee can browse open shifts and see the details needed to decide whether to request one.
- The employee can submit a request for an open shift and see that it is pending manager review.
- Submitting a request does not make the swap final or remove the need for manager approval.

### PBI-5 — Review and decide on a request
**Priority:** P1 · **Type:** User story

As the responsible manager, I want to review a shift offer and pickup request and approve or reject it so that coverage changes follow the agreed approval process.

**Acceptance criteria**
- The manager can review the relevant shift and request details.
- The manager can approve or reject a pending request.
- Only an eligible pending request can be approved; approval makes the swap final and updates the shift’s availability consistently with PBI-1 rules.
- Rejection does not make the swap final.

### PBI-6 — Show request status and decision
**Priority:** P1 · **Type:** User story

As an employee affected by a request, I want to see its current status and the manager’s decision in the app so that I know whether the swap is final.

**Acceptance criteria**
- The affected employees can distinguish pending, approved, and rejected requests.
- The approved status is shown as final only after manager approval.
- Status is available in the app; third-party email and SMS notifications are not required.

### PBI-7 — Validate and demonstrate the end-to-end MVP
**Priority:** P1 · **Type:** Validation

As the project team and stakeholders, we need to test and review the complete workflow so that Sprint 1 demonstrates the intended MVP.

**Acceptance criteria**
- A test covers offering a shift, requesting it, manager approval and rejection, and visible outcomes.
- No critical defect prevents completion of the core offer–request–approval workflow.
- Operations, HR, and frontline employee representatives review a working demonstration by the end of Sprint 1.

## Sprint 1 Goal
Demonstrate an end-to-end MVP in which an employee offers a shift, a coworker requests it, and the responsible manager approves or rejects the request before any swap is treated as final.
