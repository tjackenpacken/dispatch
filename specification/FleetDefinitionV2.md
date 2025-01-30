# Fleet Definition Message

## Overview

The **Fleet Definition Message** shall be the first message sent by both actors upon connection.

Actors shall be able to receive and process a new fleet definition message with updated content at runtime.  
This message shall be re-sent by an actor when the list of monitored machines changes. The list can change by adding, deleting, or modifying a machine.  

Both actors shall use the same **GUID** and an equivalent description for the same physical machine, ensuring semantic consistency across systems.  
Only the actor owning the modified list shall send an updated **Fleet Definition Message**.

## Fleet Definition Message Initiator and Trigger

| Trigger Condition  | AHS to FMS | FMS to AHS |
|-------------------|------------|------------|
| At connection    | ✅ Yes      | ✅ Yes      |
| Runtime change   | ✅ Yes      | ✅ Yes      |

> **Note:**  
> The purpose of this message is to detect discrepancies between the AHS and FMS fleet configurations.  
> It helps end-users complete machine definitions within their respective systems.  
> This message **does not** synchronize a single source of equipment definition but serves as an alert mechanism.

---

## Fleet Definition Message Structure

The content of a **Fleet Definition Message** must comply with the following structure:

### Table: Fleet Definition Structure

| Member             | Req. Level | Type            | Description                                                             | Example |
|-------------------|------------|----------------|-------------------------------------------------------------------------|---------|
| **FleetDefinitionV2** | shall      | Object         | Identifies this structure as a Fleet Definition                          | —       |
| **AHSId**         | shall      | GUID           | Unique identifier for the AHS instance                                  | `5318e44c-e9f0-42e2-9965-a4a1ff364f4b` |
| **Equipment**     | shall      | Array of objects | Collection of equipment objects (can be empty but **not null**)         | `[ ]`   |
| **EquipmentId**   | shall      | GUID           | Unique key used in messages to reference a specific equipment           | `0c83193f-8772-446a-89c0-a3977e282b8a` |
| **HID**          | shall      | String         | Human-readable label (only meaningful to people)                        | `LV033`, `"Bucyrus 05"` |
| **Type**         | shall      | Enumeration    | Equipment category                                                      | `HaulTruck`, `Shovel` |
| **OEM**          | shall      | String         | Original Equipment Manufacturer                                         | `Honda` |
| **Model**        | shall      | String         | OEM model number/name                                                   | `Civic`, `793D` |
| **Autonomous**   | shall      | Boolean        | Indicates autonomy capability                                           | `true`, `false` |
| **Length**       | shall      | Decimal        | Distance from front to rear in meters                                   | `4.56` |
| **Width**        | shall      | Decimal        | Distance from left to right in meters                                   | `1.43` |

> **Note:**  
> - Editing the fleet (adding, deleting, or modifying a machine) simply updates the **Equipment List** in the Fleet Definition Message.  
> - **No delete command exists**.

---

## Fleet ID

- The **Fleet ID** shall be **unique** across all fleets connecting to an FMS instance.
- It **must be immutable** across connections and system reboots.
- Each **Fleet Definition** must have exactly **one Fleet ID**.

> **Use Cases for Fleet ID:**  
> - Multiple different AHS fleets connecting to a single FMS.  
> - A single AHS instance managing multiple fleets within one FMS.  
> - A single AHS establishing multiple concurrent sessions with an FMS.

---

## Equipment Type

Only valid enumerations from the list below shall be used as **Equipment Type**:

```json
{
  "HaulTruck", "Shovel", "Excavator", "Loader", "LightVehicle", 
  "WaterCart", "Grader", "FuelTruck", "LubeTruck", "Dozer", 
  "RubberTireDozer", "Drill", "Crusher", "Scraper", "BellyDumper", 
  "EmergencyVehicle", "Ambulance", "Dragline", "SurfaceMiner", 
  "Bus", "Train", "Trailer"
}


{
  "Protocol": "ISO23725",
  "Version": 1,
  "Timestamp": "2018-10-31T09:30:10.43.511Z",
  "FleetDefinitionV2": {
    "AHSId": "5318e44c-e9f0-42e2-9965-a4a1ff364f4b",
    "Equipment": [
      {
        "EquipmentId": "0c83193f-8772-446a-89c0-a3977e282b8a",
        "HID": "HT042",
        "Type": "HaulTruck",
        "OEM": "ETF",
        "Model": "Virtual-F",
        "Autonomous": true,
        "Length": 14.57,
        "Width": 9.02
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