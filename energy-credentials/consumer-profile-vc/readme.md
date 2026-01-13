# Utility Consumer/Prosumer Credential

This credential represents a consumer profile issued by electricity distribution utilities. It supports both pure consumers and prosumers (consumers with distributed energy resources).

## Consumer vs Prosumer

- **Pure Consumer**: Has no DER blocks (no `derSolar` or `derBattery`)
- **Prosumer**: Has at least one DER block (solar and/or battery)

The example shows a prosumer with both solar and battery installations.

## Consumer Fields

| Field | Description | Required |
| :---- | :---- | :----: |
| consumerNumber | Unique consumer account number | Yes |
| fullName | Full name as per ID proof | Yes |
| installationAddress | Full address, city, district, stateProvince, postalCode, country | Yes |
| premisesType | Residential / Commercial / Industrial / Agricultural | Yes |
| connectionType | Single-phase / Three-phase | Yes |
| sanctionedLoadKW | Approved electrical load in kW | Yes |
| tariffCategoryCode | Billing category code | Yes |
| meterNumber | Meter serial number | Yes |
| serviceConnectionDate | Connection activation date | Yes |

## Address Fields

| Field | Description | Required |
| :---- | :---- | :----: |
| fullAddress | Complete street address | Yes |
| city | City name | No |
| district | District or county name | No |
| stateProvince | State, province, or region | No |
| postalCode | Postal or ZIP code | Yes |
| country | ISO 3166-1 alpha-2 country code | Yes |

## DER Fields (Optional)

### derSolar

Present if the consumer has a solar installation (makes them a prosumer).

| Field | Description |
| :---- | :---- |
| capacityKWp | Installed solar generation capacity in kWp |
| commissioningDate | Date when solar was activated |

### derBattery

Present if the consumer has battery storage (makes them a prosumer).

| Field | Description |
| :---- | :---- |
| storageCapacityKWh | Battery storage capacity in kWh |
| powerRatingKW | Battery charge/discharge rate in kW |
| commissioningDate | Date when battery was activated |

## Files

- `schema.json` - JSON Schema for validation
- `context.jsonld` - JSON-LD context for semantic interoperability
- `example.json` - Sample prosumer credential with both solar and battery

## Usage

Context URL:
```
https://nfh-trust-labs.github.io/vc-schemas/energy-credentials/consumer-profile-vc/context.jsonld
```

Schema URL:
```
https://nfh-trust-labs.github.io/vc-schemas/energy-credentials/consumer-profile-vc/schema.json
```
