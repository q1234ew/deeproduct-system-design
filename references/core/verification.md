# Verification

Verification should establish that the designed behavior works through the path users and systems actually run.

## Match evidence to impact

| Change | Primary evidence |
|---|---|
| Pure rule or transformation | Unit and property tests |
| State transition or lifecycle | Transition, failure, cancellation, and recovery tests |
| Capability composition | Real provider + definition + consumer assembly |
| User-visible behavior | Interaction test or stable output snapshot |
| External provider | Contract test plus bounded live end-to-end test where feasible |
| Persistence or migration | Versioned fixtures, restart, corruption, and rollback tests |
| Authorization or isolation | Negative tests through direct and alternate execution paths |
| Packaging or deployment | Built-artifact install and startup smoke |

Mocks isolate external nondeterminism; they must not replace the assembly whose correctness is under test.

## Runtime evidence

Define observability from product questions:

- Can operators determine whether the user outcome succeeded?
- Can one request or workflow be traced across boundaries?
- Are retries, cancellation, queue delay, external failures, and partial completion visible?
- Can security-sensitive effects be audited without logging secrets?
- Are cost, quota, latency, and saturation measurable at their owner?

Use runtime invariants for relationships that should always hold, such as a published projection corresponding to an authoritative fact or a disposed registration no longer being discoverable. Do not use invariants to re-test fixed examples or method presence.

## Release and rollout

For risky changes define:

- compatibility and migration prerequisites;
- feature exposure or staged rollout;
- leading success and failure indicators;
- rollback mechanism and the point after which rollback is unsafe;
- data reconciliation or cleanup;
- owner and response procedure.

Choose the narrowest local checks that cover the change, while CI owns exhaustive platform and compatibility matrices. Report only checks actually run.
