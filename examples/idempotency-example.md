# Idempotency Example

## Example Request

```http id="9w1pgx"
POST /api/v1/transactions/fund
```

---

## Headers

```http id="6tm00l"
Idempotency-Key: abc-123
```

---

# Retry Scenario

A client retries the same request due to network timeout.

The platform:

* detects duplicate idempotency key
* returns previous result
* prevents duplicate transaction creation

---

# Design Goals

The idempotency workflow prioritizes:

* financial safety
* deterministic outcomes
* replay-safe behavior
