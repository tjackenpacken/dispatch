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


# MachineAllStopV1 Message Example
### AllStop
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T11:11:10.511Z",
  "MachineAllStopV1": {
    "ModeAllStop": "On",
    "ModeAllStopId": "fd5fe53b-1716-41aa-9367-bb273eee9b76"
  }
}
```
