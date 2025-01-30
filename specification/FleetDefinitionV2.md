# FleetDefinitionV2

This message is the first message sent by both actors at connection. 

|Sender| Triggered by | 
|---|---|
|`AHS` |  At Connection |
|`AHS` |  At Runtime change |
|`FMS` |  At Connection |
|`FMS` |  At Runtime change |



## Message attributes

| key             |  format            | Description                                                             
|-------------------|------------|----------------|
| `"AHSId"`         | GUID           | Unique identifier for the AHS instance                                  |
| `"Equipment"`      | Array of objects | Collection of equipment objects (can be empty but **not null**)         |
| `"EquipmentId"`     | GUID           | Unique key used in messages to reference a specific equipment           | 
|`"HID"`            | String         | Human-readable label (only meaningful to people)                        | 
|`"Type"`           | Enumeration    | Equipment category                                                      | 
| `"OEM"`          | String         | Original Equipment Manufacturer                                         | 
| `"Model"`       | String         | OEM model number/name                                                   | 
| `"Autonomous"`      | Boolean        | Indicates autonomy capability                                           | 
| `"Length"`            | Decimal        | Distance from front to rear in meters                                   | 
| `"Width"`            | Decimal        | Distance from left to right in meters                                   | 



## Fleet ID

- The **Fleet ID** shall be **unique** across all fleets connecting to an FMS instance.
- It **must be immutable** across connections and system reboots.
- Each **Fleet Definition** must have exactly **one Fleet ID**.

> **Use Cases for Fleet ID:**  
> - Multiple different AHS fleets connecting to a single FMS.  
> - A single AHS instance managing multiple fleets within one FMS.  
> - A single AHS establishing multiple concurrent sessions with an FMS.

---

### Equipment Type Enumerations

Only valid enumerations from the list below shall be used as **Equipment Type**:

```json
{
  "HaulTruck", "Shovel", "Excavator", "Loader", "LightVehicle", 
  "WaterCart", "Grader", "FuelTruck", "LubeTruck", "Dozer", 
  "RubberTireDozer", "Drill", "Crusher", "Scraper", "BellyDumper", 
  "EmergencyVehicle", "Ambulance", "Dragline", "SurfaceMiner", 
  "Bus", "Train", "Trailer"
}
```

### FleetDefinitionV2 Message Example
```json

{
  "Protocol": "ISO23725",
  "Version": 1,
  "Timestamp": "2025-01-30T11:20:13.511Z",
  "FleetDefinitionV2": {
    "AHSId": "5318e44c-e9f0-42e2-9965-a4a1ff364f4b",
    "Equipment": [
      {
        "EquipmentId": "0c83193f-8772-446a-89c0-a3977e282b8a",
        "HID": "HT042",
        "Type": "HaulTruck",
        "OEM": "Scania",
        "Model": "ATS",
        "Autonomous": true,
        "Length": 9.51,
        "Width": 2.55
      },
      {
        "EquipmentId": "2248d535-3daf-4a86-b1e1-4951a22beec6",
        "HID": "LV033",
        "Type": "LightVehicle",
        "OEM": "Ford",
        "Model": "F350",
        "Autonomous": false,
        "Length": 4.67,
        "Width": 2.52
      }
    ]
  }
}
```
