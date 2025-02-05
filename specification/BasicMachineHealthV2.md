# BasicMachineHealthV2

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|
| `"FuelLevel"`           | shall     | integer      | %    | Current Fuel level                   |
| `"TotalMachineHour"`    | should    | decimal      | h    | Number of hours the Machine has been running       |
| `"TotalEngineHour"`     | shall     | decimal      | h    | Number of hours the Machine has been running        | 
| `"Tire"`               | should    | Object Array | -    | A list of tire information       | 

### Array Of `[ ]`
| Key             | Req. Level | Type    | Unit  | Description                            | 
|-------------------|-----------|--------|------|--------------------------------|
| `"TirePosition"`  | shall     | string  | -    |           |       
| `"TirePressure"`  | shall     | integer | kPa  | Pressure for the actual tire      |
| `"TireTemperature"` | shall     | integer | °C   | Temperature for the actual tire       |

# BasicMachineHealthV2 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.316Z",
  "EquipmentId": "f4d95a41-831e-4a27-9353-32872b7d6103",
  "BasicMachineHealthV2": {
  "FuelLevel": 74,
  "TotalMachineHour": 4511.4,
  "TotalEngineHour": 93.1,
  "Tire": [
    {“TirePosition”:"1.7", “TirePressure”: 123, “TireTemperature”: 42},
    {“TirePosition”:"1.9", “TirePressure”: 124, “TireTemperature”: 42},
    {“TirePosition”:"2.7", “TirePressure”: 111, “TireTemperature”: 43},
    {“TirePosition”:"2.9", “TirePressure”: 125, “TireTemperature”: 43},
    {“TirePosition”:"3.7", “TirePressure”: 131, “TireTemperature”: 41},
    {“TirePosition”:"3.9", “TirePressure”: 132, “TireTemperature”: 41}
    ]
  }
}
```
