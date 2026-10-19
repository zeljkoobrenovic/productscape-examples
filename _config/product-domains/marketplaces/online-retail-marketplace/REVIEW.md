# online-retail-marketplace Review

> **Status note (2026-07-04):** The `## Product Domain Review` and `## Product Bricks Review` sections were refreshed against the current source data.

## Product Domain Review

Updated: 2026-07-04

### Executive assessment

- The current domain model validates cleanly with `python3 .codex/skills/scripts/validate-domain-model.py online-retail-marketplace` (`14 JSON files, 30 product bricks`) and is strategically coherent enough for generated documentation.
- Customer segmentation is now materially distinct across Prime shoppers, sellers, advertisers, marketplace trust/compliance operators, and fulfillment/customer-resolution operators. Modeling the two operator groups as customers is justified by the jobs and guardrail KPIs they carry.
- Recent changes fixed several previous review findings: insight items now carry stable KPI, stream, and brick links plus confidence/type labels; curated links now have IDs and `lastChecked`; competition records now include structured overlap/threat fields; and product `p6` now explains its narrow operator-console scope.
- Strategy horizons remain strong. The 1-year, 3-year, and 5-year narratives include useful tradeoff guardrails around privacy, personalization, retail-media density, fulfillment cost-to-serve, seller trust, enforcement automation, and recovery economics.
- Implementation grounding is materially better than the older review implied: all 30 product bricks are deployed, streams include customer/KPI/insight IDs and supporting brick dependencies, and the data model has 26 assets with governance and system-of-record bricks.
- The remaining domain-quality gaps are decision provenance and scope metadata: KPI values are still illustrative, and some top-level competition/product-scope metadata is thinner than the rest of the model.

### High-priority findings

1. KPI values are labeled as examples but still not decision-provenance ready

   - Evidence: `_config/product-domains/marketplaces/online-retail-marketplace/customers/customers.json` contains 70 KPI objects with `currentValue`, `target`, `unit`, and `valueStatus: "example"`. All 70 lack `period`, `valueSource`, and `calculationMethod`; 20 branch composite KPIs such as `co-cg1-b1`, `co-cg3-b2`, `bo-cg4-b1`, and `bo-cg4p2-b2` have no explicit `target`.
   - Why it matters: Marking values as examples prevents false precision, but the KPI tree still cannot support real product tradeoff decisions. Branch scores can hide critical misses in false positives, regulator SLA, refund leakage, checkout success, or on-time promise adherence unless weighting and guardrail behavior are explicit.
   - Suggested direction: Keep `valueStatus: "example"` if values are illustrative. For any operational KPI, add `period`, `valueSource`, and `calculationMethod`; for branch composites, define weighting or cap/guardrail behavior so critical leaf metrics can constrain the branch score.

### Medium-priority findings

1. Competition coverage is broad, but the file lacks top-level scope and caveats

   - Evidence: `_config/product-domains/marketplaces/online-retail-marketplace/business/competition.json` includes 12 players: `amazon`, `walmart_marketplace`, `mercado_libre`, `ebay`, `pdd_holdings_temu`, `shopify`, `instacart`, `tiktok_shop`, `google_ads_commerce`, `meta_commerce_ads`, `target_roundel`, and `costco`. Business stats preserve metric, value, period, scope, source title, and source URL, and player records include `customerOverlap`, `threatAxes`, `differentiators`, `weaknesses`, and related customer/insight IDs.
   - Why it matters: Coverage and per-player structure are now strong, but the file does not expose a top-level scope, inclusion logic, regional caveat, or comparability caveat. A generated landscape can therefore look more comparable than the market really is across marketplace, retail media, grocery, social commerce, and warehouse-club models.
   - Suggested direction: Add lightweight top-level metadata that explains inclusion criteria, comparison caveats, and the intended use of `category`, `customerOverlap`, and `threatAxes`.

