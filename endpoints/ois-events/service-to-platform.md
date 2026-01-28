# OIS-Events Service to Platform

## Scope

Real-time signals and state updates for live orchestration.

## Real-time events

* `WSS /events` - stream real-time events and state changes.

Example payload:

```json
{
  "event": "screen.state.update",
  "timestamp": "2026-01-06T14:22:14Z",
  "screenId": "store-00421-aisle7-endcap-1",
  "payload": {
    "currentMedia": "cmp-934883",
    "uptimeSeconds": 443223,
    "lastInteractionSecondsAgo": 2,
    "activeSensors": ["nxm-7712"]
  }
}
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-events/realtime-event.schema.json",
  "title": "OIS Events Realtime Event",
  "type": "object",
  "additionalProperties": false,
  "required": ["event", "timestamp", "screenId", "payload"],
  "properties": {
    "event": { "type": "string" },
    "timestamp": { "type": "string", "format": "date-time" },
    "screenId": { "type": "string" },
    "payload": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "currentMedia",
        "uptimeSeconds",
        "lastInteractionSecondsAgo",
        "activeSensors"
      ],
      "properties": {
        "currentMedia": { "type": "string" },
        "uptimeSeconds": { "type": "integer", "minimum": 0 },
        "lastInteractionSecondsAgo": { "type": "integer", "minimum": 0 },
        "activeSensors": {
          "type": "array",
          "items": { "type": "string" }
        }
      }
    }
  }
}
```
