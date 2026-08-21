# Public Roadmap

The public roadmap describes engineering direction without exposing private production implementation details.

## Phase 1 — Compiler Core

- canonical campaign model;
- schema validation;
- capability registry;
- API version registry;
- operation dependency graph;
- deterministic mutation planning.

## Phase 2 — Execution Runtime

- dry-run mode;
- validation mode;
- mutation batching;
- normalized result parsing;
- checkpointing;
- safe resume;
- reconciliation.

## Phase 3 — Execution Adapters

- Google Ads Scripts adapter;
- Google Ads API adapter;
- Search campaign adapter;
- Performance Max adapter;
- Demand Gen adapter.

## Phase 4 — SaaS Infrastructure

- account connections;
- tenant isolation;
- launch history;
- template management;
- audit logs;
- usage metering;
- operational monitoring.

## Public/non-public boundary

The roadmap intentionally excludes:

- credentials;
- customer or tenant identifiers;
- proprietary adapter internals;
- production infrastructure topology;
- operational security rules;
- commercial pricing logic;
- private launch heuristics;
- internal test-account data.
