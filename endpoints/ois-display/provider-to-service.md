# OIS-Display Provider to Service

## Inventory query

* `POST /display/screens/query` - return screen inventory for one or more stores.

Request parameters:

* `storeId` (string, optional)
* `storeIds` (array, optional)

Example request:

```json
{
  "storeIds": ["store-00421", "store-00918"]
}
```

Example response (`examples/ois-display/screen-inventory.json`):

```json
[
  {
    "screenId": "store-00421-aisle7-endcap-1",
    "storeId": "store-00421",
    "type": "endcap-display",
    "manufacturer": "Samsung",
    "orientation": "landscape",
    "resolution": { "width": 1920, "height": 1080 },
    "zones": [
      { "zoneId": "primary", "width": 1920, "height": 900 },
      { "zoneId": "ticker", "width": 1920, "height": 180 }
    ],
    "supportedFormats": ["image/png", "video/mp4", "html5", "interactive"],
    "placement": {
      "aisle": "7",
      "department": "Beverages",
      "category": "Soft Drinks"
    },
    "state": {
      "status": "active",
      "lastHeartbeat": "2026-01-06T13:01:44Z"
    }
  }
]
```
