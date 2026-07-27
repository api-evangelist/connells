---
name: Assemble Connells local market presence
description: >-
  Build a picture of Connells' presence and reputation in a local area —
  geography, branch coverage, service lines and published customer testimonials
  — from the read-only JSON endpoints on www.connells.co.uk.
api: openapi/connells-website-openapi.yml
operations:
  - listLocations
  - searchPlaces
  - listBranches
  - listTestimonials
generated: '2026-07-26'
method: generated
---

# Assemble Connells local market presence

Use this when someone asks where Connells operates, what it offers in an area,
or what customers there say about it.

**Scope warning, state it up front.** The data below covers the `connells.co.uk`
brand only. Connells Group runs 80+ brands (Countrywide, Hamptons, Sequence,
Bairstow Eves, Fox & Sons, John D Wood, Blundells, Barnard Marcus, William H
Brown, Gascoigne Halman and more) and none of them expose these endpoints — the
Homeflow-hosted sibling sites 302-redirect `/api/*` to their homepage. Any
answer built here describes one brand, not the group.

Authentication: none. All operations are anonymous HTTPS GETs.

## Step 1 — geography

```
GET https://www.connells.co.uk/api/locations
```

Returns a **bare JSON array** — no `results`/`pagination` envelope, unlike every
other endpoint. Each record is `{id, name, countyName, urlLabel}` where `id` is a
24-character hex ObjectId. `name` and `urlLabel` are empty strings on several
records; `countyName` is the field you can rely on.

For a specific place, use `searchPlaces` instead — it requires `name` and returns
positional `[label, id, slug]` arrays:

```
GET https://www.connells.co.uk/api/places?name=sheffield
```

## Step 2 — branch coverage and service mix

```
GET https://www.connells.co.uk/api/branches
```

`pagination.totalCount` is the one genuinely group-relevant number this surface
gives you: **162 branches** for the Connells brand. Report that from
`pagination`, not from `results.length` — you only receive 12 records and no
paging parameter works, so `results` is a sample, never the population.

Within those 12, `services[]` tells you the real service mix per branch
(Sales, Lettings, Land and New Homes, each with `enabled` and its own phone and
email), and `isSalesEnabled` / `isLettingsEnabled` restate it as flags. `lat` and
`lng` are populated, so the sample is mappable.

There is **no property inventory here**. `/api/properties` returns HTTP 500;
listings are server-rendered on the website from the Homeflow platform. Never
imply you can count or price stock from this surface.

## Step 3 — reputation

```
GET https://www.connells.co.uk/api/testimonials
```

Returns 12 published customer testimonials as `{id, name, content, displayDate,
contactCounty, createdAt}`. Two things to handle carefully:

- The envelope is inconsistent — `pagination` is **null** and the error key is
  singular (`error`, not `errors`). Do not reuse the branch parser here.
- `contactCounty` is free text and the only geography on a testimonial. There is
  no id linking a testimonial to a branch or a location, so you can group by
  county string but you cannot truthfully attribute a review to a branch.

These are **curated, published marketing testimonials** selected by Connells, not
a review sample. `name` is partially redacted in the source (e.g. "Ms V.L. Hall
(V)"). Present them as published testimonials and say so; do not compute a
rating or a sentiment score from them and do not present them as independent
reviews. Independent reviews for Connells Group brands live on third-party
platforms (Feefo is referenced on the Connells Survey & Valuation site), not
here.

## Assembling the answer

A defensible local-presence summary from this surface contains: the 162-branch
brand total, the branch or branches from the sample that match the area with
their address, coordinates and service lines, the county-level geography, and
any testimonials whose `contactCounty` matches — each clearly labelled as
published testimonials.

State the two limits every time: you can only see the first 12 records of each
collection, and this is the Connells brand rather than Connells Group.

## Rate limiting

Cloudflare enforces an unpublished limit and answers HTTP 429 with the plain-text
body `Too many requests` and a `Retry-After` header (34 seconds observed). Four
sequential calls is fine; a sweep is not. There are no `RateLimit-*` headers to
warn you in advance.
