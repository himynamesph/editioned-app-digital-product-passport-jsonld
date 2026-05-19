# Properties

Every term in the `dpp:` namespace, with type, expected values, and notes.

## Edition

### `dpp:editionNumber`
- Type: integer (>= 1)
- This piece's number within the edition.
- Example: `7`

### `dpp:editionTotal`
- Type: integer (>= 1)
- Total number of pieces in the edition.
- Example: `50`

## Compliance

### `dpp:euOperator`
- Type: string
- The entity registered as responsible for the product in the EU. Required for ESPR.
- Example: `"Example Atelier S.r.l."`

### `dpp:conformityMarkings`
- Type: array of strings
- Compliance marks the product carries.
- Example: `["CE", "REACH", "RoHS"]`

### `dpp:reachSvhc`
- Type: string
- REACH Substance of Very High Concern declaration.
- Example: `"Cobalt dichloride 0.15%"`

## Lifecycle

### `dpp:dateManufactured`
- Type: ISO 8601 date string
- The date the piece was manufactured.
- Example: `"2026-03-14"`

### `dpp:expectedLifespan`
- Type: QuantitativeValue with `value` and `unitCode`
- Expected lifespan. UN/CEFACT unit codes: `ANN` (years), `MON` (months), `DAY` (days), `HUR` (hours).
- Example: `{ "@type": "QuantitativeValue", "value": 10, "unitCode": "ANN" }`

### `dpp:repairInstructions`
- Type: URL
- Link to care and repair instructions.
- Example: `"https://example.com/care/sku-001"`

### `dpp:repairScore`
- Type: decimal (0.0 to 10.0)
- Repairability score. Optional. Aligns with EU energy label repair index where available.
- Example: `8.2`

## Materials

### `dpp:materialComposition`
- Type: array of `{ material, percentage }` objects
- Percentages should sum to 100.
- Example: `[{ "material": "organic cotton", "percentage": 65 }, { "material": "recycled polyester", "percentage": 35 }]`

### `dpp:recyclability`
- Type: string
- Free-text recyclability statement. Will be replaced with a structured grade when CEN EN 18000 publishes.

### `dpp:recycledContentPercent`
- Type: integer (0 to 100)
- Percentage of recycled content by mass.
- Example: `35`

## Footprint

### `dpp:carbonFootprint`
- Type: QuantitativeValue with `value` and `unitCode`
- Embodied carbon. UN/CEFACT unit codes: `KGM` (kg CO2e), `GRM` (g CO2e), `TNE` (tonnes CO2e).
- Example: `{ "@type": "QuantitativeValue", "value": 8.4, "unitCode": "KGM" }`

## Unit code reference

| Code | Meaning |
|---|---|
| KGM | kilograms |
| GRM | grams |
| TNE | tonnes |
| ANN | years |
| MON | months |
| DAY | days |
| HUR | hours |

UN/CEFACT Recommendation 20 codes. Same as GS1 and most EDI systems use.
