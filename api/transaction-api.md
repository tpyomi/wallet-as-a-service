# Transaction API

This document describes transaction-related workflows.

---

# Fund Wallet

```http id="4otup8"
POST /api/v1/transactions/fund
```

Creates a wallet funding transaction.

---

## Request Example

```json id="v1l6rt"
{
  "walletId": "uuid",
  "amount": 1000,
  "currency": "USD"
}
```

---

## Response Example

```json id="cc8o6l"
{
  "transactionId": "uuid",
  "status": "PENDING"
}
```

---

# Debit Wallet

```http id="69whko"
POST /api/v1/transactions/debit
```

Creates a debit transaction.

---

# Get Transaction

```http id="j5e0yv"
GET /api/v1/transactions/{transactionId}
```

Returns transaction state and metadata.

---

# Transaction States

Possible states:

* PENDING
* PROCESSING
* COMPLETED
* FAILED
* REVERSED

---

# Design Goals

The transaction API prioritizes:

* replay safety
* immutable transaction history
* auditability
* eventual consistency support
