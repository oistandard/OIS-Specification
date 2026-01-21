# OIS-Events Provider to Service

## Real-time events

* `WSS /events` - stream real-time events and state changes.

Example payload (`examples/ois-events/realtime-event.json`):

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
