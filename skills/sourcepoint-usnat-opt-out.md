---
name: sourcepoint-usnat-opt-out
description: Server-side opt an end-user out of every U.S. Multi-State Privacy choice and vendor for a Sourcepoint property, and understand when the server-side call does and does not reach the browser.
api: sourcepoint
generated: '2026-08-12'
method: generated
source: openapi/sourcepoint-usnat-openapi.yml
operations:
  - postUsnatRejectAll
  - getUsnatConsentHistory
---

# Opt an end-user out of all U.S. Multi-State Privacy choices

Base: `https://cdn.privacy-mgmt.com/usnat`

## Steps

1. **Reject all** — `postUsnatRejectAll`
   `POST /consent/{siteId}/reject-all` with the end-user's `authId` **or** `uuid` (`usnatUUID`).
2. **Verify** — `getUsnatConsentHistory`
   `GET /consent/history/{siteId}?latest=true` with the same identifier, and confirm the returned
   GPP sections reflect the opt-out.

## The constraint that matters

This is a **server-side** call. Sourcepoint states plainly:

> This is a server-side call and will not update client-side end-user consent unless your
> organization is utilizing `authId`.

So:

- With `authId` (authenticated consent), the opt-out follows the user to the browser and other devices.
- With only `uuid`, the stored record changes but the end-user's current browser session does not.
  To opt out client-side, call the `postRejectAll` command on the `__gpp` / `_sp_` surface in the page
  instead — see `components/sourcepoint-components.yml`.

Choose the path from which identifier you have, and say which one you used when you report the result.

## Scope

`reject-all` covers the U.S. National section and every applicable state section (CA, CO, CT, DE, FL,
IA, MT, NE, NH, NJ, OR, TN, TX, UT, VA). It does not touch GDPR TCF, GDPR Standard, Global Enterprise
or Preferences records — those have their own surfaces (`sourcepoint-dsar-consent-erasure`).
