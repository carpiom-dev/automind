# Vehicle Telemetry Service Architecture

## Architecture Style

The service follows:

- Clean Architecture
- Hexagonal Architecture
- SOLID
- DDD tactical patterns where appropriate

## Dependency Rule

Dependencies must point toward the domain.

The domain must not depend on infrastructure technologies.

## Layers

### Domain

Contains:

- entities
- value objects
- domain services
- domain exceptions
- business rules

### Application

Contains:

- use cases
- input ports
- output ports
- application DTOs

### Adapters

Contains:

- REST controllers
- persistence adapters
- external integrations

### Infrastructure

Contains:

- Spring configuration
- security configuration
- observability configuration
- technical configuration

## Expected Flow

REST Controller

↓

Input Port

↓

Application Use Case

↓

Domain

↓

Output Port

↓

Persistence Adapter

↓

PostgreSQL

## Persistence

PostgreSQL is the initial relational database.

JPA/Hibernate must remain outside the domain layer.

Persistence entities must not be exposed through REST.

## API

The external API uses versioned endpoints:

/api/v1/...

## Resilience

The service should use:

- timeouts
- bounded retries
- backoff
- circuit breakers where justified
- idempotency

## Observability

The service must expose:

- health
- metrics
- structured logs
- tracing support

## Vehicle Safety

The service is read-only with respect to vehicle control.

It must not provide commands that manipulate safety-critical
vehicle systems.
vehicle systems.