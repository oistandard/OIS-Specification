# Use Case: Ad Server Media Delivery

## Summary

An ad server submits a media request to a signage Provider and receives
delivery instructions and proof-of-play events for reporting.

## Flow

1. Provider exposes discovery at `/.well-known/ois`.
2. Service retrieves supported layers and auth requirements.
3. Service submits a media request to Provider.
4. Provider responds with media deliveries.
5. Provider emits proof-of-play events back to Service.

## Endpoints

* `GET /.well-known/ois`
* `POST /media/requests`
* `POST /proof-of-play/events`

## Example payloads

See:

* `endpoints/ois-core/provider-to-service.md`
* `endpoints/ois-media/service-to-provider.md`
* `endpoints/ois-proof-of-play/provider-to-service.md`
