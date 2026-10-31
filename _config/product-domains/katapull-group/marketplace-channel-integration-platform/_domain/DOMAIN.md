# Marketplace Channel Integration Platform

This domain models **EffectConnect** (effectconnect.com), the marketplace integrator of the Dutch software group **Katapull** (katapull.nl). EffectConnect calls itself an "integrator platform voor Europese marketplaces". It connects webshops, back offices, ERP/PIM/WMS systems and SaaS partners to **50+ European marketplaces** (bol, Amazon, Kaufland, Decathlon, MediaMarkt, eBay, Kruidvat, Hornbach, Praxis and others) and to product-feed channels. It is based at Tolhuisweg 5a, Swalmen (NL).

## Katapull group and sibling domains

Katapull ("samen commerce bouwen") was formed in 2025 from Logic4, DeliveryMatch, EffectConnect, Highbiza and Vendit (Dutch IT Channel, 31 March 2025). Transus and Returnista were added later, and Picqer (WMS) followed on 7 October 2026. Katapull presents these labels as one **Commerce Hub** and reports 175+ specialists, 4,500+ customers in 40+ countries, 27,500+ users and 140+ marketplaces. These are group-level figures, not EffectConnect figures. The group calls EffectConnect's role "Marketplace performance optimaliseren".

The sibling Katapull brands are modeled as sibling domains in the `katapull-group` group:

| Brand | Domain ID |
|---|---|
| Vendit | `retail-pos-and-store-management-platform` |
| Logic4 | `omnichannel-commerce-erp-platform` |
| Highbiza | `b2b-wholesale-ecommerce-platform` |
| DeliveryMatch | `shipping-and-carrier-management-platform` |
| Transus | `edi-and-b2b-document-exchange-platform` |
| Returnista | `ecommerce-returns-management-platform` |

Picqer was acquired after the user's brand list was written. It is not modeled as its own domain. This domain mentions it only as a partner and as a residuality stressor.

### Evidence of integration between brands

- **Logic4 ↔ EffectConnect (fact).** EffectConnect has a Logic4 integration page. In the Fitwinkel case, Logic4 phased out its own bol.com integration and the customer moved to EffectConnect. Search snippets of EffectConnect's Logic4 page describe it as a "sister company" connection. PitchBook and CB Insights list a Logic4–EffectConnect merger or acquisition, dated 20 June 2022 by CB Insights. This could not be confirmed from primary sources.
- **DeliveryMatch ↔ EffectConnect (fact).** DeliveryMatch is the named reference partner for Embedded Integrations. Its managing director gives the testimonial.
- **Vendit, Highbiza, Transus, Returnista (fact, limited depth).** EffectConnect's partner page lists them as Katapull partners. No technical integration detail was found for Vendit, Transus or Returnista, and Returnista's own integrations page does not list EffectConnect.
- **Picqer ↔ DeliveryMatch/Returnista (fact, per Katapull release).** The companies already work together. A Picqer–EffectConnect link is an **inference**, modeled as a candidate stressor.

## Domain boundary

**Core scope:** connecting merchant systems to marketplaces and keeping catalogue, listings, prices, stock, orders and shipments in sync. Also in scope are repricing and competitor analysis, the Fulfilment Manager (LVB/FBA), the Feed Manager, reporting, Embedded Integrations for SaaS partners, the REST API v3, the app store and service-led onboarding.

**Adjacent scope (light):** the Retail Media Dashboard (built with OMG Transact) for brands, and the optimisation advice that consultants give.

**Excluded:** running the marketplaces themselves, webshop and back-office functionality (sibling domains), carrier booking (DeliveryMatch), returns handling (Returnista), EDI (Transus), warehouse management (Picqer) and agency services.

## Value exchange

Merchants and brands pay a subscription. The **Platform** plan starts at EUR 305 per month and covers 1,000 EANs, 500 orders, one marketplace, stock sync, the feed manager with 5 exports, reporting and personal support. **Add-on modules** start at EUR 30 per month: extra products, extra marketplaces, feed credits, the repricer, offer analysis, the Fulfilment Manager and AI translation. **Scale** is priced on request and includes unlimited products, marketplaces and all modules. bol's partner listing says EffectConnect takes no percentage of revenue and can be cancelled monthly.

Embedded partners set their own price to their customers. Their financial model is agreed during partner registration. Marketplaces receive commission from merchants and do not pay EffectConnect; bol states it receives no compensation from the partner.

## Strategic spine (modeled)

