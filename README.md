# AdsForge

**Google Ads Campaign Compiler & Execution Engine**

AdsForge is an automation layer for turning normalized campaign specifications into validated, deterministic Google Ads execution workflows.

Instead of manually recreating campaign structures in the Google Ads UI, AdsForge is designed around a compiler-style pipeline:

```text
Campaign Input
→ Canonical Specification
→ Validation
→ Dependency Graph
→ Mutation Plan
→ Execution Adapter
→ Dry Run / Validation
→ Execution
→ Result Parsing
→ Checkpoint / Resume
→ Audit Log
```

## Why AdsForge

Launching and maintaining Google Ads campaigns through scripts and APIs becomes difficult when workflows need to be repeatable, recoverable, version-aware, and safe to retry.

AdsForge focuses on the engineering layer behind campaign deployment:

- deterministic campaign compilation;
- technical schema validation;
- capability-aware execution;
- dependency-aware mutation ordering;
- idempotent launch behavior;
- dry-run and validation modes;
- checkpointing and resume;
- structured error mapping;
- multi-account and tenant isolation;
- Google Ads Scripts and Google Ads API execution targets.

## Supported campaign families

The architecture is designed around campaign-specific adapters, including:

- Search
- Performance Max
- Demand Gen

Support is version-aware and capability-gated rather than assumed globally.

## Execution targets

### Google Ads Scripts

Generated JavaScript can use Google Ads Scripts mutation primitives for supported workflows.

Typical flow:

```text
Specification
→ Operation Graph
→ Script-Compatible Mutation Objects
→ AdsApp.mutateAll()
→ Result Inspection
```

### Google Ads API

Backend execution is designed around versioned Google Ads API adapters.

Typical flow:

```text
Specification
→ Operation Graph
→ Versioned Serializer
→ GoogleAdsService.Mutate
→ Normalized Results
```

## Core engineering principles

### Deterministic compilation

The same canonical specification should produce the same mutation plan for the same adapter version.

### Idempotency

Repeated execution must not create unintended duplicate resources.

### Dependency-aware execution

Campaign budgets, campaigns, ad groups, assets, ads, criteria, and related resources are compiled according to explicit dependencies.

### Safe defaults

Launch workflows are designed around validation-first execution and paused initial state unless activation is explicitly requested.

### Resume and reconciliation

Long-running or partially completed workflows should preserve checkpoints and known resource identifiers so execution can resume safely.

### Version isolation

Google Ads API-specific serialization is kept behind versioned adapters instead of being spread across application code.

## Architecture

See [docs/architecture-overview.md](docs/architecture-overview.md).

## Public repository scope

This repository intentionally documents the architecture and engineering approach without publishing production credentials, tenant data, customer identifiers, proprietary production adapters, operational playbooks, or private commercial configuration.

See [SECURITY.md](SECURITY.md).

## Project status

AdsForge is under active development.

The current public repository is intended to demonstrate the architecture, compiler model, execution strategy, and engineering direction of the project.

## Technology direction

- Node.js / JavaScript or TypeScript
- Google Ads API
- Google Ads Scripts
- JSON Schema validation
- REST / mutation adapters
- structured logging
- idempotency and checkpoint persistence
- multi-tenant backend architecture

## License

No license is granted unless a license file is explicitly added to this repository.
