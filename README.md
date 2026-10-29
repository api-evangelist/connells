# Connells Group

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

Connells Limited, trading as Connells Group, is the United Kingdom's largest estate agency and property services group, headquartered at Cumbria House in Leighton Buzzard, Bedfordshire, and a wholly owned subsidiary of Skipton Building Society. It states 1,200+ branches, 16,000+ colleagues, more than 80 local brands including Connells, Countrywide, Hamptons, Sequence, Bairstow Eves, Fox & Sons, John D Wood & Co, Gascoigne Halman and Blundells, roughly 115,000 property sales a year and about 10% market share, 165,000+ managed tenancies and £33bn+ of arranged mortgage lending. It occupies almost the entire residential value chain at once: estate agency, residential and corporate lettings, new homes, land and planning, auctions, surveys and valuations, conveyancing, mortgage services, asset management, affordable housing, EPCs and inventories, commercial agency and a research and consultancy practice. Its home market is the United Kingdom, where there is no MLS and no cooperative listing standard — residential stock reaches consumers through the Rightmove and Zoopla portal duopoly by way of agency CRM and website software rather than a shared pool, and Connells' own consumer property sites are built on the Homeflow platform. Its API posture is closed and undocumented. No developer portal exists: developer., developers., api. and docs.connellsgroup.co.uk do not resolve, and /developers, /api, /docs, /openapi.json, /swagger.json, /api-docs and /.well-known/openid-configuration return 404 on both connellsgroup.co.uk and connells.co.uk. It publishes no OpenAPI, no GraphQL, no AsyncAPI, no MCP server and no client SDK — the only first-party package on any public registry is a dormant npm colour-token file for its website. Probing on 2026-07-26 did, however, find a small live JSON surface underneath the consumer site at https://www.connells.co.uk/api: six anonymous read-only Next.js route handlers serving the branch finder, people directory, testimonials wall and place autocomplete, plus a seventh (/api/properties) that returns HTTP 500. These are undocumented internal website routes, not a product — unversioned, unsupported, rate limited by Cloudflare, capped at 12 records because no paging parameter works, and carrying application errors inside HTTP 200 bodies. Only connells.co.uk exposes them; the sibling brand sites redirect /api/* away. The group's 88-URL corporate sitemap contains no developer path — its one /developers/ page is addressed to property developers, not software developers. Integration is real but partner-only: Connells Survey & Valuation advertises delivering "totally integrated panel and risk management technology solutions to lenders" for the 40+ lenders whose valuation panels it manages, and reaches them through third-party platforms such as Cotality's LenderHub, while Countrywide Surveying Services' Geoconnect engine is described as connecting internal and external data sources through API integrations it consumes rather than publishes. There is no RESO Web API or Data Dictionary certification, no OData $metadata document and no Universal Property Identifier anywhere in the estate — RESO is a North American NAR/MLS mechanism and the UK has no MLS to certify against. Connells publishes no open data either; its research product, covering 88% of UK postcode areas from branch-level proprietary data, is sold through a brochure request and a contact form, and the genuinely open UK property layer belongs to the public sector (HM Land Registry Price Paid Data and Ordnance Survey), not to the brokerage.

**Areas:** Real Estate · United Kingdom · Property Listings · Brokerage · Estate Agency · Rentals · Valuation · Conveyancing · Mortgage · Property Management · Auctions · PropTech

## Connells Group on APIs.io

Everything profiled for Connells Group is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/connells/](https://apis.io/providers/connells/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Connells Group Branches API](https://apis.io/apis/connells/connells-branches-api/) — Connells branch (office) directory.
- [Connells Group Locations API](https://apis.io/apis/connells/connells-locations-api/) — Geographic locations and place-name lookup.
- [Connells Group People API](https://apis.io/apis/connells/connells-people-api/) — Connells staff directory.
- [Connells Group Testimonials API](https://apis.io/apis/connells/connells-testimonials-api/) — Published customer testimonials.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [connells](https://apis.io/servers/connells/connells/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Connells Agentic Access](https://apis.io/agentic-access/connells/connells-agentic-access/)

#### Examples (5)

Example requests and responses.

- [Connells Branch By Id Response](https://apis.io/examples/connells/connells-branch-by-id-response/)
- [Connells Branches Response](https://apis.io/examples/connells/connells-branches-response/)
- [Connells Places Search Response](https://apis.io/examples/connells/connells-places-search-response/)
- [Connells Staff Response](https://apis.io/examples/connells/connells-staff-response/)
- [Connells Testimonials Response](https://apis.io/examples/connells/connells-testimonials-response/)

#### Collections (1)

Postman and Open Collection request collections.

- [Connells Website JSON API (undocumented)](https://apis.io/collections/connells/open-connells-website/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Connells Authentication](https://apis.io/security/connells/connells-authentication/)
- [Connells Domain Security](https://apis.io/security/connells/connells-domain-security/)

#### Rate limits (1)

Published request limits.

- [Connells Rate Limits](https://apis.io/rate-limits/connells/connells-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.connellsgroup.co.uk/)
- [Blog](https://www.connellsgroup.co.uk/news/)
- [Compliance](https://www.connellsgroup.co.uk/required-disclosures-inc-modern-slavery-act-statement/)
- [Terms of service](https://www.connellsgroup.co.uk/legal-notices/)
- [Privacy policy](https://www.connellsgroup.co.uk/privacy-policy/)

## API Evangelist rating

**Kin Score 22.7** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 15.2 |
| Contract governance | 18.2 |
| Operational transparency | 0.0 |
| Developer ergonomics | 16.1 |
| Access clarity | 28.9 |

**Agent readiness 30.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | verified |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 27.8** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/connells/](https://apis.io/providers/connells/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Connells Group: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/connells/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
