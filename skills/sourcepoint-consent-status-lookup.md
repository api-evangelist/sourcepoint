---
name: sourcepoint-consent-status-lookup
description: Read one end-user's current or historical consent state for a Sourcepoint property on whichever regulatory surface applies — GDPR TCF, GDPR Standard, U.S. Multi-State Privacy, Global Enterprise, or Preferences.
api: sourcepoint
generated: '2026-08-12'
method: generated
source: openapi/sourcepoint-gdpr-tcf-openapi.yml, openapi/sourcepoint-gdpr-standard-openapi.yml, openapi/sourcepoint-usnat-openapi.yml, openapi/sourcepoint-global-enterprise-openapi.yml, openapi/sourcepoint-preferences-openapi.yml
operations:
  - getGdprTcfConsentHistory
  - getGdprStandardConsentHistory
  - getUsnatConsentHistory
  - getGlobalEnterpriseConsentHistory
  - getPreferencesHistory
---

# Look up an end-user's consent state

## Pick the surface first

| Regulation / product | Operation | Base | Path | End-user id |
|---|---|---|---|---|
| GDPR TCF (IAB TCF v2.2) | `getGdprTcfConsentHistory` | `https://cdn.privacy-mgmt.com/consent/tcfv2` | `GET /consent/v3/history/{siteId}` | `consentUUID` or `authId` |
| GDPR Standard (non-TCF) | `getGdprStandardConsentHistory` | `https://cdn.privacy-mgmt.com/consent/tcfv2` | `GET /consent/v3/history/{siteId}` | `consentUUID` or `authId` |
| U.S. Multi-State Privacy | `getUsnatConsentHistory` | `https://cdn.privacy-mgmt.com/usnat` | `GET /consent/history/{siteId}` | `usnatUUID` (`uuid`) or `authId` |
| Global Enterprise | `getGlobalEnterpriseConsentHistory` | `https://cdn.privacy-mgmt.com/global-cmp` | `GET /consent/history/{siteId}` | `globalcmpUUID` (`uuid`) or `authId` |
| Preferences | `getPreferencesHistory` | `https://cdn.privacy-mgmt.com/preferences` | `GET /user-preference/history` | `accountId` + `id` (uuid or authId) |

## Steps

1. Resolve the property id. On the consent surfaces it is the path parameter `siteId`; on Preferences
   it is `accountId` plus the `id` query parameter.
2. Supply exactly one end-user identifier. `authId` is the cross-device identifier set by
   authenticated consent; the per-surface UUID is the cookie/device-scoped one.
3. Set `latest=true` when you only need the current state. Without it you get the full history,
   which is unbounded — there is **no pagination on any Sourcepoint response**
   (`conventions/sourcepoint-conventions.yml`).

## Reading the result

- GDPR responses carry the IAB `euconsent` TCString plus decoded `grants`, `categories`,
  `legIntCategories` and vendor structures (`IABAndCustomVendors`, `customVendors`, `GoogleATPVendors`).
- U.S. Multi-State Privacy responses are GPP-section shaped — the U.S. National section plus any
  state sections (CA, CO, CT, DE, FL, IA, MT, NE, NH, NJ, OR, TN, TX, UT, VA) that apply.
- Each record carries the `consentDate`, and the `messageId` / `vendorListId` that produced it.
- **Decode, do not re-derive.** The TCString is the authoritative artifact; the decoded fields are a
  convenience view of it.

## Failure modes

- No non-2xx response is documented for any of these operations. An unknown property returns a plain
  text body such as `no active vl for siteId` with a 404.
- An empty array means "no record for that identifier", not "no consent". Do not translate an empty
  response into a consent decision.
