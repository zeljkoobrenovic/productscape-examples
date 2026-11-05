# Warehouse Management & Fulfilment Platform

This domain models **Picqer** (picqer.com / picqer.nl), the Dutch cloud warehouse management system (WMS) for online stores, wholesalers and fulfilment companies that run their own warehouse. On 7 October 2026 the Dutch software group **Katapull** (katapull.nl) announced it had acquired Picqer to add warehouse management, order processing and inventory to its Commerce Hub.

## Katapull group context

Katapull presents a "Commerce Hub" of specialised software companies serving the operational e-commerce chain. It reports group figures of 175+ specialists, 4,500+ customers in 40+ countries, 27,500+ users and 140+ marketplaces (group figures, not Picqer figures). CEO: Gino Keijzer. The other brands are modeled as sibling domains in the `katapull-group` group:

| Brand | Sibling domain |
|---|---|
| Vendit (retail/POS) | `retail-pos-and-store-management-platform` |
| Logic4 (commerce platform / ERP) | `omnichannel-commerce-erp-platform` |
| Highbiza (custom B2B webshops) | `b2b-wholesale-ecommerce-platform` |
| EffectConnect (marketplace integration) | `marketplace-channel-integration-platform` |
| DeliveryMatch (shipping and carrier management) | `shipping-and-carrier-management-platform` |
| Transus (EDI) | `edi-and-b2b-document-exchange-platform` |
| Returnista (returns) | `ecommerce-returns-management-platform` |

### Integrations with siblings

- **Facts (evidenced):**
  - **DeliveryMatch.** Picqer's integrations page lists DeliveryMatch ("Integration by DeliveryMatch"). DeliveryMatch publishes a Picqer integration page: an API link where shipments created in Picqer get DeliveryMatch carrier selection and labels.
  - **Returnista.** The integration is native and runs both ways. Picqer's blog describes Returnista retrieving orders from Picqer and pre-registering returns, which are then scanned and restocked in Picqer.
  - **Logic4.** Katapull's acquisition release positions Picqer as the next step for Logic4 customers whose warehouse needs go beyond Logic4's functionality. This is a positioning statement; no Logic4–Picqer connector was found.
  - **Transus and Vendit.** Both publish Picqer partner pages inside their Katapull partner sets. The pages are generic and give no technical flow.
  - **Co-founder statement.** At the acquisition, co-founder Casper Bakker mentioned "even better integration" with long-standing partners Returnista and DeliveryMatch.
- **Assumptions:**
  - The Logic4 bridge (orders, products and stock) and the Transus EDI flows (retailer orders, dispatch advice).
  - Vendit store-stock exchange.
  - Any EffectConnect or Highbiza connection; none was found.

All sibling connections are modeled in the `ktpl` brick (Katapull Commerce Hub Bridges) and the `ptnr` persona.

## Domain boundary

**Core scope:** software that runs the inside of an e-commerce warehouse.

- Store and marketplace connectors (Picqer-built connectors for Magento, Shopify, WooCommerce, Lightspeed, Shopware, CCV Shop and bol). Multi-channel order management with backorders, partial deliveries, priorities and pausing. A B2B customer portal.
- Product master and barcodes (GS1, DataMatrix, QR). An inventory ledger that records every change. Multiple warehouses, locations, containers and A/B classification. Replenishment, cycle counting, and batch and best-before traceability.
- Purchase advice, purchase orders, and receipts with put-away.
- Batch, singles and bulk picking on optimal routes. A packing station with scan verification and packaging advice.
- Shipping integrations (10+ carriers and shipping platforms) with automatic labels and printing. Returns processing.
- A rules engine, the mobile app for handhelds, comments, tasks and notifications, and reports.
- Picqer Fulfilment: client separation, a branded client portal, packaging cost pass-through, and client invoicing (in development).
- Hardware and robotics connectivity via intralogistics partners. The public REST API and webhooks.

**Adjacent (light):** carrier selection and rate management (DeliveryMatch and other shipping platforms), return portals (Returnista and others), advanced forecasting (Optiply, Rewize), accounting (Exact Online via xCore), ERP (Logic4 and others).

**Excluded:** assembly and manufacturing (Picqer says products ship "the same way you received them"). Also excluded: transport execution, webshop front-ends, marketplace listing management, and the physical intralogistics hardware itself.

## Value exchange

Webshops, wholesalers and fulfilment companies pay a monthly plan that includes a number of orders, plus a fee per extra order. Users, stores and support are unlimited.

- **Online-store plans:** Team (EUR 379), Business (EUR 825), Premium (EUR 1,349), Premium+ (EUR 2,475) and Enterprise (EUR 5,500).
- **Fulfilment plans:** Fulfilment (EUR 825), Plus (EUR 2,475), Next (EUR 3,850) and Max (on request).

Fulfilment clients use the portal at no charge to Picqer; the 3PL pays. Partners integrate to reach shared customers. Value repeats for two reasons: every order adds to Picqer's revenue, and every account builds up locations, rules, stock history and integrations that make switching costly.

## Strategic spine

- **Year 1: calm, peak-proof and billable.** Effortless self-service onboarding, peak-proof execution, batch traceability and client invoicing for 3PLs, a reliable API, and the first productised hub bridges (DeliveryMatch, Returnista, Logic4).
- **Year 3: productive teams and a hub-native core.** Rules templates, interleaved floor tasks, standard mechanisation adapters, client self-service and SLA dashboards, and Transus/Vendit/EffectConnect flows.
- **Year 5: a self-steering, orchestrated warehouse.** Workload and stock forecasting, people and robots orchestrated together, capacity shared with DeliveryMatch for promise dates, and fulfilment networks.

## Personas (customers.json)

