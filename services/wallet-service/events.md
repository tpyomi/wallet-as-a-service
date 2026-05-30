# Wallet Events

Example wallet events include:

* WALLET_CREATED
* WALLET_ACTIVATED
* WALLET_FROZEN
* WALLET_CLOSED
* WALLET_LIMIT_UPDATED

---

# Event Philosophy

Wallet events represent immutable domain milestones.

Events should remain:

* replay-safe
* immutable
* traceable
* schema-versioned

---

# Design Goals

Wallet events improve:

* asynchronous coordination
* service decoupling
* operational visibility