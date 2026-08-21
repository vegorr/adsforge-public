# Security & Public Disclosure Policy

`adsforge-public` is a sanitized public engineering repository. The production AdsForge implementation remains private.

The public/private boundary is intentional: this repository documents architecture and selected synthetic examples without exposing credentials, customer data, proprietary production internals, or operational secrets.

## Data that must never be committed

- OAuth client secrets;
- refresh or access tokens;
- Google Ads developer tokens;
- API keys;
- database credentials;
- signing keys or webhook secrets;
- real Google Ads customer or manager IDs;
- production tenant or workspace identifiers;
- production endpoint credentials;
- customer campaign specifications;
- raw mutation requests or responses containing account data;
- production checkpoints;
- private tracker configuration;
- internal infrastructure addresses;
- production logs containing sensitive identifiers.

## Synthetic examples only

Public documentation and fixtures must use synthetic values.

Example:

```text
customerId: 1234567890
tenantId: demo-tenant
launchId: demo-launch-001
destination: https://example.com
```

Synthetic identifiers are illustrative and must never be copied from a production account.

## Repository model

```text
Private source of truth
        ↓ explicit allowlist / sanitization
Public architecture repository
```

The private repository contains the production implementation.

The public repository may contain:

- architecture documentation;
- public engineering principles;
- sanitized workflow examples;
- high-level roadmap information;
- non-sensitive project updates.

There is no automatic private-to-public repository mirror.

## Production details intentionally excluded

The public repository does not publish the complete production versions of:

- canonical schemas;
- capability and version registries;
- operation graph definitions;
- serializers and enum maps;
- idempotency persistence;
- retry and reconciliation implementation;
- tenant authorization middleware;
- credential storage;
- tracker adapters;
- operational infrastructure configuration.

## Reporting accidental exposure

If a secret, credential, customer identifier, or other sensitive production value is accidentally exposed, do not repost it in a public issue. Revoke or rotate the affected credential where applicable and remove the exposed value from the public repository and its accessible history as part of incident handling.
