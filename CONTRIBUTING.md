# Contributing a new profile

Thank you for contributing! This guide walks you through adding a
new profile to the repository.

## 1. Choose a profile identifier

- Use **lowercase**, avoid separators where possible
  (e.g. `allergeninfo`, not `allergen-info` or `allergen_info`).
- For region- and category-specific profiles, use **nested paths**,
  e.g. `masterdata/de/food`.

## 2. Copy the template

    cp -R profiles/_template/v1 profiles/<your-slug>/v1

## 3. Adapt the six standard files

| File | Action |
|---|---|
| `profile.jsonld` | Replace all `_template` placeholders with your slug and metadata. |
| `schema.json` | Replace with your profile's JSON Schema (draft 2020-12). |
| `shape.ttl` | Replace with your profile's SHACL shape. |
| `example.jsonld` | Provide a conformant example that passes both schema and shape. |
| `index.html` | Adapt the landing page for humans. |
| `CHANGELOG.md` | Start the version history. |

## 4. Register in the catalogue

Add a `dcat:dataset` entry to catalog.jsonld
following the pattern already present for the FAQ profile.

## 5. Validate locally

Before opening a PR, verify:

- `example.jsonld` validates against `schema.json`
  (any JSON Schema draft 2020-12 validator).
- `example.jsonld` validates against `shape.ttl`
  (any SHACL 1.0 processor).

## 6. Open a Pull Request

Please include in the PR description:

- The **use case** the profile addresses.
- The **GS1 link type** it targets (e.g. `gs1:hasRetailers`).
- **Validation evidence** (screenshot, log excerpt, or test file).
- Any **dependencies** on other profiles or vocabularies.

## Versioning

- **Breaking change?** → open a `/v2` folder alongside `/v1`.
  Never delete or silently mutate a published version.
- **Additive change?** → update in place, bump `CHANGELOG.md`.

## Licence

By contributing, you agree that your contribution is licensed under
the same ./LICENSE licence as the rest of the repository.
