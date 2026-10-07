# AutoMind - Engineering Guidelines

## Project

AutoMind is a vehicle intelligence platform composed of independent
microservices, a React Native mobile application and an Angular web
application.

The backend follows:

- Microservices Architecture
- Clean Architecture
- Hexagonal Architecture
- Domain-Driven Design where appropriate
- SOLID principles
- Secure-by-design principles
- API-first development
- Automated testing
- Observability
- Resilience

## General Rules

1. Prefer simple, maintainable and scalable solutions.
2. Do not introduce unnecessary complexity.
3. Do not introduce a technology only because it is popular.
4. Every architectural decision must have a reason.
5. Follow SOLID principles.
6. Prefer composition over inheritance.
7. Use dependency inversion.
8. Use constructor injection.
9. Never use field injection.
10. Never hardcode secrets or credentials.
11. Never expose persistence entities through REST APIs.
12. Use DTOs for external contracts.
13. Validate all external input.
14. Business rules must not live inside controllers.
15. Controllers must remain thin.
16. Use centralized exception handling.
17. Do not expose stack traces to clients.
18. Use structured logging.
19. Do not log secrets or sensitive information.
20. Write automated tests for business logic.
21. Prefer immutable objects where practical.
22. Keep classes and methods focused on one responsibility.
23. Avoid premature abstractions.
24. Avoid unnecessary frameworks and dependencies.

## Architecture Rules

The domain layer must not depend on:

- Spring
- Spring Boot
- JPA
- Hibernate
- PostgreSQL
- REST
- HTTP
- RabbitMQ
- Kafka
- Docker
- Infrastructure implementations

The dependency direction must point toward the domain.

Expected flow:

Adapter -> Application -> Domain

Infrastructure adapters implement application/domain ports.

## REST

REST controllers:

- receive HTTP requests
- validate input
- map DTOs
- invoke application use cases
- map responses

Controllers must not contain business logic.

## Persistence

Persistence implementations belong to infrastructure/adapter layers.

Domain models must not contain persistence annotations.

Do not expose JPA entities through REST.

## Security

Security must follow defense-in-depth principles.

Never:

- hardcode credentials
- commit secrets
- expose tokens in logs
- trust internal requests automatically

All external input must be validated.

## Resilience

Use resilience patterns when justified:

- timeouts
- limited retries
- exponential backoff
- circuit breakers
- idempotency
- graceful degradation

Do not use infinite retries.

## Testing

Every use case must have automated tests.

Prefer:

- JUnit 5
- Mockito
- Spring Boot Test
- Testcontainers

Tests should verify behavior rather than implementation details.

## Observability

Services should provide:

- health checks
- metrics
- structured logs
- distributed tracing readiness

## Git

Commits should be small and meaningful.

Use conventional commit style when practical:

feat:
fix:
refactor:
test:
docs:
build:
ci:
chore:

## Important

Do not invent requirements.

When requirements are ambiguous, consult the project specifications
under /docs before implementing.

The documentation is the source of truth for the implementation.