# Security and Disclosure Policy

The public AdsForge repository must not contain production secrets or customer data.

## Never publish

- OAuth client secrets;
- refresh tokens;
- access tokens;
- Google Ads developer tokens;
- API keys;
- database credentials;
- signing keys;
- webhook secrets;
- customer IDs tied to real clients;
- login customer IDs tied to real clients;
- tenant IDs or workspace IDs from production;
- production endpoint credentials;
- raw execution logs containing user or account data;
- production checkpoints;
- private tracker configuration;
- internal infrastructure addresses;
- customer campaign specifications.

## Public-safe examples

Examples should use synthetic identifiers and clearly fake values.

Example:

```text
customerId: 1234567890
tenantId: demo-tenant
launchId: demo-launch-001
```

Do not reuse real production identifiers in documentation or fixtures.

## Repository strategy

Recommended setup:

```text
adsforge                 PRIVATE
adsforge-public          PUBLIC
```

The private repository remains the source of truth for implementation.

The public repository contains architecture documentation, selected sanitized examples, non-sensitive interfaces, and project updates.

Do not mirror the private repository automatically into the public repository without an explicit allowlist.
