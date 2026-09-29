# Private Security Services ERP Platform

This domain models zvoove Group's **private-security software line**, centred on **Freematica** (Spain, with offices in Mexico and Colombia), acquired on 5 September 2024. Freematica's SaaS ERP e-Satellite serves temporary staffing, cleaning and events as well, but private security is its largest segment; Freematica states that 600+ security and auxiliary companies use e-Satellite. zvoove describes personal security as one of its three core industries. Sibling domains: `temporary-staffing-software-platform`, `commercial-cleaning-operations-platform`.

## Domain boundary

**Core:** Quote -> Contract and posts -> Roster (cuadrantes) -> Cover -> Patrol and report -> Comply (licences, authorities) -> Pay (multi-convention) -> Bill -> Steer, plus client transparency.

**Adjacent:** Mexico and Colombia operations; event staffing on the same ERP.

**Excluded:** alarm receiving centres, video surveillance and cash transport technology; zvoove does not provide guarding. No zvoove-branded security product in DACH was found in public sources, so DACH security is not modeled.

## Sources

freematica.com security solution page (features, 600+ companies, 33%/40%/70% claims); PR Newswire acquisition release (5 Sep 2024); APROSER 2023 figures; Asuntos Legales interview with Colombia's superintendent; Policía Nacional private-security procedures; trackforce.com; Spanish vendor sites for competition.

## Assumptions

- **All KPI values are modeled seed values** unless a description quotes a Freematica figure.
- Evidence is thinner than for staffing and cleaning; the domain is deliberately smaller (18 bricks, 6 personas, 7 teams).
- Regulatory details (TIP, habilitations, refresher training, Segurpri audits, Supervigilancia) are described generically; exact filing formats were not verified.
- Stressors `techsecurity` and `globalstd` are plausible scenarios, not announced events.
