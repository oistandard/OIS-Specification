# OIS-Sense Provider to Service

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

Example response (`examples/ois-sense/sensor-event.json`):

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

## Device inventory (optional)

* `GET /sense/devices` - retrieve sensors or other sensing devices by store.

Example payload (`examples/ois-sense/device-inventory.json`):

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
