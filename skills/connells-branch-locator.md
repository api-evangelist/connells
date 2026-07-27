---
name: Locate a Connells branch and its people
description: >-
  Find a Connells estate agency branch by place, read its address, coordinates,
  service lines and branch manager, and reach the right team — using the
  undocumented read-only JSON endpoints on www.connells.co.uk.
api: openapi/connells-website-openapi.yml
operations:
  - searchPlaces
  - listBranches
  - getBranch
  - listStaff
generated: '2026-07-26'
method: generated
---

# Locate a Connells branch and its people

Connells Group is the UK's largest estate agency group — 1,200+ branches under
80+ brands. Only the `connells.co.uk` brand exposes machine-readable branch data,
through undocumented route handlers at `https://www.connells.co.uk/api`.

**Read this before you start.** These endpoints are not a Connells product.
There is no developer portal, no documentation, no version, no SLA and no
support channel. They can change or break without notice — `/api/properties`
was already returning HTTP 500 when this skill was written. Do not build
anything load-bearing on them.

## Authentication

None. Every operation answers anonymous requests over HTTPS. Send no key, no
token and no cookie.

## Step 1 — resolve the place the user named

Call `searchPlaces` with the `name` query parameter. It is **required**; omitting
it returns HTTP 200 with `{"results":[],"errors":[{"message":"Name required for
places search"}]}` rather than a 400.

```
GET https://www.connells.co.uk/api/places?name=bedford
```

Matches come back as positional 3-string arrays, not objects:
`["Bedford, Bedfordshire", "51e7c40773dadaf60feea517", "bedford"]` —
`[label, placeId, placeSlug]`. Index them positionally.

Note the place id is a 24-character hex ObjectId, and **it does not join to any
branch**. Use the place only to confirm the user's intent and to get a clean
county label.

## Step 2 — list branches

```
GET https://www.connells.co.uk/api/branches
```

The response envelope is `{results, pagination, errors}`. `pagination` reports
`totalCount: 162` across `pageCount: 14` — **but no paging parameter works**.
`page`, `pageSize`, `per_page`, `limit` and `offset` were all tested and every
one returns page 1. You will only ever see the first 12 branches, alphabetically
from Abingdon.

There is also no server-side filter: `lat`, `lng`, `distance`, `search`, `q` and
`slug` are all ignored. To match a user's place, **filter client-side** on
`displayAddress` (newline-delimited postal address) or compute distance from
`lat`/`lng`, which are populated WGS84 coordinates.

Be honest with the user when the branch they want is outside the first 12 — say
the surface cannot reach it rather than implying no such branch exists.

## Step 3 — read one branch

```
GET https://www.connells.co.uk/api/branches/8020
```

The path segment must be the **numeric** `id` from step 2. Passing the slug
(`abingdon`) returns HTTP 200 with `{"result":null,"errors":null}` — a silent
miss with no 404 and no message. Always null-check `result`.

A branch carries what a caller usually wants inline: `displayAddress`,
`contactTelephone`, `salesTelephone`, `lettingsTelephone`, `email`, `lat`/`lng`,
`branchUrl`, an embedded `branchManager` object, and a `services` array of
`{service, phone_number, email_address, enabled}` covering Sales, Lettings and
Land and New Homes. Prefer the per-service phone and email over the branch-level
ones when routing a specific enquiry — they differ (lettings enquiries have
their own `...let@connells.co.uk` address).

`departments` is present but empty on every record, and `distance` is always
null. Do not present either as meaningful.

## Step 4 — find a named colleague

```
GET https://www.connells.co.uk/api/staff
```

Same envelope and the same paging limitation — 12 of 841. `branchId` is the only
foreign key in the whole model and joins back to `Branch.id`. `email` and
`mobileNumber` were null on every record sampled, so route contact through the
branch's addresses from step 3, not through the staff record.

## Errors and rate limiting

Application errors arrive **inside HTTP 200 bodies** under `errors` (an array of
`{message}`). The testimonials endpoint uses a singular `error` key instead.
Never rely on the status code to detect an application failure.

Rate limiting is real and unannounced. Cloudflare returns **HTTP 429** with the
plain-text body `Too many requests` and a `Retry-After` header (34 seconds
observed). There are no `RateLimit-*` headers on success, so you get no forward
warning — pace your calls, and honour `Retry-After` on a 429. Note that a 429
body is `text/plain` and a 404 body is `text/html`, so guard your JSON parsing.

## Idempotency and writes

There are none. `OPTIONS /api/branches` reports `Allow: GET, HEAD, OPTIONS`.
This is a read-only surface with no idempotency key and no write path. You
cannot book a valuation, register an applicant or submit an enquiry through it —
send the user to the branch's phone number, email address, or `branchUrl` on the
website instead.
