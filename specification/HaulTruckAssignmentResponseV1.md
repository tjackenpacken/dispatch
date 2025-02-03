# HaulTruckAssignmentResponseV1

|Sender| Triggered by | 
|---|---|
|`FMS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          |  Description                                             |
|-------------------------|-----------|--------------|---------------------------------------------------------|
| `"AssignmentId"`           | shall     | GUID      | Unique ID for the assignment                 |
| `"Response"`    | shall    | enum       |  `{ Accepted, Rejected }`       | 
| `"Detail"`     | may     | string      |   Human Readable string explaining the reason.   |

# HaulTruckAssignmentRequestV2 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
  "HaulTruckAssignmentResponseV1": [
    {
      "AssignmentId": "eeb723a5-a2a7-4d67-b8c7-b40eb3fa86b6",
      "Response": "Accepted"
    }
  ]
}
```
