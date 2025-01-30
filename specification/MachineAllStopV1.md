# MachineAllStopV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |

## Message attributes

| key             |  format            | Description                                                             
|-------------------|------------|----------------|
| `"ModeAllStop"`         | Enum           | On or Off                                 |
| `"ModeAllStopId"`      | GUID |          |


# MachineAllStopRequestV1 Message Example
### AllStop
```json
{
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43.511Z",
  "MachineAllStopRequestV1": {
    "ModeAllStop": "On",
    "ModeAllStopId": "0e45793f-f1d0-420b-a1fa-85e3f42a7219"
  }
}
```
