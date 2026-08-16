# Architecture Review: <scope>

## 1. Review scope

- Mode: review
- Requested decision:
- Repository/system scope:
- Evidence inspected:
- Explicit exclusions:

## 2. Current system

Summarize the observed runtime composition, responsibility boundaries, authoritative state, and critical paths. Separate facts from inference.

## 3. Strengths worth preserving

List decisions that currently support product outcomes, safety, operability, or maintainability. Cite evidence.

## 4. Findings

For each finding include:

- Severity: blocker / material / improvement
- Location or affected flow
- Observed fact
- User or system impact
- Root responsibility or lifecycle issue
- Recommendation
- Tradeoff and migration effect
- Verification required

Do not report preferences as defects.

## 5. Responsibility and state analysis

| Subject | Current owner | Authority | Consumers | Problem or confirmation |
|---|---|---|---|---|

## 6. Lifecycle and boundary analysis

Cover publication, cancellation, recovery, disposal, authorization, validation, tenant isolation, external effects, and resource limits where relevant.

## 7. Simplification opportunities

Identify duplicate state, unused abstractions, speculative extension points, wrappers that relocate complexity, and providers or consumers coupled through implementation details. Require production evidence.

## 8. Recommended target

Describe the smallest target design that resolves material findings. State what remains unchanged and what is deliberately deferred.

## 9. Migration and delivery

Sequence changes to preserve behavior, data, and rollback. Give each phase observable acceptance evidence.

## 10. Open questions

List only questions whose answers can change the recommendation, with the minimum evidence needed.
