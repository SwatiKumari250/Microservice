# Planned Architecture

## Status

This document describes the intended learning architecture for ShopFlow. It is a design target, not proof that the components already exist in code.

## Context

ShopFlow is a small e-commerce example used to learn service boundaries, HTTP communication, asynchronous events, reliability, and deployment. Begin with the fewest services necessary; add infrastructure only when it teaches a concrete lesson.

## Proposed components

| Component | Responsibility | Data ownership |
| --- | --- | --- |
| Product Service | Product catalogue and product details | Product data |
| Inventory Service | Stock availability and stock changes | Inventory data |
| Order Service | Order creation and lifecycle | Order data |
| API Gateway | Routes client requests and applies edge policies | No business data |
| Discovery (optional) | Locates service instances in supported deployments | Service registry |
| Message broker (later) | Delivers domain events asynchronously | Queues/messages, not business tables |

## High-level request flow

1. A client sends an order request to the gateway.
2. The gateway routes it to Order Service.
3. Order Service validates the request and checks required product/inventory information.
4. The order workflow records state and handles downstream failures explicitly.
5. In the asynchronous phase, an order event is published and consumers react idempotently.
6. Logs, metrics, health checks, and traces help explain requests across service boundaries.

Exact behavior must be decided and tested during implementation. A production design must not assume that a workflow across services is one atomic database transaction.

## Boundary rules

- Each service owns its schema and persistence.
- Other services use APIs or events, not another service's database tables.
- Share contracts sparingly; avoid a large shared library that forces every service to deploy together.
- Keep the gateway focused on edge concerns rather than business rules.
- Use events to communicate facts that have happened; document event ownership and schema changes.
- Make consumers safe against duplicate delivery.
- Set explicit timeouts for every remote call and define behavior when a dependency is unavailable.

## Data consistency

A local database transaction protects changes inside one service. It does not make a workflow across multiple services atomic. Later milestones should explore eventual consistency, idempotency, transactional outbox, and saga compensation.

## Resilience

For every remote dependency, define an explicit timeout, retryable errors (if retries are appropriate), bounded retry policy with backoff, circuit breaker/bulkhead where justified, and observable failure behavior. Retries must not duplicate non-idempotent business actions.

## Security

- Keep secrets out of source control.
- Validate authentication and authorization at appropriate boundaries.
- Do not trust client-supplied identity headers unless a trusted gateway strips and sets them correctly.
- Use TLS and managed secrets in deployed environments.
- Avoid logging tokens or sensitive request data.

## Architecture decisions

Record significant choices in small ADR files under `docs/adr/` using this template:

- **Title**
- **Status:** proposed / accepted / superseded
- **Context**
- **Decision**
- **Consequences**
- **Alternatives considered**
