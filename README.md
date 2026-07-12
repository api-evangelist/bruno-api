# Bruno (bruno-api)

Bruno is an open-source (MIT), git-native API client - a lightweight, offline-first alternative to Postman and Insomnia for exploring and testing APIs. **Bruno is a developer tool, not a hosted HTTP API provider.** It runs as a desktop application (with a CLI companion) and stores API collections on your local filesystem as folders of plain-text files, so requests are version-controlled in Git right alongside your code.

Collections are written in Bruno's own `.bru` "Bru" markup language (with OpenCollection YAML now recommended for new collections). Bruno sends HTTP, REST, GraphQL, and gRPC requests, manages environments and variables, and runs pre-request/post-response scripts, tests, and assertions. The `@usebruno/cli` runner (`bru`) executes collections headlessly in CI/CD with JSON, JUnit, and HTML reporters.

Bruno is **offline-only** and does not sync your request data to a Bruno-hosted cloud. Paid Pro/Ultimate tiers add native in-app Git integration, OpenAPI sync, and enterprise admin controls (SSO/SCIM/audit logs) that run through *your own* Git provider and identity systems. **Bruno does not expose a documented public REST HTTP API**, so the "APIs" below are its logical capability surfaces (the client, the file formats, the CLI, and the Git integration), not hosted endpoints.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bruno-api/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bruno-api/refs/heads/main/apis.yml)

## Tags

- API Client
- API Testing
- Developer Tools
- Open Source
- Git-Native
- CLI
- Postman Alternative

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## Capability Areas

> These are Bruno's logical surfaces, not hosted HTTP APIs. Bruno has no public REST endpoints or base URL of its own.

### Bruno API Client

The core open-source, git-native desktop API client (a lightweight Postman/Insomnia alternative). Compose and send HTTP, REST, GraphQL, and gRPC requests; organize them into collections; manage environments and variables; and write pre-request/post-response scripts plus tests and assertions. Offline-only with no cloud sync of request data.

- **Human URL:** [https://docs.usebruno.com/introduction/what-is-bruno](https://docs.usebruno.com/introduction/what-is-bruno)
- [Documentation](https://docs.usebruno.com/)
- [Source Code](https://github.com/usebruno/bruno)

### Bru Markup Language (.bru)

Bruno's plain-text domain-specific markup language. Each request is stored as a `.bru` file capturing the HTTP method, URL, query params, headers, body, authentication, scripts, tests, assertions, and variables - so a collection is a folder of human-readable text files reviewable in Git pull requests.

- **Human URL:** [https://docs.usebruno.com/bru-lang/overview](https://docs.usebruno.com/bru-lang/overview)
- [Documentation](https://docs.usebruno.com/bru-lang/overview)
- [Source Code](https://github.com/usebruno/bruno)

### OpenCollection Format

The open, YAML-based collection format Bruno now recommends for new collections as an alternative representation to `.bru`. Like `.bru`, it stores requests, folders, auth, and scripts as version-friendly text.

- **Human URL:** [https://docs.usebruno.com/](https://docs.usebruno.com/)
- [Documentation](https://docs.usebruno.com/)

### Bruno CLI (bru)

The `@usebruno/cli` command-line runner (invoked as `bru`, installed via `npm install -g @usebruno/cli`) executes individual requests or entire collections headlessly for CI/CD, with JSON, JUnit, and HTML test reporters, environment selection, and assertions. Since v3.0.0 it defaults to Safe Mode; Developer Mode features (filesystem access, external npm packages) require the `--sandbox=developer` flag.

- **Human URL:** [https://docs.usebruno.com/bru-cli/overview](https://docs.usebruno.com/bru-cli/overview)
- [Documentation](https://docs.usebruno.com/bru-cli/overview)
- [Source Code](https://github.com/usebruno/bruno)

### Bruno Git Integration and Sync

Paid Bruno (Pro and Ultimate) adds native in-app Git integration and OpenAPI sync (5 syncs/month on Pro, unlimited on Ultimate) plus SSO, SCIM, audit logs, and license/admin controls. Collaboration happens through your own Git provider and identity systems - Bruno stays offline-only and does not sync request data to a Bruno-hosted cloud.

- **Human URL:** [https://www.usebruno.com/pricing](https://www.usebruno.com/pricing)
- [Pricing](https://www.usebruno.com/pricing)
- [Documentation](https://docs.usebruno.com/)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/usebruno)
- [Website](https://www.usebruno.com/)
- [Documentation](https://docs.usebruno.com/)
- [GitHub Organization](https://github.com/usebruno)
- [Plans](plans/bruno-api-plans-pricing.yml)
- [Rate Limits](rate-limits/bruno-api-rate-limits.yml)
- [Fin Ops](finops/bruno-api-finops.yml)
- [Blog](https://blog.usebruno.com/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
