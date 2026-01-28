# Use Case: Sensor-Only Execution

## Summary

A sensor Execution implements only OIS-Core and OIS-Sense, sending engagement
signals to the Orchestration for reporting and optimization.

## Flow

1. Execution exposes discovery at `/.well-known/ois`.
2. Orchestration validates supported layers (OIS-Core, OIS-Sense).
3. Execution emits sensor events to the Orchestration.

## Endpoints

* `GET /.well-known/ois`
* `POST /sense/events/query`

## Example payloads

See:

* `endpoints/ois-core/execution-to-orchestration.md`
* `endpoints/ois-sense/execution-to-orchestration.md`
