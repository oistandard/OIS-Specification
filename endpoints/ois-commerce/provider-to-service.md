# OIS-Commerce Provider to Service

## Scope

Commerce attribution and outcome signaling.

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

Example response:

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

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-commerce/transaction-attribution.schema.json",
  "title": "OIS Commerce Transaction Attribution",
  "type": "object",
  "additionalProperties": false,
  "required": [
    "eventType",
    "storeId",
    "screenId",
    "campaignId",
    "mediaId",
    "product",
    "interaction",
    "transaction",
    "confidence"
  ],
  "properties": {
    "eventType": { "type": "string", "enum": ["commerce-attribution"] },
    "storeId": { "type": "string" },
    "screenId": { "type": "string" },
    "campaignId": { "type": "string" },
    "mediaId": { "type": "string" },
    "product": {
      "type": "object",
      "additionalProperties": false,
      "required": ["sku", "name"],
      "properties": {
        "sku": { "type": "string" },
        "name": { "type": "string" }
      }
    },
    "interaction": {
      "type": "object",
      "additionalProperties": false,
      "required": ["type", "dwellSeconds"],
      "properties": {
        "type": { "type": "string", "enum": ["viewed", "touched", "engaged"] },
        "dwellSeconds": { "type": "number", "minimum": 0 }
      }
    },
    "transaction": {
      "type": "object",
      "additionalProperties": false,
      "required": ["posSystem", "transactionId", "occurredAt"],
      "properties": {
        "posSystem": { "type": "string" },
        "transactionId": { "type": "string" },
        "occurredAt": { "type": "string", "format": "date-time" }
      }
    },
    "confidence": { "type": "number", "minimum": 0, "maximum": 1 }
  }
}
```
