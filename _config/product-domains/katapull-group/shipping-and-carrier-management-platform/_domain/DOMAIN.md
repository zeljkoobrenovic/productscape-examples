# Shipping and Carrier Management Platform

This domain models **DeliveryMatch** (deliverymatch.eu), the logistics brand of the Dutch software group **Katapull** (katapull.nl). DeliveryMatch describes itself as "het order- en verzendplatform" - multi-carrier shipping software that connects webshops, ERP and WMS systems with 200+ carriers and optimises the shipping process "from check-out to delivery and return".

## Katapull group context

Katapull presents a "Commerce Hub" of eight specialised labels. The other brands are modeled as sibling domains in the `katapull-group` group:

| Brand | Sibling domain |
|---|---|
| Vendit (retail/POS) | `retail-pos-and-store-management-platform` |
| Logic4 (ERP for trading companies) | `omnichannel-commerce-erp-platform` |
| Highbiza (custom B2B webshops) | `b2b-wholesale-ecommerce-platform` |
| EffectConnect (marketplace integration) | `marketplace-channel-integration-platform` |
| Transus (EDI) | `edi-and-b2b-document-exchange-platform` |
| Returnista (returns) | `ecommerce-returns-management-platform` |

Picqer (WMS), acquired by Katapull in October 2026, is not modeled as a separate domain here.

**Evidence of real integrations between siblings (facts):** deliverymatch.eu publishes integration pages for Logic4, Vendit, EffectConnect, Highbiza, Transus, Returnista and Picqer. The Logic4, Vendit, EffectConnect and Highbiza pages each state the product "is coupled with the DeliveryMatch software" and is "partner of DeliveryMatch and part of the Katapull Group". The Transus page describes Transus EDI exchanging orders, packing slips and invoices while DeliveryMatch handles carrier selection and labels; the Returnista page describes Returnista structuring returns while DeliveryMatch handles return transport. Picqer's co-founder mentioned tighter integration with DeliveryMatch and Returnista at the acquisition. DeliveryMatch and Vendit share the address 's-Gravenweg 433, Rotterdam (Katapull site). These are modeled in the `ktpl` brick (Katapull Commerce Hub Bridges) and the `swpt` persona.

## Domain boundary

**Core scope** - software that turns orders into delivered (and returned) shipments:

- Order intake from 40+ webshop systems, marketplaces and 75+ ERP/WMS/planning systems; public API and partner programme.
- Dynamic, stock-aware checkout with delivery days, pickup points, price and CO2.
- Shipping rules, automatic carrier/service selection, purchase and sales rate calculation.
- Booking and labels with 200+ carriers (parcel, pallet, freight), transport documents (CMR, customs, ADR), scan-to-ship and print management.
- Multi-warehouse routing and external fulfilment / dropshipping.
- Tracking, branded e-mail/SMS/WhatsApp communication, exception management and carrier performance.
- Returns portal and return transport.
- Carrier Invoice Control (freight audit), dashboards/KPI reports and CO2 calculation.

**Adjacent (light):** returns handling beyond transport (Returnista), warehouse picking (Picqer, WMS partners), EDI trade documents (Transus).

**Excluded:** carriers' physical operations, warehouse management, ERP/finance, marketplace listing management (sibling domains).

## Value exchange

Shippers (webshops, omnichannel retailers, manufacturers, wholesalers), 3PLs and brokers pay for the platform (pricing not published; per-shipment components are an assumption). Recipients use checkout, tracking and returns for free via the merchant. Carriers and software partners integrate to gain reach. The compounding asset is the network of carrier and system connections plus each tenant's rules, rates and history, which make the promise, selection and freight audit better over time.

## Strategic spine

- **Year 1 - Zero-touch shipping and fast onboarding.** Automate order-to-label for every channel, scan-to-ship, client templates for 3PLs, bridges to all Katapull siblings including Picqer.
- **Year 3 - Shipping control layer.** Carrier Invoice Control, cost per customer, carrier scorecards and CO2 as standard; broker TMS; Commerce Hub co-selling.
- **Year 5 - Pull-driven logistics across the hub.** The checkout steers ship-from, carrier and delivery moment together across Katapull products and 3PL networks.

## Personas (customers.json)

`ecom` E-commerce Operations Manager, `whsl` Logistics Manager at a Manufacturer or Wholesaler, `tpls` Fulfilment and 3PL Operations Lead, `crbr` Carrier or Transport Broker Partner, `swpt` Software Integration Partner, `rcpt` Online Shopper and Parcel Recipient. Segments follow DeliveryMatch's own target groups (e-commerce & retail, fulfilment & 3PL, manufacturers & wholesalers, software & system providers, carriers & brokers).

