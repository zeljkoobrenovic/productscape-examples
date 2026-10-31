# B2B Wholesale E-commerce Platform (Highbiza, Katapull group)

## Scope

This domain models **Highbiza**, the webshop and website software label of the Dutch
commerce software group **Katapull**. Highbiza (Hengelo) builds and runs webshops for
trading companies on its own platform, which is based on Django, Django Oscar and Wagtail.

- **Core scope:** B2B and B2C webshops for wholesalers, technical wholesalers, e-tailers,
  retailers and jewellers. This covers customer-specific prices and assortments, quotes and
  reorder, checkout, payments and shipping, ERP and marketplace integration, CMS and SEO,
  and the managed service (hosting, backups, automated QA, test environments, support).
- **Adjacent scope:** Wagtail-based websites without a shop (Highbiza Website Software).
  Group siblings for ERP/POS, marketplaces, shipping, EDI and returns appear only as
  integrations.
- **Excluded:** Highbiza's (semi-)government websites and portals (WCAG/ISO work for public
  bodies), marketing agency services, and the internal operations of Katapull siblings.

**Value exchange:** the trading company pays a monthly package fee plus a one-off setup fee,
and pays separately for paid building blocks and custom work. Its trade buyers and consumers
use the shop for free and get speed and certainty. Highbiza earns more when many shops share
the same building blocks.

## Source-backed facts (retrieved 2026-10-30)

