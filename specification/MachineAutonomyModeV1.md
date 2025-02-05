# MachineAutonomyModeV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             | Example   |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|-----------|
| `"AutonomyMode"`           | shall     | enum      | `{ Manual, Autonomous }`  | `Autonomous`      |



# MachineAutonomyModeV1 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "1c558480-cb1c-4bae-bbc7-89b12516aca5",
  ""MachineAutonomyModeV1":": {
    "AutonomyMode": "AutonomyMode"
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
