# Health Checks

Health endpoints improve:

* orchestration visibility
* deployment safety
* operational monitoring

---

# Liveness Endpoint

```http id="q9q0jo"
GET /health/live
```

Verifies service process availability.

---

# Readiness Endpoint

```http id="ypjlwm"
GET /health/ready
```

Verifies dependency readiness.

Checks may include:

* PostgreSQL connectivity
* RabbitMQ connectivity
* Redis connectivity

---

# Health Philosophy

Health checks should remain:

* lightweight
* deterministic
* operationally meaningful
