# OIS-Core Execution to Orchestration

## Scope

Connectivity metadata and discovery for the OIS API.

## Discovery

* `GET /.well-known/ois` - public discovery document.

Example payload:

```json
{
  "oisVersion": "1.0",
  "provider": {
    "id": "company-name-or-identifier",
    "capabilities": ["ois-display", "ois-events", "ois-location"],
    "endpoint": "https://api.signage-provider.com/ois"
  },
  "authentication": {
    "type": "oauth2",
    "tokenEndpoint": "https://auth.signage-provider.com/ois/token",
    "scopes": ["ois.read", "ois.write", "ois.events"]
  },
  "security": {
    "transport": "TLS1.3",
    "signing": "HMAC-SHA256"
  },
  "compliance": {
    "certification": "OIS-Core",
    "lastValidated": "2026-01-04T15:22:11Z"
  }
}
```

Schema:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "https://ois.foundation/schemas/ois-core/authentication.schema.json",
  "title": "OIS Core Authentication Profile",
  "type": "object",
  "additionalProperties": false,
  "required": [
    "oisVersion",
    "provider",
    "authentication",
    "security",
    "compliance"
  ],
  "properties": {
    "oisVersion": { "type": "string" },
    "provider": {
      "type": "object",
      "additionalProperties": false,
      "required": ["id", "capabilities", "endpoint"],
      "properties": {
        "id": { "type": "string" },
        "capabilities": {
          "type": "array",
          "minItems": 1,
          "items": {
            "type": "string",
            "enum": [
              "ois-core",
              "ois-display",
              "ois-media",
              "ois-proof-of-play",
              "ois-sense",
              "ois-location",
              "ois-events",
              "ois-commerce"
            ]
          }
        },
        "endpoint": { "type": "string", "format": "uri" }
      }
    },
    "authentication": {
      "type": "object",
      "additionalProperties": false,
      "required": ["type", "tokenEndpoint", "scopes"],
      "properties": {
        "type": { "type": "string", "enum": ["oauth2"] },
        "tokenEndpoint": { "type": "string", "format": "uri" },
        "scopes": {
          "type": "array",
          "minItems": 1,
          "items": { "type": "string" }
        }
      }
    },
    "security": {
      "type": "object",
      "additionalProperties": false,
      "required": ["transport", "signing"],
      "properties": {
        "transport": { "type": "string", "enum": ["TLS1.2", "TLS1.3"] },
        "signing": { "type": "string" }
      }
    },
    "compliance": {
      "type": "object",
      "additionalProperties": false,
      "required": ["certification", "lastValidated"],
      "properties": {
        "certification": { "type": "string", "enum": ["OIS-Core"] },
        "lastValidated": { "type": "string", "format": "date-time" }
      }
    }
  }
}
```
