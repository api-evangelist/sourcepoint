---
name: sourcepoint-dsar-consent-erasure
description: Erase one end-user's consent and preference records across every Sourcepoint regulatory surface (GDPR TCF, GDPR Standard, U.S. Multi-State Privacy, Global Enterprise, Preferences) for a single property, as part of a data subject erasure request.
api: sourcepoint
generated: '2026-08-12'
method: generated
source: openapi/sourcepoint-gdpr-tcf-openapi.yml, openapi/sourcepoint-gdpr-standard-openapi.yml, openapi/sourcepoint-usnat-openapi.yml, openapi/sourcepoint-global-enterprise-openapi.yml, openapi/sourcepoint-preferences-openapi.yml
operations:
  - deleteGdprTcfConsent
  - deleteGdprStandardConsent
  - deleteUsnatConsent
  - deleteGlobalEnterpriseConsent
  - deletePreferencesHistory
---

# Erase an end-user's Sourcepoint consent records (DSAR)

There is no single erasure endpoint. Each regulatory surface owns its own record and its own
end-user identifier, so an erasure request means calling the DELETE on **every** surface the
property runs.

## Before you start

- You need the **property id** (`siteId`, called `propertyId` on the Preferences surface).
- You need **either** the surface's end-user UUID **or** the `authId` your organization passed to
  the CMP for authenticated consent. `authId` is the only identifier that resolves the same person
  across surfaces and devices — if the property uses authenticated consent, prefer it.
- The consent surfaces declare **no security scheme** (see `authentication/sourcepoint-authentication.yml`).
  Treat the UUID/`authId` as a capability token: never log it, never put it in a URL you persist.

## Steps

1. **GDPR TCF** — `deleteGdprTcfConsent`
   `DELETE https://cdn.privacy-mgmt.com/consent/tcfv2/consent/v3/{siteId}` with `consentUUID` **or** `authId`.
2. **GDPR Standard** — `deleteGdprStandardConsent`
   `DELETE https://cdn.privacy-mgmt.com/consent/tcfv2/consent/v3/{siteId}` with `consentUUID` **or** `authId`.
   Same path shape as TCF; which one applies depends on how the property's campaign is configured.
3. **U.S. Multi-State Privacy** — `deleteUsnatConsent`
   `DELETE https://cdn.privacy-mgmt.com/usnat/consent/{siteId}` with `usnatUUID` (`uuid`) **or** `authId`.
4. **Global Enterprise** — `deleteGlobalEnterpriseConsent`
   `DELETE https://cdn.privacy-mgmt.com/global-cmp/consent/{siteId}` with `globalcmpUUID` (`uuid`) **or** `authId`.
5. **Preferences** — `deletePreferencesHistory`
   `DELETE https://cdn.privacy-mgmt.com/preferences/user-preference` with required `propertyId` plus `uuid` or `authId`.

## Reading the result

Success is `200` with a Mongo-style acknowledgement array — objects carrying `n`, `ok` and
`deletedCount`. **A `deletedCount` of 0 is a successful call that erased nothing**: it means no
record matched that identifier on that surface. Do not report an erasure you did not observe.

## Limits and failure modes

- **Single subject only.** The docs are explicit: "This endpoint does not support mass deletions of
  end-user consent records. Please speak to your Sourcepoint representative to execute any mass
  deletions."
- No `4xx`/`5xx` responses are modelled on any of these operations. Observed failures return a bare
  text body, not JSON — e.g. `no active vl for siteId` (404). See `errors/sourcepoint-problem-types.yml`.
- There is **no idempotency key** (`conventions/sourcepoint-conventions.yml`). Re-running a DELETE is
  safe by shape — the second call simply reports `deletedCount: 0` — but nothing on the wire
  distinguishes a retry from a new request, so record your own audit trail of what you called and when.
- Erasing the stored record does **not** clear the end-user's browser state. To also reset the client,
  use the `resetUserState` command on the web/native surface.
