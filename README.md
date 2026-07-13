# GS1 Digital Link Resource Profiles

Machine-readable **profiles** for resources referenced from
GS1-conformant Digital Link resolvers via the `context` parameter
of a linkset (cf. GS1 Conformant Resolver Standard, §2.5.6).

> **⚠️ Status: Experimental.** All identifiers currently use
> `https://ralphtro.github.io/gs1-profiles/` as the interim base URI.
> They may be migrated to `https://w3id.org/{TBD}/profiles/` once
> persistent identifiers are registered. 

---

## 📚 Profile catalogue

The machine-readable DCAT catalogue is
available at catalog.jsonld.

Human-browsable overview:

| Profile | GS1 link type | Latest | Identifier |
|---|---|---|---|
| FAQs | `gs1:faqs` | v1 | `…/profiles/faqs/v1` |
| Master Data (core) | `gs1:masterData` | 🚧 | `…/profiles/masterdata/core/v1` |
| Master Data (DE, Food) | `gs1:masterData` | 🚧 | `…/profiles/masterdata/de/food/v1` |
| Master Data (DE, Non-Food) | `gs1:masterData` | 🚧 | `…/profiles/masterdata/de/nonfood/v1` |
| Retailers | `gs1:hasRetailers` | 🚧 | `…/profiles/hasretailers/v1` |
| Allergen Info | `gs1:allergenInfo` | 🚧 | `…/profiles/allergeninfo/v1` |
| Sustainability Info | `gs1:sustainabilityInfo` | 🚧 | `…/profiles/sustainabilityinfo/v1` |

🚧 = placeholder; profile not yet published.

---

## 🧱 Anatomy of a profile

Every profile follows the same structure and file names:

| File | Purpose |
|---|---|
| `profile.jsonld` | W3C PROF description (canonical metadata) |
| `schema.json` | JSON Schema (JSON validation, draft 2020-12) |
| `shape.ttl` | SHACL shape (RDF/JSON-LD validation) |
| `example.jsonld` | conformant example instance |
| `index.html` | human-readable landing page |
| `CHANGELOG.md` | version history for this profile |

This uniform layout means clients and autonomous agents can locate
any profile artefact deterministically, e.g.:

    <profile-identifier>/schema.json
    <profile-identifier>/shape.ttl
    <profile-identifier>/example.jsonld

---

## 🔀 Versioning policy

- **Breaking changes** → new path segment (`/v2`, `/v3`, …).
  Older versions remain accessible indefinitely.
- **Additive / non-breaking changes** → updated in place;
  documented in the profile's `CHANGELOG.md`.
- **Editorial fixes** (typos, formatting) → updated in place;
  no changelog entry required.

Rule of thumb: **once published and referenced from a linkset,
a profile URI never changes its semantics.**

---

## 🧪 Validating an instance

- **JSON validation:** any JSON Schema validator supporting draft 2020-12
  (e.g. [ajv-cli](https://github.com/ajv/ajv-cli).
- **RDF/JSON-LD validation:** any SHACL 1.0 processor
  (e.g. https://shacl-playground.zazuko.com/,
   [SHACL Play!](https://shacl-play.sparna.fr/play/validate),
   [pySHACL](https://github.com/RDFLib/pySHACL)).

---

## 🔗 Using a profile in a linkset

```json
{
  "href": "https://example.com/products/04262431780036/faqs.jsonld",
  "title": "FAQs",
  "type": "application/ld+json",
  "hreflang": ["en"],
  "context": ["https://ralphtro.github.io/gs1-profiles/profiles/faqs/v1"],
  "public": true,
  "@linkType": "https://ref.gs1.org/voc/faqs"
}
```

The context value points to a dereferenceable profile description
(HTML for humans, JSON-LD/PROF for machines via content negotiation
or by requesting profile.jsonld directly).

## 🤝 Contributing

See CONTRIBUTING.md.

## 📜 Licence
This repository is licensed under the
./LICENSE.
The choice of Apache-2.0 is consistent with the licensing of the
https://ref.gs1.org/voc/ and provides an
explicit patent grant — a valuable property for standards-adjacent
artefacts.