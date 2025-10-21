# BasicMachineHealthV2

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|
| `"FuelLevel"`           | shall     | integer      | %    | Current Fuel level as percentage of full capacity. Range 0-100. If unavailable or sensor error, value shall be null.    |
| `"AdBlueLevel"`         | should    | integer      | %    | Current AdBlue (Diesel Exhaust Fluid) level as percentage of full capacity. Range 0-100. If unavailable or sensor error, value shall be null.  |
| `"TotalMachineHour"`    | should    | decimal      | h    | Number of hours the Machine has been running. If unavailable, value shall be null.       |
| `"TotalEngineHour"`     | shall     | decimal      | h    | Number of hours the Engine has been running. If unavailable, value shall be null.        | 
| `"Tire"`               | should    | Object Array | -    | A list of tire information       | 

### Array Of `[ ]`
| Key             | Req. Level | Type    | Unit  | Description                            | 
|-------------------|-----------|--------|------|--------------------------------|
| `"TirePosition"`  | shall     | string  | -    |           |       
| `"TirePressure"`  | shall     | integer | kPa  | Pressure for the actual tire. If unavailable or sensor error, the value shall be null.      |
| `"TireTemperature"` | shall     | integer | °C   | Temperature for the actual tire. If unavailable or sensor error, the value shall be null.       |
> [!NOTE]
> All numeric attributes in `BasicMachineHealthV2` **may be null**.\
> A `null` value **shall indicate** that the corresponding sensor value or signal is unavailable or that a measurement error occurred.\
> Implementations **shall not** substitute default numeric values for missing data.


# BasicMachineHealthV2 Message Example
```json
{
  "Protocol":"Open-Autonomy",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.316Z",
  "EquipmentId": "f4d95a41-831e-4a27-9353-32872b7d6103",
  "BasicMachineHealthV2": {
  "FuelLevel": 74,
  "AdBlueLevel": null,
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
