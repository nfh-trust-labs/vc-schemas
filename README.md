# Verifiable Credential Schemas

A collection of standardized schemas for Verifiable Credentials (VCs), aligned with [Schema.org](https://schema.org) vocabulary wherever applicable.

## Overview

This repository maintains JSON-LD schemas for various types of verifiable credentials. Each schema is designed to be:

- **Interoperable**: Based on Schema.org vocabulary standards
- **Extensible**: Custom properties for domain-specific needs
- **Semantic**: Rich, machine-readable metadata using JSON-LD
- **Verifiable**: Compatible with W3C Verifiable Credentials standards

## Available Schemas

| Schema | Description | Status |
|--------|-------------|--------|
| [Salary Slip](./schemas/salary-slip/) | Universal salary slip/payslip schema | ✅ Active |

## Schema.org Alignment

All schemas in this repository prioritize alignment with Schema.org vocabulary:

- **Core Types**: We use standard Schema.org types (Person, Organization, MonetaryAmount, etc.) wherever possible
- **Properties**: Standard Schema.org properties are preferred over custom properties
- **Extensions**: When domain-specific properties are needed, we create custom vocabularies that extend Schema.org
- **Compatibility**: Schemas maintain backward compatibility with Schema.org tooling and validators

## Repository Structure

```
vc-schemas/
├── schemas/
│   └── salary-slip/
│       ├── schema.json          # JSON-LD schema
│       └── README.md            # Schema documentation
├── docs/
│   └── schema-org-alignment.md  # Schema.org mapping guidelines
└── README.md                    # This file
```

## Usage

### Using a Schema

Each schema can be referenced directly or embedded in verifiable credentials:

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://schema.org",
    {
      "salary": "https://example.org/salary#"
    }
  ],
  "type": ["VerifiableCredential"],
  "credentialSubject": {
    "@type": ["Invoice", "salary:SalarySlip"],
    ...
  }
}
```

### Validating Schemas

All schemas follow JSON-LD format and can be validated using standard JSON-LD processors:

```bash
# Install jsonld CLI tool
npm install -g jsonld-cli

# Validate schema
jsonld format --validate schemas/salary-slip/schema.json
```

## Contributing

### Adding New Schemas

1. Create a new directory under `schemas/` with a descriptive name
2. Add `schema.json` with your JSON-LD schema
3. Include comprehensive `README.md` documentation
4. Ensure maximum alignment with Schema.org vocabulary
5. Document any custom extensions clearly

### Schema Requirements

- Use JSON-LD format with `@context`, `@type`, and semantic properties
- Align with Schema.org types and properties wherever applicable
- Document Schema.org mappings in a field mapping table
- Include example data
- Specify custom vocabulary extensions clearly
- Follow consistent naming conventions

## Resources

- [Schema.org Documentation](https://schema.org)
- [W3C Verifiable Credentials](https://www.w3.org/TR/vc-data-model/)
- [JSON-LD 1.1](https://www.w3.org/TR/json-ld11/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Maintainer

**Networks for Humanity**

Building open standards and digital public infrastructure for verifiable credentials.
