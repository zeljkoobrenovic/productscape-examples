# Commercial Cleaning Operations Platform

This domain models **zvoove Clean**, the cleaning and facility-services division of zvoove Group. zvoove Clean states 2,500+ customers, 250,000 cleaners on its platforms and 15+ countries, and describes itself as "the digital foundation for cleaning businesses across Europe". Sibling domains cover staffing (`temporary-staffing-software-platform`) and private security (`private-security-services-erp-platform`).

## Domain boundary

**Core scope** - software that cleaning companies use along *Quote -> Specify -> Plan -> Cover -> Clean and prove -> Audit -> Resolve -> Pay -> Bill -> Steer*:

- fortytools by zvoove (DE): quotes, planning, mobile time tracking, invoicing, QM and tickets; 1,200+ customers.
- KleanApp (DE, acquired 31 March 2026): quality audits, ticketing, assignments, NFC/barcode/terminal attendance; used by 7 of the top 20 German facility companies.
- CleanManager (DK/DE/AT/UK, acquired August 2025): scheduling, time tracking, quality control and cost calculation; 425+ customers, 15,000 users.
- adata (DE, acquired October 2025): payroll and HR for facility management; ~450 customers; basis for managed payroll.
- Leviy (NL): quality control, work orders, sensors; 150+ companies.
- Nocore (NL, acquired May 2025): cleaning ERP.

**Adjacent:** Freematica's cleaning users in Spain and LatAm; cleaning companies that also lease staff (bridges to the staffing domain).

**Excluded:** cleaning service delivery itself (zvoove does not clean), CAFM/IWMS for property owners, cleaning robots and chemicals.

## Value exchange

Cleaning companies pay subscriptions (SME tiers, enterprise contracts) and optionally managed payroll; cleaners and client facility managers use apps and portals free. Value comes from calculated-versus-actual hour control, proof for clients and correct payroll for a large part-time workforce.

## Strategic spine

- **Year 1 - Integrate quality, attendance and payroll.** KleanApp and adata bridges, multilingual cleaner app, substitution.
- **Year 3 - One European suite.** Shared object register, tariffs, audits and portal across brands; managed payroll.
- **Year 5 - Demand-driven, AI-assisted cleaning.** Sensor-triggered tasks, AI quotes and audits, outcome-based contracts.

## Sources

zvoove-clean.com; fortytools.com; zvoove.com news (KleanApp); PR Newswire releases (CleanManager, adata, Nocore); leviy.com; Bundesinnungsverband Branchenreport 2025 and August 2026 employment release; 2026 German software comparison (dynvon). Competitor descriptions from vendor sites and comparison articles.

## Assumptions

- **All KPI values are modeled seed values** unless a description quotes a zvoove figure.
- Teams, headcounts and the shared-platform organisation are modeled, not zvoove's actual structure.
- Leviy's acquisition year is reported as 2019 in Nocore coverage and 2021 on zvoove's timeline; the model does not depend on it.
- Stressors `brandsprawl` and `robots` are plausible scenarios, not announced events.
