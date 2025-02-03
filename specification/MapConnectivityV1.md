# MapConnectivityV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |

## Message attributes
| Key                     | Req. Level         | Type          | Unit      | Description                                                                                                    | Example |
|-------------------------|-------------------|--------------|-----------|----------------------------------------------------------------------------------------------------------------|---------|
| `"MapConnectivityV1"`   | shall             | Object       | —         | Identifies this structure as a Map connectivity                                                               | -       |
| `"WayId"`              | shall             | Integer      | Unique ID | The ID of the current map object that is being described as connected to.                                     | `12345` |
| `"WayType"`            | shall             | Enum         | {Road, Area} | The type of map object this is; Either an Area or a Road.                                                     | `"Road"` |
| `"RoadProperty"`       | Shall when Road   | Object       | —         | See below                                                                                      | -       |
| `"AreaProperty"`       | Shall when Area   | Object       | —         | See below                                                                                            | -       |
| `"Connection"`         | shall             | array of WayId | Unique ID | The connection array is a list of other map objects that can be reached from the WayId attribute defined above. This connectivity is **unidirectional**. Defining a connection starting from the WayId attribute above to each individual map object in the connection list. | `[67890, 54321]` |

## RoadProperty
| Key       | Req. Level | Type    | Unit  | Description           |                                                                             
|-----------|-----------|---------|-------|-----------------------------------------------------------------------------------------------------|
| `"Length"` | shall     | Decimal | meter | The linear length of the road segment. Used by the FMS to calculate a seed theoretical travel time to drive this road segment. |
| `"Name"`   | should    | String  | -     | A human meaningful road name used by AHS.                                                          | 


## AreaProperty
| Key       | Req. Level | Type    | Unit  | Description            |                                                                             
|-----------|-----------|---------|-------|-----------------------------------------------------------------------------------------------------|
| `"DefaultTask"` | shall     | Enum |  | Main purpose of this area Usually "Load", "Offload", "Park", "Fuel" |
| `"Name"`   | should    | String  | -     | A human meaningful area used by AHS.                                                          |



# MapConnectivityV1 Message Example
```json
"MapConnectivityV1": [
  {
  "WayId": D,
  "WayType": "Area",
  "AreaProperty":{
    "DefaultTask": "Offload",
    "Name": "Main Dump"
  }
  "Connection": [ {"WayId": 1} ]
  },
  {
    "WayId": C,
    "WayType": "Area",
    "AreaProperty":{
      "DefaultTask": "Offload",
      "Name": "Crusher"
    }
  "Connection": [ {"WayId": 2} ]
  },
  {
    "WayId": L,
    "WayType": "Area",
    "AreaProperty":{
      "DefaultTask": "Load",
      "Name": "Active Face"
      }
    "Connection": [ {"WayId": 3} ]
  },
  {
    "WayId": 1,
    "WayType": "Road",
    "RoadProperty":{
      "Length": 200.4,
      "Name": "Towards dump"
    },
    "Connection": [
      {"WayId": D},
      {"WayId": 2},
      {"WayId": 1}
      ]
  },
  {
    "WayId": 2,
    "WayType": "Road",
    "RoadProperty":{
      "Length": 194.8,
      "Name": "Crusher Avenue"
      },
    "Connection": [
      {"WayId": C},
      {"WayId": 1},
      {"WayId": 3}
    ]
  },
  {
    "WayId": 3,
    "WayType": "Road",
    "RoadProperty":{
      "Length": 202.3,
      "Name": "Towards Active face"
    },
    "Connection": 
      {"WayId": L},
      {"WayId": 1},
      {"WayId": 2}
    ]
  }
```
