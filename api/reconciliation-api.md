# Reconciliation API

The reconciliation APIs support:

* consistency validation
* replay workflows
* operational recovery
* financial integrity checks

---

# Trigger Reconciliation

```http id="kvzj91"
POST /api/v1/reconciliation/run
```

Triggers reconciliation processing.

---

# Get Reconciliation Status

```http id="9f97x0"
GET /api/v1/reconciliation/{jobId}
```

Retrieves reconciliation status.

---

# Recovery Philosophy

Reconciliation workflows are considered:

* operationally critical
* replay-safe
* idempotent

---

# Architectural Goals

The reconciliation architecture prioritizes:

* financial correctness
* operational recoverability
* distributed consistency validation
