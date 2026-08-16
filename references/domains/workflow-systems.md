# Workflow Systems

Load this guidance for approvals, orchestration, scheduled work, multi-step business processes, or long-running operations.

## Model facts, not screens

Define the business states and allowed transitions independently of UI pages. Distinguish:

- command: a request to attempt a transition;
- event: a fact that a transition or external occurrence happened;
- task: work assigned to a human or system;
- timer: a future eligibility check, not necessarily guaranteed execution;
- projection: a query view of workflow history.

Name the authoritative workflow instance, transition version, actor, input, outcome, and timestamp.

## Delivery and retries

Assume messages, webhooks, and jobs may be duplicated, delayed, reordered, or delivered after cancellation. Define idempotency at the business operation, not only the queue transport. State retry owner, retryable failures, backoff, deadline, and terminal handling.

## Long-running lifecycle

Specify:

- who may start, pause, cancel, resume, or override;
- what happens to in-flight steps after cancellation;
- which transitions require human approval;
- timeout and escalation behavior;
- compensation for completed irreversible steps;
- recovery after worker or process loss;
- version behavior for already-running instances.

Do not imply atomicity across independent external systems. Record partial completion and reconcile it explicitly.

## Human participation

Human tasks require assignment, reassignment, delegation, absence handling, due dates, reminders, comments, evidence, and audited decisions where the product needs them. Separate a person’s task inbox from the durable workflow state; the inbox is usually a projection.

Test transition denial, duplicate commands, stale approvals, retries after partial success, cancellation races, timer recovery, and version upgrades of active instances.
