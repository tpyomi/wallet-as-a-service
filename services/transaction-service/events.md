# Transaction Events

Example transaction events include:

* TRANSACTION_CREATED
* TRANSACTION_COMPLETED
* TRANSACTION_FAILED
* TRANSACTION_REVERSED
* TRANSACTION_EXPIRED

---

# Event Philosophy

Transaction events represent immutable financial milestones.

Events should remain:

* replay-safe
* traceable
* schema-versioned
* asynchronously consumable

---

# Design Goals

Transaction events improve:

* asynchronous coordination
* operational visibility
* distributed recoverability