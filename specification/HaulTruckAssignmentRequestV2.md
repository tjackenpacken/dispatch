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
  "EquipmentId": "3f4964b3-66a2-41ef-89b1-83b5af0da44e",
  "HaulTruckAssignmentRequestV2": [
    {
      "AssignmentId": "7a846ede-5048-4529-b820-d6b712b7e113",
      "Task": "Load",
      "DestinationId": 24594,
      “DestinationEquipmentId”: "ae9c2b65-3adc-4622-96d8-c261c004ca9d",
      "RouteV1": [
        {"WayId": -456},
        {"WayId": 457},
        {"WayId": -458},
        {"WayId": 459},
        {"WayId": -460}
      ]
    }
  ]
}

```
