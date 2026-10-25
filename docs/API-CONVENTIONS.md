# REST API Conventions

Apply these conventions consistently as services are implemented. These are project guidelines, not endpoints that already exist.

## Resource naming

- Use plural nouns for collections: `/api/v1/products`, `/api/v1/orders`.
- Use an identifier for an individual resource: `/api/v1/products/{productId}`.
- Use HTTP methods according to their semantics: GET to read, POST to create/action, PUT to replace, PATCH to partially update, DELETE to remove.
- Version public APIs deliberately and document compatibility expectations.

## Status codes

- `200 OK` — successful request with a response body.
- `201 Created` — resource created; include a Location header when appropriate.
- `204 No Content` — success without a response body.
- `400 Bad Request` — malformed request or validation failure.
- `401 Unauthorized` — authentication is missing or invalid.
- `403 Forbidden` — caller is authenticated but not permitted.
- `404 Not Found` — resource does not exist.
- `409 Conflict` — request conflicts with current resource state.
- `422 Unprocessable Content` — optional convention for semantic validation failures.
- `429 Too Many Requests` — rate limit exceeded.
- `500 Internal Server Error` — unexpected server failure.
- `503 Service Unavailable` — service temporarily cannot handle the request.

Choose one consistent policy for validation errors and document it.

## Example error response

```json
{
  "timestamp": "2026-01-01T12:00:00Z",
  "status": 400,
  "code": "VALIDATION_FAILED",
  "message": "Request validation failed",
  "path": "/api/v1/products",
  "traceId": "example-trace-id",
  "fieldErrors": [
    { "field": "name", "message": "must not be blank" }
  ]
}
```

This is an example contract. Implement it with global exception handling; never expose stack traces or secrets to clients.

## Validation and compatibility

- Validate request DTOs at the service boundary.
- Return DTOs instead of exposing persistence entities directly.
- Document required/optional fields, formats, limits, and error responses.
- Keep changes backward-compatible where possible.
- Document pagination, sorting, and filtering.
- Use OpenAPI when endpoints are implemented.

## Reliability

- Set a timeout for every outbound HTTP call.
- Use idempotency keys for operations where clients may retry after an uncertain response.
- Do not automatically retry every 4xx response or every non-idempotent POST.
- Include a correlation/trace ID in logs and errors when available.
