# Changelog

All notable changes to this schema follow [Semantic Versioning](https://semver.org/).

## [1.0.0] — 2026-05-19

### Added
- Initial release of the `dpp:` JSON-LD namespace.
- Core properties:
  - `dpp:editionNumber`, `dpp:editionTotal`
  - `dpp:euOperator`
  - `dpp:dateManufactured`
  - `dpp:carbonFootprint`
  - `dpp:recycledContentPercent`
  - `dpp:expectedLifespan`
  - `dpp:repairInstructions`
  - `dpp:conformityMarkings`
  - `dpp:reachSvhc`
  - `dpp:materialComposition`
  - `dpp:recyclability`
  - `dpp:repairScore`
- JSON Schema validator (`schema/dpp-1.0.schema.json`).
- Five sector examples: textile, battery, electronics, jewelry, spirits.
- Documentation: properties reference, CEN relationship, GS1 relationship, implementation guide.
- CC0 1.0 Universal license.
