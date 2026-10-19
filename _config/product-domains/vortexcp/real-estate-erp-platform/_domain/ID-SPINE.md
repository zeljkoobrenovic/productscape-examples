# ID Spine — real-estate-erp-platform

Authoritative ID contract for this domain. Every artifact file MUST use exactly these
IDs when referencing entities owned by another file. Names/descriptions here are
one-liners; the artifact author expands them to reference-domain density.
All ids lowercase. Modeled on Bloxs + Informant (see DOMAIN.md).

## Customer groups and customers (customers.json)

Group "Real Estate Investors and Asset Managers" — institutional and private-equity style investors and asset management firms owning residential, commercial, retail, logistics and healthcare portfolios (Bloxs reference customers: Rockfield, Urban Interest, Burgstate, Dunavast):
- `asmg` — Asset and Portfolio Manager. Steers portfolio performance: occupancy, rent growth, indexation, valuations, capex and transformation projects, hold/sell decisions, investor reporting.
- `finc` — Real Estate Finance Controller. Runs multi-entity real estate accounting: rent runs, direct debit and bank reconciliation, debtors, supplier invoices, VAT, service charge settlements, period close, consolidation and investor statements.

Group "Property Management and VvE Firms" — third-party managers administering portfolios and owners' associations for owners (Bloxs reference customers: FIT Vastgoedbeheer, Ruijters, CRMD Vastgoed Management; Informant base: property managers, owners, VvE administrators):
- `prpm` — Property Manager. Manages leases and tenant relations for owner clients: letting vacant units, candidate screening and rent-price checks, contract creation and e-signing, indexation, terminations, deposits, owner statements.
- `tecm` — Technical and Maintenance Manager. Handles fault reports and tickets, dispatches work orders to suppliers, keeps installation registers and periodic maintenance schedules, multi-year maintenance plans and budgets.
- `vvea` — Owners' Association (VvE) Administrator. Administers homeowners' associations: budgets and contributions, reserve funds, meetings and decisions, owner communication, association accounts.

Group "Real Estate Business Leadership" — the buyers and controllers of the ERP:
- `mdir` — Real Estate Company Director. Managing director or owner of a 5–200 FTE investment or management firm; buys the ERP; cares about units per FTE, margin, compliance, client retention, growth by acquisition, total cost of ownership.

Group "Tenants, Owners and Maintenance Partners" — the people who use the organisation's portals:
- `tena` — Tenant. Residential or commercial tenant who pays rent, reports faults, views contract and service charge documents, and communicates through the tenant portal and app.
- `ownr` — Private Property Owner. Owner or small investor whose properties or apartment are managed by a property manager or VvE administrator; wants statements, performance, approvals and documents through the owner portal.
- `supp` — Maintenance Supplier. Contractor, installer or handyman receiving work orders, submitting quotes, planning visits, reporting completion and invoicing through the supplier portal.

### JTBD ids (customers.json jobsToBeDone; insights link jobIds to these)
- asmg: `jtbd-asmg-1` Know portfolio performance in real time, `jtbd-asmg-2` Grow rental income through indexation, letting and active asset management, `jtbd-asmg-3` Report to investors and lenders without a reporting project.
- finc: `jtbd-finc-1` Invoice and collect every euro of rent on time, `jtbd-finc-2` Keep multi-entity books accurate and reconciled every day, `jtbd-finc-3` Close the period and settle service charges without spreadsheets.
- prpm: `jtbd-prpm-1` Fill a vacant unit with the right tenant fast and compliantly, `jtbd-prpm-2` Run every lease through indexation, changes and termination without errors, `jtbd-prpm-3` Keep owners informed and paid with minimal effort.
- tecm: `jtbd-tecm-1` Resolve every fault report quickly with the right supplier, `jtbd-tecm-2` Keep installations compliant and maintained on schedule, `jtbd-tecm-3` Plan and budget multi-year maintenance for the portfolio.
- vvea: `jtbd-vvea-1` Run association budgets, contributions and reserves accurately, `jtbd-vvea-2` Prepare and follow up owner meetings and decisions, `jtbd-vvea-3` Serve owners with self-service information.
- mdir: `jtbd-mdir-1` Scale units under management without scaling headcount, `jtbd-mdir-2` Win and retain owner and investor clients with service quality, `jtbd-mdir-3` Run a compliant, insight-driven real estate business.
- tena: `jtbd-tena-1` Pay rent and understand my charges without calling, `jtbd-tena-2` Report a fault and see it fixed, `jtbd-tena-3` Manage my tenancy documents and changes myself.
- ownr: `jtbd-ownr-1` See how my property performs and what I am paid, `jtbd-ownr-2` Approve decisions and expenses quickly, `jtbd-ownr-3` Find every document and statement in one place.
- supp: `jtbd-supp-1` Receive and accept work orders without phone calls, `jtbd-supp-2` Report completed work and get paid on time.

