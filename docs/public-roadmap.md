# AdsForge Public Roadmap

This roadmap communicates engineering direction without exposing private production implementation details.

## Status legend

| Status | Meaning |
|---|---|
| **Defined** | Architecture and public contract are documented |
| **In development** | Private implementation work is active |
| **Planned** | Intended future engineering phase |

---

## Phase 1 — Compiler Core

**Status: Defined / In development**

- canonical campaign model;
- schema validation;
- capability registry;
- API version registry;
- operation dependency graph;
- deterministic mutation planning;
- source-path-to-operation mapping.

### Goal

Create a stable compiler boundary between campaign intent and Google Ads-specific execution formats.

---

## Phase 2 — Execution Runtime

**Status: Defined / In development**

- dry-run mode;
- validation mode;
- bounded mutation batching;
- normalized result parsing;
- checkpoint persistence;
- safe resume;
- reconciliation before retry;
- structured retry classification.

### Goal

Make launches recoverable and safe to retry without creating unintended duplicate resources.

---

## Phase 3 — Execution Adapters

**Status: Defined / In development**

- Google Ads Scripts adapter;
- Google Ads API adapter;
- Search campaign adapter;
- Performance Max adapter;
- Demand Gen adapter;
- version-specific serializers and enum mapping.

### Goal

Keep the compiler core transport-independent while allowing execution behavior to evolve by Google Ads API version and execution target.

---

## Phase 4 — SaaS Infrastructure

**Status: Planned / In development**

- Google account connections;
- tenant isolation;
- launch history;
- reusable campaign templates;
- audit logs;
- usage metering;
- operational monitoring;
- launch and reconciliation dashboards.

### Goal

Turn the compiler and runtime into a low-touch multi-tenant campaign execution platform.

---

## Phase 5 — Scale and Operations

**Status: Planned**

- bulk launch orchestration;
- queue-based execution;
- richer observability;
- adapter regression suites;
- account-level reconciliation tooling;
- version migration workflows;
- operational analytics.

---

## Public / private boundary

The public roadmap intentionally excludes:

- credentials and OAuth secrets;
- customer or tenant identifiers;
- production schemas and internal registries in full;
- proprietary adapter internals;
- infrastructure topology;
- production authorization logic;
- private tracker configuration;
- production logs and checkpoints;
- commercial pricing and customer data.

The private repository remains the source of truth for production implementation.
