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
| Key              | Req. Level | Type    | Unit      | Description                                                 | Example       |
|---------------------|-----------|---------|----------|-------------------------------------------------------------|---------------|
| `"Heading"`        | shall     | integer  | degrees  | Degrees, WGS84 Compass heading in degrees with range 0-359 | `67`          |
| `"Latitude"`       | shall     | decimal  | degrees  | WGS84 Latitude with a minimum of 6 decimals                | `49.176854`   |
| `"Longitude"`      | shall     | decimal  | degrees  | WGS84 Longitude with a minimum of 6 decimals               | `-123.071800` |
| `"Elevation"`      | shall     | decimal  | Meter    | WGS84 Elevation in meters with 2 decimals                  | `175.23`      |
| `"LatitudeAccuracy"`  | shall     | decimal  | Meter    | Latitude error @ 1 sigma probability                       | `0.06`        |
| `"LongitudeAccuracy"` | shall     | decimal  | Meter    | Longitude error @ 1 sigma probability                      | `0.07`        |
| `"ElevationAccuracy"` | shall     | decimal  | Meter    | Elevation error @ 1 sigma probability                      | `0.12`        |
| `"HeadingAccuracy"`   | shall     | decimal  | degrees  | Heading error @ 1 sigma probability                        | `1.7`         |
| `"Speed"`         | shall     | integer  | km/h     | Ground speed of the machine                                | `52`          |
| `"Timestamp"`     | shall     | UTC Time | -        | The timestamp is the time the position was measured        |               |
| `"Attachment[]"`  | may       | array    | -        | Attachment(s) connected to the main tractor if it applies  |               |

# AttachmentV1
| Key   | Req. Level | Type    | Unit      | Description                                               |
|------------------------|-----------|---------|----------|-----------------------------------------------------------|
| `"EquipmentID"`       | shall     | GUID    | -        | Unique Equipment ID in the fleet                          |
| `"Heading"`           | shall     | integer  | degrees  | Degrees, WGS84 Compass heading in degrees with range 0-359 |
| `"Latitude"`          | shall     | decimal  | degrees  | WGS84 Latitude with a minimum of 6 decimals              |
| `"Longitude"`         | shall     | decimal  | degrees  | WGS84 Longitude with a minimum of 6 decimals             |
| `"Elevation"`         | shall     | decimal  | meter    | WGS84 Elevation in meters with 2 decimals                |
| `"LatitudeAccuracy"`  | shall     | decimal  | meter    | Latitude error @ 1 sigma probability                     |
| `"LongitudeAccuracy"` | shall     | decimal  | meter    | Longitude error @ 1 sigma probability                    |
| `"ElevationAccuracy"` | shall     | decimal  | meter    | Elevation error @ 1 sigma probability                    |
| `"HeadingAccuracy"`   | shall     | decimal  | degrees  | Heading error @ 1 sigma probability                      |
| `"Speed"`            | shall     | integer  | km/h     | Ground speed of the machine                              |

# MachinePosition Message Example
### Parked Machine
```json
{
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43511Z",
  "EquipmentId":"2248d535-3daf-4a86-b1e1-4951a22beec6",
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
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2018-10-31T09:30:10.43511Z",
  "EquipmentId":"2248d535-3daf-4a86-b1e1-4951a22beec6",
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
    "Speed": 52

    "AttachmentV1":
    [
      {
        "EquipmentId": "e66c739e-b5f3-41f2-8bbb-5a29875ae70d",
        "Heading": 220,
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
