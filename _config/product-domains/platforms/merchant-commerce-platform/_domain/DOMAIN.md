# Merchant Commerce Platform

The Merchant Commerce Platform domain models a Shopify-style platform (https://www.shopify.com/) that lets merchants
of every size run their own branded commerce: storefront, checkout, orders, payments, point of sale,
wholesale, marketing and an app ecosystem, now extended into AI assistants as a sales channel.

## Why this domain

- Shopify reported FY2025 GMV of $378.4bn (+29%) and revenue of $11.6bn, with merchant solutions at
  76% of revenue and Shopify Payments processing 65.6% of GMV (FY2025 10-K). In Q2 2026 GMV was
  $115.6bn (+32%) and payments penetration 68%.
- The value loop is multi-sided: merchants pay subscriptions and transaction-based fees; shoppers get a
  network-wide wallet and app; partners build apps and services billed through the platform; AI
  assistants increasingly bring demand through an open commerce protocol.

## Scope

- **Core:** merchant onboarding and storefronts, checkout and buyer identity, catalog, inventory,
  markets, B2B, orders, shipping, returns, POS, payments, risk, payouts, capital, tax, platform
  billing, marketing and ads, analytics, the merchant AI assistant, agentic commerce and channels,
  APIs, extensions and the app store.
- **Adjacent (modeled as external systems):** payment processing partners and card networks, carriers
  and fulfillment networks, banking and lending partners, AI assistant platforms, social and
  marketplace platforms, ERP and warehouse systems.
- **Excluded:** Shopify's corporate functions, its sold logistics business, and marketplace
  operations it does not run.

## Customers

Merchants (Independent Brand Founder, Scaling DTC Brand Ecommerce Lead, Enterprise Omnichannel Retail
Director), Shoppers (Repeat Mobile Shopper) and Ecosystem Partners (Commerce App Developer and Agency
Partner).

## Evidence, assumptions and inference

- **Sourced:** GMV, revenue, MRR, payments penetration, app count, merchant geography, lending changes
  (Shopify 10-K FY2025 and Q2 2026 release); product facts on Catalog, UCP, Agentic Storefronts,
  Sidekick, Shop Pay reach (Shopify Spring '26 Edition and newsroom); competitor metrics in
  `business/competition.json`.
- **Assumptions:** KPI `currentValue`s are illustrative modeling baselines unless the KPI description
  cites a source. Shop Pay GMV (~$43bn FY2025) comes from third-party coverage of Shopify results and
  should be checked against company filings.
- **Inference:** brick decomposition, module layering, data stores and deployment surfaces are an
  architectural model inferred from public product behavior, not Shopify's internal design.

## Open questions

- Full-year 2025 Shop Pay GMV and Shop app usage from primary sources.
- Pricing of the agentic plan and AI channel economics as they mature.