## Sources (facts)

- https://www.deliverymatch.eu/ - 200+ connected carriers, 4,000+ users, 40+ webshop systems, 75+ ERP/WMS/planning systems; news on ISO 27001 (June 2026), ICT & Logistiek 2026 with Monta WMS, idyn webinar for Dynamics 365 Business Central partners.
- https://www.deliverymatch.eu/over-ons/ - timeline: research 2009-2012 by founder Dr. Roland Slegers; platform development from 2013 under CTO Rick van der Mark; company founded 2013 with the vision "the Last Mile starts with the First Click"; first customer Flinders (2014); 100th carrier (2016); first office Utrecht (2018); 10 million shipments (2019); first BE/DE/FR/UK customers (2020); 200th integrated system (2021); Emerce no. 1 shipping software (2022) and best shipping software five years in a row (2026); new platform (2024); joined Katapull (dated 1 Nov 2024 on the site); Tom van Dam succeeded Roland Slegers as managing director (2025); moved to a larger Rotterdam office (2025); Nederlandse Logistiek Prijs 2025; ISO 27001 (2026).
- https://www.deliverymatch.eu/platform/ and sub-pages (transportmanagement, dynamische-verzendopties, verzendproces-automatiseren, calculatie-op-basis-van-voorraadbeschikbaarheid, retourenmanagement, automatiseren-extern-fulfillment, dashboard, gepersonaliseerde-klantcommunicatie) - feature scope used for bricks.
- https://www.deliverymatch.eu/integraties/ (350+ standard integrations), /integraties/webshop/, /integraties/erp/, /integraties/wms/ (implementation within two months), /integraties/marketplaces/ and sitemap integration pages (carriers, ERPs, WMSs, Katapull siblings).
- https://www.deliverymatch.eu/doelgroepen/ segment pages (fulfillment-3pl, fabrikanten-groothandels, software-systeem-providers with 50+ fulfilment connections, vervoerders-brokers) and customer pages (e.g. Flinders, Kamera Express, Dartshopper, Deli Home, FOX Global Warehousing, Movianto, KET Marine, Moonen Packaging).
- https://apps.shopify.com/deliverymatch - Shopify app launched 27 Aug 2019, listed as free, developer address 's-Gravenweg 435 Rotterdam.
- https://katapull.nl/ , https://katapull.nl/deliverymatch/ (180+ carriers, freight audit module, fixed project manager, Emerce Top 100), https://katapull.nl/over-katapull/ (group: 175+ specialists, 4,500+ customers in 40+ countries, 27,500+ users, 140+ marketplaces).
- https://katapull.nl/katapull-breidt-commerce-hub-uit-met-overname-van-picqer/ and https://dealroom.co/news/161390-katapull-buys-wms-provider-picqer-to-fill-out-its-commerce-hub/ - Picqer acquisition (October 2026), CEO Gino Keijzer.
- Competitors: https://www.sendcloud.com/about-us/ , https://nshift.com/about , https://wuunder.com/en , https://www.myparcel.com/nl-NL/ , https://shipitsmarter.net/ , https://sendy.nl/ .

## Assumptions and inferences

- **All KPI current/target values are modeled seed values**, not DeliveryMatch-reported figures (stated in each pyramid top).
- Carrier count differs by source (200+ on deliverymatch.eu, 180+ on katapull.nl); the model uses DeliveryMatch's own figure with the caveat.
- The Katapull join date is taken from DeliveryMatch's timeline (1 Nov 2024); a third-party report referenced a March 2025 announcement. Treat the exact date as approximate.
- Pricing (subscription, per-shipment fees, module add-ons) is not published; revenue streams in strategies are labelled as assumptions where not sourced.
- Brick internals (modules, stores, event bus) are inferred architecture from published features, not documented implementation.
- The 92% / 93% / 84% consumer statistics are vendor-cited research without a named original study.
- nShift HQ (Oslo) is an assumption from company history; Wuunder, MyParcel and Viya have no sourced business stats in the model.

## Open questions

- How DeliveryMatch returns and Returnista are divided commercially for shared customers.
- Whether Picqer's built-in shipping will be steered towards DeliveryMatch.
- Share of revenue from merchants vs 3PLs vs brokers and partners.
