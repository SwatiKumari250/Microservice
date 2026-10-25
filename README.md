# Microservices with Java & Spring Boot

A hands-on, beginner-to-advanced learning project for understanding how to design, build, test, secure, and run **microservices with Java and Spring Boot**.

> **Project status:** Initial documentation scaffold. The architecture and milestones below describe the planned implementation; this repository is not yet a runnable microservices application.

## Goals

- Understand when a monolith is sufficient and when microservices are justified.
- Build independently testable Spring Boot services with clear responsibilities.
- Practice REST APIs, service communication, gateways, and service discovery.
- Learn persistence, messaging, reliability, security, and distributed data consistency.
- Add automated tests, observability, Docker, and CI as the project evolves.
- Document design decisions and trade-offs instead of treating microservices as a checklist.

## Planned technology stack

| Area | Technology |
| --- | --- |
| Language | Java 21 |
| Framework | Spring Boot 3.x |
| Build | Maven |
| API | REST, JSON, OpenAPI |
| Persistence | Spring Data JPA, PostgreSQL |
| Gateway / discovery | Spring Cloud Gateway; Eureka where appropriate |
| Messaging | RabbitMQ in a later phase |
| Resilience | Resilience4j |
| Security | Spring Security, OAuth 2.0 / JWT concepts |
| Testing | JUnit 5, Mockito, Spring Boot Test, Testcontainers |
| Delivery | Docker, Docker Compose, GitHub Actions |
| Observability | Actuator, Micrometer, structured logs, tracing concepts |

Versions will be pinned and checked for compatibility when implementation begins. Not every technology listed above is configured yet.

## Learning project: ShopFlow

The planned example is a small e-commerce platform designed to teach service boundaries and communication patterns.

- **Product Service** — product catalogue and product details.
- **Inventory Service** — stock availability and inventory changes.
- **Order Service** — order creation and order status.
- **API Gateway** — a single entry point for client traffic.
- **Service Discovery** — optional registration and lookup for deployments that need it.
- **Messaging** — later, publish events such as `OrderCreated` and consume them asynchronously.
- **Shared infrastructure** — databases, broker, health checks, metrics, and local development configuration.

Each service should own its data and expose a small documented API. Avoid sharing database tables across services.

## Repository structure

```text
Microservice/
├── README.md
├── .gitignore
├── CONTRIBUTING.md
└── docs/
    ├── ARCHITECTURE.md
    ├── API-CONVENTIONS.md
    └── ROADMAP.md
```

This documentation structure will expand as service code, tests, Docker configuration, and CI workflows are added.

## Learning roadmap

1. **Foundations** — HTTP, REST, JSON, Java, Maven, Spring Boot, configuration, and logging.
2. **First service** — implement Product Service with validation, error handling, persistence, and tests.
3. **Synchronous communication** — connect services with explicit timeouts and documented failure behavior.
4. **Gateway and discovery** — route external traffic and explore service registration.
5. **Data and consistency** — database-per-service, idempotency, eventual consistency, and local transactions.
6. **Messaging** — events, retries, dead-letter queues, and the transactional outbox pattern.
7. **Resilience** — timeouts, bounded retries, circuit breakers, bulkheads, and graceful degradation.
8. **Security** — authentication, authorization, secrets, and service-to-service trust.
9. **Testing** — unit, integration, contract, and end-to-end tests.
10. **Operations** — Docker Compose, health probes, metrics, logs, traces, and CI.
11. **Advanced design** — saga workflows, API versioning, caching, and architecture trade-offs.

See [docs/ROADMAP.md](docs/ROADMAP.md) for the full plan.

## Getting started

At the documentation-scaffold stage, there may not be a runnable service. Review the architecture and roadmap, then implement one milestone at a time.

When code is added, each module should document its prerequisites and commands. The intended local workflow is:

1. Install a compatible JDK and Maven.
2. Clone the repository.
3. Configure local environment variables; never commit credentials.
4. Start required dependencies using the documented Docker Compose setup.
5. Run the available tests before starting a service.
6. Check its health endpoint and API documentation.

## Engineering principles

- Start small; split services only when boundaries justify the complexity.
- Keep controllers thin and business logic testable.
- Validate input and return consistent error responses.
- Set explicit network timeouts and do not blindly retry failures.
- Design event consumers to tolerate duplicate delivery.
- Keep secrets out of source control.
- Add tests and observability alongside features.
- Document known limitations and design decisions.

## Contributing

Choose a focused milestone from the roadmap, create a branch, implement the smallest useful change, add tests, update documentation, and open a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Official learning resources

- [Spring Boot](https://spring.io/projects/spring-boot)
- [Spring Cloud](https://spring.io/projects/spring-cloud)
- [Spring Guides](https://spring.io/guides)
- [Apache Maven](https://maven.apache.org/guides/)
- [Docker documentation](https://docs.docker.com/)
- [JUnit 5](https://junit.org/junit5/)
- [Testcontainers](https://testcontainers.com/)

## License

No license has been selected yet. Add a license file after deciding how others may use, modify, and distribute the project.