2. Product portfolio descriptions are uneven

   - Evidence: `_config/product-domains/marketplaces/online-retail-marketplace/product-deployments/products.json` gives `p6` a strong description and `consumesProductsForOperations`, while `p1` through `p5` mostly contain `id`, `name`, `type`, and `primaryCustomers`.
   - Why it matters: `p6` now resolves the old ambiguity around operator consoles, but the customer-facing and partner-facing products are not equally explicit about scope. Generated product pages can show names and customers but not enough about what each product owns, exposes, or depends on.
   - Suggested direction: Add concise descriptions and product-scope notes to `p1` through `p5`, especially where products share bricks or operational dependencies such as identity, reporting, payout, delivery promise, and partner APIs.

3. High-assumption insights are correctly labeled but still need validation paths

   - Evidence: `_config/product-domains/marketplaces/online-retail-marketplace/customers/insights.json` items `orm-09` and `orm-10` are marked as `evidenceType: "strategic-inference"` with `assumptionLevel: "high"`.
   - Why it matters: The model now distinguishes sourced facts from strategic inferences, which is good. The next risk is that high-assumption insights may be treated as equally proven in roadmap or KPI conversations.
   - Suggested direction: Add a short validation note, research question, or follow-up evidence target for high-assumption insights so future editors know what would raise confidence or narrow the claim.

### Targeted improvement backlog

1. Add `period`, `valueSource`, and `calculationMethod` to KPI objects in `customers/customers.json` where the values are intended to be more than illustrative examples.
2. Define weighting or guardrail behavior for composite KPI branch scores in `customers/customers.json`; expected outcome: branch health scores do not hide critical metric misses.
3. Add top-level scope, inclusion logic, and comparison caveats to `business/competition.json`; expected outcome: broad competition coverage remains interpretable across different business models.
4. Add concise descriptions and scope notes to products `p1` through `p5` in `product-deployments/products.json`; expected outcome: product pages explain ownership and dependency boundaries as clearly as `p6`.
5. Add validation notes or follow-up evidence targets for high-assumption insights `orm-09` and `orm-10` in `customers/insights.json`.

### Open assumptions

- Are KPI `currentValue` fields intended to remain generated illustrative examples, or should some be upgraded to measured/benchmarked values with periods and sources?
- Should competition remain a broad archetype-level landscape, or should later edits model regional and category-specific competitors more deeply?
- Should `p1` through `p5` stay as lightweight product entries, or should they receive the same explicit scope treatment as `p6`?
- Are `orm-09` and `orm-10` acceptable as high-assumption strategic inferences, or should they be backed by additional research before strategy use?

## Product Bricks Review

Updated: 2026-07-04

### Architecture assessment

- The implementation model validates cleanly with `python3 .codex/skills/scripts/validate-domain-model.py online-retail-marketplace`, covering 14 JSON files and 30 product bricks.
- The recent architecture changes fixed several previous blockers: all 30 product bricks are deployed at least once, the data catalog has 26 governed assets with system-of-record bricks, and streams now carry customer/KPI/insight links.
- Brick taxonomy is credible for a mature marketplace: Shopper Experience, Seller Growth, and Marketplace Foundations are durable capability groups rather than a task list.
- Product streams are now outcome-based and implementation-aware. Important support dependencies have been added to trust, retail media, recovery, and fulfillment streams, including appeal/regulator-evidence and payout-reconciliation flow steps.
- The layered module model is stronger than before. Important bricks now include APIs, workers, integration modules, event processors, model-serving modules, and stateful service modules where the architecture needs them.
- Remaining implementation risk is now about operating precision rather than coverage: some external-system IDs diverge between stream and brick levels, and several mature bricks remain thinly modeled.

### Critical findings

1. External-system IDs are stable locally but not normalized across stream and brick levels

   - Severity: High
   - Source: `_config/product-domains/marketplaces/online-retail-marketplace/product-bricks/product-stream.json`; `_config/product-domains/marketplaces/online-retail-marketplace/product-bricks/product-bricks.json`.
   - Why it matters: External systems now have IDs, which fixes the old text-only problem. However, equivalent systems still use different IDs at different levels, for example stream `ext-regulator-reporting-endpoints` versus brick `ext-regulator-and-transparency-reporting-endpoints`, stream `ext-banking-tax-rails` versus brick `ext-banking-and-tax-rails`, and stream `ext-seller-erp-integrators` versus brick `ext-seller-erp-repricer-and-integrator-systems`. This prevents clean reuse, ownership, and consistency checks.
   - Suggested direction: Introduce a small external-system catalog or normalize IDs across stream and brick objects. Keep stream descriptions outcome-focused, but link them to the same governed system IDs used by brick modules.

