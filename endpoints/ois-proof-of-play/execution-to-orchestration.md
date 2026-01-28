# OIS-Proof-of-Play Execution to Orchestration

## Scope

Playback confirmation, compliance, and audit data.

## Playback event query

* `POST /proof-of-play/events/query` - retrieve proof-of-play events by store or screen.

Request parameters:

* `storeId` (string, optional)
* `storeIds` (array, optional)
* `screenId` (string, optional)
* `startAt` (string, date-time, optional)
* `endAt` (string, date-time, optional)

Example request:

```json
{
  "storeId": "store-00421",
  "startAt": "2026-01-06T00:00:00Z",
  "endAt": "2026-01-06T23:59:59Z"
}
```

Example response:

```json
[
  {
    "eventType": "proof-of-play",
    "mediaId": "cmp-934883",
    "screenId": "store-00421-aisle7-endcap-1",
    "playedAt": "2026-01-06T14:22:09Z",
    "durationSeconds": 15,
    "result": "completed",
    "sessionId": "pop-77ab1290",
    "deviceState": {
      "temperature": "normal",
      "connectivity": "online"
    },
    "audit": {
      "signature": "MEYCIQDQ…",
      "source": "signage-player"
    }
  }
]
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-proof-of-play/playback-event.schema.json",
  "title": "OIS Proof-of-Play Playback Event",
  "type": "array",
  "items": {
    "type": "object",
    "additionalProperties": false,
    "required": [
      "eventType",
      "mediaId",
      "screenId",
      "playedAt",
      "durationSeconds",
      "result",
      "sessionId",
      "deviceState",
      "audit"
    ],
    "properties": {
      "eventType": { "type": "string", "enum": ["proof-of-play"] },
      "mediaId": { "type": "string" },
      "screenId": { "type": "string" },
      "playedAt": { "type": "string", "format": "date-time" },
      "durationSeconds": { "type": "integer", "minimum": 1 },
      "result": {
        "type": "string",
        "enum": ["completed", "partial", "failed"]
      },
      "sessionId": { "type": "string" },
      "deviceState": {
        "type": "object",
        "additionalProperties": false,
        "required": ["temperature", "connectivity"],
        "properties": {
          "temperature": { "type": "string" },
          "connectivity": {
            "type": "string",
            "enum": ["online", "offline", "degraded"]
          }
        }
      },
      "audit": {
        "type": "object",
        "additionalProperties": false,
        "required": ["signature", "source"],
        "properties": {
          "signature": { "type": "string" },
          "source": { "type": "string" }
        }
      }
    }
  }
}
```
