# Extensibility

Extensibility is valuable when independent implementations or consumers must evolve without coordinated core changes. It is costly when introduced before that need exists.

## Extension-point test

Before adding a plugin API, registry, event, hook, strategy, configurable default, or public abstraction, identify:

1. the current owner of the behavior;
2. at least one production consumer;
3. the independent variation that must be supported;
4. the semantics all variants share;
5. registration, conflict, selection, and disposal rules;
6. the compatibility obligation created by publication.

If these cannot be answered, keep the behavior local or require an explicit value rather than inventing a default.

## Prefer composition over privileged branching

When variation is real:

- keep the central lifecycle small and stable;
- attach behavior through documented services or events;
- make contributions reversible;
- prevent provider-specific behavior from leaking into consumers;
- expose explicit configuration at the owner that resolves it;
- fail clearly when required providers or references are missing.

Do not use extension points to hide a responsibility that lacks an owner. A registry is not an architecture by itself.

## Compatibility and migration

Choose deliberately among:

- private and freely changeable;
- internal but shared across modules;
- public pre-release with explicit instability;
- stable public API or durable format.

Preserve compatibility when real consumers, persisted data, or external integrations require it. Otherwise prefer correcting the foundation over permanent aliases and translation layers. For irreversible formats, include versioning, forward/backward reading policy, migration ownership, rollback limits, and invalid-data behavior.

## Simplification review

Periodically search for extension points whose only consumers are tests, documentation, or the implementation that declares them. Remove speculative options, unused events, duplicate representations, and wrappers that relocate rather than delete complexity.
