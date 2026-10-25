# Beginner-to-Advanced Roadmap

This roadmap is a suggested sequence, not a claim that every feature is already implemented. Complete each phase with code, tests, and a short explanation.

## Phase 1 — Foundations

Learn HTTP methods, status codes, headers, JSON, REST naming, Java fundamentals, Maven lifecycle, Spring Boot auto-configuration, dependency injection, configuration properties, profiles, logging, and validation.

**Deliverable:** a small Product API with CRUD operations and tests.

## Phase 2 — A production-shaped first service

Learn controller/service/repository layering, request and response DTOs, Bean Validation, global exception handling, Spring Data JPA, PostgreSQL migrations, and integration tests.

**Deliverable:** Product Service with persistence, documented endpoints, and automated tests.

## Phase 3 — Service boundaries and synchronous communication

Learn service ownership, avoiding shared database tables, HTTP clients, DTO compatibility, timeouts, error mapping, API contracts, versioning, correlation IDs, and tracing.

**Deliverable:** Order Service communicates with Product/Inventory APIs with explicit timeout and failure behavior.

## Phase 4 — Gateway, configuration, and discovery

Learn gateway routing and filters, externalized configuration, environment-specific settings, service discovery where useful, and health/readiness endpoints.

**Deliverable:** one local entry point routes requests to services.

## Phase 5 — Resilience and reliability

Learn timeouts, bounded retries with backoff, circuit breakers, bulkheads, rate limits, fallbacks, idempotency keys, graceful degradation, and failure-mode testing.

**Deliverable:** documented behavior when a downstream service is slow or unavailable.

## Phase 6 — Asynchronous messaging

Learn events versus commands, queues, acknowledgements, retries, dead-letter queues, at-least-once delivery, idempotent consumers, event schema evolution, transactional outbox, and eventual consistency.

**Deliverable:** an `OrderCreated` event triggers a tested asynchronous workflow.

## Phase 7 — Security

Learn authentication versus authorization, Spring Security, OAuth 2.0 / OpenID Connect, JWT validation, role/scope checks, service credentials, secrets management, least privilege, and browser security considerations.

**Deliverable:** protected endpoints with a documented local testing strategy.

## Phase 8 — Testing strategy

Learn JUnit 5 and Mockito unit tests, Spring Boot slice tests, Testcontainers integration tests, contract testing, end-to-end smoke tests, and test data management.

**Deliverable:** repeatable test commands and CI checks.

## Phase 9 — Operations and delivery

Learn Docker images, multi-stage builds, Docker Compose, Actuator, Micrometer, structured logs, tracing, health checks, resource limits, environment-based configuration, and GitHub Actions.

**Deliverable:** reproducible local setup and automated build/test pipeline.

## Phase 10 — Advanced architecture

Learn saga orchestration/choreography, compensating actions, outbox/inbox patterns, caching and invalidation, API compatibility/deprecation, data ownership, eventual consistency, operational cost, and when *not* to use microservices.

**Deliverable:** one architecture decision record (ADR) that explains a trade-off and a tested workflow.

## Definition of done for each milestone

- Feature works locally.
- Success and failure cases are tested.
- Configuration and commands are documented.
- Logs and errors are useful without exposing secrets.
- Known limitations and trade-offs are recorded.
