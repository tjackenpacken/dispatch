# HaulTruckProductionStateV2

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          |  Description                                             |
|-------------------------|-----------|--------------|---------------------------------------------------------|
| `"AssignmentId"`           | shall     | GUID      | Unique ID for the assignment                 |
| `"WayId"`    | shall    | integer       | What is the WayId that the truck is currently at        | 
| `"AutonomyMode"`     | shall     | Enum      |       `{ Manual, Autonomous, TransitionToAutonomous, TransitionToManual, AllStop, EmergencyStop, RemoteControl }`   |
| `"ProductionState"`               | Shall    | Enum |  `{ Off, Driving, Spotting, Loading, Hauling, Dumping, Queued, Stopped, Parked }  `     |  

# HaulTruckProductionStateV2 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
  "HaulTruckProductionStateV2": {
    "AssignmentId": "eeb723a5-a2a7-4d67-b8c7-b40eb3fa86b6",
    "WayId": 750321442,
    "AutonomyMode": "Manual",
    "ProductionState": "Hauling"
  },
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
