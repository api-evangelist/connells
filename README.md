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

None. Connells Group publishes no documented public API.

Every conventional developer entry point was probed on 2026-07-26 and every one failed. `developer.`, `developers.`, `api.` and `docs.connellsgroup.co.uk` do not resolve; `/developers`, `/api`, `/docs`, `/openapi.json`, `/swagger.json`, `/api-docs`, `/$metadata` and `/.well-known/openid-configuration` return 404 on both connellsgroup.co.uk and connells.co.uk. The group's 88-URL corporate sitemap contains no developer path — its one `/developers/` page addresses property developers, not software developers. No OpenAPI, Swagger, OData `$metadata`, AsyncAPI, GraphQL schema or Postman collection was found, so there is no `openapi/` directory in this repo and `apis[]` in `apis.yml` is empty.

### RESO posture

No RESO reference exists anywhere in the Connells Group estate. There is no RESO Web API certification, no Data Dictionary certification, no OData `$metadata` document and no Universal Property Identifier. The RESO certified-organizations directory at [reso.org/certificates](https://www.reso.org/certificates/) (fetched 2026-07-26, HTTP 200) contains no Connells entity and no UK entity at all. This is structural: RESO is a North American NAR/MLS mechanism, the UK has no MLS, and the de facto UK interchange format is the Rightmove V3 BLM XML feed — a private portal's bulk upload specification, not a standards-body contract.

### Access gate

`partner-only`. There is no developer signup, no application form, no sandbox, no API terms and no published key issuance. Programmatic integration is real but reachable only through a commercial relationship: a panel management agreement with Connells Survey & Valuation, which advertises "totally integrated panel and risk management technology solutions to lenders" for the 40+ UK lenders whose valuation panels it manages, or through third-party platforms such as Cotality's LenderHub. The Connells Group Research data product — proprietary branch data covering 88% of UK postcode areas, blended at UDPRN level — is sold through a brochure request and a contact form, not served over a feed.

### Open data

None from Connells. The genuinely open UK property layer belongs to the public sector — HM Land Registry Price Paid Data and ownership data under the Open Government Licence, and Ordnance Survey's addressing and mapping open products — not to the brokerage.

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
