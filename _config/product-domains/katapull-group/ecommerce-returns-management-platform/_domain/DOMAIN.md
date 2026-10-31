# E-commerce Returns Management Platform

Product domain for **Returnista** (https://www.returnista.nl/en; returnista.com redirects there), the returns management brand of the Dutch commerce software group **Katapull** (https://katapull.nl/). The katapull.nl site could not be fetched automatically during research ("socket hang up"). Group facts come from press and deal notes and are listed below.

## Scope

- **Core:** a branded self-service returns portal, return policy rules, labels and carrier choice, paid returns, tracking and notifications, exchanges and store credit, return operations (AI rule agent, automations, warranty and damage claim approval, receipt and inspection, resolutions, in-store returns, inquiry handling), and returns insights (dashboard, Product Return Impact Index, benchmarks, BI export).
- **Adjacent:** connectors to shop platforms, carriers, WMS and fulfilment, ERP, helpdesk, marketing, size-and-fit, fraud and stock-planning apps, plus a public API and webhooks.
- **Excluded:** outbound shipping and carrier management (DeliveryMatch domain), warehouse management (Picqer and partners), ERP and order management (Logic4), POS (Vendit), marketplace channel management (EffectConnect), B2B webshops (Highbiza) and EDI (Transus).
- **Value exchange:** merchants pay a subscription. Shoppers use the portal for free but may pay return fees that the merchant sets. Fulfilment and WMS partners integrate and refer clients. Value repeats because each return can be turned into an exchange or credit, and it also produces data that helps prevent future returns.

## Katapull group and sibling domains

Katapull launched in March 2025 when Logic4, DeliveryMatch, EffectConnect, Highbiza and Vendit came together, backed by the investor Nedvest. The group acquired Returnista in February 2026 and the WMS vendor Picqer in October 2026. Transus is also listed in the group's Commerce Hub. Each sibling brand is modeled as a separate domain in the `katapull-group` group:

| Brand | Domain ID |
|---|---|
| Vendit | `retail-pos-and-store-management-platform` |
| Logic4 | `omnichannel-commerce-erp-platform` |
| Highbiza | `b2b-wholesale-ecommerce-platform` |
| EffectConnect | `marketplace-channel-integration-platform` |
| DeliveryMatch | `shipping-and-carrier-management-platform` |
| Transus | `edi-and-b2b-document-exchange-platform` |
| Returnista | `ecommerce-returns-management-platform` (this domain) |

**Integration evidence between Returnista and its siblings:**

- **Picqer (now a Katapull company):** this is a native integration, documented by both Returnista and Picqer. It is a real link within the group.
- **Logic4, Vendit, DeliveryMatch, EffectConnect, Transus, Highbiza:** none of them was listed on Returnista's integrations page in October 2026.
  - The Lexence deal note describes Returnista joining "an end-to-end platform covering orders, fulfilment, returns and data flows".
  - From that we *infer* likely future flows: Logic4 ERP sync, Vendit POS in-store returns and DeliveryMatch return labels. These are modeled as candidates in residuality and in brick descriptions, not as current facts.
- Integrations among the siblings themselves (for example Logic4 or Vendit with EffectConnect, DeliveryMatch and Transus) are documented in those domains.

## Source-backed facts

- Founded in 2017 in Amsterdam by brothers Quinten and Olivier Muller. Their growth accelerated during COVID-19. Returnista took part in the Techleap Rise programme. Source: Silicon Canals, October 2022.
- HQ is in Amsterdam, with a DACH office in Munich. The team has about 25 people. Returnista claims 1,000+ brands across Europe and more than 10 million returns processed. Source: About page.
- **Modules:**
  - returns portal (branding, configurable reasons and carriers, instant labels, rules by product, region and segment)
  - exchanges (size exchanges on live stock, instant or after inspection, bonus credit up to EUR 10 or 15%)
  - store credit
  - insights (return rate dashboard, Product Return Impact Index, payment method, exchange, store credit and behaviour analysis)
  - return operations (AI rule agent, automations, warranty and damage gatekeeping with photos, tracking, optional handling of inquiries)
- **Pricing:**
  - Essential: EUR 179/month (EUR 149 billed annually)
  - Professional: EUR 279/month (EUR 233 billed annually), adds own carrier contracts and dedicated customer success
  - Enterprise: custom, adds custom platforms and BI connection
  - Warranty flow add-on: EUR 39/month
  - The feature matrix also lists in-store returns, multi-country returns, paid returns, API and webhooks.
- **Integrations:**
  - Shop platforms: Shopify/Plus, Shopware, Lightspeed, WooCommerce, Magento
  - ERP: ACA, Becosoft, itsperfect, xCore
  - WMS: Active Ants, Bleckmann, Montapacking, Picqer
  - Fulfilment: Monta, ModeXpress, QLS
  - 12 carriers
  - Other apps: Channeldock, Optiply, CM.com, Engaige, Trengo, Gorgias, Klaviyo, Faslet, Easysize, Guzco, Leat
- Shopify App Store listing: "Returnista - Return & Exchange", launched July 2023.
- **Benchmark report 2026:**
  - Category return rates: home 6%, accessories 7%, footwear 28%, clothing 29%, swimwear 37%.
  - Method: 1,000+ consumers surveyed, 100+ merchants interviewed and flows from 1,000+ brands on the platform.
- Customer claims: Esqualo's return rate fell from 47% to 32%. Steve Madden reports a 12.7% reduction. A Bestseller analytics lead says that a 1% drop in return rate gives about a 1.5% gain in net result.
- **Vendor marketing claims (no period or sample stated):** up to 40% of return value retained, a 30-40% exchange rate and 10-20% store credit conversion.
- **Acquisition by Katapull:** dated 11 Feb 2026 in the Lexence deal note and 16 Feb 2026 by Dutch IT Channel.

## Assumptions and inferences

- **KPI values:** all KPI `currentValue`/`targetValue` numbers are modeled seed values. Only the clothing return rate seed (29%) comes from the benchmark.
- **Inferred bricks:** receipt and inspection, restock assignment, the analytics pipeline, benchmark views and the LLM provider are inferred from the features Returnista describes. Hosting, data stores and the EU data residency are assumptions.
- **Older claims:** label-free returns and CO2 compensation come from the 2022 article. The current site does not repeat them.
- **Personas:** chosen by analysis, not taken from Returnista segmentation material.

## Open questions

- Which Katapull sibling integrations (Logic4, Vendit, DeliveryMatch) are on the roadmap?
- Is inspection done in Returnista or only in partner WMSs?
- Which payment provider is used for return fees?
- How many merchants are on each plan, and how does revenue break down by country?

## Sources

- https://www.returnista.nl/en
- https://www.returnista.nl/en/about-us
- https://www.returnista.nl/en/pricing
- https://www.returnista.nl/en/integrations
- https://www.returnista.nl/en/returns-portal
- https://www.returnista.nl/en/exchanges
- https://www.returnista.nl/en/insights
- https://www.returnista.nl/en/return-operations
- https://www.returnista.nl/en/benchmark-report
- https://platform.returnista.com
- https://apps.shopify.com/returnista-return-and-exchange
- https://siliconcanals.com/returnista-turns-returns-into-opportunities/
- https://www.lexence.com/en/article/lexence-acted-as-legal-counsel-to-the-shareholders-of-returnista-holding-b-v/
- https://www.dutchitchannel.nl/news/724827/katapull-breidt-e-commerce-platform-uit-met-overname-returnista
- https://www.dutchitchannel.nl/news/603618/vijf-softwarebedrijven-bundelen-krachten-in-katapull
- https://www.osborneclarke.com/node/29400
- https://picqer.com/en/blog/new-returnista-integration
- https://en.returnista.nl/integraties/monta
- https://siliconcanals.com/eindhoven-returnless-acquired-by-jtl-software/
- https://katapull.nl/ (group source; not reachable for automated fetch)
