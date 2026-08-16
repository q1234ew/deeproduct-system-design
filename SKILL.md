---
name: deeproduct-system-design
description: Evidence-driven product system design and architecture review for greenfield products, existing systems, feature evolution, and lightweight designs. Use when defining system responsibilities, capability boundaries, authoritative state, lifecycle ownership, security enforcement, extensibility, verification, or staged delivery across SaaS, workflow, integration, data, web, and agent systems.
license: MIT
---

# Deeproduct System Design

Design proportionate systems from product evidence. This skill is guidance, not a rigid checklist. Prefer the smallest design that satisfies current goals and credible near-term change.

## Select the mode

Infer the mode from the request and state it briefly:

- **greenfield** — design a new product or system.
- **review** — assess an existing implementation or architecture.
- **evolution** — add a capability or restructure part of an existing system.
- **lightweight** — make a bounded decision for a small product, prototype, or local feature.

If the mode or scope changes the answer materially and cannot be inferred, ask one focused question. Otherwise continue with explicit assumptions.

## Establish evidence

For repository work, read the applicable agent instructions, product documentation, architecture documents, manifests, entry points, schemas, persistence code, and current consumers before proposing structure. Search for actual call sites and runtime composition. Do not treat tests or documentation as proof that a production consumer exists.

Classify important statements as:

- **Fact** — directly supported by code, product evidence, or user input.
- **Inference** — the most likely explanation of observed facts.
- **Assumption** — needed to proceed but not yet verified.
- **Proposal** — a recommended future decision.

Keep this classification visible when uncertainty affects the design.

## Design workflow

### 1. Frame the problem

Define users, outcomes, constraints, success measures, non-goals, current pain, and the decision horizon. Read [problem framing](references/core/problem-framing.md) when goals are ambiguous or competing.

### 2. Map responsibilities and capabilities

Identify actors, domains, authoritative owners, consumers, and external dependencies. Design each replaceable capability as definition, provider, and consumer roles. Read [capability design](references/core/capability-design.md).

### 3. Design state and lifecycle

For each important fact or resource, name its owner, source of truth, projections, creation point, commit point, cancellation behavior, recovery behavior, and disposal condition. Read [state and lifecycle](references/core/state-and-lifecycle.md).

### 4. Place boundaries and enforcement

Locate trust, process, network, storage, tenant, and human-approval boundaries. Validate at untyped or durable boundaries and enforce denial at the operation that performs the effect. Read [boundaries and security](references/core/boundaries-and-security.md).

### 5. Plan evolution without speculative generality

Prefer explicit extension points where multiple current implementations or consumers justify them. Keep local behavior local when no stable capability exists. Read [extensibility](references/core/extensibility.md).

### 6. Match evidence to impact

Plan tests, runtime invariants, observability, migration checks, and release signals that exercise the real affected path. Read [verification](references/core/verification.md).

### 7. Record decisions and delivery

Separate current system facts, durable decisions, open questions, and implementation tasks. Sequence delivery by risk retirement and user value. Read [decision documentation](references/core/decision-documentation.md).

## Load domain guidance selectively

Load only the files relevant to the product:

- SaaS, tenancy, roles, quotas, billing: [SaaS and multitenancy](references/domains/saas-and-multitenancy.md)
- Approvals, orchestration, retries, compensation: [workflow systems](references/domains/workflow-systems.md)
- Webhooks, APIs, credentials, third parties: [integration platforms](references/domains/integration-platforms.md)
- Schemas, pipelines, quality, lineage: [data platforms](references/domains/data-platforms.md)
- Browser state, UI composition, client/server protocols: [web applications](references/domains/web-applications.md)
- Models, prompts, tools, sessions, evaluation: [agent systems](references/domains/agent-systems.md)

A product may require several domain files. Do not load a domain merely because it is available.

## Choose the output

Use the smallest artifact that resolves the request:

- Greenfield system: [system design template](assets/system-design-template.md)
- Existing system review: [architecture review template](assets/architecture-review-template.md)
- Local or early-stage decision: [lightweight template](assets/lightweight-design-template.md)

Do not fill sections with generic prose. Omit inapplicable sections and explain only material omissions.

## Quality bar

Before finishing, verify that the design:

- traces every major component and abstraction to a current goal or consumer;
- gives each durable fact and long-running operation an owner;
- distinguishes authoritative state from projections and caches;
- defines success publication, failure, cancellation, recovery, and cleanup;
- enforces permissions and limits at the effectful operation;
- states assumptions, tradeoffs, and intentionally deferred choices;
- includes a proportionate verification and rollout plan;
- avoids distributed systems, event sourcing, plugins, microservices, or AI components without evidence they are needed;
- can be translated into staged product and engineering work.

When evidence is insufficient, present the decision that is blocked, the minimum evidence needed, and a safe temporary choice instead of inventing certainty.
