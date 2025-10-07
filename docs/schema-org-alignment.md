# Schema.org Alignment Guidelines

This document outlines our approach to aligning verifiable credential schemas with Schema.org vocabulary.

## Principles

### 1. Schema.org First

Always start with Schema.org vocabulary:

- **Use existing types**: Before creating custom types, check if Schema.org has a suitable type
- **Use existing properties**: Leverage Schema.org properties even if the names aren't perfect
- **Extend, don't replace**: Build on Schema.org rather than creating parallel vocabularies

### 2. Semantic Compatibility

Ensure schemas remain semantically compatible with Schema.org:

- Use `@context` to define Schema.org as primary context
- Maintain Schema.org type hierarchies
- Follow Schema.org naming conventions for custom properties

### 3. Custom Extensions

When Schema.org doesn't cover specific needs:

- Define clear namespaces for custom vocabularies
- Document the rationale for custom properties
- Keep custom extensions minimal and focused
- Consider proposing additions to Schema.org for widely-applicable concepts

## Mapping Strategy

### Step 1: Identify Core Concept

Find the closest Schema.org type that represents your credential's core concept:

| Credential Type | Schema.org Type | Rationale |
|----------------|-----------------|-----------|
| Salary Slip | `Invoice` | Financial document with line items |
| Educational Certificate | `EducationalOccupationalCredential` | Educational achievement |
| Employment Letter | `EmployeeRole` | Employment relationship |
| Address Proof | `PostalAddress` | Address verification |

### Step 2: Map Standard Properties

Use Schema.org properties directly:

```json
{
  "@type": "Person",
  "name": "Jane Doe",           // Standard Schema.org
  "email": "jane@example.com",  // Standard Schema.org
  "telephone": "+1-555-0100"    // Standard Schema.org
}
```

### Step 3: Handle Domain-Specific Properties

For properties not in Schema.org, create custom extensions:

```json
{
  "@context": [
    "https://schema.org",
    {
      "salary": "https://example.org/salary#",
      "earnings": "salary:earnings"
    }
  ],
  "@type": ["Invoice", "salary:SalarySlip"],
  "earnings": [...]  // Custom property
}
```

### Step 4: Use Aliases for Clarity

When Schema.org property names are unclear in your domain, create aliases:

```json
{
  "@context": {
    "employee": "customer",  // Alias for clarity
    "employer": "provider"   // Alias for clarity
  }
}
```

## Common Patterns

### Identifiers

Use `PropertyValue` for structured identifiers:

```json
{
  "identifier": [
    {
      "@type": "PropertyValue",
      "propertyID": "employee-id",
      "value": "EMP-00123"
    },
    {
      "@type": "PropertyValue",
      "propertyID": "IN-PAN",
      "value": "ABCDE1234F"
    }
  ]
}
```

### Monetary Values

Always use `MonetaryAmount`:

```json
{
  "amount": {
    "@type": "MonetaryAmount",
    "currency": "INR",
    "value": 75000
  }
}
```

### Dates and Periods

Use ISO 8601 dates with Schema.org date properties:

```json
{
  "dateCreated": "2025-07-31",
  "startDate": "2025-07-01",
  "endDate": "2025-07-31"
}
```

### Organizations and People

Use full Schema.org types with all relevant properties:

```json
{
  "employer": {
    "@type": "Organization",
    "name": "Acme Corp",
    "taxID": "12-3456789",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "123 Main St",
      "addressLocality": "New York",
      "addressRegion": "NY",
      "postalCode": "10001",
      "addressCountry": "US"
    }
  }
}
```

## Validation Checklist

When creating a new schema:

- [ ] Identified the most appropriate Schema.org base type
- [ ] Used Schema.org properties for all standard fields
- [ ] Created custom namespace only for truly domain-specific properties
- [ ] Documented all custom extensions with rationale
- [ ] Used aliases to improve clarity without changing semantics
- [ ] Followed Schema.org naming conventions (camelCase)
- [ ] Included proper `@context` with Schema.org as primary context
- [ ] Validated JSON-LD syntax
- [ ] Added example data demonstrating all properties
- [ ] Created mapping table showing Schema.org alignment

## Resources

- [Schema.org Full Hierarchy](https://schema.org/docs/full.html)
- [Schema.org Pending Extensions](https://pending.schema.org/)
- [JSON-LD Best Practices](https://w3c.github.io/json-ld-bp/)
- [Schema.org Proposals](https://github.com/schemaorg/schemaorg/issues)

## Contributing Schema.org Proposals

If you identify properties that would benefit the broader community:

1. Check existing [Schema.org proposals](https://github.com/schemaorg/schemaorg/issues)
2. Review the [How We Work](https://www.w3.org/community/schemaorg/how-we-work/) guide
3. Submit a proposal with:
   - Use case description
   - Proposed property/type definition
   - Examples
   - Rationale for inclusion

## Version History

- **v1.0** (2025-10-07): Initial alignment guidelines
