# OIS-Media Service to Provider

## Scope

Media lifecycle, ingestion, and delivery across signage networks.

## Media request

* `POST /media/requests` - originating Service submits display and location context to a Provider for media selection.

Request parameters:

* `storeId` (string, required)
* `screenId` (string, optional)
* `deviceId` (string, optional, for audio or non-screen devices)
* `deviceType` (string, optional, e.g., `audio-player`)
* `zoneId` (string, optional)
* `department` (string, optional)
* `category` (string, optional)

Example request:

```json
{
  "storeId": "store-00421",
  "screenId": "store-00421-aisle7-endcap-1",
  "zoneId": "beverages-aisle-7",
  "department": "Beverages",
  "category": "Soft Drinks"
}
```

Example response:

```json
[
  {
    "mediaId": "cmp-934883",
    "campaignId": "winter-coke-2026",
    "asset": {
      "uri": "https://cdn.retailmedia.com/assets/coke_15s.mp4",
      "type": "video/mp4",
      "checksum": "f2ca1bb6c7e907d06dafe4687e579fce"
    },
    "targets": ["store-00421-aisle7-endcap-1"],
    "playback": {
      "durationSeconds": 15,
      "loop": false,
      "triggers": ["schedule", "motion"]
    },
    "caching": {
      "mode": "edge",
      "refreshOnChange": true
    },
    "validUntil": "2026-02-01T00:00:00Z"
  }
]
```

Schema (request):

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-media/media-request.schema.json",
  "title": "OIS Media Request",
  "type": "object",
  "additionalProperties": false,
  "required": ["storeId"],
  "properties": {
    "storeId": { "type": "string" },
    "screenId": { "type": "string" },
    "deviceId": { "type": "string" },
    "deviceType": { "type": "string" },
    "zoneId": { "type": "string" },
    "department": { "type": "string" },
    "category": { "type": "string" }
  }
}
```

Schema (response):

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-media/media-delivery.schema.json",
  "title": "OIS Media Delivery",
  "type": "array",
  "items": {
    "type": "object",
    "additionalProperties": false,
    "required": [
      "mediaId",
      "campaignId",
      "asset",
      "targets",
      "playback",
      "caching",
      "validUntil"
    ],
    "properties": {
      "mediaId": { "type": "string" },
      "campaignId": { "type": "string" },
      "asset": {
        "type": "object",
        "additionalProperties": false,
        "required": ["uri", "type", "checksum"],
        "properties": {
          "uri": { "type": "string", "format": "uri" },
          "type": {
            "type": "string",
            "enum": ["video/mp4", "video/webm", "image/png", "image/jpeg"]
          },
          "checksum": { "type": "string" }
        }
      },
      "targets": {
        "type": "array",
        "minItems": 1,
        "items": { "type": "string" }
      },
      "playback": {
        "type": "object",
        "additionalProperties": false,
        "required": ["durationSeconds", "loop", "triggers"],
        "properties": {
          "durationSeconds": { "type": "integer", "minimum": 1 },
          "loop": { "type": "boolean" },
          "triggers": {
            "type": "array",
            "minItems": 1,
            "items": {
              "type": "string",
              "enum": ["schedule", "motion", "manual", "event"]
            }
          }
        }
      },
      "caching": {
        "type": "object",
        "additionalProperties": false,
        "required": ["mode", "refreshOnChange"],
        "properties": {
          "mode": { "type": "string", "enum": ["edge", "origin", "device"] },
          "refreshOnChange": { "type": "boolean" }
        }
      },
      "validUntil": { "type": "string", "format": "date-time" }
    }
  }
}
```
