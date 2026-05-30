# Wallet API

This document describes high-level wallet management endpoints.

---

# Create Wallet

```http id="sh5yhd"
POST /api/v1/wallets
```

Creates a new wallet.

---

## Request Example

```json id="h8x65u"
{
  "userId": "uuid",
  "currency": "USD"
}
```

---

## Response Example

```json id="3em7b8"
{
  "walletId": "uuid",
  "status": "ACTIVE"
}
```

---

# Get Wallet

```http id="3z2b77"
GET /api/v1/wallets/{walletId}
```

Retrieves wallet information.

---

# Freeze Wallet

```http id="8g5msf"
POST /api/v1/wallets/{walletId}/freeze
```

Temporarily disables wallet activity.

---

# Design Goals

The wallet API prioritizes:

* explicit state transitions
* auditability
* operational traceability
