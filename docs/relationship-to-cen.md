# Relationship to CEN/CENELEC EN 18000

## Status (May 2026)

CEN/CENELEC is drafting the **EN 18000 series** as the official European standard for Digital Product Passports under ESPR Regulation 2024/1781. Publication is expected mid-2026 to early 2027.

Until EN 18000 publishes:
- Editioned uses the `dpp:` namespace defined here.
- Field names are designed to map cleanly onto CIRPASS-2 reference architecture, which the CEN draft tracks.
- We treat the namespace URI as **provisional**. When EN 18000 publishes its official URI, we will publish a new context file mapping every `dpp:` term to the CEN equivalent. Existing JSON-LD documents will be machine-translatable with a single context swap.

## Mapping strategy

| Our term | Likely EN 18000 equivalent (provisional) | Confidence |
|---|---|---|
| `dpp:editionNumber` | CEN edition identifier field | High — fundamental concept |
| `dpp:editionTotal` | CEN edition size field | High |
| `dpp:euOperator` | CEN responsible operator | Very High — ESPR mandates this |
| `dpp:dateManufactured` | CEN production date | Very High |
| `dpp:carbonFootprint` | CEN/PEF carbon footprint | Very High — PEF method is CEN-referenced |
| `dpp:recycledContentPercent` | CEN recycled content | Very High |
| `dpp:expectedLifespan` | CEN expected lifetime | Very High |
| `dpp:repairInstructions` | CEN repair info link | High |
| `dpp:conformityMarkings` | CEN compliance assertion | High |
| `dpp:reachSvhc` | CEN substance declaration | High |
| `dpp:materialComposition` | CEN material breakdown | High |

## Why bridge instead of wait

EU ESPR enforcement starts **February 2027** for batteries, **late 2028** for textiles, **2028-2030** for the rest. CEN's official URI cannot be a hard prerequisite — merchants need production-ready JSON-LD now.

When EN 18000 publishes:
1. We publish `dpp.v2.jsonld` mapping every term to the CEN URI.
2. Existing implementations consume the new context with a single line change.
3. Both v1 and v2 contexts remain dereferenceable indefinitely.

## How to track CEN progress

- **CEN/CENELEC JTC 24** is the joint technical committee responsible.
- **CIRPASS-2** is the EU-funded reference architecture that CEN tracks. <https://cirpass.eu>
- The ESPR working plan publication will pin specific delegated acts to specific CEN deliverables.
