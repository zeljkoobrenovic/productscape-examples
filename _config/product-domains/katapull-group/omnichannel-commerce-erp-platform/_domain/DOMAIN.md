# Omnichannel Commerce ERP Platform

This domain models **Logic4** (logic4.nl), the all-in-one webshop and ERP software brand of the Dutch software group **Katapull** (katapull.nl). Logic4 describes itself as all-in-one webshop and business software for trading companies: webshop, product data (PIM), stock (WMS), order processing (OMS), CRM and administration in one central system, with implementation, support and free updates included.

Sibling Katapull brands are modeled as sibling domains in the `katapull-group` group:

| Brand | Domain | Relation to Logic4 |
|---|---|---|
| Vendit | `retail-pos-and-store-management-platform` | Retail POS/ERP; overlaps with Logic4's own cloud POS. No public Logic4-Vendit integration found. |
| Highbiza | `b2b-wholesale-ecommerce-platform` | B2B webshops; shares the Hengelo office with Logic4 from July 2026 (logic4.nl/over-logic4). No documented connector found. |
| EffectConnect | `marketplace-channel-integration-platform` | Sister company since 2021; **documented** Logic4 integration (order export with payment ledger/journal IDs, shipping-method and VAT mapping). |
| DeliveryMatch | `shipping-and-carrier-management-platform` | Shipping platform; no public direct Logic4 connector found (Logic4's documented carrier route is nShift). Modeled as a roadmap bridge. |
| Transus | `edi-and-b2b-document-exchange-platform` | EDI network; Logic4's Professional package lists EDI integrations, but no public Logic4-Transus connector found. Modeled as the natural EDI partner (inference). |
| Returnista | `ecommerce-returns-management-platform` | Returns portal; Returnista's partner page does not list Logic4. Modeled as a roadmap bridge (inference). |

Picqer (WMS, acquisition announced October 2026) is positioned by Katapull as a step-up for Logic4 customers needing deeper warehouse management; it is not in the requested brand list and has no sibling domain here.

## Domain boundary

**Core scope** - software used by mid-sized non-food trading companies (wholesale, retail, e-tail, office supplies; B2B and B2C) to run *Buy -> Store -> Sell on every channel -> Fulfil -> Invoice -> Steer*:

- Webshop (webshop Next, multi-shop, B2B portal, CMS, SEO), checkout and payment plugins.
- Cloud POS for multi-branch retail.
- PIM, supplier article import, pricing and price agreements.
- Order management (quote to invoice), CRM, returns and service.
- Inventory, warehouse app (scanner picking), purchasing, shipping connectors, route planning.
- Accounting with multi-administration, management information.
- Platform: tenancy and permissions, public API and Katapull bridges, migration, workflow automation.

**Adjacent (light):** marketplace middleware, EDI networks, carrier platforms, returns portals and advanced WMS - provided by Katapull siblings or partners and modeled only as connectors.

**Excluded:** manufacturing ERP, food retail, the sibling brands' own products.

## Value exchange

The trading company pays a monthly subscription by package (Smart from EUR 499/month incl. 3 users; Business from EUR 999/month adding accounting and multiple webshops; Professional and Premium on request adding multi-warehouse, EDI/marketplace integrations, workflow automation, SLA). Its staff use the system; its customers use the webshops and portals. The compounding asset is one shared model of items, prices, orders, stock and ledger.

## Strategic spine

- **Year 1 - One commerce core in the Katapull hub.** Reliable all-in-one core; standard bridges to EffectConnect, Picqer and DeliveryMatch; real-time stock events.
- **Year 3 - Automated trading operations.** Workflow automation, assisted purchasing and content, EDI and Peppol e-invoicing by default.
- **Year 5 - Network commerce.** Logic4 as the ERP node of a connected Katapull network with suppliers, channels, carriers and returns; ready for agentic buying.

## Sources (facts)

- logic4.nl home: module list, target branches, 4.5/5 Google rating, move to Hengelo.
- logic4.nl/over-logic4: founded 2003 (roots 1998), accounting 2006, BE/DE 2009, new webshop platform 2015, refocus 2017, Nedvest 2019, CEO Daniel Ruff 2020, Katapull March 2025, EffectConnect sister since 2021, Hengelo office shared with Highbiza from July 2026.
- logic4.nl/prijzen: packages and prices.
- logic4.nl/oplossingen/webshop-software: 500+ webshops, ~20 function modules.
- logic4.nl/oplossingen/erp-software/voorraadbeheer-software: WMS scope.
- logic4.nl/oplossingen/erp-software/multi-filiaal-met-cloud-kassa: multi-branch POS model.
- logic4.nl/branches/groothandel: wholesale features.
- katapull.nl (group source; unreachable to automated fetch during research).
- Dutch IT Channel: Katapull launch (2025-03-31, five companies: Logic4, DeliveryMatch, EffectConnect, Highbiza, Vendit); Returnista acquisition (2026-02-16).
- Dealroom and Quasa: Picqer acquisition (announced 2026-10-07), Picqer as WMS step-up for Logic4 customers; CEO Gino Keijzer.
- effectconnect.com/en/knowledge/logic4: Logic4 order export configuration.
- pay.nl/en/plug-ins/logic4: payment plugin; nshift.com/partners/logic4-b-v: carrier partner.
- speakerdeck ToolMax deck (sponsored, April 2025): 215,000+ items, ~1,300 orders/day, +10% revenue 2024.
- Competitors: lightspeedhq.com FY2026 results; jtl-software.com; exact.com; afas.nl; odoo.com; shopify.com; Microsoft Business Central.

## Assumptions and inferences

- **All KPI current and target values are modeled seed values** for a representative Logic4 customer, except the 4.5 Google rating.
- Brick architecture (modules, layers, stores, event bus) is an inferred logical decomposition of the published functionality, not Logic4's actual implementation.
- Bridges to DeliveryMatch, Transus, Returnista and Picqer are roadmap inferences from group positioning; only EffectConnect, Pay. and nShift integrations are documented publicly.
- Transus's membership of Katapull comes from search coverage and the workflow brief; the launch article lists five founding companies without Transus.
- Residuality stressors marked `candidate` are plausible scenarios, not announced changes.

## Open questions

- Logic4 customer and user counts (not published).
- How Katapull will position Logic4 POS versus Vendit, and Logic4 webshop B2B versus Highbiza.
- Whether and when standard Logic4 connectors to DeliveryMatch, Transus, Returnista and Picqer will ship.
- Conflicting secondary dates for the EffectConnect combination (2021 per Logic4 and PitchBook; June 2022 per CB Insights).
