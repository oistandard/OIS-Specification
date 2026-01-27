# The Open In-Store Standard Specification

<img width="auto" height="200" alt="ois-brand" src="https://github.com/user-attachments/assets/fde9f442-7100-4797-b73d-3bc5fdcc6384" />

### Introducing OIS, a Retail & Commerce Media Industry Initiative
In-store retail and commerce media is entering a period of rapid growth. Screens, sensors, retail media networks, and AI-driven commerce experiences are expanding faster than the technical foundations that support them.

Today, most in-store integrations remain proprietary, custom, and vendor-locked — requiring costly, one-off engineering efforts between digital signage and sensor providers and the platforms that activate, measure, and optimize media. This fragmentation limits scale, slows innovation, and prevents physical retail from operating like a modern, interoperable media environment.

To address this, a cross-industry initiative is being formed to establish **OIS — the Open In-Store Standard**, a single API standard with optional layer implementation.

OIS defines:

* A provider-to-service ingest interface for inventory, signals, and measurement.
* A service-to-provider delivery interface for media, configuration, and orchestration.
* Canonical payload schemas and discovery metadata for interoperable integration.


## Founding Technical Steering Committee Members

The individuals guiding the formation of the OIS initiative, defining its initial scope, and coordinating early working groups:

* **Chris Foster** — EVP Product & Technology, DEEL Media
* More to come.

## Founding Members

Organizations formally participating in the development of the OIS standard.

* To be determined.

## Supporting Organizations

Organizations supporting the OIS initiative and its mission to establish open standards for in-store digital signage as a service.

* To be determined.

> Logos displayed for identification only. Participation does not imply endorsement of any specific product or commercial service.

# Core Objectives of the OIS Standard

The Open In-Store Standard (OIS) is being established to provide a common technical foundation for **In-Store Infrastructure as a Service (IIaaS)** in support of in-store retail and commerce media.

## 1. Simplify In-Store Retail & Commerce Media Integration

OIS is intended to significantly reduce the technical complexity of deploying in-store retail media by defining clear, standards-based integration paths between digital signage and sensor platforms and the in-house and third-party systems already used across retail media ecosystems.

By establishing common APIs, schemas, and operational contracts, OIS enables retail media networks, SSPs, DSPs, ad servers, analytics platforms, and commerce systems to integrate with in-store media environments without custom, vendor-specific development.

## 2. Make In-Store Screens a Native Extension of Retail Media Networks

OIS positions in-store screens as standardized, addressable media inventory within existing retail media and advertising ecosystems.

By aligning in-store screen definitions, delivery workflows, and measurement signals with established digital media paradigms, OIS enables physical screens to function as natural extensions of retail websites, apps, and on-site placements.

This allows Orchestration Systems, SSPs, DSPs, and Ad Servers to activate, manage, and measure in-store media using the same systems, workflows, and reporting models already in use.

## 3. Future-Proof In-Store Media and Experience Infrastructure

OIS is designed as an extensible standard that supports both current in-store retail media requirements and emerging technologies.

Beyond screen-based media delivery, OIS provides a structured framework for integrating sensor systems, contextual data, real-time events, and future AI-driven retail and commerce experiences.


# OIS Specification Layers

The OIS standard is structured into a set of specification layers. Each layer represents a defined functional domain within an in-store retail and commerce media ecosystem.

These layers are intended to establish a common, interoperable contract between digital signage and sensor platforms (including CMS, player, and device networks) and in-house or third-party systems such as retail media networks, SSPs, DSPs, measurement providers, and commerce platforms.

Each layer defines standardized APIs, data schemas, and operational behaviors to enable consistent discovery, activation, delivery, measurement, and contextualization of in-store media across heterogeneous signage infrastructures.

The following layers represent the initial scope of the OIS initiative and are provided as a foundation for industry collaboration, refinement, and formal specification.

## Provider and Service Roles

OIS is a single API standard with optional layer implementations. A Provider
may implement only the layers that match its capabilities (for example, a
sensor company may only implement OIS-Sense), while the Service/Platform side
ingests provider data and delivers media, configuration, or signals back to
providers. Each layer includes role-specific guidance for:

* Provider to Service (ingest)
* Service to Provider (delivery)

## Endpoints

This is a quick-start summary. Canonical endpoint documentation lives in
`endpoints/` and includes inline examples and schemas.

| Layer | Direction | Endpoint |
| --- | --- | --- |
| OIS-Display | Provider to Service | `POST /display/screens/query` |
| OIS-Media | Service to Provider | `POST /media/deliveries` |
| OIS-Proof-of-Play | Provider to Service | `POST /proof-of-play/events/query` |
| OIS-Sense | Provider to Service | `POST /sense/events/query` |
| OIS-Location | Provider to Service | `GET /location/stores` |
| OIS-Events | Provider to Service | `WSS /events` |
| OIS-Commerce | Service to Provider | `POST /commerce/sales` |
| OIS-Commerce | Provider to Service | `POST /commerce/attribution` |


## OIS-Core
### Foundation Layer

OIS-Core defines the baseline technical and governance framework required for interoperability across all OIS-compliant systems. This layer establishes the universal conventions used by all other specifications.

OIS-Core will standardize:

* API architectural patterns and transport requirements (e.g., HTTPS, WSS)
* Authentication and authorization models
* Canonical data schema conventions and object definitions
* Security requirements and privacy controls
* Versioning, compatibility, and deprecation policies
* Compliance, validation, and certification requirements