### Model-quality findings

1. Several mature bricks remain thinly modeled

   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/online-retail-marketplace/product-bricks/product-bricks.json` bricks `bran`, `price`, `supp`, `iden`, `reco`, and `apii`.
   - Why it matters: The module model is much stronger than before, but several mature marketplace capabilities still have minimal layer decomposition. Brand registry, offer health, seller-fulfilled operations, identity/entitlements, personalization, and external integrations usually need explicit APIs, workers, policy services, data quality checks, or operational tooling where reliability and ownership are material.
   - Suggested direction: Add modules only where they clarify ownership or risk: verification/review workflows for `bran`, offer-health event processing for `price`, carrier/event adapters for `supp`, entitlement/audit interfaces for `iden`, model/feature pipeline boundaries for `reco`, and partner onboarding/observability modules for `apii`.

2. Product stream dependency types are useful but need consistent semantics

   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/online-retail-marketplace/product-bricks/product-stream.json` streams `receive-and-recover-reliably`, `fulfill-with-prime-grade-reliability`, `grow-demand-with-retail-media`, and `protect-marketplace-trust`.
   - Why it matters: Streams now include `composition` and `support` dependencies, which is good. The next issue is semantics: support dependencies sometimes mean evidence, sometimes analytics, sometimes operational fallback, and sometimes external integration. Without conventions, generated stream pages can show the relationship but not the operating expectation.
   - Suggested direction: Define a small vocabulary or description convention for support dependencies, such as evidence, analytics, operational fallback, partner integration, or control-plane dependency.

3. Product deployment scope is improved, but product-to-product dependency semantics live outside the architecture map

   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/online-retail-marketplace/product-deployments/products.json` product `p6`; `_config/product-domains/marketplaces/online-retail-marketplace/product-deployments/deployment.json`.
   - Why it matters: `p6` now correctly says it consumes `p2`, `p4`, and `p5` capabilities instead of owning duplicate runtimes. That relationship is visible in product metadata, but not reflected in product streams or architecture dependency views.
   - Suggested direction: Keep `p6` narrow, but expose cross-product consumption in architecture traceability so operator-console dependencies on returns, FBA, inventory, analytics, and reporting are visible outside `products.json`.

### Traceability findings

1. Deployment coverage is complete, but product entries are unevenly descriptive

   - Severity: Medium
   - Source: `_config/product-domains/marketplaces/online-retail-marketplace/product-deployments/deployment.json`; `_config/product-domains/marketplaces/online-retail-marketplace/product-deployments/products.json`.
   - Why it matters: All 30 bricks are deployed, and `p6` has clear scope notes. Products `p1` through `p5` are much thinner, so the architecture is easier to trace at deployment level than product-scope level.
   - Suggested direction: Add concise product descriptions and scope notes for `p1` through `p5`, especially for shared runtime dependencies and partner/API surfaces.

### Edit backlog

1. Normalize external-system IDs across `product-bricks/product-stream.json` and `product-bricks/product-bricks.json`, or introduce a small external-system catalog; expected improvement: stream and brick dependencies can be cross-referenced consistently.
2. Enrich selected bricks only where module boundaries affect reliability or ownership: `bran`, `price`, `supp`, `iden`, `reco`, and `apii`.
3. Define support-dependency semantics in `product-bricks/product-stream.json`; expected improvement: readers can distinguish evidence, analytics, operational fallback, partner integration, and control-plane dependencies.
4. Expose `p6` cross-product consumption beyond `products.json`, likely through architecture traceability; expected improvement: operator-console dependencies are visible without overstating runtime ownership.
5. Add concise product descriptions and scope notes for `p1` through `p5` in `product-deployments/products.json`.

