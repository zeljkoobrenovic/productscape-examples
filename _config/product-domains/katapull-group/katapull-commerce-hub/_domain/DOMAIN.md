# Katapull Commerce Hub (aggregated productscape)

Domain ID `katapull-commerce-hub`, group `katapull-group`. Authored 2026-11-04.

## Purpose and scope

This productscape is built from the eight Katapull platform productscapes in this group.
It does not repeat their detail. It answers one question: **which customers do the Katapull
platforms share, and which platforms does each one use for which job?**

| Brand | Platform productscape | Brick here |
|---|---|---|
| Highbiza | `b2b-wholesale-ecommerce-platform` | `hbza` |
| EffectConnect | `marketplace-channel-integration-platform` | `efco` |
| Vendit | `retail-pos-and-store-management-platform` | `vndt` |
| Logic4 | `omnichannel-commerce-erp-platform` | `lgc4` |
| Transus | `edi-and-b2b-document-exchange-platform` | `trns` |
| Picqer | `warehouse-management-and-fulfilment-platform` | `pcqr` |
| DeliveryMatch | `shipping-and-carrier-management-platform` | `dlvm` |
| Returnista | `ecommerce-returns-management-platform` | `rtns` |

- **In scope:** shared customer personas (each one merges the matching personas of several
  platforms), their cross-platform jobs, one high-level brick per platform, two group-level
  hub bricks, cross-platform streams, the integrations between platforms, and customer relations.
- **Competition:** 14 players that compete with the hub as a whole. These are suite, stack or
  app-ecosystem vendors that overlap two or more Katapull platforms, plus ChannelEngine as a benchmark.
  Their stats and links are copied from the sibling competition files. The role and the overlap
  are this productscape's own analysis.
- **Data assets:** 15 hub-level business objects in four groups:
  - Commerce master data
  - Orders, shipments and returns
  - Trade documents and money
  - Hub connectivity and shared customer data

  Each asset names the platforms that hold a copy and the matching platform asset id, and marks
  whether that copy is the system of record, read-write or read-only. Stores are summarised as
  one per brand plus four inferred hub stores. Residency is an assumption except for Transus.
- **Out of scope:** platform internals (see each platform productscape) and residuality,
  which is left as an empty scaffold on purpose.

## Brick map

- **Sell Across Channels:** Highbiza (own webshops), EffectConnect (marketplaces), Vendit (stores).
- **Run the Trading Business:** Logic4 (commerce ERP), Transus (EDI and e-invoicing).
- **Fulfil and Deliver:** Picqer (warehouse and 3PL), DeliveryMatch (shipping), Returnista (returns).
- **Commerce Hub Foundation:** `hubc` Commerce Hub Bridges and Connection Registry, and `hubv` Shared
  Customer and Commerce Chain Insight. Both are **inferred** group-level bricks. Today the bridges
  live inside each brand.

Each platform brick has a workspace UI, an API, three summary capability services and a
"Commerce Hub Connectors" integration module. Brick dependencies between platforms carry an
evidence label in the description: **Documented**, **Partner listing** or **Inferred**.
These labels come from the integration evidence in the sibling `DOMAIN.md` files.

## Shared customers and the platforms they use

The matrix comes from the JTBD steps in `customers.json`. Each step lists the platform bricks it uses.

| Persona | Highbiza | EffectConnect | Vendit | Logic4 | Transus | Picqer | DeliveryMatch | Returnista | Hub |
|---|---|---|---|---|---|---|---|---|---|
| Trading Company Owner-Director (`twow`) | x | x | x | x |  | x | x | x | x |
| E-commerce and Channel Manager (`ecmm`) | x | x | x | x |  |  | x | x | x |
| Warehouse and Logistics Operations Lead (`opsl`) | x | x | x | x |  | x | x | x |  |
| IT, ERP and Integration Lead (`itin`) | x | x | x | x | x |  | x |  | x |
| Financial Controller (`fico`) |  | x |  | x | x |  | x | x | x |
| Specialty Retailer and Store Chain Manager (`rtlr`) | x | x | x |  | x |  | x | x |  |
| Supplier and Brand Selling to Retail (`supb`) | x | x |  | x | x | x | x | x |  |
| Fulfilment and 3PL Company (`tpls`) |  | x |  |  |  | x | x | x | x |
| Webshop Brand Outsourcing Fulfilment (`fcln`) | x | x |  |  |  | x | x | x |  |
| Software and Implementation Partner (`sipt`) |  | x |  |  | x | x | x |  | x |
| Online and In-Store Shopper (`shpr`) | x | x | x |  |  |  | x | x |  |
| Professional Trade Buyer (`trdb`) | x |  |  | x | x |  | x |  |  |
| Shopify-Based Merchant (`shpm`) |  | x |  |  |  | x | x | x | x |

