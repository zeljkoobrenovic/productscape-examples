# EDI and B2B Document Exchange Platform

Product domain for **Transus**, the EDI (electronic data interchange) and e-invoicing
brand of the Dutch software group **Katapull** (Katapull Commerce Hub). Domain ID
`edi-and-b2b-document-exchange-platform`, group `katapull-group`. Researched 2026-10-30.

## What Transus is (sourced facts)

- EDI and e-invoicing platform that connects retailers, suppliers and logistics partners;
  tagline "Digital trade. Made easy." ([home](https://www.transus.com/en/), [about](https://www.transus.com/en/about-us/))
- States **100,000+ connected trading partners** in **40+ countries**, simple connections often live
  **within 24 hours**, **100+ available report formats**, **75+ IT, ERP and WMS partners**, "95% fewer
  repetitive manual tasks" (marketing claims; [home](https://www.transus.com/en/), [retailers](https://www.transus.com/en/retailers/)).
- Documents: ORDERS, ORDRSP, DESADV, INVOIC, inventory and price messages; standards EDIFACT, UBL,
  XML/CSV in-house formats ([what is EDI](https://www.transus.com/en/edi/what-is-edi/)).
- Over 20 years in business ("nearly 25 years"); offices in **Amersfoort (HQ, Databankweg 20)**, **Antwerp**
  and **Dusseldorf**; support in Dutch, German, English ([about](https://www.transus.com/en/about-us/), [partners](https://www.transus.com/en/partners/)).
- Pricing: flat fee, unlimited messages and partners. **Basic** (web EDI portal) from EUR 79/month annual
  (EUR 99 monthly); **Plus** (SSCC labels, transport configuration, link with administration package) from
  EUR 149/month annual (EUR 189 monthly); **Premium** on request (premium support, ERP/WMS API,
  certified-partner connection, invoice archive) ([prices](https://www.transus.com/en/prices/)).
- **Traci AI**: AI agent that recognises and links trading documents to connect partners without manual
  mapping ([Traci AI](https://www.transus.com/en/traci-ai/)).
- **E-invoicing**: XRechnung, ZUGFeRD and Peppol on EN 16931, with partner **Tickstar**; German send
  obligation from 2027 (turnover > EUR 800,000) and 2028 (all) ([news](https://www.transus.com/en/about-us/news/e-invoicing-germany-mandatory-from-2027/)).
- **Security**: ISO/IEC 27001:2022, encryption in transport (TLS/AS2/SFTP), data centres Frankfurt with DR in
  Amsterdam, annual pentest, incident response; NIS2 information pack for customers ([news](https://www.transus.com/en/about-us/news/ready-for-the-cybersecurity-law/)).
- **SSCC label service** accepted by Hornbach; validation blocks erroneous messages with plain-language
  alerts; trading partners can view message status even if not customers ([Hornbach news](https://www.transus.com/en/about-us/news/transus-meets-hornbachs-requirement-with-edi-and-sscc-label-service/)).
- **VMI** used by Henri van de Bilt for Albert Heijn ([case](https://www.transus.com/en/about-us/customer-cases/henri-van-de-bilt/)).
  Other cases: bol.com, Anova Seafood, Artiteq, Diversi Foods, Leev, Patisserie Unique, Veritas
  ([cases](https://www.transus.com/en/about-us/customer-cases/), [Anova](https://www.transus.com/en/about-us/customer-cases/anova-seafood/), [Katapull Transus page](https://katapull.nl/transus/)).
- ERP partners shown: AFAS (via Ecobit), Exact, KING, Odoo, SAP, Unit4, Picqer; Business Central app NC365 by
  NAS conception ([partners](https://www.transus.com/en/partners/), [Ecobit](https://www.transus.com/en/partners/ecobit/)).
- **Katapull**: Transus states it is part of the Katapull Commerce Hub of eight specialised companies.
  Katapull lists Highbiza, Vendit, DeliveryMatch, EffectConnect, Logic4, Transus, Returnista and Picqer;
  175+ specialists, 4,500+ customers in 40+ countries, 27,500+ users, 140+ marketplaces
  ([katapull.nl](https://katapull.nl/), [over Katapull](https://katapull.nl/over-katapull/)).
  Jasper de Vreugt from parent Katapull was interim MD from February 2026; **Arjan Sloot** became MD on
  30 June 2026 ([news](https://www.transus.com/en/about-us/news/arjan-sloot-new-managing-director-at-transus/)).

katapull.nl was reachable by direct HTTP fetch during research (some automated fetchers failed).

## Sibling Katapull domains in this group

| Brand | Domain ID |
|---|---|
| Vendit | `retail-pos-and-store-management-platform` |
| Logic4 | `omnichannel-commerce-erp-platform` |
| Highbiza | `b2b-wholesale-ecommerce-platform` |
| EffectConnect | `marketplace-channel-integration-platform` |
| DeliveryMatch | `shipping-and-carrier-management-platform` |
| Returnista | `ecommerce-returns-management-platform` |

Picqer (WMS, acquired by Katapull in 2026) is not modelled as a domain here.

**Integration evidence**: Transus has a partner page for each sibling (Logic4, Vendit, Highbiza,
EffectConnect, DeliveryMatch, Returnista, Picqer), categorised "Commerce Hub", each stating the company
"can be connected with Transus" ([partners](https://www.transus.com/en/partners/), e.g.
[Logic4](https://www.transus.com/en/partners/logic4/), [Vendit](https://www.transus.com/en/partners/vendit/)).
Logic4 and EffectConnect merged in 2022 (secondary sources) and EffectConnect publishes a Logic4 integration
([EffectConnect Logic4](https://www.effectconnect.com/en/logic4-integration)). The depth of each
Transus-sibling connector is **not** publicly documented; the `kpch` brick models it as an assumption.

## Scope

- **Core**: EDI network and partner directory, onboarding, translation/validation/routing, order,
  despatch/SSCC, e-invoicing, archive, VMI, web portal, monitoring, ERP/WMS integration, Traci AI.
- **Adjacent**: Katapull sibling connectors, partner programme, security assurance.
- **Excluded**: ERP functionality itself (Logic4/Vendit domains), shipping (DeliveryMatch), marketplaces
  (EffectConnect), payments, customs.

## Value exchange

Suppliers (mostly) pay a flat subscription; retailers drive adoption through EDI mandates and benefit from
announced deliveries and matching invoices; ERP partners resell and implement; Transus earns recurring
revenue and grows the network effect.

## Assumptions and inferences

- Approximate Katapull acquisition timing (around early 2026) is **inferred** from the interim MD note; no
  acquisition announcement was found.
- Brick decomposition, modules, data stores and retention values marked "(assumption)" are architectural
  inferences, not Transus disclosures. AI model provider is unknown.
- KPI `currentValue`s and `targetValue`s in customer pyramids are **illustrative baselines**, not measured or
  published figures (top nodes are labelled "Modeled seed value for a representative account").
- Personas are inferred from Transus audience pages (retailers, suppliers, partners) and cases.
- Transus E-Invoicing and VMI are modelled as separate products for clarity; Transus sells them inside its plans.

## Open questions

- Exact acquisition date and deal terms; Transus customer count and revenue.
- Which sibling connectors are productised vs. project-based.
- Traci AI maturity and pricing.

## Competition

SPS Commerce (incl. TIE Kinetix since 2023), TrueCommerce, ecosio, EDICOM, Banqup Group. See
`business/competition.json`.

## App store channels (added 2026-11-04)

Two Microsoft AppSource apps for Business Central connect to Transus. Both are published by
partners, not by Transus:
- NC365 Transus EDI connect by NAS conception
  (https://www.transus.com/en/this-is-transus/news/transus-edi-interface-to-microsoft-business-central).
- Transus API Connector by Micro Apps
  (https://marketplace.microsoft.com/product/web-apps/PUBID.microapps|AID.transus_edi_connector|PAPPID.08ca7dc9-163f-441f-8a1e-3cdd846f4585).

No Transus app was found in the Shopify App Store.