- **Year 1: Commerce-Hub-native connectivity.** Logic4, Vendit and Highbiza connectors run as products. Migration from commission-based integrators is made painless. Repricing, content mapping and AI translation become standard setup. Embedded Integrations are rolled out to sibling brands.
- **Year 3: Marketplace performance intelligence.** Margin-after-fees reporting, expansion advice, retail media budget recommendations, and a hub-wide fulfilment flow with Picqer, DeliveryMatch and Returnista.
- **Year 5: Autonomous channel operations.** Guardrailed agents for listings, pricing and fulfilment, with EffectConnect acting as the marketplace layer for commerce SaaS.

## Model contents

- **Customers:** 6 personas in 4 groups (merchant owner, marketplace manager, operations lead, brand/retail media manager, IT lead, embedded SaaS partner), with JTBD, adoption journeys, two 15-node KPI pyramids each and 1/3/5-year strategy.
- **Product model:** 27 bricks in 6 root groups, 10 streams, 21 data assets in 6 stores and 7 products.
- **Supporting artifacts:** a competitive landscape of 6 players, 6 residuality stressors and a beginner tutorial.

## Sources (facts)

- EffectConnect pages:
  - https://www.effectconnect.com/ : 50+ marketplaces, modules, address, testimonials
  - https://www.effectconnect.com/nl/prijzen : plans and add-ons
  - https://www.effectconnect.com/nl/hoe-het-werkt : four onboarding steps, integration routes, about 2 weeks via app or plugin, NPS 67, claims of 40% annual customer revenue growth and 50% more buy boxes
  - https://www.effectconnect.com/nl/integraties : named marketplaces, webshop platforms, feed channels, 100+ integrations
  - https://www.effectconnect.com/nl/repricer-tool : strategies and the claim that about 98% of sales go via the buy box
  - https://www.effectconnect.com/nl/fulfilment-manager-voor-marketplaces : LVB switch, replenishment and the claim of up to 14x more sales from own stock
  - https://www.effectconnect.com/nl/product-informatie-management : content mapping, custom attributes, translations
  - https://www.effectconnect.com/nl/retail-media-dashboard : OMG Transact, Amazon/bol/AH APIs, Criteo
  - https://www.effectconnect.com/nl/embedded-integraties : Partner API, branded pages, DeliveryMatch
  - https://www.effectconnect.com/en/partners : Katapull partners, agency, logistics and software partners
  - https://www.effectconnect.com/en/top-sports-on-marketplaces-the-thriving-success-of-fitwinkel.nl : Logic4 phase-out, fixed fee per order, case figures
  - https://developers.effectconnect.com/docs/v3/redoc.html : REST API v3
- bol partner platform, https://partnerplatform.bol.com/en/cpdp/effectconnect : Gold Partner, first integrator to bol in 2011, support hours and languages, no revenue percentage.
- Katapull pages:
  - https://katapull.nl/ : brands, addresses, Commerce Hub
  - https://katapull.nl/over-katapull/ : group figures
  - https://katapull.nl/effectconnect/ : group positioning
  - https://katapull.nl/katapull-breidt-commerce-hub-uit-met-overname-van-picqer/ : Picqer acquisition
- Dutch IT Channel, 31 March 2025, https://www.dutchitchannel.nl/news/603618/vijf-softwarebedrijven-bundelen-krachten-in-katapull (formation; seen via search snippet, page blocked to automated fetch). Dealroom snippet: Nedvest-backed, CEO Gino Keijzer, Returnista acquisition February 2026.
- Competitors:
  - https://www.channelengine.com/en : 1,300+ channels
  - https://www.channelengine.com/en/blog/channelengine-welcomes-vendiro : Vendiro acquisition, June 2023
  - https://www.lengow.com/ : 3,600+ customers, 90+ marketplaces
  - https://www.koongo.com/ : 500+ channels, 1,500+ stores

katapull.nl could be fetched with curl but not with the web-fetch tool.

## Assumptions and inferences

- **KPI current and target values are modeled seed values** for a representative account. The exceptions are values quoted from EffectConnect: NPS 67 and about two weeks to go live.
- EffectConnect's marketing claims (98% of sales via the buy box, 14x, 40% growth, 50% more buy boxes) are its own figures and are recorded as claims.
- The brick architecture is inferred from product features. EffectConnect does not publish its internal architecture. The Account Health and Optimisation Advice brick and the Integration Runtime are modeled inferences based on the onboarding and monitoring claims.
- Returns-status sync to marketplaces is an inference. No EffectConnect page describes it explicitly.
- Residuality stressors marked `candidate` are scenarios, not announcements.

## Open questions

- The corporate history between Logic4 and EffectConnect before Katapull: a 2022 merger, or acquisition by Logic4?
- Total customer count and revenue of EffectConnect. These are not published, and no figure is modeled.
- How the Embedded Integrations financial model is structured.
- Whether Vendit, Transus and Returnista have productised connectors with EffectConnect or only partner listings.
