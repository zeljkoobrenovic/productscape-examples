# Payments and Revenue Infrastructure Review

## Product Domain Review

Updated: 2026-11-15

The assessment below records the model **before the approved implementation**. The [implementation record](#implementation-record--2026-11-15) at the end documents the completed changes and final verification.

Scope: the source model for `other/payments-and-revenue-infrastructure`, current public product documentation, financial disclosures, and regulatory sources. The domain brief explicitly models **Stripe**. Adyen is examined in depth as a competing platform and as a test of the model's completeness. Findings below distinguish local defects, reported facts, availability restrictions, and proposed modeling changes.

### Executive assessment

- **Keep the core thesis.** Merchant payments, recurring revenue, and platform money movement remain useful organizing loops. The model already connects customer jobs to recognizable capabilities and has properly branching KPI pyramids.
- **The research baseline needs a substantial refresh.** The competition file still uses FY2024 statistics, and all nine insight sources concern Stripe. Important developments in monetization, merchant-of-record services, money movement, and agentic commerce are missing or represented only as future scenarios.
- **Adyen needs more than a refreshed competitor card.** Its expansion into enterprise liquidity, usage-based billing, and loyalty changes the comparison across several existing products. The detailed assessment below separates established services, acquisitions undergoing integration, and restricted availability.
- **Structural validation passes, but semantic defects remain.** The KPI checker reports 54 unresolved strategy-to-pyramid names. Thirteen of 25 bricks have no product assignment through the deployment model. The data catalog contains capability descriptions and generated storage placeholders where financial entities and ownership should be.
- **Fix traceability and evidence before adding breadth.** A credible update should first repair the existing model, then introduce the few missing jobs and flows that explain the new market evidence. At the time of the initial assessment, this review added an editing backlog without changing domain JSON or the generated site. Implementation is recorded separately below.

### Evidence and validation

All local file references below are relative to this domain directory. Public sources were accessed on 2026-11-15. Publication dates are stated where they establish a sequence; a documentation access date is not a product launch date.

| Area | Current source model | Assessment |
| --- | --- | --- |
| Customer coverage | 3 groups, 3 personas, 6 jobs, 3 adoption journeys | Useful primary buyers; several operational responsibilities are compressed into the same personas. |
| KPIs | 6 pyramids, 42 nodes, 18 `dashboard.example.com` links | Tree structure is useful; references, measurement definitions, and target provenance need repair. |
| Product portfolio | 5 products | Broad enough for the original thesis, but assignments do not cover the advertised capabilities. |
| Capability model | 25 bricks, 50 module definitions | Every brick has exactly one web component and one service. This is a logical template, not evidence of vendor implementation. |
| Streams | 4 streams, each with one three-step flow | Too little operational detail for the breadth of payments, billing, finance, and devices. |
| Deployment model | 15 channels; 10 empty `Cloud 01`–`Cloud 10` channels | Remove unused scaffolding and qualify inferred operating surfaces. |
| Data | 17 assets and 17 stores | Every store uses `generated-starter`; every asset declares EU residency. |
| Research | 8 insights, 9 sources, 9 curated links | Stripe-only insight evidence; no substantive Adyen research. |
| Competition | Stripe plus 3 competitors | All reported financial periods are FY2024 or Q4 2024. |
| Residuality | 6 stressors | Useful scenarios, but fact labels and survival claims exceed the modeled evidence. |

Commands run from the data repository:

```text
python3 productscapes.py validate payments-and-revenue-infrastructure --strict-ids
PASS: 12 JSON files, 25 product bricks

python3 productscapes.py check-kpis payments-and-revenue-infrastructure
FAIL: 54 problems, 18 for each persona
```

The structural validator's success does not establish factual currency, metric consistency, or complete capability coverage. Counts above come from source objects; module dependency references are not counted as module definitions.

### High-priority findings

#### P1-01 — Refresh the factual baseline and separate vendor evidence from interpretation

**Evidence:** [business/competition.json](business/competition.json), `generatedOn: 2026-04-18`, players `stripe`, `adyen`, `paypal_braintree`, and `block_square`; [customers/insights.json](customers/insights.json), `updated: 2026-03-31`, insights `pri-01`–`pri-08`; [customers/links.json](customers/links.json), `updated: 2026-06-17`.

**Why it matters:** Recent metadata makes the model look current while the market statistics and product assumptions remain older. The source set supports a Stripe product overview but cannot substantiate a balanced competitive assessment. For example, the FY2025 Stripe and Adyen releases were already available before the competition file's generation date.

**Suggested direction:** Replace the current snapshot with the reported FY2025 baseline and separately labeled 2026 interim updates below. Preserve historical figures only when used as explicit comparisons. Add product documentation, Adyen evidence, competing business models, and scoped regulatory references to insights and curated links. Replace unsupported superlatives such as Adyen being the “strongest” challenger with the dimensions on which it competes. Keep published dates, access dates, and modeled assumptions distinguishable using schema-supported fields and notes.

#### P1-02 — Repair strategy references and make KPI targets honest

**Evidence:** [customers/customers.json](customers/customers.json), all `productStrategy.year1/year3/year5` objects for `cg1-p1`, `cg2-p1`, and `cg3-p1`. At lines 249 and 394, the pyramid name `Successful payment conversion` becomes `Successful payment conversion to 97.5%` in strategy. Later horizons contain aspirations such as `Lower close-cycle stress` in fields checked as KPI names. There are 18 placeholder dashboard URLs. Line 1383 places increased dependence on Stripe-managed flows in a customer KPI list.

**Why it matters:** Strategy cannot reliably resolve its measures. Precise figures such as 97.5% conversion, 112% net revenue retention, and 98.9% on-time payouts have no modeled baseline, cohort, observation window, or target rationale. Increased vendor attachment is a supplier outcome; it does not by itself demonstrate customer benefit.

**Suggested direction:** Use canonical pyramid names in references. Put target values in the supported descriptions or target fields, with an explicit illustrative-target label until grounded. Define numerator, denominator, cohort, period, and owner for each important measure. Keep customer economics separate from Stripe retention and cross-sell. Remove placeholder dashboard links or identify them as examples. Retain the existing branching structure; the defect is semantic, not a need for more KPI nodes.

#### P1-03 — Replace the starter data catalog with financial records and ownership

**Evidence:** [data/data-assets.json](data/data-assets.json), all 17 stores and their `technology: generated-starter`; all asset residency fields; assets including `payment-elements`, `authorization-optimization`, and `terminal-and-reader-operations`. In [product-bricks/product-bricks.json](product-bricks/product-bricks.json), `auth` depends on identity credentials, session tokens, access policy, and audit logs. `revn` depends on profile/contact/consent/payment-instrument records. Assets `revenue-recognition` and `tax-determination-and-registration` have no brick data references.

**Why it matters:** Payment authorization is being modeled like user login. Revenue recognition has no modeled revenue schedule to operate on. A capability label such as Payment Elements is not a substitute for a payment session, token reference, or authorization attempt. Blanket EU residency and one named database per asset appear more certain than the evidence supports.

**Suggested direction:** Define logical records first: payment intent/order reference, authorization attempt, capture, refund, dispute, token reference, subscription, price/contract version, usage event, credit grant, invoice, ledger entry, balance, transfer, payout, settlement batch, legal entity, beneficial owner, verification case, tax registration, and revenue schedule. Add records only for modeled flows. Assign ownership and read/publish dependencies to the relevant bricks. Treat physical stores, retention periods, and residency as unknown or explicitly assumed where public evidence does not establish them. Preserve identity/access records where they actually support operator or customer authentication.

#### P1-04 — Complete product and flow coverage before expanding the catalog

**Evidence:** [product-deployments/deployment.json](product-deployments/deployment.json), `channels[].channels[].deployedBricks[].usedInProducts`; [product-bricks/product-stream.json](product-bricks/product-stream.json), `accept-payments-globally` and its `protect-and-operate-the-transaction` step.

Eleven bricks have no deployment entry: `capm`, `disp`, `elem`, `iden`, `issu`, `kycb`, `pmtd`, `pyot`, `revn`, `taxx`, and `usag`. These plus `pmlk` and `rpts` have no product assignment. No stream references `term`, `pmlk`, `issu`, or `capm`. Terminal does have a product and customer job, so it is specifically a stream gap. The final payment-flow step has an empty dependency list despite promising transaction protection and operations.

**Why it matters:** Billing advertises usage, tax, and recognition without assigning their bricks to the product. Platform payouts lack assigned payout and verification capabilities. The model's views give different answers about what each product contains.

**Suggested direction:** Repair the authoritative `usedInProducts` associations and distinguish shared capabilities from product-specific ones. Connect the payment exception step to its actual risk, dispute, ledger, event, and reconciliation responsibilities. Add a unified-commerce flow. Either connect issuing and capital to explicit platform jobs or mark their scope as optional. Do not create speculative vendor deployments simply to make the graph complete: logical delivery surfaces are sufficient when labeled accordingly.

#### P1-05 — Model commercial responsibility and eligibility as part of the product

**Evidence:** [product-deployments/products.json](product-deployments/products.json), `p2`, `p3`, and `p5`; bricks `acct`, `kycb`, `taxx`, `pyot`, `issu`, and `capm`; [residuality/residuality.json](residuality/residuality.json), `liab` and `vpvr`.

**Why it matters:** Payment acceptance, being merchant of record, holding funds, extending finance, and sending payouts impose different responsibilities and have different eligibility rules. The current model groups several of these under a broad platform-money-movement narrative. Product availability also depends on the business's location and legal entity, not just the recipient country.

**Suggested direction:** For each material offering, record the buyer, merchant of record, account/funds owner, liability allocation, supported entity/region, funding source, and maturity. Separate Connect payouts, standalone Global Payouts, business financial accounts, and embedded financial accounts. Keep previews and acquisition plans out of the default production promise. The Stripe and Adyen assessments below supply the concrete distinctions.

### Stripe updates to incorporate

These changes affect the modeled business itself, rather than only its competitor list.

| Development and evidence | Consequence for this Productscape |
| --- | --- |
| **FY2025 scale:** Stripe reported $1.9 trillion in total volume, up 34%, and more than five million businesses using it directly or through platforms. Its February 24, 2026 update described the Revenue suite as on track for a $1 billion annual run rate in 2026; that statement is a forecast, not an achieved result. [Stripe 2025 update](https://stripe.com/newsroom/news/stripe-2025-update). | Replace the FY2024 volume headline. Preserve the reported metric name and distinguish processed volume, revenue, and forecast run rate. |
| **Metronome:** the acquisition completed on January 14, 2026. Current documentation directs new usage-billing integrations toward Metronome; Billing Meters remains supported for existing integrations and has different compatibility. [Acquisition completion](https://stripe.com/newsroom/news/stripe-completes-metronome-acquisition), [usage-billing documentation](https://docs.stripe.com/billing/subscriptions/usage-based). | Expand `usag`, `subs`, `invo`, and `cg2-p1` to cover contract pricing, commitments, credit consumption, usage corrections, and migration choices. Do not imply all existing Billing integrations require migration. |
| **AI monetization:** token billing through Metronome is documented as public preview, with usage ingestion, provider-price synchronization, markups, credits, and hybrid charging. [Token billing](https://docs.stripe.com/billing/token-billing). | Add the job of controlling margin while prices and usage change. Distinguish customer-visible credits from money balances and preserve the price version applied to each usage event. |
| **Managed Payments:** Stripe can act as merchant of record for eligible digital products and handle specified transaction, tax, fraud, and support responsibilities. The documented integration has product restrictions, including no Connect support. [Managed Payments](https://docs.stripe.com/payments/managed-payments). | Add an explicit choice between merchant-operated payments/tax and an eligible merchant-of-record arrangement. This changes the recurring-revenue buyer's work and introduces Paddle as a material alternative. |
| **Standalone money movement:** Global Payouts can pay recipients in more than 160 markets and requires a Treasury financial account. Sender availability is narrower: the US and UK, with specified EU countries and Australia in private preview in the documentation reviewed. [Global Payouts](https://docs.stripe.com/global-payouts). | Split `pyot` into clearly described responsibilities or submodules. Recipient reach must not be presented as sender eligibility. Model prefunding, beneficiary verification, FX, payout status, returns, and reconciliation. |
| **Business financial accounts:** Treasury documentation distinguishes business accounts from Treasury for platforms, and gives public/private preview limits by region. Stripe states that it is not a bank and describes partner-bank arrangements. [Treasury](https://docs.stripe.com/treasury). | Represent the contracting entity and bank relationship. A balance, bank account, and stablecoin wallet should not collapse into one data object or one universal availability claim. |
| **Stablecoin acceptance:** the documented flow supports customer payment in stablecoins with settlement in local fiat, subject to merchant-region restrictions. Refunds return to the original wallet; the flow differs from cards in disputes and capture support. [Stablecoin payments](https://docs.stripe.com/payments/stablecoin-payments). | Add a rail-specific path under payments and reconciliation. Keep acceptance, custody/wallets, cross-border payout, and stablecoin issuance as separate capabilities. |
| **Processor orchestration:** Stripe Orchestration is in private preview. It supports routing/retry across supported processors, but excludes non-card payments, Link, Connect, Terminal, and several other products; third-party disputes and settlement remain outside its management. [Orchestration](https://docs.stripe.com/payments/orchestration). | `pmtd` currently selects payment methods. Add processor routing as a distinct responsibility and update stressor `orch`; an existing limited product does not prove universal processor replaceability. |
| **Connect account model:** Accounts v2 supports configurations and capabilities around a shared identity, with remaining product/version limitations. [Accounts v2](https://docs.stripe.com/connect/accounts-v2). | Review `acct`, `kycb`, and customer/recipient records. Describe capability state and responsibility instead of treating a connected account as a single fixed role. |
| **Agentic commerce and treasury:** the Agentic Commerce Suite was announced in December 2025; Treasury for agents followed on October 21, 2026. The latter describes permissioned financial actions and human approvals, while some card/spending features were still described prospectively. [Commerce suite](https://stripe.com/en-es/newsroom/news/agentic-commerce-suite), [Treasury for agents](https://stripe.com/en-es/newsroom/news/treasury-for-agents). | Split agent-assisted selling from an agent spending a business budget. Extend `agnt` with authority, approval, revocation, and auditable execution records. Keep announced future functions distinct from current ones. |

Maintain a separate acquisition watchlist. Stripe's primary announcements describe **agreements** to acquire OpenRouter on August 19 and Parafin on September 30, 2026. Those announcements alone do not establish completed acquisitions or integrated product availability. [OpenRouter agreement](https://stripe.com/en-es/newsroom/news/stripe-agrees-to-acquire-openrouter), [Parafin agreement](https://stripe.com/en-es/newsroom/news/stripe-agrees-to-acquire-parafin).

### Adyen in depth

#### Financial and commercial baseline

The existing Adyen card's FY2024 figures should be replaced with a full-year baseline and a separately dated current update.

| Reporting period | Reported measures | Interpretation for the model |
| --- | --- | --- |
| **FY2025** | Processed volume **€1,394.3 billion**; net revenue **€2,364.2 million**; point-of-sale volume **€311.0 billion**; EBITDA **€1,245.7 million**, margin **53%**. [H2/FY2025 results, February 12, 2026](https://www.adyen.com/press-and-media/adyen-publishes-h2-2025-financial-results-3pgu2). | Use net revenue and processed volume as distinct measures. The substantial POS business supports deeper unified-commerce coverage. |
| **H1 2026** | Processed volume **€803.8 billion**; net revenue **€1,302.9 million**; EBITDA **€641.5 million**, reported margin **49%**. [H1 2026 results, August 13, 2026](https://www.adyen.com/press-and-media/adyen-publishes-h1-2026-financial-results-3wjne). | Preserve the half-year period. Acquisition-related costs affect interpretation of the margin. |
| **Q3 2026** | Processed volume **€451 billion**, up **30%**; net revenue **€738 million**, up **23% reported / 22% constant currency**. Acquisitions contributed about **2 percentage points** to constant-currency net-revenue growth. [Q3 prepared remarks, October 28, 2026](https://brand.adyen.com/api/asset/eyJjbGllbnRJZCI6bnVsbCwiaWQiOjE0NzUwOSwidGltZXN0YW1wIjoxNzkzMTc3ODM5LCJ2ZXJzaW9uIjoxNzkzMTc3ODM1fQ:adyen:W8c6ztVo-QbPUT0kc06ygd7XySPDZ8kt8nyG-73WhGs/download). | Latest quarterly evidence is more useful than another undated scale claim. Separate organic expansion from acquired revenue. |

Adyen's Q3 breakdown was €387 million Digital, €250 million Unified Commerce, and €100 million Platforms net revenue; rounding explains the difference from the total. Management identified increased share of existing merchants' volume as the largest growth contributor. This supports a customer-expansion strategy, but it does not turn vendor share of wallet into a customer-success KPI. [Q3 prepared remarks](https://brand.adyen.com/api/asset/eyJjbGllbnRJZCI6bnVsbCwiaWQiOjE0NzUwOSwidGltZXN0YW1wIjoxNzkzMTc3ODM5LCJ2ZXJzaW9uIjoxNzkzMTc3ODM1fQ:adyen:W8c6ztVo-QbPUT0kc06ygd7XySPDZ8kt8nyG-73WhGs/download).

Do not rank Stripe, Adyen, PayPal, and Square by these figures as though they measured identical businesses. Currency, period, payment scope, business mix, and revenue definitions differ. The current competition file already acknowledges comparability limits; retain that useful caveat.

#### Positioning and licensed infrastructure

Adyen belongs in the comparison for online acceptance, physical commerce, platform payments, and financial operations. Its April 9, 2026 Intelligent Money Movement announcement brings payments, liquidity management, and payouts into an enterprise proposition. This makes treasury and finance decision-makers relevant alongside payments and commerce teams. [Intelligent Money Movement](https://www.adyen.com/press-and-media/adyen-launches-intelligent-money-movement).

The legal infrastructure is a meaningful comparison dimension, but it needs precise labels. Adyen's European disclosure describes its Dutch credit-institution authorization and EEA passporting, with separate UK arrangements. Its US disclosure describes a federally licensed branch supervised by the OCC and Federal Reserve. A generic “bank everywhere” badge would conceal product and jurisdiction differences. [European licenses](https://www.adyen.com/en_GB/licenses/europe), [US licenses](https://www.adyen.com/licenses/united-states).

**Model implication:** introduce a jurisdiction/capability/responsibility view across acceptance, accounts, payouts, issuing, and financing. This is a proposed logical model, not a claim about Adyen's internal database design. It should let a reader answer who may use a service, which entity supplies it, where funds sit, and what happens when a capability is suspended.

#### Payments performance extends across the funnel

Adyen Uplift combines five named modules: Personalize, Tokenize, Protect, Authenticate, and Optimize. The product links method presentation, credentials, fraud decisions, authentication, and authorization rather than treating authorization rate as an isolated outcome. [Adyen Uplift](https://www.adyen.com/uplift).

**Model implication:** compare the joint behavior of `chck`, `elem`, `pmtd`, `auth`, and `rada`. Add explicit token lifecycle and payment-authentication responsibilities where needed. Measure successful collection together with fraud loss, payment cost, and customer friction. A vendor's selected case-study uplift should not become a general target or an apples-to-apples benchmark against another provider.

A useful evaluation flow would select a payment cohort, establish a baseline, change an eligible optimization, and observe conversion and economic guardrails over a defined period. The model currently jumps from a product promise to a precise target without this measurement work.

#### Unified commerce needs a complete operational flow

Adyen's unified-commerce documentation covers connected shopper insights and cross-channel experiences, including purchases and returns across online and physical channels. Its POS support is country-specific. This is broader than attaching a reader to checkout. [Unified commerce documentation](https://docs.adyen.com/unified-commerce).

The recommended flow for `p4` is: configure the merchant/store and device estate; initiate an online or in-store sale; authenticate and collect payment; identify the order across channels; handle returns or adjustments; reconcile settlement to the order and finance system. Include the handoffs to the merchant's commerce and inventory systems as external dependencies, rather than implying the payment provider owns them.

Offline behavior belongs in this flow. Adyen documents offline EMV and store-and-forward options with method/device restrictions and merchant exposure if payment cannot subsequently be collected. Offline processing is not a general solution to an Adyen platform outage. [Offline payments](https://docs.adyen.com/point-of-sale/offline-payment/).

**Specific updates:** connect `term` to a stream; give store operators responsibility for reader readiness and exception handling; distinguish a locally accepted transaction from successful later capture and settlement; add offline queue and reconciliation outcomes. Preserve the existing omnichannel customer job rather than adding a duplicate.

#### Platforms require a richer account and liability model

Adyen for Platforms covers onboarding, verification, payment splitting, balances, payouts, and financial products for platform users. Its payment-processing hierarchy and balance platform are different structures. [Platforms overview](https://docs.adyen.com/platforms).

The account documentation distinguishes company/merchant/store resources from legal entities, account holders, balance accounts, payment instruments, and grant accounts. The platform's liable balance account can cover negative user balances arising from refunds and chargebacks. Balance platforms are also separated by acquiring region. [Account structure](https://docs.adyen.com/platforms/account-structure-resources).

**Model implication:** keep the vendor-neutral concepts of legal party, permissions, owned balance, transfer destination, reserve/liability, and verification state. Map these separately to Stripe and Adyen terminology. A Stripe connected account is not a universal synonym for every Adyen resource. Add the seller or recipient's view: why activation is blocked, which documents are needed, when funds become available, and how to resolve a payout failure.

Adyen's **multi pay-in** can bring funds acquired by third parties into the platform balance system, but its documentation labels the feature a limited pilot. It should not be described as a generally available checkout failover router. [Multi pay-in](https://docs.adyen.com/platforms/multi-pay-in).

#### Money movement and embedded financial products need separate availability labels

| Offering | Verified boundary | Recommended treatment |
| --- | --- | --- |
| Intelligent Money Movement | Enterprise proposition combining collection, liquidity, and payouts. The announcement is not a country-by-country entitlement list. [Announcement](https://www.adyen.com/press-and-media/adyen-launches-intelligent-money-movement). | Add treasury operations and cash availability to the competitive comparison; qualify deployment by the contracted product and region. |
| Business accounts | Documentation labels the feature **in development**. Eligibility depends on the legal entity and associated individuals/beneficial owners, with supported US, UK, and Eurozone regions and exclusions. [Business accounts](https://docs.adyen.com/business-accounts). | Track account eligibility, onboarding evidence, transfer authorization, and account statements. Do not mark worldwide general availability. |
| Issuing | Supports physical/virtual cards, transaction rules, and authorization integrations. [Issuing documentation](https://docs.adyen.com/issuing). | Separate issued cards from acceptance credentials. Model controls, authorization decisions, balance impact, and disputes within an explicit use case. |
| Capital | Financing is offered to eligible platform users, with a fixed fee and repayment linked to processed volume; supported regions and invitation requirements apply. [Capital documentation](https://docs.adyen.com/capital). | Give `capm` a financing offer, acceptance, repayment, and exception lifecycle. Do not infer universal credit access from payment-processing eligibility. |

For both vendors, evaluate money movement through actual funds availability, failed/returned transfers, cutoffs, prefunding needs, FX, and reconciliation. A payout API acknowledgement is not evidence that the beneficiary has received spendable money. These are proposed customer outcomes, not published vendor service guarantees.

#### Orb and Talon.One change the revenue and loyalty comparison

Adyen completed the acquisitions of **Orb and Talon.One on July 1, 2026**. The completion announcement says integration was beginning. They should therefore be represented as acquired offerings with integration progress, not as independent competitors or proof that every function already shares one technical implementation. [Acquisition completion](https://www.adyen.com/press-and-media/adyen-closes-talonone-and-orb-acquisitions-announces-leadership-updates).

Orb brings usage-based billing and flexible pricing into the comparison with Stripe's revenue products. Adyen's September explanation describes pricing simulation, credits, and varied commercial models, while also describing future integration benefits. [Why Adyen acquired Orb](https://www.adyen.com/knowledge-hub/why-adyen-acquired-orb).

Talon.One adds promotion and loyalty capabilities. Its joint direction with Adyen connects incentives to the commerce relationship; the payment provider's access to transaction data does not automatically establish consent for every personalization use. [Talon.One's account of the combination](https://www.talon.one/blog/the-next-chapter-for-adyen-and-talon-one).

**Model implication:** revise the recurring-revenue comparison to cover pricing flexibility, metering correctness, credits, enterprise contracts, invoicing, collection, and accounting handoffs. Add promotion/loyalty as an adjacent capability or external dependency where it supports a modeled customer job. Do not infer native tax filing, merchant-of-record services, or full revenue-recognition parity merely from the Orb acquisition. Similarly, do not continue a blanket claim that Adyen's entire expanded portfolio was built internally.

#### Agentic commerce changes channels and delegation

Adyen Agentic was announced on June 16, 2026 with Feed, Cart, and Payments layers. These connect product discovery, current checkout information, and payment processing while preserving the merchant's commercial relationship. The announcement specified limited availability for US enterprise merchants; the current product page still identifies US availability. [Launch announcement](https://www.adyen.com/press-and-media/adyen-agentic), [current product page](https://www.adyen.com/agentic-commerce).

The documentation now distinguishes merchants from agent platforms and provides integration paths for agentic protocols. That establishes concrete integration work, not a universal guarantee of access or interoperability across every emerging agent ecosystem. [Agentic documentation](https://docs.adyen.com/online-payments/agentic-commerce).

**Model implication:** model at least three separate responsibilities: publish accurate purchasable offers; preserve current price, availability, tax, and fulfillment information at checkout; validate authorized payment execution. For the existing corporate-spending stressor `agnt`, additionally represent the principal, delegated authority, spending constraints, approval escalation, revocation, and evidence of execution. Selling through an agent and authorizing an agent to spend treasury funds are related but different jobs.

#### Compare operating economics and integration effort

Adyen's pricing page separates a processing fee from the payment-method fee and prices additional products separately. Card pricing can use interchange-plus-plus. These facts do not establish that it is cheaper or more expensive for a particular merchant. [Pricing](https://www.adyen.com/pricing).

A useful Stripe–Adyen comparison should therefore use a stated merchant profile: regions, channels, method mix, average transaction size, cross-border share, refund/dispute rates, payout needs, and product bundle. Assess total payment cost, retained revenue after loss, cash availability, and integration/operations effort. Avoid a generic “Stripe for startups, Adyen for enterprises” conclusion: the domain's jobs require a more specific comparison.

Integration reliability also belongs in the model. Stripe documents duplicate and unordered webhook delivery; Adyen requires appropriate acknowledgement, authenticity checks, and duplicate handling. The merchant integration needs durable event processing and state reconciliation, rather than treating `webh` as a dashboard feature. [Stripe webhooks](https://docs.stripe.com/webhooks), [Adyen webhook handling](https://docs.adyen.com/development-resources/webhooks/handle-webhook-events).

### Refresh the wider competitive landscape

#### Update existing players without mixing metric scopes

| Player | Replacement facts | Scope to preserve |
| --- | --- | --- |
| Stripe | FY2025 total volume **$1.9 trillion**. [Annual update](https://stripe.com/newsroom/news/stripe-2025-update). | Company-reported volume; not Stripe revenue. |
| Adyen | Use the FY2025 and 2026 figures above. | Net revenue, processed volume, and POS volume remain separate measures. |
| PayPal / Braintree | FY2025 TPV **$1.79 trillion**, **25.4 billion** payment transactions, **439 million** active accounts at year end. Q3 2026 TPV **$487.1 billion**, **440 million** active accounts. [FY2025 Form 10-K](https://www.sec.gov/Archives/edgar/data/1633917/000163391726000024/pypl-20251231.htm), [Q3 2026 release](https://www.sec.gov/Archives/edgar/data/1633917/000163391726000086/pypl3q-26earningsrelease.htm). | These are PayPal group measures, not Braintree-only volume or unique people. TPV excludes gateway-exclusive transactions. |
| Block / Square | FY2025 **Square GPV $250.461 billion**; Q3 2026 **Square GPV $76.359 billion** and Square gross profit **$1.157 billion**. [FY2025 shareholder letter](https://www.sec.gov/Archives/edgar/data/1512673/000119312526076557/d108590dex991.htm), [Q3 2026 shareholder letter](https://www.sec.gov/Archives/edgar/data/1512673/000162828026069513/q32026shareholderletter.htm). | Square segment GPV is distinct from Block total GPV and group gross profit. |

FY2026 is not complete at the review date. Do not annualize the quarterly figures into reported full-year results. Update each retained statistic individually with its source, period, units, and business scope; do not merely change the file's date.

#### Add alternatives where they change a customer decision

| Alternative | Why it belongs | Evidence and modeling consequence |
| --- | --- | --- |
| **Checkout.com** | Direct enterprise payment-performance alternative for `cg1-p1`. | Reported roughly $300 billion processed in 2025 and offers acceptance optimization. Add it to global digital acceptance evaluations, with merchant-specific performance evidence. [FY2025 update](https://www.checkout.com/newsroom/checkout-com-returns-to-full-year-profitability-and-surpasses-300b-in-volume-as-it-positions-for-the-era-of-agentic-commerce). |
| **Global Payments / Worldpay** | Enterprise acquiring, physical commerce, and platform distribution are material alternatives. | Worldpay's acquisition by Global Payments completed January 12, 2026. Represent the current ownership rather than presenting an outdated FIS-owned business. [Completion announcement](https://investors.globalpayments.com/financial-information/all-sec-filings/content/0001104659-26-002705/tm262856d1_ex99-1.htm). |
| **Airwallex** | Relevant where global accounts, FX, spend, payouts, and embedded finance drive the purchase. | Its current regional offering combines accounts, payments, billing, and spend. Compare by the customer's entity and region. [US product/pricing scope](https://www.airwallex.com/en-us/pricing). |
| **Paddle** | A different operating model for eligible SaaS/digital sellers. | Merchant-of-record billing includes specified payment, subscription, and tax responsibilities. This is a decision about who performs the work and bears obligations, not another gateway checkbox. [Paddle for SaaS](https://developer.paddle.com/get-started/how-paddle-works/saas/). |
| **Chargebee** | A revenue-system alternative for `cg2-p1`, including usage/hybrid pricing and revenue operations. | Distinguish the billing layer and its processor integrations from direct acquiring. [Chargebee Billing](https://www.chargebee.com/billing/). |
| **Spreedly** | A substitute architecture for merchants retaining control across processors. | Vaulting, routing, and payment connectivity make it relevant to `orch`, even though its role differs from an acquirer. [Spreedly platform](https://www.spreedly.com/). |

Organize competitors by the jobs and buying choices they contest. A single undifferentiated ranking would hide the difference between an acquirer, a billing system, a merchant of record, a business-account provider, and an orchestration layer. Avoid double-counting Orb and Metronome as independent vendors after their acquisitions.

### Medium-priority findings

#### P2-01 — Make secondary buyers and operators visible

**Evidence:** [customers/customers.json](customers/customers.json), `cg1-p1` Growth Commerce GM, `cg2-p1` SaaS Revenue Operations Lead, and `cg3-p1` Platform Payments GM; [customers/relations.json](customers/relations.json), all eight relations.

**Why it matters:** These three personas are useful commercial anchors, but they compress store operations, treasury, finance control, integration engineering, risk/compliance, and platform recipients into managerial buyers. The relationship graph also implies particular commerce/SaaS/platform interactions without establishing that they apply to all members of each group.

**Suggested direction:** Add explicit stakeholders or a small number of distinct personas where ownership changes the job. Prioritize a treasury/controller role and the platform seller/recipient experience; make store and integration responsibilities visible in their flows. Label the relations as illustrative ecosystem hypotheses. Do not expand persona counts merely to match another domain.

#### P2-02 — Replace generic adoption prose and anchor the strategy horizons

**Evidence:** [customers/customers.json](customers/customers.json), journeys `journey-cg1-p1-1`, `journey-cg2-p1-1`, and `journey-cg3-p1-1`, especially Discovery and Evaluation; all `productStrategy` objects. [start/config.json](start/config.json) contains a name and description but no integrated strategic narrative.

**Why it matters:** The journeys use the correct adoption stages, but repeat generic channels and instructional prose such as “Discovery is the awareness moment.” They do not explain how a payments procurement exercise differs from a billing migration or platform launch. Relative year-one/three/five ambitions also lack a declared starting point.

**Suggested direction:** Ground evaluation in the actual choice: market/method coverage and cohort performance for merchants; pricing correctness and migration reconciliation for revenue operators; onboarding conversion, liability, and payout exceptions for platforms. Add trial exit criteria and adoption evidence. Anchor horizons to the refresh date and sequence foundations, expansion, and optional bets. Describe supplier strategy and customer value separately.

#### P2-03 — Qualify architecture claims and add external dependencies

**Evidence:** [product-bricks/product-bricks.json](product-bricks/product-bricks.json), all 25 two-module bricks and empty external-system lists; [product-deployments/deployment.json](product-deployments/deployment.json), `runtime-cloud` and `core-api-runtime`; [product-bricks/product-stream.json](product-bricks/product-stream.json), empty external-system lists.

**Why it matters:** Public products do not reveal a provider's complete internal service topology. At the same time, the logical flows omit the external relationships that explain money movement and failure: issuers/acquirers, schemes, bank rails, identity sources, commerce systems, and finance systems. Webhooks, metering, readers, and settlement are awkwardly forced into identical web-component/service pairs.

**Suggested direction:** Explicitly identify the architecture as a logical capability model. Remove empty cloud scaffolding. Use the repository's supported module types to distinguish interfaces, asynchronous processing, devices, and operator surfaces where that distinction explains responsibility. Add justified external actors and contracts. Avoid inventing vendor cloud regions, storage technologies, internal services, or physical deployments.

#### P2-04 — Rework resilience scenarios against current capabilities and legal scope

**Evidence:** [residuality/residuality.json](residuality/residuality.json), metadata note describing stressors as business-context facts; `exit`, `curr`, and `liab` marked integrated; `agnt` and `orch` candidate; `vpvr` already survived. The residuality method reference does not substantiate specific legal events or vendor readiness.

**Why it matters:** Some stressors are deliberate hypothetical changes; others overlap with current offerings or obligations. A narrative reuse of an earlier residue does not prove the existing bricks and data implement the required behavior. In particular, instant credit transfers and beneficiary verification should not become a blanket assertion that every merchant payout must be instant.

**Suggested direction:** Preserve scenario exploration, but label scenario premises separately from established facts. For an integrated or survived status, identify the actual modeled capability, data, owner, and exception flow that carries the response. Revisit `agnt` and `orch` using the restricted current offerings above, while retaining future scale and concentration risks as scenarios.

The EU Instant Payments Regulation has different implementation dates by institution type, currency, and location. The ECB identifies the 2025 euro-area milestones and later deadlines for other categories. Tie `vpvr` to the relevant payment service and institution rather than treating the rule as universal. [ECB implementation overview](https://www.ecb.europa.eu/paym/retail/instant_payments/html/instant_payments_regulation.ht.html).

Update trust references beyond a generic PCI homepage. PCI DSS v4.0.1 retained the March 31, 2025 effective date for the previously future-dated requirements. DORA has applied since January 17, 2025 to in-scope financial entities; its relevance depends on the modeled entity and ICT relationship. Add responsibility and operational evidence, not an unqualified compliance badge. [PCI SSC version guidance](https://blog.pcisecuritystandards.org/just-published-pci-dss-v4-0-1), [ESMA DORA overview](https://www.esma.europa.eu/esmas-activities/digital-finance-and-innovation/digital-operational-resilience-act-dora).

### Proposed customer outcomes and flow improvements

These are candidate measures and modeling actions, not claims about current vendor performance. Select the ones needed by the chosen personas and give each a baseline before setting targets.

| Job or flow | Observable outcome | Important guardrails and dependencies |
| --- | --- | --- |
| Improve online payment performance | Captured payments per eligible checkout attempt, segmented by market/method/cohort. | Fraud/dispute loss, payment cost, abandonment, duplicate charges; distinguish checkout conversion from issuer authorization. |
| Operate online and physical commerce | Orders and refunds reconciled across channels; device readiness; aged unresolved offline transactions. | Store identity, order linkage, terminal state, delayed capture, inventory/commerce handoffs. |
| Monetize usage and AI services | Correctly billed usage, invoice adjustment rate, pricing-change lead time, and gross margin by pricing cohort. | Late/duplicate usage, rate versions, credit exhaustion, enterprise commitments, collections, and accounting treatment. |
| Activate a platform seller | Eligible applicants reaching their first successful financial activity within a defined period. | Verification exceptions, capability restrictions, negative balances, seller support, and risk review. |
| Make funds available to recipients | Beneficiaries receiving funds within the promised window; aged failed/returned transfers. | Available balance, verification result, prefunding, currency, route, cutoff, and return handling. |
| Close and reconcile financial activity | Automatic match rate and age/value of unreconciled items; time to close. | Gross/net/fee/FX differences, late events, refunds/chargebacks, settlement batches, and finance-system exports. |
| Execute delegated spending | Correctly authorized actions completed within policy; approval and exception resolution time. | Mandate scope, revocation, budget, recipient, audit evidence, and recovery from ambiguous execution. |

Start with the existing streams. Complete payment protection, flesh out billing corrections and collections, and deepen platform onboarding/payout exceptions. Add unified commerce because an existing product and job already require it. Introduce separate treasury or delegated-spending streams only when their customer roles and product boundaries are explicit.

### Targeted improvement backlog

| Order | Priority | Affected files and objects | Edit-ready action and completion criterion |
| --- | --- | --- | --- |
| 1 | P1 | `customers/customers.json`, all three personas | Resolve all 54 KPI-name failures; remove or label the 18 example dashboard links. Separate targets from canonical names and distinguish customer measures from supplier expansion. KPI checker passes without weakening its rules. |
| 2 | P1 | `business/competition.json`, all four players | Replace stale statistics with the reported periods above. Each statistic preserves metric, units, period, entity scope, and source. Preserve comparability caveats. |
| 3 | P1 | `customers/insights.json`, `customers/links.json` | Refresh `pri-01`–`pri-08` and add evidence for changed responsibilities, monetization, financial accounts, and Adyen. Every implication has a supporting source or an explicit assumption label. |
| 4 | P1 | `business/competition.json`, `adyen` | Expand beyond processing scale: Uplift, unified commerce, Platforms, Intelligent Money Movement, financial products, Orb, Talon.One, and Agentic. Show integration/availability boundaries and comparison dimensions. |
| 5 | P1 | `data/data-assets.json`; brick `dataDependencies` | Replace capability-shaped records with financial entities, assign ownership, repair `auth`/`revn`/`taxx`, and remove unsupported physical-store/residency assertions. Every important flow has the data it needs. |
| 6 | P1 | `product-deployments/deployment.json`, `products.json` | Resolve the 13 missing product assignments and 11 missing delivery mappings, with documented exclusions where intentional. Remove the 10 empty cloud channels. Do not invent physical infrastructure. |
| 7 | P1 | Bricks `usag`, `subs`, `invo`, `taxx`, `acct`, `pyot`; products `p2`, `p3`, `p5` | Represent Metronome/Billing choices, merchant-of-record boundaries, account configurations, and distinct payout/financial-account products. Each has an explicit buyer, responsibility, and availability statement. |
| 8 | P2 | `customers/customers.json`, `customers/relations.json` | Add missing operational ownership, differentiate evaluations, anchor strategy horizons, and label illustrative ecosystem relations. Each new role must justify a distinct decision or job. |
| 9 | P2 | `product-bricks/product-stream.json` | Complete payment exceptions, usage corrections, onboarding remediation, and payout returns. Add unified commerce and connect `term`. Explain the scope of `pmlk`, `issu`, and `capm`. |
| 10 | P2 | `product-bricks/product-bricks.json`, deployment and stream external dependencies | Replace uniform module scaffolding where misleading; add justified bank/rail, commerce, identity, and finance-system dependencies. Clearly label logical architecture. |
| 11 | P2 | `residuality/residuality.json`, `agnt`, `orch`, `liab`, `vpvr` | Separate hypothetical stress from current facts, correct regulatory scope, and require concrete capability/data evidence for integrated or survived claims. |
| 12 | P2 | `business/competition.json` | Add the job-relevant alternatives above, grouped by role. Avoid obsolete ownership and acquired-company double counting. |
| 13 | P3 | `start/config.json`, `_domain/DOMAIN.md`, generated docs/media | Refresh the overview after substantive model edits. Regenerate only the selected domain and inspect customer, competition, stream, data, and deployment views for consistency. |

For the implementation pass, run strict domain validation and the KPI checker, then check coverage explicitly: active bricks assigned or intentionally excluded; important jobs represented in streams; data ownership and dependencies plausible; sources resolvable; placeholder assumptions visible. Build and inspect the selected domain after those checks. The initial review required no rebuild; the approved implementation below includes one.

### Open assumptions

- **Domain scope:** retain the explicit Stripe-centered brief. A vendor-neutral infrastructure taxonomy or a separate Adyen Productscape would be a different modeling decision; this review provides comparison evidence without silently changing that scope.
- **Architecture:** public documentation establishes product contracts and integration behavior, not either company's complete internal architecture. Physical deployment, storage, residency, and proprietary optimization internals remain unverified where not directly documented.
- **Performance:** vendor case studies and selected cohorts do not establish merchant-wide results or a universal provider ranking. Existing numerical targets need either measured baselines or clearly stated illustrative intent.
- **Availability:** eligibility is product-, entity-, jurisdiction-, and contract-specific. Preview labels, development notices, and acquisition integration state should travel with the capability wherever it is displayed.
- **Commercial and legal responsibility:** merchant-of-record, platform liability, funds ownership, financing, and regulated services require product-specific descriptions. Neither a product name nor a general license proves every proposed use is available.
- **Future changes:** an acquisition agreement is not a completion notice, a roadmap is not shipped capability, and annual guidance is not reported financial performance. Recheck these items when the model is edited.

## Implementation record — 2026-11-15

The approved update retains the Stripe-centered scope and incorporates Adyen throughout the comparison evidence, customer insights and relevant capability contracts. All 13 backlog items have been addressed in the source model and selected-domain build.

### Completed model

| Artifact | Before | After |
| --- | --- | --- |
| Customer groups / personas | 3 / 3 | 4 / 5 |
| Jobs / adoption journeys | 6 / 3 | 10 / 5 |
| KPI pyramids / nodes | 6 / 42 | 10 / 70 |
| Products | 5 | 7 |
| Bricks / module definitions | 25 / 50 | 29 / 70 |
| Streams / flow steps | 4 / 12 | 10 / 50 |
| Logical data assets / asserted physical stores | 17 / 17 | 48 / 0 |
| Delivery surfaces | 15, including 10 empty cloud channels | 5 logical surfaces |
| Comparison providers | 4 | 10 |
| Insights / registered sources / curated links | 8 / 9 / 9 | 20 / 60 / 59 |

The new customers are **Platform Seller and Payout Recipient** and **Treasury and Finance Controller**. Their distinct jobs cover usable earnings, remediation, voluntary financial offers, funded obligations, liquidity and financial close. The customer relationships and product assignments include both roles. All five personas now use full-color workplace illustrations generated with the built-in imagegen tool, following the merchant-commerce domain's portrait style. Their final filenames and complete prompt set are recorded in [customer-portraits.prompt.txt](customers/icons/customer-portraits.prompt.txt).

The portfolio adds **Business Treasury and Global Payouts** and **Managed Payments for Digital Sellers**. New capabilities separate processor routing, financial accounts, merchant-of-record responsibility and delegated authority. Ten operational flows cover payment exceptions, usage corrections, platform onboarding and payout returns, unified commerce, embedded finance, treasury, managed payments, agent commerce and delegated spending.

### Backlog disposition

| Order | Implemented result |
| --- | --- |
| 1 | Resolved all 54 strategy-to-KPI name failures. Removed 18 example dashboard links and all 42 unsupported current readings. Metrics have definitions, units, review windows and measurement owners; customer value and supplier outcomes are distinguished. |
| 2 | Replaced FY2024 snapshots with scoped FY2025 figures and separately labeled 2026 interim results. Source, currency, period and business scope travel with every statistic. |
| 3 | Reworked the original insights and expanded the primary evidence registry to 60 sources. All 20 insights link to existing customers, jobs and KPIs; modeling implications are labeled. |
| 4 | Added substantial Adyen evidence for Uplift, unified commerce, Platforms, Intelligent Money Movement, financial products, Orb, Talon.One, agent commerce, licenses, pricing and availability. |
| 5 | Replaced capability-shaped data entries with 48 logical financial and control records. Every asset has exactly one modeled owning brick. Removed generated storage technologies and blanket residency assertions. |
| 6 | All 29 active bricks have delivery, product and stream associations. Removed all 10 empty cloud channels and labeled the remaining delivery surfaces as logical. |
| 7 | Separated usage-billing choices, merchant-of-record duties, connected-account roles, standalone payouts and financial-account products. Optional and preview capabilities retain eligibility limits. |
| 8 | Added recipient and treasury responsibilities; rewrote adoption evaluations and pilots; anchored distinct strategies to 2027, 2029 and 2031. Illustrative ecosystem relations are labeled. |
| 9 | Expanded four short flows into ten flows with 50 steps, including operational failure, recovery and reconciliation work. Terminal, Payment Links, Issuing and Capital now have explicit flow roles. |
| 10 | Reworked modules into UI, operator interfaces, workers, services and integrations. Added external contracts for banks, rails, commerce, identity, accounting and agents without inventing vendor deployment topology. |
| 11 | Qualified all six resilience scenarios. Five responses remain candidates; liability handling is integrated only at the logical-model level. No survived exercise is claimed. Instant-transfer requirements are scoped to the applicable institution and service. |
| 12 | Added Checkout.com, Global Payments/Worldpay, Airwallex, Paddle, Chargebee and Spreedly according to the customer decision they affect. Acquired providers are not double-counted as independent competitors. |
| 13 | Updated the domain brief, start summary and overview diagram, generated the missing display assets, and rebuilt only this domain. Preserved unrelated global catalog entries while updating this domain's summary. |

### Additional Adyen evidence incorporated during implementation

The Q3 release gives precise values behind the rounded prepared remarks: **€738.1m net revenue** and **€451.1bn processed volume**. The comparison now also includes Digital, Unified Commerce and Platforms net revenue, each with its own reported and constant-currency growth scope. Guidance remains separate from achieved results. [Adyen Q3 2026 business update](https://www.adyen.com/press-and-media/adyen-publishes-q3-2026-business-update-6r9vz0).

Two recent announcements further qualify availability. Visa Payment Passkey starts through Authenticate in the **UK**; wider expansion is planned for 2027. Sage describes a **planned first implementation in France** for its business-account and card proposition with Adyen and Mastercard. Neither announcement establishes global availability. These distinctions are included in the competitor profile, insights and source links. [Visa Payment Passkey](https://www.adyen.com/press-and-media/adyen-visa-payment-passkey), [Sage partnership](https://www.adyen.com/press-and-media/adyen-sage-partnership).

### Verification and remaining boundaries

```text
python3 productscapes.py validate payments-and-revenue-infrastructure --strict-ids
PASS: 12 JSON files, 29 product bricks

python3 productscapes.py check-kpis payments-and-revenue-infrastructure
PASS: branching, unique IDs and canonical strategy references

python3 productscapes.py build payments-and-revenue-infrastructure
PASS: selected domain rebuilt

Semantic coverage audit
PASS: every persona has jobs, adoption, metrics, strategy and a serving product
PASS: every job reaches a serving product through a stream or capability
PASS: all 29 bricks have product and stream coverage
PASS: all 48 logical assets have exactly one modeled owner
PASS: all insight customer/job/KPI/source references resolve

Chromium browser checks
PASS: 19 representative pages, including customer, Adyen, product, capability,
      stream, data and resilience views
PASS: expected content, local navigation, assets and JavaScript execution

git diff --check
PASS
```

The balance audit used ride-sharing-marketplace as a density reference: 4 personas, 20 bricks, 17 data assets and 11 comparison providers. The payment model's larger record catalog reflects distinct financial obligations and control evidence. It has no unresolved P1 traceability gaps in the checks above. The three-level KPI trees remain intentionally concise; deeper diagnostic trees should follow actual instrumentation, not filler metrics.

Measurement baselines, contractual eligibility, physical storage, exact retention schedules and operational resilience exercises remain unverified. These are explicit boundaries of the illustrative model, not claims that the vendors lack those controls. Public evidence supports product contracts and comparisons; it does not establish either vendor's complete internal architecture. The update is local and has not been published or committed.
