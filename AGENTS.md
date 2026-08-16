# AGENTS.md

This repository is the source of truth for the `deeproduct-system-design` Agent Skill.

- Keep `SKILL.md` concise: workflow, routing, guardrails, and output selection only.
- Put detailed principles in `references/core/`, domain-specific guidance in `references/domains/`, and reusable forms in `assets/`.
- Keep the core method independent of a specific framework, programming language, architecture style, or AI provider.
- Require evidence before introducing public abstractions, distributed components, event sourcing, plugin systems, or AI-specific machinery.
- Treat proportionate design and avoidance of over-engineering as acceptance criteria.
- Test outside repositories whose agent instructions already encode the same methodology.
- Do not copy project-specific instructions verbatim; preserve the general principle and provide neutral examples.
- Update the evaluation rubric when a new durable quality criterion is added.
