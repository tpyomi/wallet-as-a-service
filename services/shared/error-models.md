# Error Models

The platform uses structured error responses across services.

---

# Recommended Metadata

Error responses may include:

* correlationId
* errorCode
* timestamp
* retryable flag

---

# Design Goals

Structured error models improve:

* debugging
* operational diagnostics
* distributed tracing