| Group | Persona |
|---|---|
| Online Stores with Their Own Warehouse | `wsop` Webshop Owner Running Their Own Warehouse; `whmg` Warehouse Manager at a Scaling Brand or Wholesaler |
| Fulfilment Companies and Their Clients | `fulf` Fulfilment (3PL) Company Owner or Operations Lead; `fcli` Webshop Brand Outsourcing to a Picqer-Run Fulfilment Company |
| Warehouse Floor | `pick` Order Picker and Packer |
| Ecosystem and Commerce Hub Partners | `ptnr` Integration, Hardware and Commerce Hub Partner |

## Sources (facts)

- https://picqer.com/en : positioning ("warehouse software for online stores and fulfilment"), "process orders 5x faster" (vendor claim), customers from 25 to 5,000+ orders a day, 14-day trial.
- https://picqer.com/en/pricing : plans and per-order fees as above. Ideal size is 25 to 5,000 orders a day; no assemblies. Setup takes one day, and warehouses typically need 1–2 weeks of preparation. Card or SEPA payment. The page lists the integrated shipping providers as 10+.
- https://picqer.com/en/team : started November 2012 after seven years building custom web applications. Claims "10% of all online orders in the Netherlands are processed with Picqer". No external investors and profitable (before the acquisition). Co-founders Casper and Stephan.
- https://picqer.com/en/fulfilment : 80+ fulfilment companies; client separation; portal; packaging cost pass-through; batch and best-before traceability (new); client invoicing (in development); market-leader claim in the Netherlands.
- https://picqer.com/en/integrations : about 50 listed integrations (stores, carriers and shipping platforms including DeliveryMatch, Sendcloud, MyParcel, PostNL, DHL eCommerce, GLS, DPD and MontaShip; support tools; Returnista, Returnless and ReturnGO; Optiply; Exact Online via xCore; Itsperfect; Rewize; and others).
- https://picqer.com/en/features/picking-shipping , /inventory-management , /purchasing , /rules , /picqer-app , /api , /multi-channel-orders : feature scope used for the bricks. The picking page carries the vendor claims "walk 60-80% of the workday" and "60-70% singles".
- https://picqer.com/en/hardware-robots : the three-step hardware path, including Kardex and AutoStore.
- https://picqer.com/en/cases , /cases/vasco-fulfilment , /cases/alleeninkt : testimonials. VASCO has 12 employees and 50 clients. Alleeninkt reached 1 million orders by 2025.
- https://picqer.com/en/blog/changelog-20261029 : comment reactions and photos, the "For you" inbox, user rights tools, picklist splitting, GS1/DataMatrix/QR scanning, and portal concept orders.
- https://picqer.com/en/blog/new-returnista-integration : the Returnista flow.
- https://katapull.nl/katapull-breidt-commerce-hub-uit-met-overname-van-picqer/ (7 Oct 2026) and https://dealroom.co/news/161390-katapull-buys-wms-provider-picqer-to-fill-out-its-commerce-hub/ : the acquisition, the mid-market fit and the Logic4 positioning. Deal value was not disclosed ("miljoenendeal").
- https://www.deliverymatch.eu/integraties/picqer/ , https://www.transus.com/en/partners/picqer/ , https://www.vendit.nl/partners/picqer : sibling partner and integration pages.
- https://katapull.nl/over-katapull/ : group figures.
- Competitors: https://www.monta.nl/ and https://www.monta.nl/wms/ , https://www.goedgepickt.nl/ , https://www.wics.nl/ , https://www.shiphero.com/about-us , https://www.linnworks.com/about-us/ .

## Assumptions and inferences

- **All KPI current and target values are modeled seed values.** They are not Picqer-reported figures (each pyramid top says so). Exceptions: KPI names that cite a Picqer figure (e.g. 80+ fulfilment companies, about 50 integrations) use that figure only as a baseline.
- **Brick internals are inferred architecture**, derived from published features rather than documented implementation. This covers modules, stores, the event bus and the local print agent. Hosting location and database technology are not published; EU residency is assumed.
- **Vendor claims are labelled as such.** These include "5x faster", "10% of Dutch online orders", "market leader", the walking and singles percentages, and testimonial productivity quotes.
- **B2B portal.** The B2B customer portal and the Shopify app listing are described on Picqer pages, but their usage levels are unknown.
- **Revenue streams.** Hub bundles, partner programme fees and network services in the strategies are assumptions.
- **Persona baselines.** The portal-user, app-user and fulfilment-client counts in the `fcli`, `pick` and `ptnr` business pyramids are assumptions.
- **Competitors.** No business stats were found for Davanti-WICS. Linnworks, ShipHero and Monta stats are company-reported, with different scopes.

## Open questions

- Will Picqer's own shipping integrations be steered towards DeliveryMatch, and will they stay open to Sendcloud, MyParcel and others?
- When will a Logic4–Picqer connector ship, and how will Logic4's warehouse functions and Picqer be positioned by customer size?
- What is the Picqer customer count, revenue and headcount? Only the team page (about 30 people listed) and the claims above are public.
- What will client invoicing in Picqer Fulfilment cost, and when will it be released?
- How far will Picqer expand beyond the Netherlands and Belgium?

## App store channels (added 2026-11-04)

- Shopify App Store listing "Picqer | Pick & ship faster" (https://apps.shopify.com/picqer). It has a
  14-day trial and syncs orders, shipping status, tracking and stock. It needs unique SKUs and
  manages one Shopify location (https://picqer.com/en/support/articles/shopify-integration).
- The Picqer App is available only through the Apple App Store and Google Play
  (https://picqer.com/en/support/topics/app, https://apps.apple.com/us/app/picqer/id1600064988).
  Picqer Classic remains iOS-only and receives no further updates.
