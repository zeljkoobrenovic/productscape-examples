# Temporary Staffing Software Platform

This domain models the **temporary-staffing software portfolio of zvoove Group** (zvoove.com), the group's core business. zvoove describes itself as "the industry leading provider of software and AI solutions for the temporary staffing, cleaning services and personal security industries". The cleaning and private-security portfolios are modeled as sibling domains in this group (`commercial-cleaning-operations-platform`, `private-security-services-erp-platform`).

## Domain boundary

**Core scope** - software used by staffing agencies to run the lifecycle *Attract -> Sell -> Place -> Onboard -> Schedule -> Record hours -> Pay -> Bill -> Steer*:

- Recruiting and CRM: zvoove Recruit, zvoove Cockpit and Cockpit X AI agents, RecruitNow (NL), Online Results recruitment marketing (NL), zvoove Campaigns.
- Staffing ERP and dispatch with compliance: zvoove One (DE), Pivoton Kentro (NL), ProSolution WorkExpert (AT), Nivel IV (ES), zvoove Switzerland.
- Workforce management: Planbition (Planbition X AI scheduling), Plan4Flex, HelloFlex hours, mywage myschedule.
- Payroll, billing and filings: zvoove Payroll, HelloFlex back office, mywage payroll/mybill/mypod.
- Worker self-service: zvoove Work App and Pixi (WhatsApp onboarding and admin agent, acquired August 2026).
- Client enterprise side: DirectSkills VMS/MSP (France) and client portals.
- Managed services: zvoove Managed Payroll and Managed Sales, profitask (acquired May 2026).
- Shared foundation: zvoove Documents/DMS+, Analytics/Insights, zAIn, Connect/API, tenancy and country packs, AI platform.

**Adjacent scope (light):** recruitment marketing agency services, training and employer branding (profitask Training & Media Centers), Freematica's staffing (ETT) use in Spain and LatAm.

**Excluded:** cleaning and security operations (sibling domains), zvoove as an employer of temporary workers (it is not a staffing agency), generic HR suites.

## Value exchange

Agencies pay subscriptions per module and user (and, for services, per payslip or per engagement). Temporary workers and client managers use apps and portals for free; clients running a VMS pay the VMS operator. The compounding asset is the chain *order -> assignment -> hours -> pay and invoice* in one data model with country rule sets and AI agents on top.

## Strategic spine

- **Year 1 - AI agents in the daily workflow.** Cockpit X, Pixi, Planbition X and zAIn move first contact, onboarding, rostering and reporting to agents; timesheet automation removes paper.
- **Year 3 - Software plus services on shared capabilities.** Managed payroll and sales, one rules engine for AÜG, Wtta and other countries, brand bridges and country packs.
- **Year 5 - Autonomous agency operations across Europe and LatAm.** Agents run standard placements end to end under supervision; the VMS and agency ERPs form a network.

## Sources (facts)

- zvoove.com (home, about-us, countries, news): customer counts (6,500+; 9,000+ in the profitask release), 3M+ workers, EUR 24bn payroll, 1,000+ employees, 27-28 locations, acquisition timeline 2019-2026, leadership.
- zvoove.de product pages: zvoove One (AÜG, equal pay, GVP, HÜD, surcharges, 100,000+ users, up to 20% more efficient), Cockpit X (agents, 250 h/month), Cockpit (up to 90 min/day), Documents (up to 75%), Managed Payroll (80% fewer correction invoices).
- Brand sites: planbition.com, helloflex.com, directskills.com, mywage.co.
- Releases: Pixi (2026-08-11), profitask (2026-05-20).
- Regulation: ABU and Arbeidsinspectie Wtta pages, ZiPconomy (Wtta date confirmed May 2026), Bundesagentur für Arbeit Zeitarbeit statistics.
- Competition: bullhorn.com, easyflex.nl, beeline.com and vendor sites.

## Assumptions and inferences

- **All KPI current and target values are modeled seed values** for a representative customer, except where a description quotes a zvoove figure (payroll volume, workers, VMS invoicing, installations).
- Teams describe a **target shared-capability organisation**; zvoove's real organisation by brand and country is not public. Headcounts are modeled.
- Bricks generalise functionality across brands; not every brand implements every brick.
- Residuality stressors marked `candidate` (equal pay from day one, WhatsApp policy, demand collapse, global competitor) are plausible scenarios, not announced changes.

## Open questions

- Which brands will converge on which core platform, and on what timeline.
- Pricing models for agents (per seat vs per outcome).
- How DirectSkills will be extended beyond France.
