# AdsForge Architecture Overview

AdsForge treats campaign deployment as a compilation problem rather than a collection of UI automation steps.

## Compiler pipeline

```text
Raw Campaign Intent
        ↓
Canonical Campaign Specification
        ↓
Schema & Technical Validation
        ↓
Capability / Version Resolution
        ↓
Dependency Graph
        ↓
Mutation Plan
        ↓
Execution Adapter
   ↙                 ↘
Google Ads Script    Google Ads API
        ↓
Result Normalization
        ↓
Checkpoint / Resume / Reconcile
        ↓
Audit & Observability
```

## 1. Canonical specification

Campaign input is normalized before any Google Ads-specific mutation objects are created.

This creates a stable contract between:

- campaign templates;
- user interfaces;
- bulk import tools;
- automation services;
- Google Ads Scripts;
- Google Ads API adapters.

## 2. Capability registry

Campaign capabilities differ by campaign type, execution target, and Google Ads API version.

AdsForge therefore resolves capabilities explicitly rather than assuming that every resource or field is universally available.

Typical capability states include:

- supported;
- partially supported;
- prerequisite required;
- read-only;
- unsupported;
- deprecated;
- unknown.

Unknown or unverified execution paths should fail closed before live mutation.

## 3. Dependency graph

Campaign resources are represented as nodes with explicit dependencies.

Examples:

```text
Campaign Budget → Campaign → Ad Group → Ad / Criterion
```

and:

```text
Assets → Asset Group → Asset Group Asset Links
```

The graph determines mutation order, atomic boundaries, retry behavior, and checkpoint stages.

## 4. Versioned adapters

Google Ads-specific field names, enums, serializers, and error mappings are isolated behind version-specific adapters.

This avoids coupling the compiler core directly to one API release.

## 5. Execution runtime

The runtime is responsible for:

- dry run;
- validation;
- bounded batching;
- mutation execution;
- result inspection;
- retry classification;
- checkpoint persistence;
- resume and reconciliation.

## 6. Idempotency

Every launch is associated with stable identifiers and a specification hash.

The execution layer uses these identifiers to prevent accidental duplicate launches and to reconcile uncertain outcomes.

## 7. Error normalization

External Google Ads errors are mapped into a normalized internal structure containing enough context to identify:

- the failing operation;
- the source specification field;
- the external request identifier;
- whether retry is safe;
- the recommended technical correction.

## 8. Tenant isolation

Production architecture isolates account access, credentials, specifications, execution state, logs, and results per tenant.

Implementation details and operational controls are intentionally not published in the public repository.
