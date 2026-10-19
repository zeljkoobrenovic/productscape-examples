# general-listings-marketplace Review

## Product Domain Review

Updated: 2026-06-17

### Executive assessment

- Recent changes materially improved the strategic grounding: `_domain/DOMAIN.md` now states an EU-centric horizontal classifieds scope, category priorities, monetization model, non-goals, and sequencing tradeoffs.
- Customer segmentation is credible and materially distinct across local buyers, casual sellers, professional merchants, and merchant SaaS/feed partners. The partner side is now better reflected in deployments than in the previous review.
- Competition and customer links are much stronger: the model now covers horizontal classifieds, social/local substitutes, C2C recommerce, motors, real estate, jobs, integration platforms, payment/shipping rails, and EU regulatory context.
- Evidence quality improved because EU DSA and P2B sources were added and unsupported claims are explicitly summarized as assumptions. The remaining weakness is that 10 of 20 insights still have no `sourceIds`, so discovery/search, merchant ROI, pricing, feed reliability, and marketplace-intelligence claims are not yet research-backed.
- The largest cross-model defect remains customer-to-implementation traceability: all 54 `streamsNeeded` references in customer job steps point to product-brick IDs, while none point to the 12 product-stream IDs.
- KPI architecture is broad and useful, but the 55 `currentValue` fields and 23 `dashboard.example.com` links still read as synthetic data unless the model labels them as examples, baselines, targets, or placeholders.

### High-priority findings

1. Customer jobs still bypass product streams.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/customers/customers.json` jobs `jtbd-cg1-1`, `jtbd-cg1-2`, `jtbd-cg2-1`, `jtbd-cg2-2`, `jtbd-cg3-1`, `jtbd-cg3-2`, and `jtbd-cg4-1` use `steps[].streamsNeeded[].id` values such as `home`, `serp`, `cmse`, `papl`, `clim`, and `svih`. These are brick IDs. None of the 54 references use product-stream IDs such as `buyer-search-save-and-return`, `seller-publish-a-good-listing-fast`, or `platform-operate-marketplace-integration-and-operations` from `product-bricks/product-stream.json`.
   - Why it matters: Product streams are supposed to explain outcome delivery between JTBD and implementation. The current customer model jumps directly to bricks, so generated docs cannot show how a buyer, seller, or partner job maps to a coherent flow.
   - Suggested direction: Add stream-level references from JTBD steps to product-stream IDs first, then keep brick-level references as implementation dependencies under the stream or a renamed field.

2. KPI values and dashboard links look measured but are not provenance-backed.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/customers/customers.json` contains 55 `currentValue` fields and 23 links under `https://dashboard.example.com/general-listings-marketplace/...`.
   - Why it matters: The KPI tree appears operationally mature, but readers cannot tell whether numbers are synthetic examples, measured baselines, current production values, or targets. Placeholder dashboard URLs weaken confidence in strategy and review output.
   - Suggested direction: Add explicit baseline/target/provenance semantics, or label current values and dashboard links as examples until real measurement owners and links exist.

3. Insight assumptions are explicit but still mixed with sourced findings.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/customers/insights.json` has 20 items and four sources (`ftc-inform`, `ftc-marketplace-consumers`, `eu-dsa`, `eu-p2b`). Items `glm-05`, `glm-06`, `glm-09`, `glm-12`, `glm-13`, `glm-14`, `glm-15`, `glm-16`, `glm-17`, and `glm-20` have empty `sourceIds`; their summaries begin with "Assumption:".
   - Why it matters: The assumptions are useful, but they sit in the same collection as sourced regulatory findings. The model can overstate evidence for discovery quality, feed health, merchant ROI, pricing confidence, saved alerts, and marketplace intelligence.
   - Suggested direction: Add an evidence type or confidence field that separates sourced insight, assumption, hypothesis, and inferred strategy. Add authoritative sources for marketplace liquidity, ranking/search behavior, seller monetization, feed APIs, pricing guidance, and transaction trust.

### Medium-priority findings

1. Competitive scope is broader, but direct competitors and benchmarks need clearer labels.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/_domain/DOMAIN.md` defines a primary European horizontal-classifieds market. `business/competition.json` includes EU-relevant references such as OLX, Adevinta, Vinted, Wallapop, Rightmove, and Auto Trader UK, but also U.S. or global benchmarks such as Craigslist, OfferUp, Zillow, Indeed, Mercari, and Facebook Marketplace.
   - Why it matters: These are useful substitutes and benchmarks, but without a direct/substitute/benchmark role readers may treat incomparable businesses and regions as equal competitors.
   - Suggested direction: Add competitor role, region relevance, and category relevance fields or make those distinctions explicit in descriptions and caveats.

