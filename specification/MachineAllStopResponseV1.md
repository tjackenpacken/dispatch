# MachineAllStopResponseV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| key             |  format            | Description                                                             
|-------------------|------------|----------------|
| `"Response"`         | Enum           | Accepted or Rejected                                 |
| `"ModeAllStopId"`      | GUID | ID of the AllStop received from the FMS          |
| `"Detail"`      | String | Optional, human readable information     |


# MachineAllStopResponseV1 Message Example
```json
{
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43.511Z",
  "MachineAllStopResponseV1": {
    "Response": "Accepted",
    "ModeAllStopId": "0e45793f-f1d0-420b-a1fa-85e3f42a7219",
    "Detail": "All machines stopped"
  }
}
```
