# Connells Group (connells)

Connells Limited, trading as Connells Group, is the United Kingdom's largest estate agency and property services group, headquartered in Leighton Buzzard, Bedfordshire, and a wholly owned subsidiary of Skipton Building Society. It states 1,200+ branches, 16,000+ colleagues, more than 80 local brands (Connells, Countrywide, Hamptons, Sequence, Bairstow Eves, Fox & Sons, John D Wood & Co, Gascoigne Halman, Blundells), roughly 115,000 property sales a year and about 10% market share, 165,000+ managed tenancies and £33bn+ of arranged mortgage lending. Its home market is the United Kingdom, where there is no MLS and no cooperative listing standard, and its API posture is closed: no developer portal, no documentation, no machine-readable contract. Integration exists only inside commercial lender-panel and platform relationships.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/connells/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/connells/refs/heads/main/apis.yml)

## Tags

- Real Estate
- United Kingdom
- Property Listings
- Brokerage
- Estate Agency
- Rentals
- Valuation
- Conveyancing
- Mortgage
- Property Management
- Auctions
- PropTech

## Timestamps

- **Created:** 2026-07-26
- **Modified:** 2026-07-26

## APIs

Connells Group publishes no documented public API — but it does leak one.

Every conventional developer entry point was probed on 2026-07-26 and every one failed. `developer.`, `developers.`, `api.` and `docs.connellsgroup.co.uk` do not resolve; `/developers`, `/api`, `/docs`, `/openapi.json`, `/swagger.json`, `/api-docs`, `/$metadata` and `/.well-known/openid-configuration` return 404 on both connellsgroup.co.uk and connells.co.uk. The group's 88-URL corporate sitemap contains no developer path — its one `/developers/` page addresses property developers, not software developers. No OpenAPI, Swagger, OData `$metadata`, AsyncAPI, GraphQL schema, MCP server or Postman collection is published anywhere.

A second enrichment round went further and enumerated the Next.js App Router route handlers behind `www.connells.co.uk`, and found **six live, anonymous, read-only JSON endpoints** at `https://www.connells.co.uk/api` — plus a seventh that is simply broken:

| Operation | Path | Status |
|---|---|---|
| `listBranches` | `GET /api/branches` | 200 — 162 branches advertised, 12 returned |
| `getBranch` | `GET /api/branches/{id}` | 200 — numeric id only; a slug returns `result: null` |
| `listStaff` | `GET /api/staff` | 200 — 841 staff advertised, 12 returned |
| `listTestimonials` | `GET /api/testimonials` | 200 — inconsistent envelope |
| `listLocations` | `GET /api/locations` | 200 — bare array, no envelope |
| `searchPlaces` | `GET /api/places?name=` | 200 — `name` required |
| `listProperties` | `GET /api/properties` | **500 on every probe** |

This is not a product and should not be described as one. It is unversioned, undocumented and unsupported, with no terms and no status page. Authentication is absent entirely; the only control is a Cloudflare rate limit that answers HTTP 429 with `Retry-After` and no forward `RateLimit-*` headers. Application errors ride inside HTTP 200 bodies rather than status codes. Pagination metadata advertises 162 branches across 14 pages, but no paging parameter is honoured — pages 2..n are unreachable, so the surface cannot deliver the collection it describes. Only `connells.co.uk` exposes these handlers; the sibling brand sites run the Homeflow Rails application and redirect `/api/*` away.

The `openapi/` document in this repo was **derived by API Evangelist from captured live responses**, not published by Connells. Every schema is a transcription of a body the service actually returned, and the captures are kept alongside it in `examples/`.

There is no property listings data on this surface. The group's core asset — ~115,000 sales a year of stock — reaches consumers through Rightmove, Zoopla and OnTheMarket, server-rendered from the Homeflow platform.

### RESO posture

