# Wallet Creation Flow

## Overview

This workflow demonstrates asynchronous wallet creation within the distributed platform.

---

# Step 1 — Client Request

```http id="8d4d8k"
POST /api/v1/wallets
```

---

## Request Payload

```json id="b2j6dy"
{
  "userId": "user_123",
  "currency": "USD"
}
```

---

# Step 2 — Gateway Validation

The API Gateway validates:

* authentication
* authorization
* request schema
* rate limits

---

# Step 3 — Wallet Service Processing

The Wallet Service:

* validates business rules
* creates wallet records
* initializes wallet state

---

# Step 4 — Event Publication

The service publishes:

```txt id="v6v44z"
WALLET_CREATED
```

---

# Step 5 — Downstream Consumers

Other services may asynchronously:

* send notifications
* initialize audit workflows
* create analytics records

---

# Architectural Characteristics

This workflow demonstrates:

* asynchronous coordination
* service decoupling
* replay-safe event publishing
