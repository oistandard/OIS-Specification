# Use Case: Sensor-Only Provider

## Summary

A sensor Provider implements only OIS-Core and OIS-Sense, sending engagement
signals to the Service/Platform for reporting and optimization.

## Flow

1. Provider exposes discovery at `/.well-known/ois`.
2. Service validates supported layers (OIS-Core, OIS-Sense).
3. Provider emits sensor events to the Service.

## Endpoints

* `GET /.well-known/ois`
* `POST /sense/events`

## Example payloads

* `examples/ois-core/authentication.json`
* `examples/ois-sense/sensor-event.json`
