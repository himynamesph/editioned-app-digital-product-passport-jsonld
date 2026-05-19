# Relationship to GS1 Web Vocabulary

The `dpp:` namespace **extends** the GS1 Web Vocabulary — it does not replace it.

## Use GS1 for identifiers

| Concept | Use this | Not this |
|---|---|---|
| Product identifier | `gs1:gtin` | custom field |
| Location identifier | `gs1:gln` | custom field |
| Shipment identifier | `gs1:sscc` | custom field |
| Country of origin | `schema:countryOfOrigin` | custom field |
| Manufacturer info | `schema:Organization` | custom field |

GS1 has 40+ years of supply-chain semantics. Reuse it for everything they already cover.

## Use `dpp:` for ESPR-specific fields

Fields that ESPR Regulation 2024/1781 requires but GS1 doesn't model yet:

- Edition number/total
- EU operator declaration
- Carbon footprint with unit
- Recycled content percentage
- Expected lifespan with unit
- Repair instructions URL
- Conformity markings
- REACH SVHC declaration
- Material composition breakdown
- Repairability score

When GS1 adds equivalent fields to their vocabulary, we'll migrate properties one at a time and deprecate the `dpp:` versions over a 12-month window.

## Example: layered context

```json
{
  "@context": [
    "https://schema.org",
    {
      "gs1": "https://gs1.org/voc/",
      "dpp": "https://editioned.app/vocab/dpp#"
    }
  ],
  "@type": "Product",
  "gs1:gtin": "09506000134352",
  "dpp:editionNumber": 7
}
```

Schema.org as the base. GS1 for identifiers. `dpp:` for what neither covers.
