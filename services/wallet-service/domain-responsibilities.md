# Domain Responsibilities

The Wallet Service owns:

* wallet lifecycle management
* wallet validation rules
* wallet state enforcement
* wallet status transitions

---

# Example Rules

Examples include:

* frozen wallets cannot transact
* closed wallets cannot reactivate
* verification may be required before activation

---

# Service Boundaries

The Wallet Service should not:

* orchestrate transactions
* manage notifications
* perform reconciliation workflows