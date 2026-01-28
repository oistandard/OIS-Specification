# Use Case: Ad Server Media Delivery

## Summary

An ad server submits a media request to a signage Service and receives
delivery instructions and proof-of-play events for reporting.

## Flow

1. Service exposes discovery at `/.well-known/ois`.
2. Platform retrieves supported layers and auth requirements.
3. Platform submits a media request to the Service.
4. Service responds with media deliveries.
5. Service emits proof-of-play events back to the Platform.

## Endpoints

* `GET /.well-known/ois`
* `POST /media/requests`
* `POST /proof-of-play/events/query`

## Example payloads

See:

* `endpoints/ois-core/service-to-platform.md`
* `endpoints/ois-media/platform-to-service.md`
* `endpoints/ois-proof-of-play/service-to-platform.md`