### North-star KPI names (use these VERBATIM as pyramid node names; productStrategy northStar must match)
- asmg: north star "Net rental income growth"; supporting include "Portfolio occupancy rate", "Investor report preparation time".
- finc: north star "Days to close the period"; supporting include "Rent collection rate", "Automated bank reconciliation rate".
- prpm: north star "Units managed per FTE"; supporting include "Vacancy days per turnover", "Rent arrears share".
- tecm: north star "Ticket resolution time"; supporting include "First-time-fix rate", "Planned maintenance share".
- vvea: north star "Associations managed per FTE"; supporting include "Contribution collection rate", "Meeting preparation time".
- mdir: north star "Revenue per FTE"; supporting include "Operating margin", "Client retention rate".
- tena: north star "Self-service resolution rate"; supporting include "Fault report response time", "Tenant satisfaction score".
- ownr: north star "Owner statement timeliness"; supporting include "Net return on managed property", "Owner satisfaction score".
- supp: north star "Work order turnaround time"; supporting include "Supplier invoice payment time", "Work order acceptance rate".

KPI node id convention (mirrors tour-operator-erp-platform): `co-<cust>-top`, `co-<cust>-b1`, `co-<cust>-b1-c1`, `co-<cust>-b1-c1-l1` … and `bo-<cust>-…` for businessOutcomes. Every non-leaf has ≥2 children; target 4 levels (1+2+4+8). Set `icon` fields as `kpi-<cust>-<nodeid>.png`; icon files are backfilled later.
Customer icons: use `<cust>.png` (e.g. `asmg.png`) — backfilled later.

## Streams (product-stream.json; JTBD steps reference via streamsNeeded)

- `onboard-portfolio-and-entities` — From contracts, spreadsheets or a legacy system (Informant) to a complete portfolio in the ERP: entities, objects, complexes, units, relations, contracts and opening balances.
- `let-units-and-sign-contracts` — From vacancy to signed lease: listing, viewings, candidate screening, rent-price check, contract generation, e-signing, deposit and key handover.
- `manage-leases-through-their-lifecycle` — From signed lease to termination: rent indexation, special terms and break options, changes, renewals, terminations, deposit settlement, service charge settlement.
- `invoice-and-collect-rent` — From active contracts to money in the bank: periodic rent runs, direct debit, bank reconciliation, dunning and arrears follow-up.
- `resolve-maintenance-requests` — From fault report to closed ticket: triage, work order, supplier dispatch, completion, supplier invoice matching.
- `plan-and-execute-periodic-maintenance` — From installation register and multi-year maintenance plan to scheduled inspections, supplier reminders, executed work and budgets.
- `close-books-and-report-to-investors` — From transactions to closed period: supplier invoices, VAT, multi-entity ledger, consolidation, investor and owner statements.
- `steer-portfolio-performance` — From portfolio data to decisions: dashboards, occupancy, yield, valuations, market analysis, forecasts and asset plans.
- `run-owners-association-administration` — From association budget to owner contributions, reserve funds, meetings, decisions and association accounts.
- `serve-tenants-owners-and-partners-through-portals` — From portal account to self-service: rent, documents, fault reports, statements, approvals, work orders.
- `manage-development-and-transformation-projects` — From project budget to delivered building: cost tracking, commitments, documents, milestone monitoring and hand-over into exploitation.
- `automate-and-integrate-the-back-office` — From repetitive tasks and external systems to robots, AI assistants, certified integrations and API connections.

## Product bricks (product-bricks.json) — root group → subgroup → bricks

