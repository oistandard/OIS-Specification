# OIS-Sense Execution to Orchestration

## Scope

Sensor and engagement signals for in-store environments.

## Sensor event query

* `POST /sense/events/query` - retrieve sensor events by store or screen.

Request parameters:

* `storeId` (string, optional)
* `storeIds` (array, optional)
* `screenId` (string, optional)
* `startAt` (string, date-time, optional)
* `endAt` (string, date-time, optional)

Example request:

```json
{
  "storeIds": ["store-00421"],
  "startAt": "2026-01-06T00:00:00Z",
  "endAt": "2026-01-06T23:59:59Z"
}
```

Example response:

```json
[
  {
    "sensorId": "nxm-7712",
    "type": "proximity-dwell",
    "screenId": "store-00421-aisle7-endcap-1",
    "timestamp": "2026-01-06T14:22:12Z",
    "metrics": {
      "presence": true,
      "dwellSeconds": 8.3,
      "motionDetected": true
    },
    "confidence": 0.91,
    "privacy": {
      "containsPII": false,
      "anonymized": true
    }
  }
]
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-sense/sensor-event.schema.json",
  "title": "OIS Sense Sensor Event",
  "type": "array",
  "items": {
    "type": "object",
    "additionalProperties": false,
    "required": [
      "sensorId",
      "type",
      "screenId",
      "timestamp",
      "metrics",
      "confidence",
      "privacy"
    ],
    "properties": {
      "sensorId": { "type": "string" },
      "type": {
        "type": "string",
        "enum": ["proximity-dwell", "motion", "engagement"]
      },
      "screenId": { "type": "string" },
      "timestamp": { "type": "string", "format": "date-time" },
      "metrics": {
        "type": "object",
        "additionalProperties": false,
        "required": ["presence", "dwellSeconds", "motionDetected"],
        "properties": {
          "presence": { "type": "boolean" },
          "dwellSeconds": { "type": "number", "minimum": 0 },
          "motionDetected": { "type": "boolean" }
        }
      },
      "confidence": { "type": "number", "minimum": 0, "maximum": 1 },
      "privacy": {
        "type": "object",
        "additionalProperties": false,
        "required": ["containsPII", "anonymized"],
        "properties": {
          "containsPII": { "type": "boolean" },
          "anonymized": { "type": "boolean" }
        }
      }
    }
  }
}
```

## Device inventory (optional)

* `GET /sense/devices` - retrieve sensors or other sensing devices by store.

Example payload:

```json
[
  {
    "deviceId": "aud-1140",
    "deviceType": "audio-player",
    "storeId": "store-00421",
    "zoneId": "beverages-aisle-7",
    "status": "active"
  },
  {
    "deviceId": "sns-7712",
    "deviceType": "vision-sensor",
    "storeId": "store-00421",
    "zoneId": "beverages-aisle-7",
    "status": "active"
  }
]
```
