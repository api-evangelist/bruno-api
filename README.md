# Bruno

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Bruno is an open-source (MIT), git-native API client - a lightweight, offline-first alternative to Postman and Insomnia for exploring and testing APIs. It is a developer TOOL, not a hosted HTTP API provider. Collections are stored on the local filesystem as folders of plain-text files (the .bru "Bru" markup language, with OpenCollection YAML now recommended for new collections), so API requests are version-controlled in Git alongside code. Bruno sends HTTP, REST, GraphQL, and gRPC requests, manages environments and variables, and runs pre-request/post-response scripts, tests, and assertions. The @usebruno/cli command-line runner (bru) executes collections headlessly in CI/CD with JSON, JUnit, and HTML reporters. Bruno is offline-only and does not sync request data to a Bruno-hosted cloud; paid Pro/Ultimate tiers add native in-app Git integration, OpenAPI sync, and enterprise admin controls that run through your own Git provider and identity systems. Bruno does not expose a documented public REST HTTP API.

**Areas:** API Client · API Testing · Developer Tools · Open Source · Git-Native · CLI · Postman Alternative · A2A · Testing

## Bruno on APIs.io

Everything profiled for Bruno is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/bruno-api/](https://apis.io/providers/bruno-api/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [Bruno API Client](https://apis.io/apis/bruno-api/bruno-api-client/) — The core open-source, git-native desktop API client (a lightweight Postman/Insomnia alternative). Compose and send HTTP, REST, GraphQL, and gRPC requests,…
- [Bru Markup Language (.bru)](https://apis.io/apis/bruno-api/bruno-bru-language/) — Bru is Bruno's plain-text domain-specific markup language. Each request is stored as a .bru file capturing the HTTP method, URL, query params, headers,…
- [OpenCollection Format](https://apis.io/apis/bruno-api/bruno-opencollection/) — OpenCollection is the open, YAML-based collection format Bruno now recommends for new collections as an alternative representation to .bru. Like .bru it…
- [Bruno CLI (bru)](https://apis.io/apis/bruno-api/bruno-cli/) — The @usebruno/cli command-line runner (invoked as bru, installed via npm install -g @usebruno/cli) executes individual requests or entire collections…
- [Bruno Git Integration and Sync](https://apis.io/apis/bruno-api/bruno-git-collaboration/) — Paid Bruno (Pro and Ultimate) adds native in-app Git integration and OpenAPI sync (5 syncs/month on Pro, unlimited on Ultimate) plus SSO, SCIM, audit logs,…
- [Bruno API Client](https://apis.io/apis/bruno-api/api-client/) — Bruno is an open-source API client for exploring and testing REST, GraphQL, and gRPC APIs. Collections are stored as plain text Bru files on the filesystem,…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Bruno MCP surfaces](https://apis.io/servers/bruno-api/bruno-mcp-surfaces/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Bruno Api Domain Security](https://apis.io/security/bruno-api/bruno-api-domain-security/)
- [Bruno Api Trust Center](https://apis.io/security/bruno-api/bruno-api-trust-center/)
- [Bruno Api Vulnerability Disclosure](https://apis.io/security/bruno-api/bruno-api-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Bruno Api Plans Pricing](https://apis.io/plans/bruno-api/bruno-api-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Bruno Api Rate Limits](https://apis.io/rate-limits/bruno-api/bruno-api-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Bruno Api Finops](https://apis.io/finops/bruno-api/bruno-api-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.usebruno.com/)
- [Documentation](https://docs.usebruno.com/)
- [Getting started](https://docs.usebruno.com/introduction/getting-started)
- [Pricing](https://www.usebruno.com/pricing)
- [Sign up](https://www.usebruno.com/start-trial)
- [Support](https://www.usebruno.com/support)
- [Blog](https://blog.usebruno.com/)
- [Terms of service](https://www.usebruno.com/terms)
- [Privacy policy](https://www.usebruno.com/privacy-policy)
- [GitHub](https://github.com/usebruno)

## API Evangelist rating

**Kin Score 50.4** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 0.0 |
| Contract governance | 18.2 |
| Operational transparency | 65.8 |
| Developer ergonomics | 59.5 |
| Access clarity | 92.1 |

**Agent readiness 9.6** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | — |
| Idempotency | — |
| Error Semantics | — |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 29.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/bruno-api/](https://apis.io/providers/bruno-api/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Bruno: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/bruno-api/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