2. Journey stories still carry generated phrasing.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/customers/customers.json` journey narratives include repeated phrases such as "the current way of working can no longer protect..." and media alt text such as "Enterprise journey panel" for buyer, casual seller, professional merchant, and partner journeys.
   - Why it matters: The customer strategy is stronger than the journey copy. Generated wording makes the model feel less grounded in real marketplace behavior and weakens the generated documentation.
   - Suggested direction: Rewrite the main journey stories around concrete marketplace triggers: scam exposure, stale local supply, noisy results, feed failures, moderation rejects, merchant lead leakage, and partner breaking changes.

3. Category-gated transaction strategy should be carried into customer horizons.
   - Evidence: `_domain/DOMAIN.md` says protected transactions start in shippable goods/recommerce and are not forced onto motors, real estate, jobs, or services. Customer strategies for `cg1-p1` and `cg2-p1` discuss expanding protection, payment, shipping, reservation, proof-of-handoff, and transaction rails across high-risk or high-value categories.
   - Why it matters: The brief has the right tradeoff, but the customer horizon copy can still be read as a broad transaction-platform push. That risks blurring the intentional lead-generation model for motors, real estate, jobs, and services.
   - Suggested direction: Add category gates and explicit non-goals inside the relevant customer horizons and milestones, not only in the domain brief.

4. Customer links are useful but should become more traceable to insights and competition.
   - Evidence: `_config/product-domains/marketplaces/general-listings-marketplace/customers/links.json` now has eight groups covering reference marketplaces, industry background, trust/compliance, partner APIs, local substitutes, verticals, payment/shipping infrastructure, and EU platform regulation.
   - Why it matters: The curated links are a good context layer, but they are not connected to insight IDs, competitor IDs, or customer/job IDs. Readers cannot see which links support which modeled claims.
   - Suggested direction: Add optional references from links to insight IDs, competitor IDs, customer IDs, or JTBD IDs where a link materially grounds the model.

### Targeted improvement backlog

1. Update `customers/customers.json` so JTBD steps reference product-stream IDs from `product-bricks/product-stream.json`; keep brick IDs as lower-level implementation dependencies.
2. Add KPI provenance semantics to `customers/customers.json`: example, baseline, target, measured source, owner, reporting date, and dashboard URL status.
3. Split `customers/insights.json` items into sourced findings and assumptions, then add sources for marketplace liquidity, search/ranking, pricing guidance, merchant economics, feed reliability, and safe transaction behavior.
4. Add direct/substitute/benchmark role labels and region/category relevance to `business/competition.json`.
5. Rewrite the highest-traffic journey stories for `jtbd-cg1-1`, `jtbd-cg1-2`, `jtbd-cg2-1`, `jtbd-cg3-1`, and `jtbd-cg4-1`.
6. Carry category-scoped transaction rules from `_domain/DOMAIN.md` into customer strategy horizons for buyers and casual sellers.
7. Add optional trace links from `customers/links.json` to related insight, competitor, customer, or job IDs.

### Open assumptions

- Are the KPI `currentValue` fields examples, measured baselines, target values, or seeded demo data?
- Should `streamsNeeded` be redefined as brick references, or should customer jobs explicitly reference product streams?
- Which competitors are direct EU operating competitors versus global benchmarks or substitutes?
- Which unsupported insights are intended as accepted strategic assumptions versus hypotheses awaiting research?
- How far should protected transactions expand beyond shippable goods, and what category economics gate that expansion?
- Should customer links remain context-only, or become first-class evidence supporting insights and competitive claims?

## Product Bricks Review

Updated: 2026-06-17

### Architecture assessment

- The implementation model is broad and mostly well-wired: 88 bricks, 12 product streams, 20 data assets, no missing stream brick dependencies, and no missing data asset references were found.
- Recent data changes fixed the previous high-risk ownership defects. Data assets now align with their system-of-record brick owners, and duplicate `role: own` data dependencies were not found.
- Product and deployment coverage improved: `products.json` and `deployment.json` now reference 23 unique bricks, including partner-support bricks such as `ause`, `buan`, `doma`, and `prba`.
- The remaining architecture risk is not reference validity; it is realism. Every brick has exactly three brick dependencies, every brick has exactly two inbound and two outbound external-system relationships, and repeated module signatures make unlike capabilities look operationally identical.
- Streams are outcome-named, but they are not yet acting as the strategy-to-architecture bridge because customer jobs do not reference them and stream flows still contain repeated generated key facts and pain points.
- Investment status is too narrow for the stated strategy: only six bricks are marked `invest`, while protected transactions, payments, partner APIs, fraud/risk, pricing intelligence, data products, and marketplace intelligence remain `sustaining`.

### Critical findings

1. JTBD-to-stream traceability is absent.
   - Severity: High
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/customers/customers.json` `jobsToBeDone[].steps[].streamsNeeded`; `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-stream.json`.
   - Why it matters: The 12 product streams should be the primary architecture bridge from customer progress to composed bricks. Instead, all 54 customer job references point directly to bricks and none point to streams.
   - Suggested direction: Link job steps to stream IDs first, then let streams carry the composed `brickDependencies`, external systems, and flow steps.

