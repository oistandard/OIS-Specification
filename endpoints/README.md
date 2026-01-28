# Endpoints

OIS defines canonical endpoints by layer and direction. The base URL is the
Service's `endpoint` from discovery (e.g., `https://api.service.com/ois`)
and all paths are relative to that base. Schemas are included inline in the
endpoint documents.

* Service to Platform (ingest): Service sends data to the Platform.
* Platform to Service (delivery): Platform sends media, config, or signals
  back to the Service.

Layer-specific endpoints live in `endpoints/<layer>/`.
