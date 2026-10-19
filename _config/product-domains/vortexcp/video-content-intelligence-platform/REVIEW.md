# Video Content Intelligence Platform Review

## Product Domain Review

Updated: 2026-09-06

### Executive assessment

- The boundary is appropriate for Media Distillery: three public suites supply intelligence into existing operator services. Consumer subscriptions, rights ownership, playback and ad decisions stay with external operators.
- Four groups and six personas distinguish an economic buyer, editorial user, sports operator, revenue stakeholder, integration partner and indirect viewer. Each has two jobs, an adoption journey, two four-level KPI pyramids and distinct 1/3/5-year horizons.
- Twelve insights link twelve primary sources to actual customer, job and KPI IDs. Facts, case-study observations and proposed implications are distinguished. Vortex establishes investment context, not a growth mandate or valuation.
- The landscape contains the reference business, eight vendor alternatives/adjacent providers and an internal-build substitute. Gracenote is explicitly a partner and adjacent provider. Daily processing, cumulative indexed hours and viewer reach are not presented as comparable market shares.

### High-priority findings

No unresolved P1 realism or traceability defect identified. All six journeys follow Trigger, Discovery, Evaluation, Trial, Engagement and Retention. Viewer adoption explicitly concerns the operator's offer. All 180 KPI nodes belong to branching trees; no single-child chains or fabricated current measurements are present.

### Medium-priority findings and targeted improvement backlog

1. **P2 — Pilot thresholds need an empirical baseline.** Evidence: `_domain/DOMAIN.md`, proposed delivery, break-precision and discovery gates; `customers/customers.json`, `tvpd`, `adld`, `inte`, `view`. Why it matters: the figures are negotiation hypotheses and cannot support sales promises or an ROI forecast. Suggested direction: use `edit-customers` after an operator pilot to record cohort, denominator, tolerance, observation window and uncertainty; retain the original hypothesis alongside results.
2. **P2 — Qualitative customer research is still inferred.** Evidence: `customers/customers.json`, all six personas; `customers/insights.json`, `ispt` and `ichp`. Why it matters: official case studies do not establish universal viewer preferences or causal product lift. Suggested direction: add consented buyer/editor/integrator interviews and a controlled or clearly qualified operator experiment; keep event cohorts separate from ordinary programming.
3. **P2 — Competitive acceptance remains untested.** Evidence: `business/competition.json`, `wscs`, `valo`, `twlv`, `awsr`, `azvi`, `gcvi`, `inhs`. Why it matters: product positioning does not establish equivalent channel, language, latency or total-cost performance. Suggested direction: compare the same licensed evaluation set and integration workload; preserve reported metric scope and omit unverified pricing.

### Open assumptions

The architecture, roadmap, metric definitions, operating model, store technologies and commercial allocation policy are proposed. Private deployment details, contractual SLAs, actual headcount, training permissions and revenue were not established. Public pages without dates carry access dates. All cited source observations were reviewed on 2026-09-06; the Gracenote partnership announcement retains its historical date.

## Product Bricks Review

Updated: 2026-09-06

### Architecture assessment

- Three root groups and eight subgroups contain 24 buildable bricks with 78 modules. Responsibilities cover ingestion and identity, multimodal understanding, playback/ads, discovery, sports and service operation.
- Eight outcome streams contain 32 steps with decisions, pain points and brick dependencies. Every brick participates in a stream, and a product deployment.
- Twenty-four logical assets each have one primary system-of-record brick and one of four proposed stores. Derived assets retain source lineage; rights and editorial decisions remain separate authorities.
- All six supported architectural layers are used where appropriate. Model execution is asynchronous; retrieval and sports composition have stateless modules; source and consumer boundaries use integrations. Dependency source modules identify processing callers, and data ownership remains with stateful registries.
- Products follow the current `maas`-shaped version-4 deployment model: composition is expressed by `deployedBricks[].usedInProducts`. Legacy `neededBricks` and per-product interface catalogues are absent.

### Critical and traceability findings

No unresolved P1 finding. Both repository validators pass strict IDs. Additional checks confirm every dependency required by a product is deployed for that product, all assets are used and owned, all source/customer/job/KPI joins resolve, and stream/brick IDs are unambiguous. Four candidate stressors pass the residuality generator's catalog validation. Stressors do not invent historical survival or probability claims.

