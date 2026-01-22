# Endpoints

OIS defines canonical endpoints by layer and direction. The base URL is the
Provider's `endpoint` from discovery (e.g., `https://api.provider.com/ois`)
and all paths are relative to that base. Schemas are included inline in the
endpoint documents.

* Provider to Service (ingest): Provider sends data to the Service/Platform.
* Service to Provider (delivery): Service/Platform sends media, config, or
  signals back to the Provider.

Layer-specific endpoints live in `endpoints/<layer>/`.
