# Sourcepoint (sourcepoint)

Sourcepoint is a New York City-headquartered enterprise privacy and consent management technology company founded in 2015 by Ben Barokas and Brian Kane. The platform began as an ad-block recovery solution for publishers and evolved into a Consent Management Platform (CMP) used by leading global publishers and brands — including Axel Springer, Bauer Media, CNN International, Future, Haymarket, LADBible, Autotrader, and Ancestry — to handle GDPR, CCPA, U.S. Multi-State Privacy (USNAT), LGPD, and other regulations under the IAB TCF v2.2 and IAB Global Privacy Platform (GPP) frameworks. Sourcepoint products include the multi-campaign CMP across web, AMP, mobile (iOS, Android, React Native), Unity, Roku, HTML5 OTT and CTV surfaces, Compliance Monitoring (Diagnose), DSAR Handling, Universal Consent & Preferences, Marketing Preferences, Privacy Lens, and tooling for ad-block recovery. Sourcepoint technology powers over 30 billion consumer touchpoints per month. In July 2025, Sourcepoint was acquired by Paris-based Didomi (a Marlin Equity Partners portfolio company) to consolidate global consent management; Sourcepoint continues to operate under its existing brand and developer surface during integration.

**URL:** [https://www.sourcepoint.com](https://www.sourcepoint.com)

**Documentation:** [Sourcepoint Public API Hub](https://sourcepoint-public-api.readme.io/reference) and [Help Center](https://docs.sourcepoint.com/hc/en-us)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

- Privacy, Consent Management, CMP, GDPR, CCPA, LGPD, IAB TCF, IAB GPP, USNAT, DSAR, Adblock Recovery, Compliance Monitoring, Publisher Technology, AdTech, MarTech, Privacy Engineering, CTV, OTT, Mobile SDK, Web SDK

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Sourcepoint GDPR TCF API

REST API surfacing end-user consent operations under the GDPR using the IAB Transparency & Consent Framework (TCF v2.2). Supports retrieving end-user consent status and history by site, merging an end-user's custom vendor consent profile with the IAB vendor list derived from a provided TCString, deleting consent records (DSAR-style erasure), and mapping vendor purposes and URLs. The GDPR TCF web layer exposes the `__tcfapi` command surface (`ping`, `getTCData`, `addEventListener`, `removeEventListener`, `getCustomVendorConsents`, `getVendorPurposeMapping`, `postRejectAll`, `postCustomConsent`) plus the `tcData` object and `euconsentWithDisclosedVendors` helper.

**Human URL:** [https://sourcepoint-public-api.readme.io/reference/gdpr-tcf-end-user-consent-status](https://sourcepoint-public-api.readme.io/reference/gdpr-tcf-end-user-consent-status)

#### Tags

- Consent, GDPR, IAB TCF, TCF v2.2, Privacy

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference/gdpr-tcf-end-user-consent-status)
- [GDPR TCF implementation guide (web)](https://docs.sourcepoint.com/hc/en-us/articles/4416092045587-GDPR-TCF-implementation-guide-web)
- [Update end-user consent profile with Sourcepoint API](https://docs.sourcepoint.com/hc/en-us/articles/4405890450323-Update-end-user-consent-profile-with-Sourcepoint-API-GDPR-TCF-)
- [Retrieve end-user consent data history](https://docs.sourcepoint.com/hc/en-us/articles/4405613823123-Retrieve-end-user-consent-data-history)

### Sourcepoint GDPR Standard API

REST API exposing GDPR consent operations outside of the IAB TCF framework, for organizations that need GDPR compliance with custom vendor lists. Operations include retrieving end-user consent status, deleting consent status, mapping vendors and purposes, vendor URL mapping, and a web command surface for `getCustomVendorConsents`, `getVendorPurposeMapping`, `postRejectAll`, `postCustomConsent`, and `addEventListener`.

**Human URL:** [https://sourcepoint-public-api.readme.io/reference](https://sourcepoint-public-api.readme.io/reference)

#### Tags

- Consent, GDPR, Privacy

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference)

### Sourcepoint U.S. Multi-State Privacy API

REST API for U.S. Multi-State Privacy (USNAT) end-user consent handling, built on the IAB Global Privacy Platform (GPP) string. Supports retrieving end-user consent history, deleting consent status, opt-out across all privacy choices and vendors, and a web command surface including `hasSection`, `getSection`, `getField`, `getUserConsents`, `postRejectAll`, `ping`, `addEventListener`, and `removeEventListener`. Covers U.S. National and per-state privacy sections (CA, VA, CO, CT, UT, and newer state regimes).

**Human URL:** [https://sourcepoint-public-api.readme.io/reference](https://sourcepoint-public-api.readme.io/reference)

#### Tags

- Consent, U.S. Multi-State Privacy, USNAT, CCPA, GPP, Privacy

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference)

### Sourcepoint Global Enterprise API

REST API for the Global Enterprise consent product, providing a single multi-regulation consent surface across global properties. Supports retrieving end-user consent history, deleting consent status, and web methods including `getUserConsents` and `postRejectAll` for cross-regulation consent orchestration.

**Human URL:** [https://sourcepoint-public-api.readme.io/reference](https://sourcepoint-public-api.readme.io/reference)

#### Tags

- Consent, Global Privacy, Enterprise

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference)
- [Global Enterprise implementation guide](https://docs.sourcepoint.com/hc/en-us/articles/41919922996243-Global-Enterprise-implementation-guide)

### Sourcepoint Preferences API

REST API for Universal Consent & Preferences and Marketing Preferences, letting organizations retrieve and delete an end-user's preferences history and read `getUserPreferences` on the web surface. Enables a unified first-party preference profile across channels alongside the regulatory consent surface.

**Human URL:** [https://sourcepoint-public-api.readme.io/reference](https://sourcepoint-public-api.readme.io/reference)

#### Tags

- Preferences, Marketing Preferences, Universal Consent, First-Party Data

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference)
- [Preferences implementation guide (web)](https://docs.sourcepoint.com/hc/en-us/articles/30557096773139-Preferences-implementation-guide-web)

### Sourcepoint Reporting API

REST API exposing aggregated dashboard data for GDPR and U.S. Multi-State Privacy campaigns, including pageview and message data filtered by period for dashboard and BI integration. Powers the Sourcepoint portal's analytics views.

**Human URL:** [https://sourcepoint-public-api.readme.io/reference](https://sourcepoint-public-api.readme.io/reference)

#### Tags

- Reporting, Analytics, Consent, Dashboards

#### Properties

- [Documentation](https://sourcepoint-public-api.readme.io/reference)

## Common Properties

- [Website](https://www.sourcepoint.com)
- [Help Center](https://docs.sourcepoint.com/hc/en-us)
- [Sourcepoint Public API Hub](https://sourcepoint-public-api.readme.io/reference)
- [Consent Management Platform](https://sourcepoint.com/cmp-2/)
- [Diagnose - Compliance Monitoring](https://sourcepoint.com/diagnose/)
- [DSAR Handling](https://sourcepoint.com/dsar/)
- [Marketing Preferences](https://sourcepoint.com/marketing-preferences/)
- [Universal Consent & Preferences](https://sourcepoint.com/universal-consent-and-preferences)
- [Privacy Lens](https://sourcepoint.com/privacy-lens/)
- [CMP for OTT / CTV](https://sourcepoint.com/ott-ctv/)
- [CMP for Mobile Apps](https://sourcepoint.com/cmp-for-mobile-apps/)
- [GDPR Compliance](https://sourcepoint.com/gdpr-compliance/)
- [CCPA Compliance](https://sourcepoint.com/ccpa-compliance/)
- [Pricing](https://hs.sourcepoint.com/pricing)
- [GitHub Organization](https://github.com/SourcePointUSA)
- [LinkedIn](https://www.linkedin.com/company/sourcepoint)
- [Blog](https://www.sourcepoint.com/blog/)
- [News](https://www.sourcepoint.com/news/)

## SDKs and Plugins

| SDK | Description |
|-----|-------------|
| [iOS CMP SDK](https://github.com/SourcePointUSA/ios-cmp-app) | Swift `ConsentViewController` distributed via CocoaPods, Carthage, Swift Package Manager, and XCFramework. |
| [Android CMP SDK](https://github.com/SourcePointUSA/android-cmp-app) | Kotlin `com.sourcepoint.cmplibrary:cmplibrary` published to Maven Central. |
| [React Native CMP](https://github.com/SourcePointUSA/react-native-sourcepoint-cmp) | `@sourcepoint/react-native-cmp` bridge to the native iOS and Android SDKs. |
| [Unity SDK](https://github.com/SourcePointUSA/unity-sdk) | C# plug-and-play CMP for Unity targeting iOS and Android builds. |
| [Roku SDK](https://github.com/SourcePointUSA/sp-roku-sdk) | BrighterScript SDK for Roku channels. |
| [HTML5 OTT SDK](https://github.com/SourcePointUSA/SP_HTML5_OTT) | HTML5 SDK for OTT and CTV web environments. |
| [Mobile Core](https://github.com/SourcePointUSA/mobile-core) | Objective-C network and data layer shared across native mobile SDKs. |
| [Diagnose SDK](https://github.com/SourcePointUSA/diagnose-sdk) | Swift SDK for the Diagnose compliance monitoring product. |
| [ES3 QR SDK](https://github.com/SourcePointUSA/es3-QR-SDK-develop) | JavaScript QR-code SDK for CTV authenticated consent flows. |
| [WordPress Plugin](https://github.com/SourcePointUSA/sp-wordpress-plugin) | Sourcepoint plugin for WordPress sites. |
| [Magento Plugin](https://github.com/SourcePointUSA/sp-magento-plugin) | Sourcepoint plugin for Magento storefronts. |
| [GTM GCM Template](https://github.com/SourcePointUSA/GTM-GCM-Template) | Google Tag Manager template for Google Consent Mode integration. |

## Features

| Name | Description |
|------|-------------|
| Multi-Campaign CMP | Multi-campaign Consent Management Platform across web, AMP, mobile, OTT, CTV, and gaming surfaces from a single portal. |
| IAB TCF v2.2 | Full TCF v2.2 support including Transaction Receipts, Legal Preferences, sensitive-data opt-in, and disclosed-vendor handling. |
| IAB GPP | IAB Global Privacy Platform encoding for U.S. National and per-state privacy sections (USNAT, CA, VA, CO, CT, UT and additional states). |
| Universal Consent & Preferences | Unified first-party preference profile across regulated consent and marketing preferences. |
| Authenticated Consent | Cross-device consent syncing tied to an authenticated end-user identifier with a hosted SDK test page. |
| Diagnose | Compliance monitoring of vendors, trackers, and data flows running on a property, with a dedicated Swift SDK. |
| DSAR Handling | Data subject access request workflows for fulfilment and erasure across data sources. |
| Privacy Lens | Privacy measurement and benchmarking across publisher properties. |
| Adblock Recovery | Publisher monetization heritage product for circumventing ad-blocking and recovering revenue. |
| Google Consent Mode 2.0 | First-class Google Consent Mode v2 integration plus a GTM template for tag-manager deployments. |
| Web Messaging Library | `cdn.privacy-mgmt.com/unified/wrapperMessagingWithoutDetection.js` with optional CNAME subdomain. |
| Public REST API | GDPR TCF, GDPR Standard, U.S. Multi-State Privacy, Global Enterprise, Preferences, and Reporting endpoints surfaced via the Sourcepoint Public API Hub. |

## Use Cases

| Name | Description |
|------|-------------|
| Publisher Multi-Regulation Consent | Global publishers manage GDPR TCF, CCPA / U.S. Multi-State Privacy, and LGPD consent across web, mobile, OTT, and CTV from one CMP. |
| Brand Universal Preferences | Brands consolidate marketing, legal, and regulatory preferences into a single first-party preference center across channels. |
| DSAR Fulfilment | Privacy and legal teams handle data subject access, correction, and erasure requests across the consent and preferences history. |
| Vendor and Tracker Audit | Privacy engineering teams use Diagnose to continuously scan properties for unauthorized vendors, trackers, and data flows. |
| CTV and Gaming Consent | OTT, CTV, and gaming publishers deliver native consent experiences on Roku, Unity, HTML5 OTT, and tvOS surfaces. |

## Integrations

| Name | Description |
|------|-------------|
| Google Consent Mode 2.0 | Native integration with Google Tag Manager and Google Consent Mode 2.0 for tag-level consent enforcement. |
| IAB Frameworks | Built on the IAB Transparency & Consent Framework v2.2 and IAB Global Privacy Platform standards. |
| Identity Providers | Authenticated consent ties consent profiles to an organization's identity provider for cross-device sync. |
| Tag Managers and CMSes | WordPress and Magento plugins plus a GTM template support common publisher and brand stacks. |
| Didomi | As of July 2025, Sourcepoint is part of Didomi (Marlin Equity Partners portfolio) — the two consent platforms are converging into a single global privacy technology offering. |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
