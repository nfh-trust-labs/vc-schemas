# Discom Program Enrollment Credential

This credential is issued by electricity distribution companies (DISCOMs) when a consumer enrolls in an energy program. Programs can include peer-to-peer trading, demand flexibility, virtual power plants, and other grid services.

## Use Cases

- **P2P Energy Trading**: Consumer is authorized to trade excess solar energy with neighbors
- **Demand Flexibility**: Consumer agrees to reduce consumption during peak hours for incentives
- **Virtual Power Plant**: Consumer's DER assets are aggregated for grid services
- **Time of Use**: Consumer opts into time-based pricing programs
- **Net Metering**: Consumer is enrolled in net metering for solar exports
- **Green Energy**: Consumer subscribes to renewable energy programs
- **EV Charging**: Consumer participates in managed EV charging programs

## Fields

| Field | Description | Required |
| :---- | :---- | :----: |
| consumerNumber | Unique consumer account number | Yes |
| programName | Human-readable program name | Yes |
| programCode | Unique program identifier (e.g., P2P-2025) | Yes |
| programType | Category of program (P2P_TRADING, DEMAND_FLEXIBILITY, etc.) | No |
| enrollmentDate | Date of enrollment | Yes |
| enrollmentStatus | ACTIVE / PENDING / SUSPENDED / TERMINATED | No |
| validFrom | Start date when enrollment becomes effective | No |
| validUntil | End date when enrollment expires | No |

## Program Types

| Code | Description |
| :---- | :---- |
| P2P_TRADING | Peer-to-peer energy trading |
| DEMAND_FLEXIBILITY | Demand response / flexibility programs |
| VIRTUAL_POWER_PLANT | VPP aggregation for grid services |
| TIME_OF_USE | Time-based pricing programs |
| NET_METERING | Solar net metering programs |
| GREEN_ENERGY | Renewable energy subscription |
| EV_CHARGING | Managed EV charging programs |
| OTHER | Other program types |

## Enrollment Status

| Status | Description |
| :---- | :---- |
| ACTIVE | Enrollment is currently active |
| PENDING | Enrollment is pending approval/activation |
| SUSPENDED | Enrollment is temporarily suspended |
| TERMINATED | Enrollment has been terminated |

## Files

- `schema.json` - JSON Schema for validation
- `context.jsonld` - JSON-LD context for semantic interoperability
- `example.json` - Sample P2P trading enrollment credential

## Usage

Context URL:
```
https://nfh-trust-labs.github.io/vc-schemas/energy%20credentials/ProgramEnrollment%20VC/context.jsonld
```

Schema URL:
```
https://nfh-trust-labs.github.io/vc-schemas/energy%20credentials/ProgramEnrollment%20VC/schema.json
```
