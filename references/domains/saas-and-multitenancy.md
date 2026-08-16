# SaaS and Multitenancy

Load this guidance when accounts, organizations, workspaces, plans, roles, quotas, or billing affect the design.

## Ownership and isolation

Define the tenant boundary before schemas and APIs:

- tenant creation, suspension, deletion, and transfer;
- users who may belong to multiple tenants;
- resource ownership and cross-tenant sharing;
- service identities and delegated administration;
- data residency, retention, export, and deletion obligations.

Every tenant-owned query and effect needs an authoritative tenant context. Do not rely on UI routing or caller-supplied tenant identifiers without server-side authorization. Decide whether isolation is row-, schema-, database-, account-, or deployment-level from risk and operational evidence.

## Roles and policy

Separate authentication, tenant membership, role assignment, resource policy, and feature entitlement. Record who grants each authority and how stale or revoked authority stops taking effect. Test cross-tenant denial through batch jobs, exports, search, background work, and administrative paths.

## Plans, quotas, and billing

Assign ownership for:

- metering facts and deduplication;
- quota evaluation and reset periods;
- plan changes and entitlement timing;
- billing-provider reconciliation;
- failed payment and grace behavior;
- refunds, credits, and manual adjustment audit.

Enforce limits at the operation that consumes the resource. UI indicators and API documentation are not enforcement.

## Operations

Design tenant-aware observability without leaking one tenant’s data to another. Support scoped support access, audit it, and define emergency revocation. Include backup, restore, export, deletion, and regional migration at the same isolation level as normal reads and writes.
