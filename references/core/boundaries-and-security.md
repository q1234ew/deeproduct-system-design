# Boundaries and Security

Security design starts with actors, assets, authority, and effectful operations.

## Identify boundaries

Map:

- anonymous, authenticated, privileged, service, and delegated actors;
- tenant and workspace separation;
- browser, server, worker, process, network, and storage boundaries;
- user-controlled, model-generated, imported, queued, persisted, and third-party data;
- credentials, personal data, financial data, source code, and operational controls.

## Validate where types stop being authoritative

Runtime validation is normally required at:

- configuration and environment parsing;
- HTTP, RPC, webhook, queue, worker, and process messages;
- model or tool JSON;
- durable files and database records that may outlive code versions;
- imports and external provider responses.

Typed same-process calls generally rely on their static interface unless mutable ownership or an untyped adapter creates a real risk.

## Enforce at the operation

A control is effective only if all paths to the effect pass through it. UI visibility, prompt instructions, schema omission, route guards, and wrapper APIs can improve experience but do not replace authorization at the operation that reads, writes, sends, executes, charges, or discloses.

For each sensitive operation, record:

- authenticated actor and delegated principal;
- target resource and tenant;
- policy decision and required context;
- audit fact and correlation identifier;
- rate, byte, item, time, and cost limits over the complete operation;
- failure response without secret or internal-detail leakage.

## Failure stance

Fail closed when proceeding would bypass confinement, authorization, tenant isolation, credential rules, or data-integrity guarantees. Distinguish a safe degraded mode from an unverified fallback. Make misconfiguration fail at startup when all required facts are available, otherwise at the earliest resolvable operation.

Threat analysis should include direct callers, alternate transports, retries, redirect behavior, race conditions, stale authorization, confused-deputy paths, and recovery jobs—not only the primary UI path.
