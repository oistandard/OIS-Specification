# OIS-Commerce Orchestration to Execution

## Scope

Commerce attribution and outcome signaling.

## Sales data delivery

* `POST /commerce/sales` - deliver sales data by store.

Request parameters:

* `storeId` (string, required)

Example payload:

```json
{
  "storeId": "store-00421",
  "salesWindow": {
    "startAt": "2026-01-06T00:00:00Z",
    "endAt": "2026-01-06T23:59:59Z"
  },
  "currency": "USD",
  "totals": {
    "grossSales": 12450.32,
    "transactionCount": 642
  },
  "mediaAttributionContext": [
    {
      "campaignId": "winter-coke-2026",
      "mediaId": "cmp-934883",
      "product": {
        "sku": "049000028904",
        "name": "Coca-Cola 20oz"
      }
    }
  ]
}
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-commerce/service-sales.schema.json",
  "title": "OIS Commerce Execution Sales",
  "type": "object",
  "additionalProperties": false,
  "required": ["storeId", "salesWindow", "currency", "totals"],
  "properties": {
    "storeId": { "type": "string" },
    "salesWindow": {
      "type": "object",
      "additionalProperties": false,
      "required": ["startAt", "endAt"],
      "properties": {
        "startAt": { "type": "string", "format": "date-time" },
        "endAt": { "type": "string", "format": "date-time" }
      }
    },
    "currency": { "type": "string", "minLength": 3, "maxLength": 3 },
    "totals": {
      "type": "object",
      "additionalProperties": false,
      "required": ["grossSales", "transactionCount"],
      "properties": {
        "grossSales": { "type": "number", "minimum": 0 },
        "transactionCount": { "type": "integer", "minimum": 0 }
      }
    },
    "mediaAttributionContext": {
      "type": "array",
      "items": {
        "type": "object",
        "additionalProperties": false,
        "required": ["campaignId", "mediaId", "product"],
        "properties": {
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
          }
        }
      }
    }
  }
}
```
