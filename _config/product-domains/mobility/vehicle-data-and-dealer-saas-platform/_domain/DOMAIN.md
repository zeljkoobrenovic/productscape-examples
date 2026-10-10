# Vehicle Data and Dealer SaaS Platform

This domain models **VWE Automotive** (VWE Groep B.V., Heerhugowaard, https://vwe.nl/). VWE calls itself the number one in Dutch vehicle data and the largest officially recognised RDW provider. It serves 10,000+ business customers (homepage) or 11,000+ (September 2026 release). The 2026 shareholder release frames it as a data and SaaS platform for the used-car market, built on direct RDW access and 30+ years of vehicle and transaction data.

## Domain boundary

**Core scope:** vehicle data and the workflows built on it, along *Identify -> Check -> Value -> Stock -> Advertise -> Sell -> Register -> Trade -> Insight*:

- Vehicle data foundation: RDW register, specification (SilverDAT, Autotelex, Jato), damage/maintenance/odometer history, EV State of Health, weDAT damage calculation, market data, valuation, BPM (incl. XRAY Automotive).
- MijnVWE dealer platform: vehicle dossier, Occasion Manager, Finnik Zakelijk appraisals, advertising to 150+ channels, dealer websites, administration, financing referral (Financial Lease Partner).
- Registration and trade services: RDW transactions, import/export documents, plates and materials, B2B trade (Voorraad Nederland, XBS) with hand-off to the auction partner.
- Data products: Interdata/XMLmode/JSON APIs, file enrichment, Marktinzicht, Market Performance Manager, occasion performance meter, change-of-ownership lead generator.
- Consumer: Finnik plate checks and reports, travel documents (environmental stickers, vignette, one-day insurance).

**Adjacent:** auctions (ATC sold to Autorola in February 2026, now a partner hand-off), warranty and insurance partners, dealer management systems.

**Excluded:** selling cars, lending (the financing partner lends), repairing cars, the RDW's own systems.

## Value exchange

Dealers, traders and lessors pay monthly module subscriptions and per-report and per-transaction fees. Software vendors and data clients pay for API usage, licences and insight subscriptions. Consumers pay per report or per order. The repeatable value comes from authoritative data, which turns into decisions (what to pay, what to ask) and official transactions inside daily workflows.

## Customer segments

The `Voor wie` pages list starters, rental companies, multi-brand dealers, lease companies, dealer holdings, importers, franchise formulas and exporters. The model groups them into seven personas:

- `udlr`: independent dealer.
- `dhld`: dealer group director.
- `trex`: trader and importer-exporter.
- `lsco`: lease and rental remarketing.
- `ivnd`: software vendor.
- `dcli`: importer or insurer data analyst.
- `cons`: consumer.

## Strategic spine

- **Year 1: One dossier, one account.** Integrate Occasion Manager, history reports, RDW actions and XRAY behind shared identity and billing. Stabilise the APIs.
- **Year 3: Market-driven automation.** Automate pricing and stock signals, digital returns for lessors, modern JSON APIs with webhooks, and self-service insight.
- **Year 5: Assisted used-car business and an embedded data utility.** The platform proposes purchases and prices. VWE data is embedded across Benelux automotive software, and Finnik covers the whole ownership cycle.

## Sources

- vwe.nl product pages: MijnVWE, Occasion Manager, Finnik Zakelijk, Schadeverleden, API documentation, Marktinzicht, change-of-ownership lead generator, particulier.
- VWE news: Main Capital (2026), XRAY (2026), AVN (2022), NewPort (2022), Financial Lease Partner (2025), Nationaal Occasion Onderzoek 2025.
- Third parties: ACM concentration decision ACM/22/179803, William Blair, Journal de l'Automobile on the ATC sale, Magnet.me employee count.
- Competitors: from their official sites (see `business/competition.json`).

## Assumptions and open questions

- **All KPI values are modeled seed values.** VWE publishes no revenue, volume or adoption metrics beyond customer counts and prices.
- Teams, headcounts and the organisation are modeled, not VWE's actual structure. Product and engineering total 62 people (13 small teams plus 5 group leads), sized against Magnet.me's figure of about 125 employees at head office; sales, support, the HQ counter and remarketing operations are outside the team model.
- The founding year is inconsistent across sources (1975, 1993, "30" or "40+ years"), so the model does not depend on it.
- Whether the Main Capital transaction has closed (expected October 2026) is unconfirmed.
- The Autoveiling page still references ATC after its sale. The model treats auctions as a partner hand-off.
- Insurer and finance product lines mentioned by deal advisers have no dedicated product pages. They are modeled through APIs, enrichment and damage data.
- Brick internals (modules, stores, dependencies) are inferred from product behaviour, not from VWE architecture documentation.
- Residuality stressors `portalconsolidation`, `evshift` and `privacy` are plausible scenarios, not announced events.
