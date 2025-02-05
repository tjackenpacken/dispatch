# MachinePositionV1
Send with at least 1Hz and maximum 10Hz

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |
|`FMS` |  At Connection |
|`FMS` |  At Runtime change |


## Message attributes
# MachinePositionV1
| Key              | Req. Level | Type    | Unit      | Description                                                 | 
|---------------------|-----------|---------|----------|-------------------------------------------------------------|
| `"Heading"`        | shall     | integer  | degrees  | Degrees, range 0-359 |
| `"Latitude"`       | shall     | decimal  | degrees  | Minimum 6 decimals                | 
| `"Longitude"`      | shall     | decimal  | degrees  | Minimum 6 decimals               | 
| `"Elevation"`      | shall     | decimal  | Meter    | Elevation in meters with 2 decimals                  | 
| `"LatitudeAccuracy"`  | shall     | decimal  | Meter    |                       | 
| `"LongitudeAccuracy"` | shall     | decimal  | Meter    |                   | 
| `"ElevationAccuracy"` | shall     | decimal  | Meter    |               | 
| `"HeadingAccuracy"`   | shall     | decimal  | degrees  |                    | 
| `"Speed"`         | shall     | integer  | km/h     | Ground speed                            | 
| `"Timestamp"`     | shall     | UTC Time | -        | Timestamp        | 
| `"Attachment[]"`  | may       | array    | -        | Attachment (Trailers)  | 

# AttachmentV1
| Key   | Req. Level | Type    | Unit      | Description                                               |
|------------------------|-----------|---------|----------|-----------------------------------------------------------|
| `"EquipmentID"`       | shall     | GUID    | -        | Unique Equipment ID in the fleet                          |
| `"Heading"`           | shall     | integer  | degrees  | Degrees, range 0-359 |
| `"Latitude"`          | shall     | decimal  | degrees  | Minimum 6 decimals              |
| `"Longitude"`         | shall     | decimal  | degrees  | Minimum 6 decimals             |
| `"Elevation"`         | shall     | decimal  | meter    | Elevation in meters with 2 decimals                |
| `"LatitudeAccuracy"`  | shall     | decimal  | meter    |                     |
| `"LongitudeAccuracy"` | shall     | decimal  | meter    |                   |
| `"ElevationAccuracy"` | shall     | decimal  | meter    |                    |
| `"HeadingAccuracy"`   | shall     | decimal  | degrees  |            |
| `"Speed"`            | shall     | integer  | km/h     | Ground speed of the attachment (Trailer)                            |

# MachinePosition Message Example
### Parked Machine
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43316Z",
  "EquipmentId":"4397592b-d3db-420c-b830-9600529d0aab",
  "MachinePositionV1":
  {
    "Heading": 211,
    "Latitude": 49.176854,
    "Longitude": -123.0718,
    "Elevation": 175.23,
    "LatitudeAccuracy": 0.31,
    "LongitudeAccuracy": 0.27,
    "HeightAccuracy": 0.58,
    "HeadingAccuracy": 2.1,
    "Speed": 0
  }
}
```

### Machine with Trailer
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43316Z",
  "EquipmentId":"4397592b-d3db-420c-b830-9600529d0aab",
  "MachinePositionV1":
  {
    "Heading": 222,
    "Latitude": 49.176854,
    "Longitude": -123.0718,
    "Elevation": 175.23,
    "LatitudeAccuracy": 0.31,
    "LongitudeAccuracy": 0.27,
    "HeightAccuracy": 0.58,
    "HeadingAccuracy": 2.1,
    "Speed": 52

    "AttachmentV1":
    [
      {
        "EquipmentId": "6c4b32e4-aa31-428d-9eab-0a2206bac2b0",
        "Heading": 221,
        "Latitude": 49.176812,
        "Longitude": -123.071783,
        "Elevation": 175.18,
        "LatitudeAccuracy": 0.31,
        "LongitudeAccuracy": 0.27,
        "HeightAccuracy": 0.58,
        "HeadingAccuracy": 2.1,
        "Speed": 52
      }
    ]
  }
}
```
