# Webhook Design

Webhook support enables external systems to receive asynchronous notifications.

Examples:

* payment confirmations
* wallet funding updates
* reconciliation results

---

# Retry Philosophy

Webhook delivery should support:

* retries
* exponential backoff
* dead-letter workflows

---

# Security

Recommended protections:

* webhook signing
* timestamp validation
* replay protection
