# Architecture Decisions

## Overview

This document captures major architectural decisions made within the Wallet-as-a-Service platform and the reasoning behind those decisions.

The goal is not only to document what was chosen, but also why specific tradeoffs were accepted.

---

# Decision 1 — Event-Driven Architecture

## Decision

The platform uses an event-driven architecture with RabbitMQ as the asynchronous message broker.

---

## Reasoning

Financial systems frequently involve:

* asynchronous workflows
* retries
* external provider dependencies
* delayed processing
* operational spikes

An event-driven approach improves:

* service decoupling
* scalability
* fault isolation
* operational flexibility

---

## Tradeoffs

Accepted tradeoffs include:

* increased infrastructure complexity
* eventual consistency
* distributed debugging complexity

These tradeoffs are accepted in exchange for scalability and resilience.

---

# Decision 2 — Ledger-Based Wallet Model

## Decision

Wallet balances are derived from transaction ledgers rather than relying solely on mutable balance columns.

---

## Reasoning

Ledger-driven financial systems improve:

* auditability
* reconciliation
* replayability
* financial correctness
* dispute investigation

---

## Tradeoffs

Tradeoffs include:

* increased query complexity
* more storage usage
* additional reconciliation logic

These are accepted because financial correctness is prioritized over implementation simplicity.

---

# Decision 3 — RabbitMQ Over Synchronous Service Calls

## Decision

Critical workflows use asynchronous messaging wherever possible.

---

## Reasoning

Direct synchronous service dependencies create:

* tight coupling
* cascading failures
* reduced resilience
* scalability bottlenecks

RabbitMQ improves:

* workload buffering
* service independence
* retry management
* operational isolation

---

# Decision 4 — Redis As Performance Layer

## Decision

Redis is used strictly as a performance optimization layer rather than a source of truth.

---

## Reasoning

Redis improves:

* response times
* idempotency lookups
* distributed coordination
* temporary state access

However:

* Redis failures should not compromise financial correctness.

---

# Decision 5 — Stateless Services

## Decision

Application services remain stateless whenever possible.

---

## Reasoning

Stateless services support:

* horizontal scaling
* easier deployment
* container orchestration
* fault recovery

---

# Decision 6 — Eventual Consistency

## Decision

The system accepts eventual consistency between distributed services.

---

## Reasoning

Strong synchronous consistency across all services would:

* reduce scalability
* increase coupling
* reduce fault tolerance

Eventual consistency provides better distributed scalability characteristics.

---

# Decision 7 — At-Least-Once Delivery

## Decision

The messaging architecture assumes at-least-once event delivery semantics.

---

## Reasoning

Exactly-once delivery introduces significant distributed systems complexity and operational overhead.

Instead:

* consumers are designed to be idempotent
* retries are considered normal
* duplicate handling is built into workflows

---

# Decision 8 — API Gateway Pattern

## Decision

All external traffic enters through a centralized API Gateway.

---

## Responsibilities

The API Gateway handles:

* authentication
* routing
* request validation
* rate limiting
* request tracing

---

# Decision 9 — Service Isolation

## Decision

Services are separated according to business responsibilities.

---

## Reasoning

Service isolation improves:

* maintainability
* deployment independence
* scalability
* fault isolation

Examples:

* notification workloads should not affect transaction processing
* analytics should not block financial operations

---

# Decision 10 — Dockerized Infrastructure

## Decision

All services are containerized using Docker.

---

## Reasoning

Containerization improves:

* deployment consistency
* local development
* scalability
* infrastructure portability
* CI/CD automation

---

# Architectural Philosophy

The platform prioritizes:

* reliability over convenience
* auditability over simplicity
* scalability over tight coupling
* resilience over synchronous immediacy

These principles guide future architectural evolution.
