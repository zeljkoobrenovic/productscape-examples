# home-improvement-services-marketplace Review

## Product Domain Review

Updated: 2026-09-05

### Executive assessment

- The domain is strategically coherent and mature enough to generate: four materially distinct marketplace participants connect to eight jobs, four adoption journeys, eight KPI pyramids, five products, and nine outcome streams.
- The boundary is specific to Solvari's home-improvement marketplace value exchange and explicitly excludes contractor-of-record, manufacturing, financing, regulatory approval, and full construction-ERP responsibilities.
- All four journeys use the fixed `Trigger → Discovery → Evaluation → Trial → Engagement → Retention` lifecycle and describe adoption of the product rather than replaying JTBD task steps.
- Ten insights resolve to 13 official Solvari, investor, regulator, government, and EU sources; modeled KPI values, product architecture, and organization design are explicitly labeled as assumptions rather than claimed company facts.
- Competition is broad enough to show direct Benelux rivals, comparison services, transactional substitutes, and international trust benchmarks without treating unlike company counters as normalized market share.

### High-priority findings

- None. Strict validation and the manual customer-to-implementation traceability pass found no broken customer, job, stream, product, deployment, asset, insight-source, or KPI references.

### Medium-priority findings

1. **Observed customer evidence is thinner than public product evidence.**
   - Evidence: `customers/customers.json` personas `afpt` and `mops`; `customers/insights.json` sources are public company, terms, investor, and regulator pages rather than interviews or behavioral studies.
   - Why it matters: affiliate and operator workflows are credible inferences, but their pains and decision criteria may overrepresent the published operating model and underrepresent daily exceptions.
   - Suggested direction: add interviews, support themes, funnel analysis, and partner reconciliation samples; encode resulting implications as new sourced insights rather than silently rewriting the personas.

2. **KPI baselines and targets are modeled, not measured.**
   - Evidence: all `currentValue` descriptions in `customers/customers.json`, including `hown/hsar`, `pros/phrr`, `afpt/aqly`, and `mops/mmqt`, identify modeled targets.
   - Why it matters: internally plausible percentages cannot establish current performance, investment priority, or achievable horizon targets.
   - Suggested direction: replace modeled values with dated internal baselines and target provenance; retain explicit distinctions among request, match, contact, quote, contracted job, completed job, and verified outcome.

3. **Country variation is present as architecture context but not yet a customer segmentation axis.**
   - Evidence: `_domain/DOMAIN.md` and bricks `cont`, `qual`, `lprc`, `affl`, and `migr` cover country-aware rules, while `customers/customers.json` uses cross-Benelux personas.
   - Why it matters: language, subsidies, consent practice, trade credentials, pricing, and supply density can change adoption and economics materially by country.
   - Suggested direction: keep the shared personas until evidence demonstrates materially different jobs; then introduce country-specific context or variants rather than duplicating all customers pre-emptively.

### Targeted improvement backlog

- `customers/insights.json`: add first-party research for professional lead economics, homeowner contact tolerance, affiliate rejection reasons, and operator exception volumes; outcome: stronger prioritization and less reliance on public proposition copy.
- `customers/customers.json`: replace modeled KPI values with dated baselines and documented target rationale when internal telemetry becomes available; outcome: decision-grade scorecards.
- `business/competition.json`: refresh page counters and periods before comparative analysis; outcome: avoid treating dynamic or differently scoped figures as stable market facts.
- `customers/customers.json` and `product-bricks/product-stream.json`: add a distinct post-contract or completed-project feedback path only if Solvari has consented visibility beyond matching; outcome: improve outcome learning without implying responsibility for the underlying work.

### Open assumptions

- The published professional packages, credits, campaigns, CRM, and API proposition represents a durable commercial model rather than a transient packaging state.
- Affiliate demand remains strategically material enough to warrant a first-class product boundary.
- Solvari can obtain reliable match, contact, quote, and job-outcome signals without becoming party to the homeowner-professional contract.
- The product topology is a plausible target model, not a statement about Solvari's confidential current systems or organization.

## Product Bricks Review

Updated: 2026-09-05

### Architecture assessment

- The architecture has 28 durable bricks in four root groups and eight subgroups, with 92 modules across all six supported layers: 15 UI, 28 interface, 10 worker, 4 stateless-service, 27 service, and 8 integration layers.
- Nine outcome streams use every brick at least once and connect participant value to qualification, matching, monetization, trust, operations, partners, and acquisition integration.
- The dependency model is implementation-realistic without being fully connected: 61 brick dependencies, 42 module-scoped data dependencies, 15 inbound external-system dependencies, and explicit module endpoints.
- Thirty governed assets in 16 stores cover identity, consent, projects, professional supply, matching, leads, money, communication, trust, partners, analytics, audit, and migration. Every asset has governance, a store, and at least one brick dependency.
- Trust, claims, commercial ledgers, partner settlement, privileged access, migration rollback, and reliability are modeled as first-class capabilities rather than happy-path UI details.

