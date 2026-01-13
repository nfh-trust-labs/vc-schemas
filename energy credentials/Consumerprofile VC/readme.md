## **Consumer Fields**

| Field | Description |
| :---- | :---- |
| consumerNumber | Unique identifier |
| fullName | As per ID proof |
| installationAddress | Full address, district, pincode, state |
| premisesType | Residential / Commercial / Industrial / Agricultural |
| connectionType | Single-phase / Three-phase |
| sanctionedLoadKW | Approved load |
| tariffCategoryCode | Billing category |
| meterNumber | Meter serial number |
| serviceConnectionDate | Connection activation date |
| maskedAadhaar | Optional |
| pan | Optional (commercial/industrial) |

## DER Fields (Optional)

derSolar (if present, it's a prosumer with solar)

| Field | Description |
| :---- | :---- |
| capacityKWp | Installed generation capacity |
| commissioningDate | When solar was activated |

derBattery (if present, it's a prosumer with battery)

| Field | Description |
| :---- | :---- |
| storageCapacityKWh | Battery storage capacity |
| powerRatingKW | Charge/discharge rate |
| commissioningDate | When battery was activated |

A pure consumer has neither DER block. A prosumer has at least one. The sample shows a prosumer with both solar and battery.  
