# OIS-Sense Provider to Service

## Sensor events

* `POST /sense/events` - submit sensor and engagement events.

Example payload (`examples/ois-sense/sensor-event.json`):

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
