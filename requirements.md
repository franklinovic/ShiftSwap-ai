# ShiftSwap — Structured Requirements

This document consolidates the brainstorm notes, stakeholder emails, Slack discussion, and meeting transcripts in [the unstructured input pack](./Un-structured/unstructured-inputs-pack.md). Repeated requests have been deduplicated. Sources are noted for traceability; decisions made in the Thursday requirements session are treated as the latest direction unless flagged below.

## User Stories

### US-01 — Sign in with employee ID
**Source:** Kickoff sticky notes; Slack thread, 9:33 AM; requirements session, Thursday 2:00 PM.

As an employee or manager, I want to sign in using my employee ID, so that I can access the internal shift coverage tool without a complex login process.

**Acceptance criteria**
- An employee or manager can sign in using an employee ID.
- The app distinguishes employee and manager access for role-appropriate actions.
- The MVP does not require SSO or enterprise identity provisioning.
- The login flow’s credential and account-recovery rules are defined before production use.

### US-02 — Post a shift needing coverage
**Source:** Operations email; kickoff meeting, Tuesday 10:00 AM; requirements session, Thursday 2:00 PM.

As an employee who cannot work a shift, I want to post it as open for coverage, so that qualified coworkers can find it and volunteer.

**Acceptance criteria**
- An employee can submit a shift for coverage with the minimum details needed to identify and assess it.
- A successfully posted shift is visibly open until it is claimed or otherwise resolved.
- Required details are validated before the shift is posted.
- The app records who posted the shift and when.

### US-03 — Find and claim a qualified open shift
**Source:** Operations email; kickoff meeting, Tuesday 10:00 AM; requirements session, Thursday 2:00 PM.

As a qualified employee, I want to browse open shifts and claim one I can work, so that I can help a coworker get coverage.

**Acceptance criteria**
- Employees can browse open shifts and see enough detail to decide whether to claim one.
- The app limits claims to employees eligible for the shift, according to rules confirmed by Operations and HR.
- A successful claim becomes pending until manager approval; it does not make the swap final.
- The app records who claimed the shift and when.

### US-04 — Cancel a claim before approval
**Source:** Requirements session, Thursday 2:00 PM.

As an employee who claimed a shift, I want to cancel my claim before the manager approves it, so that I can withdraw if my availability changes.

**Acceptance criteria**
- The claimant can cancel their pending claim before manager approval.
- Cancellation returns the shift to an open state if it remains available under the agreed workflow rules.
- The claimant cannot cancel the claim after manager approval.
- The cancellation and its timestamp are recorded in the swap history.

### US-05 — Review and decide on shift claims
**Source:** Operations email; HR email; kickoff meeting, Tuesday 10:00 AM; requirements session, Thursday 2:00 PM.

As a manager, I want to review shift claims and approve or reject them, so that coverage changes are authorized before becoming official.

**Acceptance criteria**
- Managers can see pending claims and the shift details needed to review them.
- A manager can approve or reject a pending claim.
- A shift change is final only after manager approval.
- The decision, manager identity, and timestamp are recorded and made visible to the affected employees.

### US-06 — See shift coverage in one place
**Source:** Kickoff sticky notes; Operations email; requirements session, Thursday 2:00 PM.

As a manager, I want to see open shifts and their claim and approval status in one place, so that I can monitor coverage and act on unresolved shifts.

**Acceptance criteria**
- The manager view distinguishes open, claimed/pending, approved, rejected, and cancelled states.
- Managers can review the shifts and claims relevant to their responsibility.
- The view does not present a claimed shift as finally swapped before approval.
- The view surfaces open shifts that have not been claimed for escalation.

### US-07 — Receive shift and decision notifications
**Source:** Kickoff sticky notes; Operations email; Slack thread, 9:14–9:32 AM; requirements session, Thursday 2:00 PM.

As an employee affected by a shift offer or claim, I want to receive a timely notification about new open shifts and approval outcomes, so that I can act or know whether coverage is confirmed.

**Acceptance criteria**
- The system supports SMS notifications for new open shifts and approval status as the agreed primary MVP direction.
- Relevant employees are notified when a claim is made, cancelled, approved, or rejected, subject to notification rules confirmed with stakeholders.
- A manager is notified when an open shift reaches the unclaimed escalation point in US-08.
- Notification delivery status and recipient/channel preferences are defined; notification delivery does not itself make a swap final.

### US-08 — Escalate an unclaimed shift
**Source:** Slack thread, 9:40–9:41 AM; requirements session, Thursday 2:00 PM.

As a manager, I want to be alerted when a shift remains unclaimed four hours before it starts, so that I can arrange coverage manually.

**Acceptance criteria**
- The system identifies shifts that remain unclaimed four hours before their start time.
- The responsible manager receives an alert at that point.
- The shift remains visibly open and is not treated as covered by the alert.
- If a shift is posted less than four hours before its start, the escalation behavior is defined and applied consistently.

### US-09 — Use the workflow on a mobile device
**Source:** Kickoff sticky notes; Operations email; Slack thread, 9:24–9:26 AM.

As a frontline employee, I want to use the shift coverage workflow on a mobile device, so that I can manage shifts while working on the floor without needing a laptop.

