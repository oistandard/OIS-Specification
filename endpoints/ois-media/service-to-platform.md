# OIS-Media Service to Platform

## Scope

Media lifecycle, ingestion, and delivery across signage networks.

## Media delivery

* `POST /media/deliveries` - Service delivers media packages and playback instructions to the Platform.

Example payload:

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

Schema:

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
