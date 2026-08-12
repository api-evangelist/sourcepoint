---
name: sourcepoint-tcf-vendor-list-audit
description: Audit a Sourcepoint property's vendor list — list the vendors, read the vendor-to-purpose legal-basis mapping, and resolve content URLs to the vendors that own them — on the GDPR TCF or GDPR Standard surface.
api: sourcepoint
generated: '2026-08-12'
method: generated
source: openapi/sourcepoint-gdpr-tcf-openapi.yml, openapi/sourcepoint-gdpr-standard-openapi.yml
operations:
  - getGdprTcfVendors
  - getGdprTcfVendorPurposeMapping
  - postGdprTcfVendorUrlMapping
  - getGdprStandardVendorPurposeMapping
  - postGdprStandardVendorUrlMapping
---

# Audit a property's vendor list

Base for both surfaces: `https://cdn.privacy-mgmt.com/consent/tcfv2`

## Steps

1. **List the vendors** — `getGdprTcfVendors`
   `GET /vendor-list/vendors?siteId={siteId}` returns the vendors on the property's GDPR TCF vendor
   list. (There is no GDPR Standard equivalent of this operation — Standard exposes only the purpose
   mapping and the URL mapping.)
2. **Read the purpose mapping** — `getGdprTcfVendorPurposeMapping` / `getGdprStandardVendorPurposeMapping`
   `GET /vendor-list/vendor-purpose-mapping?siteId={siteId}` returns each vendor with the purposes
   that have a configured legal basis: **Consent**, **Legitimate Interest**, or **Disclosure Only**.
3. **Resolve content URLs to vendors** — `postGdprTcfVendorUrlMapping` / `postGdprStandardVendorUrlMapping`
   `POST /vendor-list/vendor-url-mapping` with a body of `{ siteId, vendorUrls: [...] }`, optional
   `allCategoryMapping` query parameter. Intended for CMS integrations that need to know whether a URL
   referenced in content maps to a vendor whose consent state can be queried.

## The trap in step 2

The mapping response is **not** the full purpose matrix. Sourcepoint documents two omissions:

- purposes set to **Not Applicable** are not returned at all; and
- a vendor with **no** purpose carrying a configured legal basis does not appear in the response.

So a vendor missing from the mapping is ambiguous — it may be unconfigured rather than absent from
the list. Cross-check against `getGdprTcfVendors` before reporting a vendor as "not present".

Step 3 also requires that vendor URL mappings were configured in the Sourcepoint portal first;
un-configured vendors return no match rather than an error.

## Failure modes

- `404` with body `no active vl for siteId` — the property has no published vendor list.
- No response beyond `200` is modelled on any of these operations; see `errors/sourcepoint-problem-types.yml`.