**Acceptance criteria**
- Core employee actions—viewing open shifts, posting a shift, claiming one, and viewing status—are usable on a mobile-sized screen.
- Core manager review actions are usable on a mobile-sized screen.
- The mobile experience does not require a desktop browser.
- A supported path for employees without a smartphone or mobile data connection is confirmed before release.

### US-10 — Maintain and export an auditable swap history
**Source:** Kickoff sticky notes; HR email, items 1 and 3; Slack thread, 9:14–9:16 AM; kickoff meeting, Tuesday 10:00 AM; requirements session, Thursday 2:00 PM.

As an HR Director, I want a timestamped history of shift swaps and a CSV export of at least the last 90 days, so that I can respond to payroll audits and verify who posted, claimed, approved, and worked each shift.

**Acceptance criteria**
- The history records the poster, claimant, manager decision-maker, relevant actions, timestamps, and final swap status.
- Authorized users can review swap history for at least the trailing 90 days.
- Authorized users can export that history as CSV.
- The record distinguishes approved changes from claims that were rejected or cancelled.
- The system’s retention period and how “who actually worked” is established are confirmed with HR.

### US-11 — Review potential overtime
**Source:** HR email, item 5; Slack thread, 9:17–9:19 AM; requirements session, Thursday 2:00 PM.

As a manager, I want a warning when a proposed swap may put an employee over 40 hours in a week, so that I can review the potential overtime before deciding.

**Acceptance criteria**
- The manager can see an overtime warning when reliable shift-hour data indicates the proposed change would put an employee over 40 hours in the relevant week.
- The warning identifies the employee and the weekly hours used to determine the threshold.
- The warning prompts manager review but does not automatically block the claim or approval.
- If the required hours data is unavailable or incomplete, the app does not imply that the employee is below the threshold.

## Conflicts & Open Questions

- **SMS, email, and push:** Early notes and the Operations email leave the channel open (“push notification, text, email, whatever works”), while the Slack discussion first questions whether SMS should outrank push (9:24–9:30 AM) and then the Thursday requirements session settles on SMS for new open shifts and approval status, with push only as a bonus. Confirm whether email is excluded from v1, whether push is included at all, and whether SMS covers claim/cancellation events as well as decisions.
- **Employees without smartphones or mobile data:** The app must work on mobile, but frontline feedback says some employees have only basic phones and no data plan (sticky notes; Slack, 9:24–9:26 AM). SMS notifications alone do not let those employees post or claim shifts. Decide whether v1 supports an alternate assisted workflow (for example, a manager entering the offer/claim) or whether those employees are outside the self-service MVP.
- **Overtime calculation data:** HR requires a warning above 40 hours/week (HR email, item 5; requirements session, Thursday 2:00 PM), while Slack says calculation requires weekly totals and should not expand v1 (9:17–9:19 AM). The meeting later says it is manageable using existing shift data, but payroll/timeclock integration is explicitly deferred. Identify the authoritative source of all weekly shift hours and confirm calculation rules before committing to this story.
- **Employee eligibility and competing claims:** Operations says only qualified employees should claim a shift (Operations email), but qualification criteria and what happens when multiple coworkers claim the same shift are not specified. Confirm eligibility rules and whether the first claim reserves the shift pending approval.
- **Shift details and approval ownership:** The inputs do not define the required shift fields, how the responsible manager is determined, or which approval rules apply. Operations and HR must confirm these before implementation.
- **Unclaimed escalation timing:** The Thursday session sets an alert four hours before shift start, but does not specify behavior for shifts posted less than four hours in advance, time-zone handling, or whether the alert repeats if still unresolved.
- **Manager acting for an employee:** The brainstorm asks whether a manager can swap shifts on behalf of an employee, but no later input resolves it (sticky notes). Confirm whether this is needed in v1; do not assume it from the manager review/approval workflow.
- **Audit retention and “who worked”:** HR requests an auditable history and at least 90 days of CSV export, while the kickoff transcript asks to show who actually worked. The retention duration beyond the export window and how actual work is verified without timeclock integration remain unspecified.
- **Timeline:** The charter frames Sprint 1 as two weeks, while the kickoff transcript mentions a workable result in about two sprints/four weeks. Confirm the delivery commitment and what constitutes the MVP demo versus production readiness.

## Deferred / Out of Scope

- **Payroll integration — later phase:** Explicitly excluded from the first release to avoid payroll accuracy risk until the workflow is trusted. **Source:** HR email, item 4; Slack thread, 9:14 AM and 9:32 AM; kickoff meeting, Tuesday 10:00 AM.
- **Slack integration — later phase:** Initially suggested as a bonus, then explicitly deprioritized. **Source:** Operations email; sticky notes (“later??”); Slack thread, 9:31–9:32 AM; requirements session, Thursday 2:00 PM.
- **SSO and enterprise identity provisioning — not v1:** The direction is to use employee-ID login for this small internal tool. **Source:** Kickoff sticky notes; Slack thread, 9:33 AM; requirements session, Thursday 2:00 PM.
- **Push notifications — bonus, not MVP commitment:** The Thursday session prioritizes SMS and says push may be added if time permits. **Source:** Slack thread, 9:30 AM; requirements session, Thursday 2:00 PM.
