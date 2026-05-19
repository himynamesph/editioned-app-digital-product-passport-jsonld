# Contributing

Thanks for considering a contribution.

## Scope

This repo is the canonical reference for the `dpp:` JSON-LD vocabulary. Good contributions:

- Bug fixes in the JSON Schema validator
- Example DPP records for additional regulated sectors (furniture, iron/steel/aluminium, ICT services)
- Translations of documentation
- Mapping clarifications to GS1 or upcoming CEN EN 18000 terms

## Out of scope

- Renaming existing properties (breaks every downstream consumer)
- Adding properties that GS1 or Schema.org already cover
- Removing properties (we deprecate, never delete)

## Process

1. Open an issue first describing the change.
2. For property additions, link the ESPR or CIRPASS-2 clause that motivates it.
3. Submit a PR with: the property added to `schema/dpp.jsonld`, validator updated in `schema/dpp-1.0.schema.json`, documented in `docs/properties.md`, and at least one example using it.
4. CI must pass (every example validates against the JSON Schema).

## Versioning

This project follows [Semantic Versioning](https://semver.org/).

- Adding a property = MINOR (1.x.0)
- Adding a non-breaking constraint = PATCH (1.0.x)
- Renaming or removing a property = MAJOR (2.0.0)

We aim to never ship a MAJOR change before CEN/CENELEC EN 18000 publishes.

## License

By contributing you agree your contributions are released under [CC0 1.0 Universal](LICENSE).
