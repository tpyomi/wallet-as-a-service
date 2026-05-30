# Webhook Example

## Example Webhook Payload

```json id="tgwwji"
{
  "eventType": "TRANSACTION_COMPLETED",
  "transactionId": "txn_123",
  "status": "COMPLETED"
}
```

---

# Retry Behavior

Webhook delivery supports:

* retries
* exponential backoff
* replay handling

---

# Security Measures

Recommended protections:

* request signing
* timestamp validation
* replay protection
