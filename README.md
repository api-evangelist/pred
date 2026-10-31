# Pred

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

Pred (PRED) is a fully decentralized, peer-to-peer sports prediction exchange built on Base, Coinbase's Ethereum Layer 2 network. Rather than a traditional sportsbook, Pred runs a real-time central limit order book where traders take LONG (YES) and SHORT (NO) positions on sporting outcomes priced between 0.00 and 1.00 USDC, and prices emerge from live supply and demand. Users keep full self-custody of collateral through per-user Gnosis Safe proxy wallets and authorize every order with EIP-712 signatures, with on-chain settlement of USDC on Base. Winning traders are welcome with no account limits, sub-200ms order execution and spreads under 2%. Pred publishes a documented HTTP trading API (login-with-signature auth, market discovery, order placement/cancellation, portfolio) plus an Ably WebSocket stream for real-time orderbook and order events. Initial markets cover the English Premier League and NBA. The company has raised $2.5M backed by Accel, Coinbase Ventures and Reverie.

**Areas:** Company · Fintech · Prediction Markets · Sports · Trading · Exchange · Web3 · Blockchain · Base · USDC · Real-Time

## Pred on APIs.io

Everything profiled for Pred is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/pred/](https://apis.io/providers/pred/)** — or go straight to one of the APIs or properties below.

### APIs (7)

- [Pred Authentication API](https://apis.io/apis/pred/pred-authentication-api/) — Required headers, token refresh, and EIP-712 CreateProxy signature for login. For overview, getting started, and environment configuration, see…
- [Pred Market Discovery API](https://apis.io/apis/pred/pred-market-discovery-api/) — Market information and discovery (public; no auth). Use this section to understand **parent_market_id** and **market_id** and to list all markets. ## What…
- [Pred Orders API](https://apis.io/apis/pred/pred-orders-api/) — Order placement, cancellation, and management endpoints. ## EIP-712 order signature All orders must be signed using EIP-712. Format: `0x<r><s><v>` (132 hex…
- [Pred Overview API](https://apis.io/apis/pred/pred-overview-api/) — ## About PRED PRED is a fully decentralized prediction market platform built on Base (Ethereum L2), enabling users to trade on real-world events with LONG…
- [Pred Portfolio API](https://apis.io/apis/pred/pred-portfolio-api/) — Portfolio, balance, positions, and open orders. **Endpoints:** - Balance: `GET /api/v1/portfolio/balance` - Positions: `GET /api/v1/portfolio/positions` -…
- [Pred User API](https://apis.io/apis/pred/pred-user-api/) — Safe approval endpoints for enabling trading on your proxy wallet. ## Safe approval signature — raw secp256k1 - Sign the `transactionHash` from prepare…
- [Pred WebSocket API](https://apis.io/apis/pred/pred-websocket-api/) — PRED uses [Ably](https://ably.com/) for real-time WebSocket data. Use Ably's token auth with `POST /api/v1/auth/ably` as your `authCallback`. ## Token auth…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (1)

Multi-step workflows that chain operations into a business task.

- [PRED trading workflows](https://apis.io/arazzos/pred/pred-trading/)

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [PRED Real-Time API (Ably WebSocket)](https://apis.io/asyncapis/pred/pred-realtime-asyncapi/)

#### Event channels (2)

Individual events and webhooks the provider emits.

- [market:{marketId}](https://apis.io/channels/pred/market-marketid/)
- [private:user:{userId}](https://apis.io/channels/pred/private-user-userid/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [pred](https://apis.io/servers/pred/pred/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Pred Agentic Access](https://apis.io/agentic-access/pred/pred-agentic-access/)

#### Collections (7)

Postman and Open Collection request collections.

- [PRED Trading Platform Authentication API](https://apis.io/collections/pred/open-pred-authentication-api/)
- [PRED Trading Platform Authentication Market Discovery API](https://apis.io/collections/pred/open-pred-market-discovery-api/)
- [PRED Trading Platform Authentication Orders API](https://apis.io/collections/pred/open-pred-orders-api/)
- [PRED Trading Platform Authentication Overview API](https://apis.io/collections/pred/open-pred-overview-api/)
- [PRED Trading Platform Authentication Portfolio API](https://apis.io/collections/pred/open-pred-portfolio-api/)
- [PRED Trading Platform Authentication User API](https://apis.io/collections/pred/open-pred-user-api/)
- [PRED Trading Platform Authentication WebSocket API](https://apis.io/collections/pred/open-pred-websocket-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Pred Openapi Overlay](https://apis.io/overlays/pred/pred-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Pred Authentication](https://apis.io/security/pred/pred-authentication/)
- [Pred Domain Security](https://apis.io/security/pred/pred-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.pred.app/)
- [Documentation](https://pred-1.gitbook.io/pred-docs)
- [Getting started](https://pred-1.gitbook.io/pred-docs/getting-started/core-concepts)
- [API reference](https://pred-1.gitbook.io/pred-docs/api-reference/overview)
- [Pricing](https://pred-1.gitbook.io/pred-docs/trading/fees)
- [Sign up](https://pred-1.gitbook.io/pred-docs/getting-started/signup)
- [Support](https://pred-1.gitbook.io/pred-docs/support/contact-us)
- [Blog](https://game.pred.app/)
- [Terms of service](https://www.pred.app/terms-of-use)
- [Privacy policy](https://www.pred.app/privacy-policy)

## API Evangelist rating

**Kin Score 41.6** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 55.5 |
| Contract governance | 4.5 |
| Operational transparency | 0.0 |
| Developer ergonomics | 56.5 |
| Access clarity | 44.7 |

**Agent readiness 31.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 23.1** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/pred/](https://apis.io/providers/pred/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Pred: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/pred/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