Root "Portfolio and Relations":
- Subgroup "Objects and Projects": `objt` Objects, Complexes and Units, `valu` Valuations and Market Data, `proj` Development and Transformation Projects.
- Subgroup "Relations and Documents": `rela` Relations and CRM, `docm` Documents and Correspondence.

Root "Letting and Contracts":
- Subgroup "Letting": `vacm` Vacancy, Letting and Candidate Screening.
- Subgroup "Contracts": `cntr` Lease Contracts and E-Signing, `indx` Rent Indexation, Renewals and Terminations, `svcc` Service Charges and Settlements.

Root "Finance and Rent":
- Subgroup "Rent and Collection": `rent` Rent Invoicing and Billing Runs, `bank` Bank Integration and Reconciliation, `dunn` Debtor Management and Dunning.
- Subgroup "Real Estate Accounting": `ledg` Multi-Entity General Ledger and Period Close, `payb` Accounts Payable and Supplier Invoices, `vatx` VAT and Tax Handling.

Root "Technical Management":
- Subgroup "Maintenance Operations": `tick` Fault Reports and Tickets, `work` Work Orders and Supplier Dispatch.
- Subgroup "Assets and Planning": `inst` Installations and Periodic Maintenance, `mjop` Multi-Year Maintenance Planning and Budgets.

Root "Owners' Associations":
- Subgroup "VvE Administration": `vveb` Association Budgets, Contributions and Reserve Funds, `vvem` Meetings, Decisions and Owner Communication.

Root "Insight and Portals":
- Subgroup "Reporting and Analytics": `dash` Dashboards and Data Analytics, `ivrp` Investor and Owner Reporting.
- Subgroup "Stakeholder Portals": `tenp` Tenant Portal and App, `ownp` Owner Portal, `sprp` Supplier and Partner Portal.

Root "Platform Foundation":
- Subgroup "Automation and Integration": `auto` Hyper Automation and Robots, `aiag` AI Assistants, `apip` Open API and Certified Integrations.
- Subgroup "Core Services": `iden` Identity, Tenants and Access, `wflw` Workflow, Tasks and Notifications, `migr` Data Migration and Onboarding Tooling.

32 bricks. Module ids must start with `module-` (e.g. `module-rent-web`, `module-rent-api`).

### Brick dataDependencies → data asset ids (see below); wire at least these
objt→property-object,rental-unit,legal-entity; valu→valuation-record,property-object; proj→project-budget,property-object; rela→contact-relation; docm→document-record,contact-relation; vacm→vacancy-listing,candidate-application,rental-unit; cntr→lease-contract,contact-relation,document-record; indx→lease-contract,rent-invoice; svcc→service-charge-settlement,lease-contract; rent→rent-invoice,lease-contract; bank→bank-statement-line,payment-transaction; dunn→rent-invoice,payment-transaction,contact-relation; ledg→general-ledger-entry,legal-entity; payb→supplier-invoice,general-ledger-entry; vatx→general-ledger-entry,rent-invoice; tick→maintenance-ticket,rental-unit; work→work-order,supplier-invoice; inst→installation-record,property-object; mjop→maintenance-plan,installation-record; vveb→association-budget-and-contribution,legal-entity; vvem→association-meeting-decision,contact-relation; dash→analytics-dataset,property-object; ivrp→analytics-dataset,general-ledger-entry; tenp→portal-account,rent-invoice,maintenance-ticket; ownp→portal-account,analytics-dataset,document-record; sprp→portal-account,work-order; auto→automation-job-run; aiag→automation-job-run,document-record; apip→integration-connection; iden→tenant-organization,portal-account; wflw→workflow-task; migr→tenant-organization,property-object.

## Data assets (data/data-assets.json)

- `property-object`
- `rental-unit`
- `legal-entity`
- `valuation-record`
- `project-budget`
- `contact-relation`
- `document-record`
- `vacancy-listing`
- `candidate-application`
- `lease-contract`
- `service-charge-settlement`
- `rent-invoice`
- `payment-transaction`
- `bank-statement-line`
- `general-ledger-entry`
- `supplier-invoice`
- `maintenance-ticket`
- `work-order`
- `installation-record`
- `maintenance-plan`
- `association-budget-and-contribution`
- `association-meeting-decision`
- `analytics-dataset`
- `portal-account`
- `automation-job-run`
- `integration-connection`
- `workflow-task`
- `tenant-organization`