2. The dependency graph looks generated rather than operational.
   - Severity: High
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json` `brickDependencies`, `externalSystemsThisBrickDependsOn`, and `externalSystemsDependingOnThisBrick`.
   - Why it matters: All 88 bricks have exactly three brick dependencies. Dependency targets are heavily concentrated on `loin` (67 incoming), `opad` (63), `ccma` (55), and `csor` (29). Every brick also has exactly two external systems it depends on and two external systems depending on it. This pattern hides real runtime, data, risk, and operational dependencies.
   - Suggested direction: Prune boilerplate dependencies and keep relationships that shape ownership, reliability, data movement, policy, release sequencing, or incident response. Add missing real dependencies only where they affect delivery or risk.

3. Deployment traceability still covers only a minority of the architecture.
   - Severity: High
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-deployments/products.json`; `_config/product-domains/marketplaces/general-listings-marketplace/product-deployments/deployment.json`; `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json`.
   - Why it matters: Products and channels now reference 23 unique bricks, but 65 of 88 bricks remain outside product and deployment coverage. Important capabilities such as `acsc`, `frde`, `clre`, `pres`, `damo`, `dapl`, `ccma`, `clma`, `geor`, `maau`, `spma`, `pdto`, and `qato` are not connected to a delivery surface.
   - Suggested direction: Add platform, data, trust/risk, monetization, and operations deployment surfaces where these bricks are delivered or operated. For intentionally non-deployable bricks, add an explicit modeling convention rather than leaving them absent.

### Model-quality findings

1. Stream flow details are still too generic.
   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-stream.json` flows such as `buyer-browse-interesting-listings-flow`, `seller-publish-a-good-listing-fast-flow`, `pro-seller-run-a-storefront-flow`, and `users-transact-on-a-trusted-marketplace-flow`.
   - Why it matters: Repeated phrases such as "Users need clear guidance and feedback here to keep moving forward" and "Confidence decreases when the product does not explain what happens next" appear across many stream steps. The stream names are good, but the flow facts do not yet expose classifieds-specific operational reality.
   - Suggested direction: Rewrite flow facts and pain points around marketplace-specific constraints: stale supply, listing quality, seller credibility, scam risk, moderation rejects, feed validation, protected payment state, dispute handling, and category-specific handoffs.

2. Module models repeat a small set of templates across unlike capabilities.
   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json` `layers`.
   - Why it matters: Thirty-four bricks share the same operations-workspace/service-api/domain-event-feed/core-domain-engine pattern, and thirteen share the same user-experience-interface/experience-backend-api/event-stream/service pattern. Search, payments, identity, fraud, feeds, media, analytics, and developer tooling should not all look architecturally interchangeable.
   - Suggested direction: Customize module shapes for the highest-risk domains: search/ranking, payments and protected transactions, identity and consent, fraud/risk scoring, feed ingestion, media processing, data platform, analytics, partner APIs, and support operations.

