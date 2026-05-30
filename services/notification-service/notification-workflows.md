# Notification Workflows

## Example Workflow

1. Domain event published
2. Notification consumer processes event
3. Template generated
4. Provider delivery attempted
5. Retry workflow triggered if necessary

---

# Delivery Channels

Potential delivery channels include:

* email
* SMS
* push notifications
* webhooks

---

# Design Goals

The workflow prioritizes:

* asynchronous execution
* delivery resilience
* provider abstraction