28 assets.

## Products (product-deployments/products.json) — id, primary customers

- `real-estate-erp-core` — Real Estate ERP Core (Relations, Objects, Contracts, Financial, Reporting) — asmg, finc, prpm, mdir
- `technical-management-suite` — Technical Management Suite (Techniek) — tecm, supp
- `owners-association-suite` — Owners' Association (VvE) Suite (Informant heritage) — vvea, ownr
- `stakeholder-portals` — Tenant, Owner and Supplier Portals and Apps — tena, ownr, supp
- `projects-and-development` — Projects and Development Finance (Projecten) — asmg, finc
- `analytics-and-investor-reporting` — Data Analytics and Investor Reporting — asmg, mdir
- `api-platform-and-integrations` — API Platform and Certified Integrations — finc, mdir
- `hyper-automation-and-ai` — Hyper Automation and AI Assistants — finc, prpm, tecm

## Deployment channels (deployment.json; maas is the structural reference)

Channel groups: "Web Applications" (back-office web app, tenant portal web, owner portal web, supplier portal web, VvE owner portal web), "Mobile Apps" (tenant app iOS/Android, technical field app), "APIs and Integrations" (open REST API / API Platform, accounting connectors, bank connectors, BI connectors such as Power BI, e-mail connectors such as Gmail and Outlook, e-signing, maintenance partner connectors such as Ziezodan and Proprli, rent-price check Huurprijscheck.app), "Automation Runtime" (hyper automation robots and AI job scheduler), "Internal Operations" (tenant administration, migration and support back office). Map deployedBricks with usedInProducts referencing product ids above.

## Sourced company facts (reuse consistently; do not invent numbers)

- Bloxs Software B.V., Utrecht (NL), founded 2015; ~35 employees (2024–2025 sources); customers in the Netherlands and Germany.
- Vortex Capital Partners became majority shareholder in a 2024 buyout (announced 28 October 2024), alongside management and other investors; Dutch and international buy-and-build strategy. Vortex partner: Joost Moerland.
- Leadership: André Proost CEO since 1 May 2025 (ex CompuGroup Medical, Centric); founder Dennis Gubbels (CEO 2015–2025) now board member, shareholder and M&A director.
- Informant Software (Wateringen; custom software from 1990, standard product on the market 1998; property managers, owners, investors and VvE administrators; "hundreds of businesses") acquired 7 July 2025 — first add-on under Vortex; phased integration; free migration to Bloxs; Informant support until 31 December 2027. Informant managing director: Arno Mulder.
- Published scale (bloxs.com): 5,000+ Bloxs users, 450,000+ rental units, €4 billion annual rent invoiced, €70 billion property value managed, 8.9/10 support rating. Vortex page: more than €4 billion annual rent invoiced, more than 500,000 rented properties. Review directories: hundreds of real estate organisations (250–300+) managing 50 to 20,000 units, residential to logistics.
- Named customers: Rockfield, Urban Interest, Burgstate (Vortex); FIT Vastgoedbeheer, Dunavast, Ruijters, CRMD Vastgoed Management (bloxs.com).
- Eight modules: Relaties, Projecten, Objecten, Techniek, Contracten, Financieel, Rapportages, Portalen. Foundation: hyper automation (AI + robotics), data analytics, connectivity (open standardised API, API Platform add-on module, certified integrations). Named partners/integrations: Proprli (technical and financial management), Huurprijscheck.app (rent-price compliance), Ziezodan (automated maintenance handling), Gmail and Microsoft Outlook; BI via Power BI connectors. Deployment: web, Android, iOS. Services: implementation, data migration, unlimited support, training, SaaS security. Tagline: "Grip op vastgoed. Lef in je route, slim in je cockpit."
- Strategy quotes: Gubbels — accelerate expanding software capabilities and customer base through Dutch and international acquisitions; Proost — Bloxs is well positioned to lead as the real estate sector rapidly digitalises; Moerland — modern SaaS that streamlines complex processes through unique automation elements.
