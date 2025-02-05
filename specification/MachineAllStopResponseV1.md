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
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43.316Z",
  "MachineAllStopResponseV1": {
    "Response": "Accepted",
    "ModeAllStopId": "cf006a03-e52f-41a7-807a-a9e210e2c16e",
    "Detail": "All machines stopped"
  }
}
```
