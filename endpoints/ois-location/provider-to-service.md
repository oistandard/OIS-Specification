# OIS-Location Provider to Service

## Layout retrieval

* `GET /location/stores` - retrieve store layouts, zones, and devices.

Request parameters:

* `storeIds` (array, optional, query param; accepts one or many)

Query string examples:

* `GET /location/stores?storeIds=store-00421,store-00918`
* `GET /location/stores?storeIds=store-00421&storeIds=store-00918`

Example response (`examples/ois-location/store-layout.json`):

```json
[
  {
    "storeId": "store-00421",
    "brand": "RetailCo",
    "address": {
      "city": "Atlanta",
      "state": "GA",
      "country": "US"
    },
    "zones": [
      {
        "zoneId": "beverages-aisle-7",
        "department": "Beverages",
        "adjacentZones": ["snacks-aisle-6", "checkout-lane-1"]
      }
    ],
    "screens": ["store-00421-aisle7-endcap-1"],
    "devices": [
      {
        "deviceId": "aud-1140",
        "deviceType": "audio-player",
        "zoneId": "beverages-aisle-7",
        "status": "active"
      },
      {
        "deviceId": "sns-7712",
        "deviceType": "vision-sensor",
        "zoneId": "beverages-aisle-7",
        "status": "active"
      }
    ]
  }
]
```
