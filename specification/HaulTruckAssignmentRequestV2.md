# HaulTruckAssignmentRequestV2

|Sender| Triggered by | 
|---|---|
|`FMS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          |  Description                                             |
|-------------------------|-----------|--------------|---------------------------------------------------------|
| `"AssignmentId"`           | shall     | GUID      | Unique ID for the assignment                 |
| `"Task"`    | shall    | enum       |  `{ Load, Offload, Fuel, Park, Wait }`       | 
| `"DestinationId"`     | shall     | integer      |   WayId number of the destation of the assignment (e.g. the Open Area for dump)  |
| `"DestinationEquipmentId"`               | may    | GUID | The Equipment Id for the machine handling kick-out (e.g. a Wheel Loader)   |  
| `"DestinationSpotId"`               | may    | integer | If a spot for a e.g. dumping assignment is given. This one and DestinationEquipmentId are mutually exclusive.    |  
| `"RouteV1"`               | may    | object | An ordered list of the wayId:s the machine is expected to travel to reach the destation. The final id shall be excluded since that is stated in DestationId  |  
| `"WayId[]"`               | may    | integer | The WayIds the machine shall travel |  

# HaulTruckAssignmentRequestV2 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.511Z",
  "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
  "HaulTruckAssignmentRequestV2": [
    {
      "AssignmentId": "eeb723a5-a2a7-4d67-b8c7-b40eb3fa86b6",
      "Task": "Load",
      "DestinationId": 24594,
      “DestinationEquipmentId”: "6cda9d3d-774d-4a31-b647-9ccc9fd251f3",
      "RouteV1": [
        {"WayId": -245875},
        {"WayId": 245896},
        {"WayId": -245974},
        {"WayId": 245836},
        {"WayId": -245878}
      ]
    }
  ]
}

```
