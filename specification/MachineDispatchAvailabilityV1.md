# MachineDispatchAvailabilityV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             | Example   |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|-----------|
| `"DispatchingCustodian"`           | shall     | enum      | { FMS, AHS }  | `FMS`      |



# MachineDispatchAvailabilityV1 Message Example
```json
{
  "Protocol":"open-autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
  "MachineDispatchAvailabilityV1": {
    "DispatchingCustodian":"FMS"
  }
}
```
