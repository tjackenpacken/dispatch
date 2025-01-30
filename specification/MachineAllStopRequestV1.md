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
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43.511Z",
  "MachineAllStopRequestV1": {
    "ModeAllStop": "Apply",
    "ModeAllStopId": "0e45793f-f1d0-420b-a1fa-85e3f42a7219"
  }
}
```
