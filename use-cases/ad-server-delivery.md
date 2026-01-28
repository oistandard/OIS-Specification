# Use Case: Ad Server Media Delivery

## Summary

This flow supports two options:

* Execution requests media from the Orchestration.
* Orchestration publishes media to the Execution.

Both options can be used together or independently, with proof-of-play events
reported back to the Orchestration.

## Flow (Option A: Execution requests media)

1. Execution exposes discovery at `/.well-known/ois`.
2. Orchestration retrieves supported layers and auth requirements.
3. Execution submits a media request to the Orchestration.
4. Orchestration responds with media deliveries.
5. Execution emits proof-of-play events back to the Orchestration.

## Flow (Option B: Orchestration publishes media)

1. Execution exposes discovery at `/.well-known/ois`.
2. Orchestration retrieves supported layers and auth requirements.
3. Orchestration publishes media deliveries to the Execution.
4. Execution emits proof-of-play events back to the Orchestration.

## Endpoints

* `GET /.well-known/ois`
* `POST /media/requests`
* `POST /media/deliveries`
* `POST /proof-of-play/events/query`

## Example payloads

See:

* `endpoints/ois-core/execution-to-orchestration.md`
* `endpoints/ois-media/execution-to-orchestration.md`
* `endpoints/ois-media/orchestration-to-execution.md`
* `endpoints/ois-proof-of-play/execution-to-orchestration.md`
