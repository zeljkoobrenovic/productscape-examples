# Productscape examples

50 product-domain examples with source JSON, domain briefs, research references,
icons, and media. The reusable authoring skills, schemas, templates, and generators
live in the separate **productscape** repository.

## Build the examples

Requires Python 3.10+ and Git. Clone the two public repositories beside each other:

```sh
git clone https://github.com/zeljkoobrenovic/productscape.git
git clone https://github.com/zeljkoobrenovic/productscape-examples.git
```

Their layout should be:

```text
workspace/
  productscape/
  productscape-examples/
```

From `productscape-examples`, print the required toolkit revision and check it out:

```sh
python3 -c "import json; print(json.load(open('productscapes.json'))['revision'])"
git -C ../productscape checkout <printed-revision>
python3 productscapes.py build --all
python3 -m http.server 8000 --directory docs
```

Open <http://localhost:8000/>. No Python package installation or API key is required
to build the committed examples. The generated site includes a domain catalog,
all seven domain sections, start packages, and the evidence explorer.

For one example:

```sh
python3 productscapes.py list
python3 productscapes.py validate ride-sharing-marketplace --strict-ids
python3 productscapes.py build ride-sharing-marketplace
```

If your toolkit checkout is elsewhere, set `PRODUCTSCAPES_HOME` to its path. The
launcher still checks the commit pinned in [productscapes.json](productscapes.json).
Use `PRODUCTSCAPES_ALLOW_UNPINNED=1` only when intentionally testing toolkit changes.

## Create or extend an example

```sh
python3 productscapes.py new my-domain --group my-group
python3 productscapes.py skills --target .agents/skills
```

Ask your coding assistant to use the installed `new-product-domain` skill to research
and populate the new source tree. For manual authoring, use the toolkit's schemas
and [model reference](https://github.com/zeljkoobrenovic/productscape/blob/main/skills/_references/domain-model.md).
`new` creates an empty scaffold; it does not research or complete a domain.
Run `python3 productscapes.py info` to locate the toolkit resources.

After source edits, validate and build the selected domain. Change shared rendering
or modeling scripts in `productscape`, verify them against these examples, then
update this repository's pinned toolkit commit. This repository contains only the
thin command launcher, not copies of the generator or skill implementation.

## Contents

Source domains live in `_config/product-domains/<group>/<domain-id>/`. Current
groups are enterprise, food-and-health, marketplaces, mobility, other, platforms,
and vortexcp; the toolkit discovers them from disk. Domain IDs are globally unique.

- `_config/product-domains/`: all 50 source examples, including domain media.
- `_config/start-packages/`: curated navigation packages.
- `_evidence/`: evidence fragments and their icons.
- `productscapes.json`: toolkit dependency path and commit.
- `productscapes.py`: launcher that delegates to the toolkit.
- `docs/`: generated site, build locally or in a publishing workflow.

These examples were copied from the current Productscape working files, including
the grouped-folder reorganization. They illustrate models of varying maturity.
See [MIGRATION.md](MIGRATION.md) for provenance and verification results.

MIT licensed; see [LICENSE](LICENSE). Existing source references and third-party
asset attribution are preserved.
