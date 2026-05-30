# Gateway Responsibilities

The API Gateway handles infrastructure-level concerns before traffic reaches backend services.

---

# Core Responsibilities

## Authentication

Validates:

* JWT access tokens
* API keys
* session integrity

---

## Authorization

Enforces:

* scopes
* permissions
* role policies

---

## Rate Limiting

Protects backend infrastructure from:

* abuse
* accidental overload
* denial-of-service scenarios

---

## Request Tracing

Generates and propagates:

* correlation identifiers
* distributed tracing metadata

---

## Request Validation

Performs:

* schema validation
* protocol normalization
* payload size enforcement
