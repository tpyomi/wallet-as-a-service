# Dead Letter Recovery Example

## Example Failure

1. Consumer repeatedly fails processing
2. Retry threshold exceeded
3. Message routed to dead-letter queue

---

# Recovery Workflow

Operators may:

* inspect payload
* replay message
* correct malformed data
* trigger reconciliation

---

# Architectural Goals

The DLQ architecture prioritizes:

* operational recovery
* failure isolation
* replay-safe correction
