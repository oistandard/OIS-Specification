# Endpoints

OIS defines canonical endpoints by layer and direction. The base URL is the
Execution's `endpoint` from discovery (e.g., `https://api.service.com/ois`)
and all paths are relative to that base. Schemas are included inline in the
endpoint documents.

* Execution to Orchestration (ingest): Execution sends data to the Orchestration.
* Orchestration to Execution (delivery): Orchestration sends media, config, or signals
  back to the Execution.

Layer-specific endpoints live in `endpoints/<layer>/`.