Source personas merged into each shared persona:

- `twow`: Highbiza ownr, Logic4 ownr, EffectConnect mown, Returnista eown, Picqer wsop.
- `ecmm`: Highbiza ecom, Logic4 ecom, EffectConnect mmgr, Returnista ecan, DeliveryMatch ecom.
- `opsl`: Picqer whmg, Logic4 whse, EffectConnect mops, Returnista rops, DeliveryMatch whsl.
- `itin`: Highbiza itop, Transus itmg, EffectConnect itld.
- `fico`: Logic4 fina, Transus sfin.
- `rtlr`: Vendit ownr, chnr and rsoh, Logic4 stor.
- `supb`: Transus sord, Vendit supl, EffectConnect brnd, DeliveryMatch whsl.
- `tpls`: Picqer fulf, DeliveryMatch tpls, Returnista fulp.
- `fcln`: Picqer fcli.
- `sipt`: EffectConnect sasp, DeliveryMatch swpt, Picqer ptnr, Transus impl.
- `shpr`: Highbiza cons, Returnista shpr, DeliveryMatch rcpt, Vendit shop.
- `trdb`: Highbiza pbuy, plus the accounts served by Logic4 b2bs and Transus retail buyers.
- `shpm`: the Shopify-store users of EffectConnect (Shopify plugin), Picqer (Shopify connector),
  DeliveryMatch (Shopify app since 2019) and Returnista (Shopify app since 2023). It is the
  only shared persona without a Katapull core system (Logic4, Vendit or Highbiza).

Personas that belong to only one platform are left out because they are not shared:
Vendit cash and wksp, Picqer pick, DeliveryMatch crbr, Transus rscm, Returnista cxmg and Logic4 purc.

Observations:

- **DeliveryMatch** shows up in every shared persona's jobs, and **EffectConnect** in all but one.
  These two are the connective tissue of the hub.
- The **3PL chain** (Picqer + DeliveryMatch + Returnista) is the most integrated combination
  for shared customers today.
- The **retail chain** is centred on Vendit, and its documented couplings are EffectConnect,
  DeliveryMatch, Transus and Highbiza.
- **Shopify** is a competitor and a host platform at the same time. It competes with Highbiza,
  Vendit and Logic4 for the store and the system of record. It hosts EffectConnect, Picqer,
  DeliveryMatch and Returnista, whose Shopify apps and connectors make Shopify merchants
  (`shpm`) a four-platform Katapull segment.
- **App stores** (deployment group "App Stores and Plugin Marketplaces"):
  - Shopify App Store: EffectConnect, Picqer, DeliveryMatch and Returnista.
  - Other webshop plugin marketplaces (Lightspeed, Magento, WooCommerce): EffectConnect and DeliveryMatch.
  - Apple App Store and Google Play: the Picqer App.
  - Microsoft AppSource: partner-published Business Central apps for Transus.
  - The EffectConnect App Store, the only app store a Katapull brand runs itself.
  - A web check in November 2026 found no app-store presence for Highbiza, Vendit or Logic4.
    Logic4's scanner app is not described as distributed through an app store.
  - The Picqer and Transus platform productscapes now carry the same channels.
- The most valuable gaps are **Logic4-Picqer**, **Logic4-Transus** and **returns to ERP/POS**.
  All three are inferred, not documented.

## Facts, assumptions and inference

- **Facts** (cited in `customers/insights.json`): group figures from katapull.nl (175+
  specialists, 4,500+ customers, 27,500+ users, 140+ marketplaces); brand join dates; and the
  integration pages of DeliveryMatch, Vendit, Transus, Highbiza, EffectConnect and Picqer.
- **Assumptions:** all KPI current and target values are modeled seed values, and each KPI
  description says so. Hub bundles and pricing are not published.
- **Inference:** the `hubc` and `hubv` bricks, the Logic4-Picqer, Logic4-Transus,
  Returnista-Logic4 and Transus-Picqer flows, and the platform module decomposition.

## Open questions

- How many of the 4,500+ customers use two or more Katapull platforms, and which pairs are most common?
- Will Katapull build a shared bridge or registry layer, or keep bridges inside each brand?
- How will the overlaps be positioned: Logic4 POS vs Vendit, Logic4 webshop vs Highbiza,
  DeliveryMatch returns vs Returnista, and Picqer shipping vs DeliveryMatch?

## Regeneration

The JSON was generated with a one-off script that reads the sibling productscapes and
copies their persona portraits and logos. To change the model, edit the JSON directly and run
`python3 productscapes.py validate katapull-commerce-hub --strict-ids`.
