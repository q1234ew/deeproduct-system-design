# Integration Platforms

Load this guidance for third-party APIs, connectors, webhooks, credentialed requests, synchronization, or automation platforms.

## Connector responsibility

Separate the product’s canonical operation from provider-specific transport and fields. A connector owns authentication, request mapping, provider limits, response mapping, retry classification, and provider diagnostics. Consumers should not branch on provider internals unless the product explicitly exposes them.

## Credentials

Define credential owner, scope, storage, encryption, rotation, revocation, and audit. Resolve secrets as late as possible and never place them in logs, durable workflow payloads, URLs, or client-visible diagnostics. Prevent automatic forwarding of credentials across redirects or untrusted hosts.

## Webhooks and synchronization

Verify webhook authenticity before parsing business effects. Treat delivery as duplicate, delayed, and potentially out of order. Persist the provider event identity or business idempotency key before acknowledging when processing guarantees require it.

For synchronization, define:

- authority per field or entity;
- cursor and checkpoint ownership;
- create/update/delete conflict rules;
- tombstones and retention;
- full rescan and reconciliation;
- schema or API-version drift;
- rate-limit and outage behavior.

## Failure model

Classify failures as invalid configuration, authentication, authorization, rate limit, transient provider failure, permanent request rejection, unknown outcome, and local processing failure. Do not retry permanent failures. Unknown outcomes require reconciliation before repeating non-idempotent effects.

## Product operations

Expose connector health, last successful synchronization, backlog, actionable error, credential status, and retry or disable controls. Keep provider payloads available only as permitted evidence, with retention and redaction rules.
