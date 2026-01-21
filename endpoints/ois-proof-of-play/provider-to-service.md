# OIS-Proof-of-Play Provider to Service

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

Example response (`examples/ois-proof-of-play/playback-event.json`):

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
