# Retail POS and Store Management Platform

Product domain for **Vendit** (https://www.vendit.nl/), the Rotterdam-based brand of the
Dutch software group **Katapull** (https://katapull.nl/) that provides point-of-sale (POS),
stock, webshop and store-management software for specialty retailers, chains, wholesalers
with a counter and franchise formulas in the Netherlands and Belgium.

Researched 2026-10-30. katapull.nl and vendit.nl were readable with a plain HTTP client;
some news sites (Dutch IT Channel) blocked automated reads, so their content is taken from
search-result summaries and recorded as such.

## Scope

- **Core:** counter checkout and payments, receipts and day closing, store hardware,
  customer file and loyalty, quotes/customer orders/invoices, repair and workshop
  management, article master, pricing and purchase-price formulas, multi-location stock,
  stocktaking, purchasing and supplier connections, reporting dashboard, accounting
  export, tenant/user administration, onboarding, support.
- **Adjacent (modeled as connectors):** webshop (Vendit's own and connected Highbiza /
  WooCommerce shops), marketplaces via EffectConnect, shipping via DeliveryMatch,
  returns via Returnista, EDI via Transus.
- **Excluded:** the internals of sibling Katapull platforms, hospitality POS, warehouse
  management (Picqer, Logic4), payment processing itself.

Value exchange: retailers pay a monthly subscription per package/modules; Vendit supplies
software, hardware, setup, migration, training and support; shoppers and suppliers
benefit indirectly through correct stock, service and electronic ordering.

## Sibling domains in `katapull-group`

Katapull brands are modeled as sibling domains in this group:

| Brand | Domain ID |
|---|---|
| Vendit | `retail-pos-and-store-management-platform` (this domain) |
| Logic4 | `omnichannel-commerce-erp-platform` |
| Highbiza | `b2b-wholesale-ecommerce-platform` |
| EffectConnect | `marketplace-channel-integration-platform` |
| DeliveryMatch | `shipping-and-carrier-management-platform` |
| Transus | `edi-and-b2b-document-exchange-platform` |
| Returnista | `ecommerce-returns-management-platform` |

Integrations with siblings, with evidence level:

- **EffectConnect** — documented: Vendit marketplace module synchronises stock, lead time,
  prices and content to bol, Amazon, VidaXL, Beslist via EffectConnect and imports orders
  (https://www.vendit.nl/modules/marketplaces-module/). Brick `mrkt`.
- **DeliveryMatch** — documented: labels and shipment announcement from Vendit with
  DeliveryMatch (marketplaces page; partner page https://www.vendit.nl/partners/deliverymatch/). Brick `ship`.
- **Transus** — documented: "Transus EDI is gekoppeld met het Vendit Systeem"
  (https://www.vendit.nl/partners/transus/). Brick `supi`.
- **Highbiza** — documented: "gekoppeld met het Vendit Systeem", never selling "no"
  (https://www.vendit.nl/partners/highbiza/). Brick `hbzc`.
- **Returnista** — partner listing only (https://www.vendit.nl/partners/returnista/);
  integration depth is an **assumption**. Brick `retn` (status invest).
- **Logic4** — listed as ERP partner (https://www.vendit.nl/partners/logic4/); a direct
  data integration is **not documented**. Modeled as a group upgrade path for chains
  (persona `chnr` horizons, residuality stressor `katapull-portfolio-consolidation`).
- Picqer (WMS, acquired by Katapull October 2026) also appears as a Vendit partner page; not modeled.

## Source-backed facts

- Active since 1986, software developed in-house, about 40 colleagues; "one of the leading
  producers and suppliers of POS systems in retail in the Netherlands and Belgium" (vendor
  claim). https://www.vendit.nl/vendit-winkelmanagement/ , https://www.vendit.nl/
- Claims 12,000+ users and 25+ branches (home page); other pages say 10,000+ users and
  40 branches (support page, references page). Treat as vendor claims with inconsistent rounding.
- Packages: POS (from EUR 119/month on /functionaliteiten/, from EUR 129/month on
  /kassasysteem/), Premium (from EUR 199/month, quotes, customer orders, multiple stores,
  up to 15 users), Enterprise (price on request; unlimited users, packing slips, price
  lists, wireless stocktaking, foreign currency, loyalty, e-vouchers), Webshop (from EUR
  299/month, only with the Vendit System). Subscription includes cloud hosting, updates,
  online help, support. https://www.vendit.nl/functionaliteiten/ , https://www.vendit.nl/kassasysteem/
- Turnkey offer: hardware (Datalogic, Epson, Zebra), installation, data migration, training,
  support; Windows POS client ("kassasoftware voor Windows").
- Branch depth: bike trade supplier connections incl. frame and DPC numbers, workshop
  functions; jewellers partnership with Federatie Goud en Zilver (July 2026).
- Filiaal solution for retail service organisations / franchise formulas; KW Groep
  (Blokker entrepreneurs) reference. https://www.vendit.nl/automatiseringsoplossingen/franchiseorganisaties/
- Reporting: online dashboard with turnover, margin, discount, transactions, average
  ticket, items per ticket vs previous period; report library. https://www.vendit.nl/modules/rapportages/
- Loyalty: customer cards, value cheques, Givacard gift cards. https://www.vendit.nl/modules/loyaliteitsmodule/
- Support Monday to Saturday, TeamViewer remote support. https://www.vendit.nl/support-op-afstand/
- Partners include CCV, Worldline, Pay., SprayPay, AFAS, Exact (via stock page), Sendcloud,
  Transsmart, Klantenvertellen, Feeddex, BViva, GfK. https://www.vendit.nl/partners/
- Katapull formed March 2025 from Logic4, DeliveryMatch, EffectConnect, Highbiza and
  Vendit (Dutch IT Channel, 31 March 2025, via search summary); Returnista acquired
  February 2026; Picqer October 2026. Katapull site lists Vendit at 's-Gravenweg 433,
  Rotterdam, same address as DeliveryMatch. https://katapull.nl/

## Assumptions and inferences

- KPI `currentValue`s in customer pyramids are **illustrative baselines**, not measured or
  published figures.
- The offline sales buffer (`module-offline-sales-sync`, store `pos-local-buffer`) is an
  assumed capability, not confirmed by Vendit.
- Brick internals (modules, events, APIs) are inferred architecture from documented
  functions, not from implementation evidence.
- Data retention follows Dutch 7-year fiscal record retention and GDPR as general
  obligations; Vendit's actual retention policies are not published.
- Persona descriptions are synthesised from Vendit's own segment pages and references.

## Open questions

- Exact customer count, revenue and growth of Vendit (not published).
- Whether Vendit and Logic4 will converge or be positioned by segment within Katapull.
- Depth of the Returnista integration and any Picqer integration.
- Cloud architecture (fully hosted vs. hybrid with local workstation data).
