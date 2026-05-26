# sigma-rules-saas

Sigma detection rules curated for multi-tenant SaaS environments. Each rule maps to MITRE ATT&CK and includes notes on data source assumptions, expected false positive rate, and tuning considerations.

**Status:** Rule library under active development. Starter rules published. Contributions welcome.

## What this is

A public companion to the detection engineering work I do as Security Engineering Manager at a multi-tenant SaaS platform. Specific rules deployed in production are employer-confidential. What is published here is a generalized companion rule set built around the same threat models, suitable for adaptation in any multi-tenant SaaS environment.

## Why SaaS-specific

Most public Sigma rule libraries are tuned for endpoint or AD-heavy enterprise environments. Multi-tenant SaaS introduces detection patterns those rule sets do not cover well:

- Tenant boundary crossing in shared-database architectures
- Authentication anomalies in OAuth / OIDC flows at scale
- Application-layer fraud patterns in self-service signup
- Bug bounty researcher behavior versus genuine attacker behavior
- Webhook abuse from misconfigured tenant integrations

## Structure

- `rules/auth/` — Authentication and identity rules
- `rules/tenant-boundary/` — Tenant isolation and boundary crossing
- `rules/application/` — Application-layer fraud and abuse
- `rules/cloud/` — AWS-specific cloud detection
- `rules/integration/` — Webhook, API token, and integration abuse
- `mappings/` — MITRE ATT&CK mappings
- `tools/` — Conversion scripts for common SIEMs

## Conventions

Every rule includes:
- `title` and `description`
- `author: Cameron Hopkin`
- `status` (experimental, test, stable)
- `references` to MITRE technique ID and external research
- `tags` with at least one MITRE technique
- `falsepositives` section, not left empty

Rules that have been tested in production environments are marked `status: stable`. Untested or theoretical rules are `experimental`.

## Contributing

PRs welcome. Please include the FP analysis in the rule body, not just the detection logic.

## License

Apache 2.0
