# Capability Design

A capability is a stable responsibility that one or more consumers rely on. Design a replaceable capability through three roles:

- **Definition** — operations, semantics, ownership, failures, and guarantees independent of implementation.
- **Provider** — implementation, external dependencies, operational limits, and deployment choices.
- **Consumer** — product workflow, API, UI, automation, or internal process that uses the capability.

## Procedure

1. Name the user or system outcome.
2. List current consumers and their actual needs.
3. Define the smallest semantics shared by those consumers.
4. Identify one or more providers only when replacement or independent evolution is real.
5. Keep provider-specific configuration and consumer presentation out of the definition.
6. Define registration, selection, failure, and disposal behavior.
7. Verify the assembled path through at least one real consumer and provider.

## Evidence threshold

Do not create a public service, plugin point, registry, strategy interface, or generic event for one private call unless a concrete boundary or current independent consumer requires it. A private function or injected closure is often the correct first design.

Do not let one consumer dictate a generic interface. If UI pagination, model schemas, transport envelopes, or provider options appear in a capability definition, determine whether they belong in an adapter at the consuming edge.

## Responsibility table

For each capability, record:

| Field | Question |
|---|---|
| Outcome | What current user or system result does it enable? |
| Definition owner | Which module owns semantics and compatibility? |
| Providers | Which implementations exist or are immediately required? |
| Consumers | Which production paths call it? |
| State | What facts does it own, borrow, or derive? |
| Failure | What errors or uncertainty can consumers observe? |
| Lifecycle | How is it registered, selected, replaced, and disposed? |
| Evidence | Which tests exercise the real composition? |

A capability split is successful when providers can change without forcing consumer-specific forks and when consumers do not need provider internals.
