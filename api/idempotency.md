# Idempotency Strategy

Financial operations must remain safe under retries and duplicate requests.

The platform therefore uses explicit idempotency keys.

---

# Request Pattern

Clients provide:

```http id="o9v2r9"
Idempotency-Key: uuid
```

---

# Replay Safety

Idempotency protects against:

* duplicate submissions
* network retries
* delayed responses
* event replay scenarios

---

# Persistence Strategy

Idempotency metadata should remain durable and queryable.

Possible storage strategies:

* PostgreSQL
* Redis
* dedicated idempotency tables

---

# Design Goals

The idempotency strategy prioritizes:

* financial correctness
* deterministic outcomes
* replay-safe processing