### Critical findings

- None. All brick, module, stream, data-asset, and product-deployment references resolve; no brick is orphaned.

### Model-quality findings

1. **System-of-record brick ownership is explicit in dependencies but not duplicated on the asset object.**
   - Severity: P3.
   - Evidence: `data/data-assets.json` uses store role `system-of-record`; owning bricks use `dataDependencies[].role: "own"`, but assets omit optional `systemOfRecordBrickId`.
   - Why it matters: current traceability is unambiguous but requires joining from bricks rather than reading the owning capability directly on each data page.
   - Suggested direction: add `systemOfRecordBrickId` to operational and ledger assets if the generated data views or governance process benefits from the redundant explicit link.

2. **Decision governance is represented, but a future learned-model lifecycle is not assumed.**
   - Severity: P3.
   - Evidence: bricks `qual`, `matc`, `lprc`, and `trst` record policies, versions, explanations, outcomes, and overrides; no standalone model registry or training-dataset asset is defined.
   - Why it matters: this is correct for rules and bounded scoring, but production ML would add training provenance, evaluation, drift, approval, and rollback obligations.
   - Suggested direction: add model-version and evaluation assets only when learned models become an actual implementation commitment; do not infer an ML platform from public use of the term AI.

### Traceability findings

- Every JTBD step resolves to an existing outcome stream; every stream resolves to existing bricks; every brick is deployed and used by at least one product.
- The current `products.json` schema has no `neededBricks` field. Product-to-brick traceability is therefore correctly represented through `deployment.json` `usedInProducts`, not through a parallel unsupported field.
- Eight key bricks and seven key streams contain direct official reference links. The remaining architecture is correctly presented as a Productscape modeling assumption in `_domain/DOMAIN.md`, not as observed implementation evidence.

### Edit backlog

- `data/data-assets.json`: optionally add `systemOfRecordBrickId` to critical operational, commercial, and audit assets; expected improvement: faster governance and architecture traceability.
- `product-bricks/product-bricks.json`: if learned decision models are introduced, add explicit model evaluation, approval, drift, and rollback modules or assets around `qual`, `matc`, `lprc`, and `trst`; expected improvement: governed AI lifecycle.

## Balance Audit

Updated: 2026-09-05

Integrity: pass — strict validation covers 13 JSON files; the manual spine audit found zero broken or orphaned references.

| Artifact | Count | Mature reference target | Assessment |
|---|---:|---:|---|
| Customer groups / personas | 4 / 4 | ~4 | On target; four distinct marketplace roles |
| Jobs / adoption journeys | 8 / 4 | Complete per persona | Two jobs and one fixed-stage adoption journey per persona |
| KPI pyramids | 8 | Two per persona | Complete; zero single-child nodes |
| Sourced insights / sources | 10 / 13 | 8+ insights | Above target; official and authoritative sources |
| Products | 5 | Domain-dependent | Covers homeowner, professional, affiliate, operations, and integration surfaces |
| Product bricks | 28 | 20+ | Above target across four root groups and eight subgroups |
| Supported layers used | 6 of 6 | Balanced | UI, interfaces, worker, stateless service, service, integration |
| Product streams | 9 | Outcome coverage | Every brick participates in at least one stream |
| Data assets / stores | 30 / 16 | 15+ assets | Above target with governance |
| Competitors | 9 | 8+ | Above target with sourced reported scope |
| Residuality stressors | 5 | Optional | Substantive coverage of change and recovery |

### P1 — realism or traceability breaks

- None.

### P2 — imbalance

- Public evidence does not validate KPI baselines, or first-party customer findings. These are explicitly labeled assumptions and should be replaced with internal evidence before investment or reorganization decisions. Use `edit-customers` and `set-domain-strategy` when that evidence is available.

### P3 — polish

- Add optional direct system-of-record brick links to governed assets if readers need one-hop data ownership views. Use `edit-data-assets`.
- Refresh dynamic competitor counters and terms dates before time-sensitive comparison. Use `edit-competition`.

Overall: **mature** — balanced customer strategy, implementation architecture, ownership, research, competition, and change-resilience modeling, with public-evidence limitations clearly separated from asserted facts.
