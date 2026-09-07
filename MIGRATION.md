# Extraction from Productscape

This repository was extracted from the current working files of Productscape on
2026-09-07. The original repository was preserved, including uncommitted changes.
The source repository's last commit was `fa09176000fddea44df64d17bf732970cf48841e`; the extracted
snapshot also includes the working-tree changes present during extraction.
The new repositories begin independent histories rather than carrying the original
repository's generated-site and example history into the toolkit.

## Preserved inputs

All 50 grouped domain directories, their JSON, domain briefs, research references,
media, and icons were copied. Curated start-package configuration and evidence
fragments/icons were also retained. Checksums matched for all 9,903 copied data
files (1,721,427,344 bytes). Agent instructions were adapted to the toolkit boundary;
OS metadata and Python caches were excluded.

Generated pages are rebuilt from these sources with the pinned productscapes
revision. They are available locally under `docs/` and ignored by Git.

## Verification

- All 50 examples generated successfully with the separated toolkit.
- All 50 examples passed schema/reference validation with strict IDs.
- The validator reported 41 pre-existing journey-stage naming warnings. These are
  retained as modeling findings; no domain content was rewritten to suppress them.
- `enterprise/big-enterprise/start/config.json` retains the old metadata ID
  `internal`. The folder ID `big-enterprise` remains authoritative for discovery
  and generation, matching the original build behavior.
- An empty data project validated and generated all seven sections without examples,
  installed dependencies, or API credentials. Static local navigation resolved.
- Browser checks of the starter and ride-sharing pages found no JavaScript errors.

Toolkit verification includes 8 CLI integration tests, 11 path/validator/wrapper
regression tests, 12 offline image tests, and validation of all 15 skills. The CLI
suite passed with both Python 3.11 and 3.13; Python source also parses as 3.10 syntax.

The toolkit adds a default start icon and generic site catalog, makes the evidence
explorer's home link independent of example packages, and recognizes the model's
existing composite residuality target IDs during strict validation.