3. Investment status is not aligned to the strategic sequencing.
   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json` `status`.
   - Why it matters: Only `serp`, `ssal`, `cdpc`, `esfu`, `prpa`, and `ocma` are marked `invest`. Strategy also depends on `hpfi`, `papl`, `svih`, `clim`, `acsc`, `frde`, `pres`, `buan`, `dapl`, and `damo`, but these are all `sustaining`.
   - Suggested direction: Reclassify statuses by horizon and category gate: foundational discovery/listing work, transaction rails for goods, partner integration, trust/risk controls, pricing intelligence, and data monetization.

4. Legacy and placeholder language remains in brick descriptions.
   - Severity: Low
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json` examples include `home` with "General Listings Marketplace brand brands", `b2cr` and `b2cc` Salesforce/country-specific CRM descriptions, and long names such as `Professional Seller / Dealer / Storefront Entity Single Source of Truth`.
   - Why it matters: The generated architecture pages will expose this language. It makes the model feel partly imported from a legacy capability map rather than intentionally normalized for this domain.
   - Suggested direction: Normalize descriptions into concise current product language and expand unavoidable legacy acronyms once.

### Traceability findings

1. Streams lack explicit customer, job, and KPI references.
   - Severity: High
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-stream.json`.
   - Why it matters: Streams are named around buyer, seller, professional seller, trust, and platform outcomes, but they do not contain explicit customer IDs, job IDs, KPI names/IDs, or strategy horizon references. Generated pages must infer mappings from names.
   - Suggested direction: Add supported mapping fields if the generator supports them; otherwise encode concise references in stream descriptions and flow metadata.

2. Data assets are structurally sound but not visible enough in streams and deployments.
   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/data/data-assets.json`; `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-stream.json`; `_config/product-domains/marketplaces/general-listings-marketplace/product-deployments/products.json`.
   - Why it matters: The data model is now strong: assets have owners, classifications, stores, interfaces, governance, and system-of-record bricks. But critical assets such as `trust-signal`, `payment-ledger`, `identity-verification-record`, `search-query-event`, and `listing` are only indirectly visible through brick dependencies, not through the streams or deployment products that carry the strategic risk.
   - Suggested direction: For high-risk streams, call out the data assets that make the flow reliable, compliant, or measurable. Add deployment/data-product surfaces for data platform and marketplace intelligence where applicable.

3. Partner architecture is improved but still blended into the professional seller product.
   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/general-listings-marketplace/product-deployments/products.json` product `p3`; `_config/product-domains/marketplaces/general-listings-marketplace/product-bricks/product-bricks.json` bricks `svih`, `ause`, `buan`, `doma`, `prba`, and `clim`.
   - Why it matters: Recent changes added partner APIs, authentication, analytics, documents, and backoffice support to `p3`, which is good. But `cg4-p2` still shares the Professional Seller Workspace product rather than having a clearly named partner integration platform surface.
   - Suggested direction: Either rename/split `p3` to make the partner integration surface first-class, or add a dedicated partner product that owns API docs, sandbox, certification, diagnostics, auth scopes, and support workflows.

### Edit backlog

1. Change customer job `streamsNeeded` references from brick IDs to product-stream IDs, then keep brick dependencies inside streams.
2. Add explicit stream-to-customer/job/KPI mappings in `product-stream.json` or in generator-supported metadata.
3. Prune generated brick dependencies and external-system boilerplate; keep only relationships with real delivery, reliability, data, policy, or operational impact.
4. Extend deployment modeling beyond the 23 currently covered bricks, especially for trust/risk, data/intelligence, platform services, monetization, operations, and quality tooling.
5. Customize module shapes for search/ranking, payments, identity, fraud/risk, feeds, media, analytics, data platform, partner APIs, and support operations.
6. Reclassify brick investment statuses to match the domain brief's sequencing and customer strategy horizons.
7. Rewrite stream flow key facts and pain points with classifieds-specific operational detail.
8. Preserve the corrected data ownership model and make high-risk data assets visible in relevant streams and deployment products.

