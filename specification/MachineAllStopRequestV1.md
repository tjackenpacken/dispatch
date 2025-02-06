# MachineAllStopRequestV1

|Sender| Triggered by | 
|---|---|
|`FMS` |  At Runtime change |

## Message attributes

| key             |  format            | Description                                                             
|-------------------|------------|----------------|
| `"ModeAllStop"`         | Enum           | Apply or Remove                                 |
| `"ModeAllStopId"`      | GUID | ID of the AllStop. Same ID used in apply must be used when removing AllStop          |


# MachineAllStopRequestV1 Message Example
### Apply AllStop
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:41:12.316Z",
  "MachineAllStopRequestV1": {
    "ModeAllStop": "Apply",
    "ModeAllStopId": "2920d124-888a-4d93-a5c7-1bf244f4fd50"
  }
}
```
