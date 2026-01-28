# Use Case: Sensor-Only Service

## Summary

A sensor Service implements only OIS-Core and OIS-Sense, sending engagement
signals to the Platform for reporting and optimization.

## Flow

1. Service exposes discovery at `/.well-known/ois`.
2. Platform validates supported layers (OIS-Core, OIS-Sense).
3. Service emits sensor events to the Platform.

## Endpoints

* `GET /.well-known/ois`
* `POST /sense/events/query`

## Example payloads

See:

* `endpoints/ois-core/service-to-platform.md`
* `endpoints/ois-sense/service-to-platform.md`
