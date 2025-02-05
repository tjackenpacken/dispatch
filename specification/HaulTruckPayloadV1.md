# HaulTruckPayloadV1

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          |  Description                                             |
|-------------------------|-----------|--------------|---------------------------------------------------------|
| `"PayloadWeight"`           | shall     | integer   |   Weight in the tray measured in metric tonnes                   |
| `"Accuracy"`    | should    | decimal     |  Error range estimate, unit i metric tonnes        |
| `"PayloadSourceId"`     | may     | decimal      | Id of the payload Source, if it is the Machine it self it is null      |


# HaulTruckPayloadV1 Message Example
```json
{
  "Protocol":"Open-Autonomy ",
  "Version": 1,
  "Timestamp": "2025-01-31T09:40:20.316Z",
  "EquipmentId": "0c83193f-8772-446a-89c0-a3977e282b8a ",
  "HaulTruckPayloadV1": {
    "PayloadWeight": 65,
    "Accuracy": 3
  },
  "MachinePositionV1": {
  "Timestamp": "2025-01-31T09:40:20.316Z",
  "Heading":"222",
  "Latitude":"65.176854",
  "Longitude":"-23.071800",
  "Elevation":"2.23",
  "LatitudeAccuracy":"0.31",
  "LongitudeAccuracy":"0.27",
  "HeightAccuracy":"0.58",
  "HeadingAccuracy":"2.1",
  "Speed":"43.1"
  }
}
```
