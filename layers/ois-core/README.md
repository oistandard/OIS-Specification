# OIS-Core

## Scope

Shared conventions and requirements across all OIS layers.

## Provider to Service (Ingest)

* Publish discovery metadata at `/.well-known/ois`.
* Declare supported layers, auth requirements, and transport expectations.

## Service to Provider (Delivery)

* Provide authorization tokens or access configuration based on discovery.

## Examples

* `examples/ois-core/authentication.json`

## Schemas

* `schemas/ois-core/authentication.schema.json`
