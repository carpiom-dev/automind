# Vehicle Telemetry Service

## Version

0.1.0

## Purpose

Receive, validate, normalize and process vehicle telemetry received
from the AutoMind mobile application.

The mobile application communicates with the vehicle through OBD-II
and Bluetooth.

The telemetry service does not communicate directly with Bluetooth
or OBD-II.

## Responsibilities

The service is responsible for:

- receiving telemetry
- validating telemetry
- normalizing telemetry
- associating telemetry with a vehicle
- storing telemetry
- exposing telemetry queries
- publishing telemetry events when required
- providing observability

## Out of Scope

The service must not:

- communicate directly with Bluetooth
- communicate directly with OBD-II
- control the vehicle
- calculate navigation routes
- search for fuel stations
- manage maintenance
- execute AI conversations
- manage user accounts

## Initial Telemetry

The initial model may contain:

- vehicleId
- telemetryId
- timestamp
- rpm
- speed
- engineTemperature
- batteryVoltage
- fuelLevel

Availability of individual vehicle parameters must not be assumed.
The actual OBD-II capabilities of the vehicle must be verified.

## Units

RPM:

revolutions per minute

Speed:

km/h

Engine temperature:

°C

Battery voltage:

V

Fuel level:

percentage

## Validation

External telemetry must be validated.

Examples:

- vehicleId is required
- telemetryId is required
- timestamp is required
- numeric values must respect valid ranges
- negative RPM is invalid
- negative speed is invalid
- invalid fuel percentages are rejected

## Idempotency

Telemetry messages must be idempotent.

Repeated delivery of the same telemetry message must not create
uncontrolled duplicates.

## API

POST /api/v1/telemetry

GET /api/v1/vehicles/{vehicleId}/telemetry/current

GET /api/v1/vehicles/{vehicleId}/telemetry

## Security

The service must not expose vehicle control operations.

Telemetry is read-only from the vehicle perspective.

## Acceptance Criteria

A valid telemetry message can be:

1. authenticated
2. validated
3. processed
4. persisted
5. queried through the API

Invalid telemetry must be rejected with a consistent error response.