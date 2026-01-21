# OIS-Media Provider to Service

## Runtime signals

* `POST /media/acknowledgements` - confirm delivery and readiness.

Example payload (`examples/ois-media/media-delivery.json`):

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
