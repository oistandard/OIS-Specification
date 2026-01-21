# Use Case: Ad Server Media Delivery

## Summary

An ad server delivers media to a signage Provider and receives proof-of-play
events for reporting.

## Flow

1. Provider exposes discovery at `/.well-known/ois`.
2. Service retrieves supported layers and auth requirements.
3. Service delivers media to Provider.
4. Provider emits proof-of-play events back to Service.

## Endpoints

* `GET /.well-known/ois`
* `POST /media/deliveries`
* `POST /proof-of-play/events`

## Example payloads

* `examples/ois-core/authentication.json`
* `examples/ois-media/media-delivery.json`
* `examples/ois-proof-of-play/playback-event.json`
