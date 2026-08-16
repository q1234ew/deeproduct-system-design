# Problem Framing

Start with the decision the product needs, not an architecture pattern.

## Required evidence

Capture:

- target users and the job they are trying to complete;
- the current workflow and measurable failure or cost;
- desired outcomes and how they will be observed;
- constraints: time, team, regulation, budget, deployment, compatibility, and data;
- non-goals and the time horizon of the decision;
- uncertainties that could reverse the design.

Separate product requirements from implementation preferences. “Use microservices,” “add an event bus,” and “make it extensible” are proposals until a current constraint or consumer justifies them.

## Questions with high decision value

Ask only questions whose answers change responsibility, state, security, delivery, or cost. Examples:

- Who is allowed to perform the operation, and on whose behalf?
- What must remain true after restart, retry, or partial failure?
- What volume, latency, availability, or regulatory requirement changes the architecture?
- Which external systems are authoritative?
- Is the change reversible after data is written or users depend on it?

If answers are unavailable, state assumptions and choose an option that preserves later decisions without building unused generality.

## Scope control

Trace every proposed component to a user outcome, constraint, current consumer, or risk. Classify anything else as deferred. A credible future need may justify preserving data or avoiding a destructive choice; it does not automatically justify implementing an abstraction now.

For small work, produce a lightweight decision containing context, choice, consequences, verification, and deferred questions. Do not force a full architecture document.
