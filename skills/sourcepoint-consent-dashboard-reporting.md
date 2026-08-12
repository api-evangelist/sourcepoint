---
name: sourcepoint-consent-dashboard-reporting
description: Pull Sourcepoint dashboard pageview/user and consent-message metrics for a property and period, for GDPR or U.S. Multi-State Privacy campaigns, using the API-key-authenticated reporting API.
api: sourcepoint
generated: '2026-08-12'
method: generated
source: openapi/sourcepoint-reporting-gdpr-openapi.yml, openapi/sourcepoint-reporting-usnat-openapi.yml
operations:
  - postGdprPageviewReport
  - postGdprMessageReport
  - postUsnatPageviewReport
  - postUsnatMessageReport
---

# Pull consent dashboard reporting data

Base: `https://portal.sourcepoint.com/api/external/v1/reports`

This is the **only** Sourcepoint surface with a declared credential.

## Credential

- Header: `X-API-KEY`
- Issued by a Sourcepoint account manager — there is no self-serve key generation.
- **Keys expire after one year.** Schedule rotation; nothing in the API signals impending expiry.

## Steps

1. **Pageview / user metrics**
   - GDPR: `postGdprPageviewReport` → `POST /tcfv2/dashboard-v2-pv-users/{periodFilter}`
   - U.S. Multi-State Privacy: `postUsnatPageviewReport` → `POST /usnat/dashboard-v2-pv-users/{periodFilter}`
2. **Consent-message metrics**
   - GDPR: `postGdprMessageReport` → `POST /tcfv2/dashboard-v2-messages/{periodFilter}`
   - U.S. Multi-State Privacy: `postUsnatMessageReport` → `POST /usnat/dashboard-v2-messages/{periodFilter}`

`periodFilter` is a path parameter; `startDate`, `endDate` and `siteId` go in the JSON body.

## Handling the response

- Responses are **unpaginated and unbounded**. Sourcepoint documents it directly: "Responses from the
  reporting API does not support pagination and there are no limits to number of entries returned by
  the API." Narrow the date window rather than expecting a cursor, and stream the parse for wide ranges.
- No rate-limit headers are returned and no limits are published
  (`rate-limits/sourcepoint-rate-limits.yml`), so use conservative concurrency and back off on any
  non-2xx rather than on a header.

## Auth failure

The spec models `401 Unauthorized` for a missing or invalid key, but the deployed service was observed
returning **`403` with the body `no route access`** for an unauthenticated request (2026-08-12).
**Branch on both.** See `errors/sourcepoint-problem-types.yml`.
