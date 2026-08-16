# Decision Documentation

Separate four kinds of information so each can remain accurate:

- **Current facts** — how the product and system behave today.
- **Durable decisions** — why a choice was made, alternatives, tradeoffs, and consequences.
- **Open questions** — evidence still required and who resolves it.
- **Delivery tasks** — implementation sequence, owners, and acceptance evidence.

Do not mix change history into current-state reference material. Do not present an implementation plan as an enduring architecture decision.

## Decision record

A durable decision should include:

1. context and forces;
2. decision and scope;
3. alternatives considered;
4. consequences and capabilities given up;
5. compatibility or migration effects;
6. verification that demonstrates the decision;
7. conditions that would justify revisiting it.

Record rationale only when it will guide later changes or prevent a plausible mistake. Keep local and reversible choices in code, tests, or a lightweight design note.

## Delivery planning

Order work to retire uncertainty and risk:

1. prove external feasibility and boundary assumptions;
2. establish authoritative state and contracts;
3. implement the thinnest end-to-end user path;
4. add failure recovery, security enforcement, and operations;
5. expand providers, consumers, scale, and optimization only with evidence.

Each phase should produce an observable outcome, define non-goals, and name the tests or operational signal that establish completion.

## Review discipline

A design review should distinguish blockers from improvements. A blocker violates a required outcome, integrity or security guarantee, lifecycle obligation, or irreversible compatibility constraint. Suggestions improve maintainability or future options without invalidating the current design.
