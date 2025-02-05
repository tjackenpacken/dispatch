# MachineDispatchAvailabilityV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             | Example   |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|-----------|
| `"DispatchingCustodian"`           | shall     | enum      | `{ FMS, AHS }`  | `FMS`      |



# MachineDispatchAvailabilityV1 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "4397592b-d3db-420c-b830-9600529d0aab",
  "MachineDispatchAvailabilityV1": {
    "DispatchingCustodian":"FMS"
  }
  "MachinePositionV1": {
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "Heading":"222",
  "Latitude":"65.176854",
  "Longitude":"-23.071800",
  "Elevation":"2.23",
  "LatitudeAccuracy":"0.31",
  "LongitudeAccuracy":"0.27",
  "HeightAccuracy":"0.58",
  "HeadingAccuracy":"2.1",
  "Speed":"43.1"
  }
}
```