OIS-Core serves as the normative foundation upon which all other OIS specifications are built.


## OIS-Display
### Screen and Inventory Definition Layer

OIS-Display defines how in-store digital display inventory is described, classified, and exposed by digital signage platforms for consumption by retail media systems and connected tools.

This layer standardizes how signage providers publish screen-level metadata and capabilities so that in-house platforms, SSPs, DSPs, and activation systems can reliably discover, evaluate, and transact against in-store display inventory.

OIS-Display will standardize:

* Screen and surface classifications
* Physical and logical attributes (orientation, resolution, aspect ratios, zones, surfaces)
* Supported creative, media, and experience formats
* Physical placement and merchandising context (store, aisle, department, category)
* Screen state, health, availability, and control interfaces
This layer establishes the foundation for treating in-store screens as structured, addressable media inventory.


## OIS-Media
### Media Lifecycle and Delivery Layer

OIS-Media defines standardized mechanisms for the distribution, validation, management, and execution of media and experiences across digital signage infrastructures.

This layer governs how creative assets, experiences, and control instructions are transmitted from external systems into digital signage platforms and reliably delivered to in-store screens.

OIS-Media will standardize:

* Media and experience ingestion workflows
* Creative validation and capability negotiation
* Distribution and synchronization mechanisms
* Playback and execution instructions (e.g., duration, sequencing, conditional triggers)
* Caching, update propagation, and lifecycle management

OIS-Media ensures consistent, secure, and measurable delivery of in-store media across heterogeneous signage networks.


## OIS-Proof-of-Play
### Measurement and Compliance Layer

OIS-Proof-of-Play defines the authoritative data models and reporting mechanisms for confirming and auditing in-store media execution.

This layer establishes standardized proof-of-play, compliance, and delivery records suitable for ingestion by retail media networks, advertisers, internal analytics platforms, and third-party measurement systems.

OIS-PoP will standardize:

* Playback confirmation events
* Duration, frequency, and scheduling compliance
* Error and failure conditions
* Auditable delivery records and reconciliation artifacts

OIS-PoP is intended to support operational reporting, financial reconciliation, and third-party verification workflows.


## OIS-Sense
### Sensor and Engagement Layer

OIS-Sense defines how in-store sensing systems and engagement technologies are identified, described, and integrated within OIS-compliant environments.

This layer standardizes the representation and exchange of non-PII, in-store sensor and interaction data to support measurement, optimization, and adaptive in-store experiences.

OIS-Sense will standardize:

* Sensor classification and capability descriptions
* Proximity, motion, dwell, and interaction signals
* Touch and interactive engagement events
* Anonymized computer vision and audience analytics outputs
* Extensible models for emerging physical-AI interfaces

This layer enables consistent contextual and engagement data flows across signage, analytics, and media platforms.


## OIS-Location
### Physical Environment and Location Intelligence Layer

OIS-Location defines how physical environments, store layouts, and device placements are represented and referenced across OIS-compliant systems.

This layer standardizes the location and merchandising context required to support targeting, reporting, analytics, and operational orchestration.

OIS-Location will standardize:

* Store, venue, and zone hierarchies
* Physical placement descriptors and relationships
* Environmental and operational attributes
* Contextual metadata required for activation and measurement

OIS-Location provides the canonical spatial framework for in-store media and data interoperability.


## OIS-Events
### Real-Time Signaling and Interaction Layer

OIS-Events defines a real-time, event-driven interface for the exchange of live in-store state, analytics, and interaction signals.

This layer enables low-latency communication between digital signage systems and connected platforms for real-time monitoring, orchestration, and adaptive experiences.

OIS-Events will standardize:

* Publish/subscribe event models
* Screen, media, and system state updates
* Live proof-of-play and sensor streams
* Triggering and orchestration signals
* Commerce and experience handshake events

OIS-Events is intended to support operational observability, responsive content, and real-time retail experiences.


## OIS-Commerce
### Media-to-Transaction Bridge Layer

OIS-Commerce defines standardized interfaces that connect in-store media activity to commerce and transaction systems.

This layer enables in-store media to participate directly in commerce workflows, attribution modeling, and retail system integrations.

OIS-Commerce will standardize:

* POS and commerce system integration models
* Offer, promotion, and product-context signaling
* Attribution and outcome event schemas
* Transaction-adjacent data exchanges

OIS-Commerce establishes the foundation for closed-loop measurement and media-driven in-store commerce experiences.

## Repository Layout

This repository contains the OIS specification, endpoint definitions, and
example payloads.

* `versions/` contains the current draft spec in Markdown.
* `endpoints/` lists canonical endpoints, examples, and schemas.
* `use-cases/` contains end-to-end flows with inline payloads.
* `proposals/` captures future changes and work-in-progress ideas.
* `tests/` provides payload fixtures used for validation and tooling.
* `scripts/` contains build, validation, and tooling scripts (as they are added).
* `.github/` holds repo configuration and templates.

## Versions

Drafts live in `versions/`. The first working draft is `versions/0.1.0.md`.

## Endpoint Documentation

Canonical endpoint documentation is in `endpoints/`, organized by layer and
direction. Examples and schemas live inline with each endpoint.

## Use Cases

End-to-end flows live in `use-cases/` and demonstrate how providers and
services exchange data across layers.

## Participation

Please review `CONTRIBUTING.md` and `GOVERNANCE.md` before opening issues or PRs.

## License

See `LICENSE`.
