# State and Lifecycle

State design begins by naming authoritative facts and owners. Do not start with databases, caches, queues, or framework stores.

## State classification

Classify each important value as:

- **authoritative fact** — the source used to decide correctness;
- **durable record** — persisted evidence needed after restart or replay;
- **projection** — derived view that can be rebuilt;
- **cache** — disposable acceleration with explicit invalidation;
- **ephemeral coordination** — locks, reservations, progress, or in-flight ownership;
- **external authority** — a fact owned by another system and observed locally.

Avoid two writable representations of the same fact. If duplication is required, name the authority, synchronization direction, lag, reconciliation process, and failure behavior.

## Lifecycle record

For every resource or long-running operation, define:

| Stage | Required decision |
|---|---|
| Acquire | Who may start it, and what is reserved? |
| Prepare | What can fail before publication? |
| Commit | At what exact point does the result become observable? |
| Run | Who owns cancellation, timeouts, retries, and progress? |
| Recover | What happens after process failure, duplicate delivery, or restart? |
| Dispose | What is stopped, detached, released, or awaited? |

Publish state and notifications only after the operation’s success point. A failure before commit must not leave a successful projection or event. Disposal should reach quiescence when callers rely on resources being inactive after it completes.

## Concurrency

Represent one asynchronous operation with one owner when possible. Add separate controllers, promises, state flags, or transactions only when they protect distinct ownership or settlement points.

Specify:

- idempotency key or duplicate policy;
- ordering requirement and stale-write behavior;
- cancellation semantics and whether effects can still complete;
- retry ownership and maximum retry horizon;
- partial failure and compensation;
- contention, fairness, and backpressure;
- process-crash recovery and abandoned work detection.

Use events when consumers need facts that occurred. Use commands for requested work. Use projections for query needs. Do not adopt event sourcing merely because events are useful.
