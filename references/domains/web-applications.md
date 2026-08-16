# Web Applications

Load this guidance when browser state, UI composition, client/server protocols, offline behavior, or frontend modularity materially affects the design.

## State placement

Place state by ownership:

- server-authoritative business facts remain on the server and are cached or projected in the client;
- URL state represents shareable navigation and filters;
- cross-view interaction state belongs in an explicit client store;
- component-private state remains local;
- derived state is computed, not synchronized into another writable copy.

Define invalidation, optimistic update, rollback, reconnect, and stale-data behavior. Avoid mirroring the same mutable fact across component state, a global store, and a request cache.

## Protocols

Specify request identity, authentication, authorization, error fields, pagination, versioning, cancellation, streaming, reconnect, and duplicate behavior. Keep transport envelopes out of business APIs where possible. Treat browser input and persisted client state as untrusted.

## Composition

Use component or plugin extension points only when independent features need to contribute UI without direct imports. Define declaration, authorization, ordering, conflict, data access, and teardown. Otherwise prefer ordinary component composition.

Keep business components dependent on explicit data and callbacks rather than global service containers. Route shared reactive facts through one owned subscription channel.

## User-visible lifecycle

Design loading, empty, partial, stale, retrying, offline, permission-denied, and terminal-error states. Accessibility, localization, keyboard operation, responsive behavior, and destructive-action confirmation are product behavior, not final styling tasks.

Test user-visible behavior and real client/server assembly. Avoid tests that only assert CSS classes, internal hook calls, or render counts.
