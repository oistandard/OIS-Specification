# OIS-Display Execution to Orchestration

## Scope

Screen and inventory definition for in-store display assets.

## Inventory query

* `POST /display/screens/query` - return screen inventory for one or more stores.

Request parameters:

* `storeIds` (array, required)

Example request:

```json
{
  "storeIds": ["store-00421", "store-00918"]
}
```

Example response:

```json
[
  {
    "screenId": "store-00421-aisle7-endcap-1",
    "storeId": "store-00421",
    "type": "endcap-display",
    "manufacturer": "Samsung",
    "orientation": "landscape",
    "resolution": { "width": 1920, "height": 1080 },
    "zones": [
      { "zoneId": "primary", "width": 1920, "height": 900 },
      { "zoneId": "ticker", "width": 1920, "height": 180 }
    ],
    "supportedFormats": ["image/png", "video/mp4", "html5", "interactive"],
    "placement": {
      "aisle": "7",
      "department": "Beverages",
      "category": "Soft Drinks"
    },
    "state": {
      "status": "active",
      "lastHeartbeat": "2026-01-06T13:01:44Z"
    }
  }
]
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-display/screen-inventory.schema.json",
  "title": "OIS Display Screen Inventory",
  "type": "array",
  "items": {
    "type": "object",
    "additionalProperties": false,
    "required": [
      "screenId",
      "storeId",
      "type",
      "manufacturer",
      "orientation",
      "resolution",
      "zones",
      "supportedFormats",
      "placement",
      "state"
    ],
    "properties": {
      "screenId": { "type": "string" },
      "storeId": { "type": "string" },
      "type": {
        "type": "string",
        "enum": [
          "endcap-display",
          "shelf-edge-display",
          "checkout-lane-display",
          "entrance-display",
          "department-wall-display",
          "kiosk-display",
          "window-display"
        ]
      },
      "manufacturer": { "type": "string" },
      "orientation": {
        "type": "string",
        "enum": ["landscape", "portrait"]
      },
      "resolution": {
        "type": "object",
        "additionalProperties": false,
        "required": ["width", "height"],
        "properties": {
          "width": { "type": "integer", "minimum": 1 },
          "height": { "type": "integer", "minimum": 1 }
        }
      },
      "zones": {
        "type": "array",
        "minItems": 1,
        "items": {
          "type": "object",
          "additionalProperties": false,
          "required": ["zoneId", "width", "height"],
          "properties": {
            "zoneId": { "type": "string" },
            "width": { "type": "integer", "minimum": 1 },
            "height": { "type": "integer", "minimum": 1 }
          }
        }
      },
      "supportedFormats": {
        "type": "array",
        "minItems": 1,
        "items": {
          "type": "string",
          "enum": [
            "image/png",
            "image/jpeg",
            "video/mp4",
            "video/webm",
            "html5",
            "interactive"
          ]
        }
      },
      "placement": {
        "type": "object",
        "additionalProperties": false,
        "required": ["aisle", "department", "category"],
        "properties": {
          "aisle": { "type": "string" },
          "department": { "type": "string" },
          "category": { "type": "string" }
        }
      },
      "state": {
        "type": "object",
        "additionalProperties": false,
        "required": ["status", "lastHeartbeat"],
        "properties": {
          "status": {
            "type": "string",
            "enum": ["active", "inactive", "maintenance", "offline"]
          },
          "lastHeartbeat": { "type": "string", "format": "date-time" }
        }
      }
    }
  }
}
```
