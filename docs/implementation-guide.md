# Implementation guide

How to embed a DPP JSON-LD record in your e-commerce product page.

## 1. Pick the right base

Always layer three vocabularies:
1. **Schema.org** — base product, brand, organization
2. **GS1 Web Vocabulary** — GTIN, GLN, country of origin
3. **`dpp:`** — ESPR-specific fields not in either

## 2. Minimum viable record

For any EU DPP-regulated product, you need at least:

```json
{
  "@context": [
    "https://schema.org",
    { "dpp": "https://editioned.app/vocab/dpp#" }
  ],
  "@type": "Product",
  "@id": "https://your-store.com/products/sku-001",
  "name": "Your Product",
  "manufacturer": {
    "@type": "Organization",
    "name": "Your Company",
    "dpp:euOperator": "Your Company Ltd"
  },
  "countryOfOrigin": "DE",
  "dpp:dateManufactured": "2026-05-19",
  "dpp:carbonFootprint": {
    "@type": "QuantitativeValue",
    "value": 5.2,
    "unitCode": "KGM"
  }
}
```

Anything beyond this is sector-specific. Batteries need cell composition; textiles need fiber composition; electronics need a repair score.

## 3. Where to embed it

| Surface | How |
|---|---|
| Web page | `<script type="application/ld+json">` in `<head>` |
| QR code on product | Encode a URL that resolves to the JSON-LD |
| API endpoint | Serve as `Content-Type: application/ld+json` |
| File export | `.jsonld` file |

## 4. Validate before shipping

| Validator | What it catches | URL |
|---|---|---|
| Schema.org Validator | Structural errors, type mismatches | https://validator.schema.org |
| Google Rich Results Test | Schema.org structured-data validity | https://search.google.com/test/rich-results |
| JSON-LD Playground | Context resolution, expansion correctness | https://json-ld.org/playground |
| CIRPASS-2 beta validator | DPP-specific field semantics (when available) | TBD |

## 5. Per-edition uniqueness

For numbered editions: every piece needs its own `@id` and JSON-LD record. Don't reuse a single record across all editions — each piece is a distinct DPP subject.

## 6. Common mistakes

1. **Missing `@context`** — JSON-LD without `@context` is just JSON. Validators reject it.
2. **Wrong unit codes** — use UN/CEFACT codes (`KGM`, `ANN`), not `"kg"` or `"years"`.
3. **`materialComposition` as a string** — must be an array of objects. Strings can't be parsed for compliance.
4. **Confusing `editionNumber` (this piece) with `editionTotal` (total in edition)** — both required for numbered editions.
5. **Using `dpp:` for fields GS1 already covers** — defeats interop. Use GS1 first.

## 7. Future-proof your records

When CEN/CENELEC EN 18000 publishes, every `dpp:` term will map to a CEN URI. To migrate:

- Wait for `dpp.v2.jsonld` (we'll publish it within 30 days of EN 18000)
- Swap `@context` reference in your records
- Re-validate

Records produced today remain valid; they just resolve through a context file that adds CEN URIs as `@id` aliases.
