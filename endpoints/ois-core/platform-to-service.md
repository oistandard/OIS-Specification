# OIS-Core Platform to Service

## Scope

Authentication and token issuance for API access.

## Authentication

* `POST /auth/token` - token issuance endpoint (referenced by discovery).

Notes:

* The `tokenEndpoint` in discovery SHOULD point to this endpoint.