### Model-quality findings and edit backlog

1. **P2 — Provider and interface contracts require implementation discovery.** Evidence: `product-bricks/product-bricks.json`, `ingp`, `catl`, `apii`, `conn`; `product-deployments/deployment.json`, `proc`, `dapi`. Why it matters: public API positioning and the Gracenote example do not reveal the vendor's private protocols or topology. Suggested direction: use `edit-product-bricks` and `edit-products` when approved interface specifications are available; attach the concrete timebase, versioning, retry and invalidation contracts.
2. **P2 — Governance must become tenant-specific before operation.** Evidence: `data/data-assets.json`, `feed`, `tran`, `modl`, `crul`, `clip`, `shlt`; `product-bricks/product-bricks.json`, `rght`. Why it matters: licensed source content may include personal or sensitive material, and permission to process does not establish permission for training or promotional reuse. Suggested direction: use `edit-data-assets` to record supplied retention, location, evaluation permission, downstream withdrawal and source-subject constraints. Current text is explicitly a proposal, not compliance evidence.
3. **P2 — Residues are design candidates.** Evidence: `residuality/residuality.json`, `peak`, `drft`, `rgts`, `subs`. Why it matters: plausible checkpoints and tombstones do not prove recovery under load or withdrawal through partner caches. Suggested direction: exercise these cases with an operator and attach acceptance evidence before changing candidate status.

## Balance Audit

Updated: 2026-09-06

Integrity: passed both domain validators with `--strict-ids`, KPI checks and additional ownership/deployment/data/relations/stressor checks.

| Dimension | New domain | Mature guidance |
| --- | ---: | --- |
| Customer groups / personas | 4 / 6 | About 4 groups; materially distinct roles |
| Jobs / adoption journeys | 12 / 6 | Substantive jobs and adoption coverage per persona |
| KPI trees / nodes | 12 / 180 | Four levels, fan-out at every non-leaf |
| Bricks / root groups / subgroups | 24 / 3 / 8 | 20+ bricks in three-level hierarchy |
| Modules / outcome streams | 78 / 8 | Realistic layered and end-to-end coverage |
| Data assets / stores | 24 / 4 | 15+ owned and connected assets |
| Products / deployment subchannels | 3 / 5 | Public offers connected to real delivery responsibilities |
| Insights / research sources | 12 / 12 | 8+ sourced insights |
| Competition entries | 10 | 8+ relevant competitors/substitutes; roles distinguished |
| Candidate stressors | 4 | Optional; grounded impacts without invented likelihood |

**P1:** None unresolved.

**P2:** Empirical customer baselines, and actual interface and governance contracts remain explicit validation assumptions. These are the edit-ready items above.

**P3:** Custom persona, brick and competition artwork is omitted. Existing repository icon conventions are used; no unverified company logos or paid image-generation output is required for this model.

**Overall:** Mature reference model for the selected scope, with an intentionally compact proposed organization. It is ready for exploration and implementation discussion, not presented as an empirically validated company strategy or a map of private infrastructure.

### Generated-output verification

- Generated 93 pages for this domain with the seven scoped generators. Regenerated only the overview and Vortex launchers; existing launcher output matched current source/templates before the additive registration changes. Vortex placement is under 2016.
- Both `.claude` and `.codex` strict domain validators pass for all 13 JSON files. KPI, single-ownership, data/store/steward, product dependency coverage, relations and residuality catalog checks pass.
- JavaScript syntax checks pass for all 95 generated/updated pages, and active static local references resolve. A pre-existing duplicate breadcrumb script in `_templates/competition/landing_page.html` was removed from the head; one inclusion remains after the breadcrumb container. Only this domain's competition output was rebuilt for that fix.
- Reused the repository's overview icon in the domain's source `start/icons/logo.png`; no generated HTML was hand-edited. Generic per-entity icon fallbacks remain intentional.
- Full browser visual verification was unavailable: local headless Chrome exited before rendering in this environment. The checks above are generation, syntax, reference and model verification, not a claim of interactive browser testing.
