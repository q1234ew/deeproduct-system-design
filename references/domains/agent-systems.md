# Agent Systems

Load this guidance when models, prompts, tools, autonomous loops, sessions, memory, evaluation, or human approval are part of the product.

## Separate capabilities

Treat model inference, prompt assembly, tool registration and execution, session persistence, memory retrieval, approval, sandboxing, and UI as distinct capabilities. Do not let one model provider or chat interface define the core contracts.

## Reconstruct model-visible inputs

Anything that can change a model request should be attributable and reconstructable when audit, replay, resume, or debugging is required. Distinguish:

- durable conversation and tool facts;
- system instructions and versioned policy;
- retrieved or injected context;
- ephemeral provider metadata;
- UI-only presentation state.

Do not persist presentation details as model history. Do not inject important model context only through transient memory if resumed behavior must remain explainable.

## Tool execution

Model output is untrusted input. Validate tool names and arguments at the execution boundary, authorize the intended effect, apply sandbox and resource limits, and record the call and result needed for continuation. Prompt instructions and tool-schema omission do not replace enforcement.

Define parallelism, cancellation, timeout, duplicate call, partial result, output-size, spill, and approval behavior. A tool’s user-facing presentation is separate from its execution semantics.

## Agent lifecycle

Specify turn and step boundaries, queued input, interruption, cancellation, retry, compaction, fork, resume, and disposal. Give every active run and background task an owner. Publish assistant output and tool effects at explicit commit points so replay does not invent success.

## Providers, cost, and safety

Keep provider routing, credentials, model limits, retry policy, token accounting, and fallback explicit. A fallback model may change behavior and cost; do not make it silent. Bound prompt bytes, tokens, tool output, parallel calls, wall time, and monetary exposure.

## Evaluation

Combine deterministic unit tests, provider contract tests, recorded or keyless scenario replay, safety denials, and bounded live evaluations. Evaluate external state and user-visible outcomes rather than trusting the model’s claim that it succeeded. Track quality, latency, cost, tool failures, approval rates, and regression by scenario.
