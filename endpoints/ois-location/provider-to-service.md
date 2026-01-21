# OIS-Location Provider to Service

## Layout ingest

* `POST /location/stores` - submit store layouts and zones.

Example payload (`examples/ois-location/store-layout.json`):

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
    "screens": ["store-00421-aisle7-endcap-1"]
  }
]
```
