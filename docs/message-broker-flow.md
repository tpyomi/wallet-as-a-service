# Message Broker Flow

## Overview

RabbitMQ acts as the asynchronous communication backbone of the Wallet-as-a-Service platform.

The message broker enables:

* service decoupling
* asynchronous workflows
* retry handling
* workload buffering
* event-driven scalability

---

# Messaging Philosophy

The platform assumes:

* services should evolve independently
* retries are normal
* temporary failures occur
* asynchronous workflows improve resilience

---

# Core Messaging Components

## Exchanges

Responsible for routing messages to queues.

---

## Queues

Store messages for asynchronous processing.

---

## Consumers

Services that subscribe to and process events.

---

# Example Event Flow

## Wallet Funding Workflow

1. Transaction Service publishes TRANSACTION_CREATED event.
2. Payment processor consumes event.
3. Settlement completes.
4. WALLET_FUNDED event emitted.
5. Notification Service consumes event.

---

# Retry Flow

Transient failures trigger:

* retries
* delayed reprocessing
* dead-letter routing if necessary

---

# Dead Letter Queues

Messages that repeatedly fail move into DLQs.

Benefits:

* operational visibility
* poison message isolation
* replay support

---

# Message Durability

Queues are configured as durable.

Messages use persistent delivery modes to reduce data loss risk.

---

# Delivery Guarantees

The platform operates using:

* at-least-once delivery semantics

This means:

* duplicate delivery is possible
* consumers must be idempotent

---

# Correlation IDs

Messages include correlation identifiers for:

* distributed tracing
* debugging
* operational observability

---

# Event Naming

Events use explicit domain-driven naming conventions.

Examples:

* WALLET_CREATED
* TRANSACTION_CREATED
* WALLET_FUNDED
* TRANSACTION_FAILED

---

# Consumer Design Principles

Consumers should:

* remain idempotent
* fail safely
* retry predictably
* avoid blocking operations

---

# Queue Isolation

Different workloads use isolated queues.

Examples:

* notifications
* reconciliation
* analytics
* transaction processing

This prevents unrelated workloads from competing excessively for resources.

---

# Messaging Tradeoffs

The architecture intentionally accepts:

* asynchronous complexity
* eventual consistency
* operational coordination overhead

in exchange for:

* scalability
* resilience
* service decoupling
* fault isolation
