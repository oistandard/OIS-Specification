# OIS-Core Provider to Service

## Discovery

* `GET /.well-known/ois` - public discovery document.

Example payload (`examples/ois-core/authentication.json`):

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
