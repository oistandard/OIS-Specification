# OIS-Commerce Provider to Service

## Attribution submission

* `POST /commerce/attribution` - submit attribution events.

## Attribution query

* `POST /commerce/attribution/query` - return attribution details by store or screen.

Request parameters:

* `storeId` (string, optional)
* `storeIds` (array, optional)
* `screenId` (string, optional)
* `startAt` (string, date-time, optional)
* `endAt` (string, date-time, optional)

Example response (`examples/ois-commerce/transaction-attribution.json`):

```json
{
  "eventType": "commerce-attribution",
  "storeId": "store-00421",
  "screenId": "store-00421-aisle7-endcap-1",
  "campaignId": "winter-coke-2026",
  "mediaId": "cmp-934883",
  "product": {
    "sku": "049000028904",
    "name": "Coca-Cola 20oz"
  },
  "interaction": {
    "type": "viewed",
    "dwellSeconds": 9.1
  },
  "transaction": {
    "posSystem": "NCR",
    "transactionId": "txn-88219912",
    "occurredAt": "2026-01-06T14:23:41Z"
  },
  "confidence": 0.82
}
```
