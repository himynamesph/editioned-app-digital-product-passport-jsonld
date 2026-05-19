# DPP Schema

**Open JSON-LD vocabulary for the EU Digital Product Passport.**

[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
[![npm version](https://img.shields.io/npm/v/@editioned/dpp-schema.svg)](https://www.npmjs.com/package/@editioned/dpp-schema)
[![Production](https://img.shields.io/badge/status-production-success.svg)](https://editioned.app/vocab/dpp)

> A free, CC0 JSON-LD schema for Digital Product Passport data on the web.
> Live in production on Shopify since May 2026. Maintained by [Editioned](https://editioned.app).

---

## Why this exists

EU **ESPR Regulation 2024/1781** makes Digital Product Passports mandatory for regulated product categories starting February 2027 (batteries), late 2028 (textiles), and 2028-2030 (electronics, iron, steel, aluminium, furniture).

Every DPP must carry structured product data — edition information, EU operator, carbon footprint, recycled-content percentage, expected lifespan, conformity markings, and more.

**The problem**: Schema.org and GS1 don't cover most of these fields yet. The official EU standard, **CEN/CENELEC EN 18000**, won't be finalized until mid-2026 to early 2027.

**This schema** is a CIRPASS-aligned bridge namespace (`dpp:`) for the gap year. Field names map cleanly onto the expected CEN URIs. When EN 18000 publishes, swap the context and existing records stay valid.

## Quick example

```json
{
  "@context": [
    "https://schema.org",
    { "dpp": "https://editioned.app/vocab/dpp#" }
  ],
  "@type": "Product",
  "@id": "https://example.com/products/jacket-001",
  "name": "Organic Cotton Field Jacket",
  "manufacturer": {
    "@type": "Organization",
    "name": "Example Atelier",
    "dpp:euOperator": "Example Atelier S.r.l."
  },
  "countryOfOrigin": "IT",
  "dpp:dateManufactured": "2026-03-14",
  "dpp:carbonFootprint": {
    "@type": "QuantitativeValue",
    "value": 8.4,
    "unitCode": "KGM"
  },
  "dpp:recycledContentPercent": 35,
  "dpp:conformityMarkings": ["REACH", "OEKO-TEX"]
}
```

Five complete examples across regulated sectors live in [`examples/`](examples/).

## Install

```bash
npm install @editioned/dpp-schema
```

Or load the JSON-LD context directly from the canonical URL:

```
https://editioned.app/vocab/dpp
```

## What's in the box

| Path | Purpose |
|---|---|
| [`schema/dpp.jsonld`](schema/dpp.jsonld) | The JSON-LD `@context` you import |
| [`schema/dpp-1.0.schema.json`](schema/dpp-1.0.schema.json) | JSON Schema for validating records |
| [`examples/`](examples/) | Five sector-specific examples |
| [`docs/properties.md`](docs/properties.md) | Every term documented with type + example |
| [`docs/relationship-to-cen.md`](docs/relationship-to-cen.md) | Migration plan when EN 18000 publishes |
| [`docs/relationship-to-gs1.md`](docs/relationship-to-gs1.md) | How `dpp:` extends GS1, doesn't replace |
| [`docs/implementation-guide.md`](docs/implementation-guide.md) | How to embed DPP JSON-LD on a product page |

## Properties at a glance

- `dpp:editionNumber`, `dpp:editionTotal` — numbered editions
- `dpp:euOperator` — ESPR-required responsible party
- `dpp:dateManufactured` — production date
- `dpp:carbonFootprint` — QuantitativeValue with `KGM` unit
- `dpp:recycledContentPercent` — 0-100
- `dpp:expectedLifespan` — QuantitativeValue with `ANN` unit
- `dpp:repairInstructions` — URL
- `dpp:repairScore` — decimal 0-10
- `dpp:conformityMarkings` — string array (CE, REACH, RoHS, ...)
- `dpp:reachSvhc` — REACH SVHC declaration string
- `dpp:materialComposition` — array of `{ material, percentage }`
- `dpp:recyclability` — free-text recyclability statement

Full reference in [`docs/properties.md`](docs/properties.md).

## Implementations

- **Editioned** ([Shopify App Store](https://apps.shopify.com/editioned)) — reference implementation, generates per-edition DPP JSON-LD for every order

If you ship `dpp:` JSON-LD in production, open a PR adding yourself here.

## Versioning

Semantic versioning. Current: **1.0.0**.

We commit to never shipping a MAJOR change before CEN/CENELEC EN 18000 publishes. See [docs/relationship-to-cen.md](docs/relationship-to-cen.md) for the migration plan.

## Cite this work

Use [`CITATION.cff`](CITATION.cff) for academic / regulatory citations.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Issues and PRs welcome — especially examples for additional regulated sectors.

## License

[CC0 1.0 Universal](LICENSE) — public domain. No attribution required, no restrictions on commercial use.