No RESO reference exists anywhere in the Connells Group estate. There is no RESO Web API certification, no Data Dictionary certification, no OData `$metadata` document and no Universal Property Identifier. The RESO certified-organizations directory at [reso.org/certificates](https://www.reso.org/certificates/) (fetched 2026-07-26, HTTP 200) contains no Connells entity and no UK entity at all. This is structural: RESO is a North American NAR/MLS mechanism, the UK has no MLS, and the de facto UK interchange format is the Rightmove V3 BLM XML feed — a private portal's bulk upload specification, not a standards-body contract.

### Access gate

`partner-only`. There is no developer signup, no application form, no sandbox, no API terms and no published key issuance. Programmatic integration is real but reachable only through a commercial relationship: a panel management agreement with Connells Survey & Valuation, which advertises "totally integrated panel and risk management technology solutions to lenders" for the 40+ UK lenders whose valuation panels it manages, or through third-party platforms such as Cotality's LenderHub. The Connells Group Research data product — proprietary branch data covering 88% of UK postcode areas, blended at UDPRN level — is sold through a brochure request and a contact form, not served over a feed.

### Open data

None from Connells. The genuinely open UK property layer belongs to the public sector — HM Land Registry Price Paid Data and ownership data under the Open Government Licence, and Ordnance Survey's addressing and mapping open products — not to the brokerage.

## Artifacts

| Artifact | File | Method |
|---|---|---|
| OpenAPI 3.1 (derived from live captures) | `openapi/connells-website-openapi.yml` | derived |
| Captured live responses | `examples/` | searched |
| Authentication profile (none required) | `authentication/connells-authentication.yml` | probed |
| Rate limits (Cloudflare 429 / Retry-After) | `rate-limits/connells-rate-limits.yml` | probed |
| Error catalogue | `errors/connells-problem-types.yml` | derived |
| API conventions | `conventions/connells-conventions.yml` | derived |
| Data model | `data-model/connells-data-model.yml` | derived |
| Lifecycle (honest negative) | `lifecycle/connells-lifecycle.yml` | probed |
| Conformance + regulatory registrations | `conformance/connells-conformance.yml` | searched |
| Packages | `packages/connells-packages.yml` | searched |
| Agent skills | `skills/` | generated |
| Agentic access contracts | `agentic-access/connells-agentic-access.yml` | generated |
| Candidate MCP tools (no server exists) | `mcp/connells-mcp.yml` | derived |
| llms.txt | `llms/connells-llms.txt` | generated |
| Domain security probe | `security/connells-domain-security.yml` | probed |
| Well-known probe (all 404) | `well-known/connells-well-known.yml` | probed |

### What is deliberately absent

No `SDKs`, `MCPServer`, `StatusPage`, `Deprecation`, `Security`, `WellKnown`, `SecurityTxt`, `Webhooks`, `AsyncAPI`, `Idempotency`, `Documentation`, `DeveloperPortal`, `APIReference`, `GettingStarted`, `SignUp`, `Postman`, `GitHubOrganization`, `CLI`, `Sandbox` or `ChangeLog` pointer is claimed, because Connells publishes none of those things. The only first-party package on any public registry is `@connells-group/design-tokens__con` — a dormant npm colour-token file for the website, verified first-party by its `@connellsgroup.co.uk` maintainer address, and not an API client.

## Properties

- [Website](https://www.connellsgroup.co.uk/)
- [Connells Estate Agents](https://www.connells.co.uk/)
- [Countrywide](https://www.countrywide.co.uk/)
- [Hamptons](https://www.hamptons.co.uk/)
- [Sequence Home](https://www.sequencehome.co.uk/)
- [Connells Survey & Valuation](https://www.connells-surveyors.co.uk/)
- [Properties for Sale](https://www.connells.co.uk/properties/sales)
- [Properties to Let](https://www.connells.co.uk/properties/lettings)
- [Research — Our Data](https://www.connellsgroup.co.uk/research/our-data/)
- [News](https://www.connellsgroup.co.uk/news/)
- [Contact](https://www.connellsgroup.co.uk/contact-us/)
- [Careers](https://www.connellsgroup.co.uk/careers/work-with-us/)
- [Privacy Policy](https://www.connellsgroup.co.uk/privacy-policy/)
- [LinkedIn](https://www.linkedin.com/company/connells-group)
- [Skipton Building Society (parent)](https://www.skipton.co.uk/)

## Maintainers

- Kin Lane — kin@apievangelist.com
