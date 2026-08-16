# Data Platforms

Load this guidance for ingestion, transformation, analytics, search, machine learning data, or shared datasets.

## Data ownership

For every dataset, define producer, semantic owner, consumers, schema, freshness, quality expectations, retention, sensitivity, and deletion requirements. Storage location does not determine semantic ownership.

Distinguish raw observations, corrected canonical data, derived datasets, indexes, features, and reports. Name which layer is authoritative for each decision.

## Contracts and evolution

Specify:

- schema compatibility and versioning;
- required and optional fields;
- event time versus processing time;
- identifiers, deduplication, and late data;
- correction, backfill, and deletion propagation;
- partitioning and ordering guarantees;
- units, locale, timezone, and null semantics.

Consumers should detect incompatible changes before production data is silently misinterpreted.

## Pipeline lifecycle

Define checkpoints, retry scope, idempotency, partial outputs, atomic publication, reprocessing, and recovery after worker loss. Publish a dataset version only after all required partitions and quality checks reach the declared commit point.

## Quality and lineage

Quality checks should cover product-relevant invariants, not only technical parse success. Record lineage sufficient to answer which inputs, code version, configuration, and run produced an output. Make backfills and manual corrections auditable.

## Serving and operations

Separate canonical datasets from serving projections such as caches, search indexes, aggregates, and feature stores. Define freshness and rebuild behavior for each projection. Observe lag, throughput, failures, rejected records, quality violations, cost, and consumer-visible freshness.
