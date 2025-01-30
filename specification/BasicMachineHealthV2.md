# BasicMachineHealthV2

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Runtime change |

## Message attributes

| Key                  | Req. Level | Type          | Unit  | Description                                             | Example   |
|-------------------------|-----------|--------------|------|---------------------------------------------------------|-----------|
| `"FuelLevel"`           | shall     | integer      | %    | As defined by SAEJ1939 SPN-96 and 38                   | `75`      |
| `"TotalMachineHour"`    | should    | decimal      | h    | As defined by SAEJ1939 SPN-246. Single decimal         | `7 451,1` |
| `"TotalEngineHour"`     | shall     | decimal      | h    | As defined by SAEJ1939 SPN-247. Single decimal         | `3 756,8` |
| `"Tire"`               | should    | Object Array | -    | A list of an object containing tire properties         |           |

### Array Of `[ ]`
| Key             | Req. Level | Type    | Unit  | Description                            | Example |
|-------------------|-----------|--------|------|--------------------------------|---------|
| `"TirePosition"`  | shall     | string  | -    | As defined by [4.2.5](#)               |         |
| `"TirePressure"`  | shall     | integer | kPa  | As defined by SAEJ1939 SPN-241         | `271`   |
| `"TireTemperature"` | shall     | integer | °C   | As defined by SAEJ1939 SPN-242         | `47`    |

# MachineAllStopRequestV1 Message Example
### Apply AllStop
```json
{
  "Protocol":"ISO23725",
  "Version": 1,
  "Timestamp": "2024-10-31T09:30:10.43.511Z",
  "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
  "BasicMachineHealthV2": {
  "FuelLevel": 74,
  "TotalMachineHour": 4876.4,
  "TotalEngineHour": 735.1,
  "PrimeMoverTemp": 147,
  "Tire": [
    {“TirePosition”:"1.7", “TirePressure”: 303, “TireTemperature”: 39},
    {“TirePosition”:"1.9", “TirePressure”: 297, “TireTemperature”: 39},
    {“TirePosition”:"2.6", “TirePressure”: 335, “TireTemperature”: 42},
    {“TirePosition”:"2.7", “TirePressure”: 334, “TireTemperature”: 41},
    {“TirePosition”:"2.9", “TirePressure”: 329, “TireTemperature”: 42},
    {“TirePosition”:"2.10", “TirePressure”: 332, “TireTemperature”: 43}
    ]
  }
}
```
