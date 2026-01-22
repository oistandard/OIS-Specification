# OIS-Location Service to Provider

## Scope

Store layout, zone hierarchy, and device placement context.

## Location updates

* `POST /location/stores` - update store layouts, zones, and devices.

Request parameters:

* `storeId` (string, optional)
* `storeIds` (array, optional)

Example payload:

```json
[
  {
    "storeId": "store-00421",
    "brand": "RetailCo",
    "address": {
      "city": "Atlanta",
      "state": "GA",
      "country": "US"
    },
    "zones": [
      {
        "zoneId": "beverages-aisle-7",
        "department": "Beverages",
        "adjacentZones": ["snacks-aisle-6", "checkout-lane-1"]
      }
    ],
    "screens": ["store-00421-aisle7-endcap-1"],
    "devices": [
      {
        "deviceId": "aud-1140",
        "deviceType": "audio-player",
        "zoneId": "beverages-aisle-7",
        "status": "active"
      },
      {
        "deviceId": "sns-7712",
        "deviceType": "vision-sensor",
        "zoneId": "beverages-aisle-7",
        "status": "active"
      }
    ]
  }
]
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-location/store-layout.schema.json",
  "title": "OIS Location Store Layout",
  "type": "array",
  "items": {
    "type": "object",
    "additionalProperties": false,
    "required": ["storeId", "brand", "address", "zones", "screens"],
    "properties": {
      "storeId": { "type": "string" },
      "brand": { "type": "string" },
      "address": {
        "type": "object",
        "additionalProperties": false,
        "required": ["city", "state", "country"],
        "properties": {
          "city": { "type": "string" },
          "state": { "type": "string" },
          "country": { "type": "string", "minLength": 2, "maxLength": 2 }
        }
      },
      "zones": {
        "type": "array",
        "minItems": 1,
        "items": {
          "type": "object",
          "additionalProperties": false,
          "required": ["zoneId", "department", "adjacentZones"],
          "properties": {
            "zoneId": { "type": "string" },
            "department": { "type": "string" },
            "adjacentZones": {
              "type": "array",
              "items": { "type": "string" }
            }
          }
        }
      },
      "screens": {
        "type": "array",
        "items": { "type": "string" }
      },
      "devices": {
        "type": "array",
        "items": {
          "type": "object",
          "additionalProperties": false,
          "required": ["deviceId", "deviceType", "zoneId", "status"],
          "properties": {
            "deviceId": { "type": "string" },
            "deviceType": {
              "type": "string",
              "enum": ["audio-player", "vision-sensor", "proximity-sensor"]
            },
            "zoneId": { "type": "string" },
            "status": { "type": "string", "enum": ["active", "inactive"] }
          }
        }
      }
    }
  }
}
```
