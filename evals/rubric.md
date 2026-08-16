# Evaluation Rubric

Compare an unassisted baseline with an explicit `/skill:deeproduct-system-design` run on the same repository state and prompt. Do not change project instructions between runs.

Score each dimension from 0 to 4:

| Dimension | 0 | 2 | 4 |
|---|---|---|---|
| Problem framing | Restates request | Identifies goals and some constraints | Defines users, outcomes, constraints, non-goals, and decision horizon |
| Evidence discipline | Invents system facts | Uses some repository evidence | Separates fact, inference, assumption, and proposal with traceable evidence |
| Responsibility design | Lists components | Assigns partial ownership | Gives capabilities, consumers, authorities, and explicit responsibility boundaries |
| State and lifecycle | Ignores ownership | Covers happy-path state | Defines authority, commit, cancellation, recovery, and disposal |
| Boundary and security | Generic security list | Identifies primary boundary | Places validation and enforcement on all material effect paths |
| Evolution quality | Proposes broad architecture | Some staged changes | Small target design, compatibility stance, reversible stages, explicit deferrals |
| Verification | Says “add tests” | Names test types | Maps risk to real-path evidence, runtime signals, and rollout checks |
| Actionability | Generic advice | Some implementation direction | Decisions can be translated into staged product and engineering work |
| Domain fit | Generic architecture | Uses relevant domain concepts | Selectively applies domain rules without importing unrelated machinery |
| Communication | Long or unclear | Understandable | Concise, decision-oriented, uncertainty visible, strongest tradeoff represented |

## Penalties

Subtract 1–4 points for each material case:

- unsupported microservices, event sourcing, plugin system, queue, distributed transaction, or AI component;
- public abstraction with no demonstrated production consumer;
- hidden assumption presented as fact;
- framework-specific recommendation without project evidence;
- security control placed only in UI, prompts, or schema;
- duplicated writable sources of truth without reconciliation;
- migration or rollback omitted for an irreversible change;
- full template filled with generic prose when a lightweight decision would suffice.

## Acceptance

An MVP is promising when it improves at least six dimensions in three distinct project types, introduces no new material factual errors, and has a lower or equal over-engineering penalty than the baseline.
