# Event Contracts

This document defines high-level domain event structures.

---

# Example Event

```json id="5gntgn"
{
  "eventType": "TRANSACTION_CREATED",
  "eventId": "uuid",
  "timestamp": "ISO_DATE",
  "payload": {
    "transactionId": "uuid",
    "walletId": "uuid",
    "amount": 1000
  }
}
```

---

# Event Philosophy

Events represent immutable domain milestones.

---

# Design Goals

The event architecture prioritizes:

* replay safety
* schema consistency
* asynchronous coordination
* operational traceability
