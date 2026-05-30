# Event-Driven Architecture

## Overview

The Wallet-as-a-Service platform is designed using an event-driven microservices architecture to ensure scalability, loose coupling, reliability, and asynchronous processing across services. The main reason for this desicion is to be able to build a single service that can be easily integrateed into any wallet based system.

Instead of relying heavily on direct synchronous communication between services, domain events are published through a message broker (RabbitMQ) and consumed asynchronously by interested services.

This architecture allows services to evolve independently while supporting high-throughput financial workflows and resilient distributed processing.

---

# Architectural Goals

The event-driven design prioritizes:

* loose coupling between services
* horizontal scalability
* asynchronous workflow processing
* operational resilience
* fault isolation
* eventual consistency
* extensibility for future integrations
* auditability of transaction workflows

---

# Core Components

## API Gateway

Acts as the primary entry point into the system.

Responsibilities:

* authentication
* request validation
* routing
* rate limiting
* aggregation
* request tracing

The gateway does not contain business logic.

---

## Wallet Service

Responsible for:

* wallet lifecycle management
* balance orchestration
* wallet state validation
* wallet-level business rules

Publishes events such as:

* WALLET_CREATED
* WALLET_FUNDED
* WALLET_DEBITED
* WALLET_FROZEN

---

## Transaction Service

Responsible for:

* transaction processing
* transaction persistence
* transaction ledger management
* transaction reconciliation
* transaction validation

Consumes and publishes transaction-related events.

---

## Notification Service

Consumes events asynchronously to send:

* email notifications
* SMS notifications
* push notifications

This service is intentionally decoupled from transactional flows to avoid blocking financial operations.

---

## RabbitMQ

Acts as the distributed event broker.

Responsibilities:

* asynchronous communication
* retry handling
* decoupling services
* buffering spikes in traffic
* supporting eventual consistency

---

## Redis

Used for:

* caching
* rate limiting
* distributed locking
* temporary state management
* idempotency key tracking

---

## PostgreSQL

Acts as the primary source of truth for:

* wallets
* transactions
* ledger entries
* audit records

---

# Event Flow Philosophy

The system treats events as facts representing completed domain actions.

Examples:

* TRANSACTION_CREATED
* WALLET_FUNDED
* WALLET_DEBITED
* TRANSACTION_FAILED

Events are immutable and represent historical system activity.

---

# Example Transaction Flow

1. Client initiates wallet funding request.
2. API Gateway validates request and forwards it.
3. Wallet Service validates wallet state.
4. Transaction Service creates transaction record.
5. TRANSACTION_CREATED event is published.
6. Payment processor confirms settlement.
7. WALLET_FUNDED event is emitted.
8. Wallet balance projection updates.
9. Notification Service sends confirmation asynchronously.

---

# Benefits of Event-Driven Architecture

## Loose Coupling

Services communicate through events rather than direct dependencies.

This reduces tight coupling and improves maintainability.

---

## Scalability

Consumers scale independently depending on workload characteristics.

For example:

* Notification Service may require higher horizontal scaling than Wallet Service.

---

## Fault Isolation

If Notification Service fails:

* wallet operations continue functioning normally.

---

## Asynchronous Processing

Long-running operations do not block client requests.

---

## Extensibility

New consumers can subscribe to events without modifying existing producers.

Example:

* analytics service
* fraud detection service
* audit service

---

# Eventual Consistency

The architecture accepts eventual consistency as a deliberate tradeoff for scalability and service independence.

Temporary state divergence between services is expected and managed through:

* retries
* reconciliation
* idempotent processing
* event replay strategies

---

# Event Delivery Guarantees

The system primarily operates using at-least-once delivery semantics.

This means:

* duplicate events are possible
* consumers must be idempotent

Exactly-once delivery is avoided due to distributed systems complexity and operational overhead.

---

# Design Tradeoffs

## Chosen Tradeoff: Async Processing Over Immediate Consistency

The system prioritizes:

* resilience
* throughput
* decoupling

over strict synchronous consistency across services.

---

## Chosen Tradeoff: Operational Complexity For Scalability

Event-driven systems introduce:

* more infrastructure
* distributed debugging complexity
* eventual consistency concerns

However, these tradeoffs are accepted for:

* scalability
* reliability
* long-term system evolution