- History: the company started over 20 years ago as UWKM, became Highbiza in 2019 and has
  been part of the Katapull group since 2025. It is located at Industrieplein 1, Hengelo,
  which is the same address Katapull lists for Logic4.
  ([over-highbiza](https://highbiza.nl/over-highbiza/), [katapull.nl](https://katapull.nl/))
- Packages ([prijzen](https://highbiza.nl/prijzen/)):
  - **Launch:** from EUR 149/month plus from EUR 1,490 one-off. Up to 2,500 products,
    100 orders/month, 3 filters and 3 users.
  - **Core:** from EUR 299 plus EUR 3,490. Up to 15,000 products, 400 orders and 6 filters.
    Multi-shop and B2B are options. 5 users.
  - **Prestige:** from EUR 599 plus EUR 5,490. Up to 50,000 products, 850 orders and
    10 filters, with Elastic search Ultimate and the B2B module included. 10 users.
  - **Enterprise:** from EUR 1,149 (one-off fee on request). Unlimited products and orders,
    dedicated hosting, 15 users.
- Technology: Django/Python, Django Oscar and Wagtail CMS, positioned against Magento,
  WooCommerce and Shopify ([technologie](https://highbiza.nl/technologie/)).
- Delivery: more than 100 reusable building blocks, a test environment that stays available
  after go-live, the four-eyes principle, and automated tests every 24 hours
  ([zo-werken-wij](https://highbiza.nl/zo-werken-wij/)). Operations add Jenkins functional
  tests, screenshot tests, security tests and daily backups
  ([veiligheid](https://highbiza.nl/veiligheid/)). Highbiza is ISO 27001 certified
  ([home](https://highbiza.nl/)). Support requests are handled within one working day
  ([support](https://highbiza.nl/support/)).
- Wholesale features: customer-specific prices and assortments, staffel and net price lists,
  Elastic Search, quotes, reordering, and integrations with ERP, PIM and accounting
  ([groothandel](https://highbiza.nl/branches/groothandel/),
  [technische groothandel](https://highbiza.nl/branches/technische-groothandel/)).
- Integrations ([onze-integraties](https://highbiza.nl/onze-integraties)):
  - **ERP:** Exact Online, Business Central, Logic4, Vendit, Gripp, Prima and MediaMagic.
  - **Payment:** Mollie, MultiSafepay, Pay., Worldpay, PayPal, CardGate and OmniKassa.
  - **Carriers:** DeliveryMatch, Sendcloud, MyParcel, PostNL, Trunkrs and Royal Mail.
  - **Marketplaces:** EffectConnect, eBay and Google Shopping.
  - Also listed: "myopayo" (purpose not verified).
- Customer cases:
  - [Loods28](https://highbiza.nl/klanten/l28/) (Core): left Magento in 2021 and handles
    50k-100k orders a year with 7,000+ direct customers.
  - [HR Premium Parts](https://highbiza.nl/klanten/hr-premium-parts/) (Prestige): on
    Highbiza since 2015 and a launch customer for Highbiza + Logic4 in 2023.
  - [Kroon-Oil](https://highbiza.nl/klanten/kroon-oil/) (Enterprise): won through a tender,
    launched 20 August 2024 and runs several brands on one platform.
  - Juwelier Bijland (Launch).
- 2026 features: a loyalty points system
  ([Feb 2026](https://highbiza.nl/nieuws/zo-beloont-u-klanten-met-spaarpunten-in-uw-webshop/))
  and a Return Form Page for the 14-day withdrawal right
  ([Jul 2026](https://highbiza.nl/nieuws/herroepingsformulier-aanmaken-voor-je-webshop/)).
- Katapull group:
  - Rotterdam-based, with "175+ specialists, 4,500+ customers in 40+ countries, 27,500+
    users, 140+ marketplaces" ([over-katapull](https://katapull.nl/over-katapull/)).
  - Its labels are Vendit, Logic4, Highbiza, EffectConnect, DeliveryMatch, Transus and
    Returnista, plus Picqer (WMS), acquired on 7 Oct 2026
    ([news](https://katapull.nl/katapull-breidt-commerce-hub-uit-met-overname-van-picqer/)).
  - Katapull describes Highbiza as "online performance and digital growth"
    ([katapull.nl/highbiza](https://katapull.nl/highbiza/)).

## Sibling domains in `katapull-group`

The other Katapull brands are modeled as sibling domains:

- Vendit: `retail-pos-and-store-management-platform`
- Logic4: `omnichannel-commerce-erp-platform`
- EffectConnect: `marketplace-channel-integration-platform`
- DeliveryMatch: `shipping-and-carrier-management-platform`
- Transus: `edi-and-b2b-document-exchange-platform`
- Returnista: `ecommerce-returns-management-platform`

Evidence found for integrations between brands:

- **Highbiza with Logic4, Vendit, EffectConnect and DeliveryMatch:** all four appear on
  Highbiza's integrations page and are described there as part of Katapull. The Vendit POS
  link is also named on the jeweller branch page.
- **Highbiza with Logic4:** HR Premium Parts went live as a joint launch customer.
- **Logic4 with Picqer:** Katapull's Picqer release positions Picqer as the next step for
  Logic4 customers that need more warehouse functionality.
- **Katapull wholesale page:** combines repricer, marketplace order processing (50+
  marketplaces), Vendit POS and EDI-to-ERP/WMS (Transus) as one offering.
- **Not found:** no published Highbiza integration with **Returnista** or **Transus**. The
  model treats a Returnista connector and Transus EDI as assumptions or candidates (brick
  `wdrw`, residuality `edi-buyers`).
- Integrations among the other siblings (for example Logic4/Vendit with EffectConnect,
  DeliveryMatch, Returnista or Transus) were not verified for this domain. The sibling
  domains cover them.

## Assumptions and inferences

- Bricks, modules, data stores and deployment channels are **inferred** from product pages.
  Highbiza does not publish its architecture, database engine or hosting provider.
- Every KPI value is a **modeled seed value**, not a figure reported by Highbiza.
- Retention periods marked "(assumption)" in data assets are not published.
- Highbiza's customer counts differ between its own pages: 420 sites, 400+ sites, 250+
  organisations and 150+ organisations. The model treats the base as about 150-250
  organisations running about 400 sites.
- Persona journeys are illustrative composites based on the published cases.
- The overlap between Highbiza and Logic4's built-in webshop is an inference from the
  product descriptions. The group's positioning between them is not published.

## Open questions

- How Katapull will position Highbiza against Logic4's integrated webshop.
- Whether Returnista, Transus EDI and Picqer connectors are on the roadmap.
- Highbiza's headcount, revenue and the share of B2B shops versus B2C shops.

## Competition

The model covers Shopify, Adobe Commerce (Magento), WooCommerce, Sana Commerce, Propeller,
CCV Shop and Lightspeed (see `business/competition.json`). It includes only one business
stat (Shopify GMV, from its 10-K), because no other official figures were found.
