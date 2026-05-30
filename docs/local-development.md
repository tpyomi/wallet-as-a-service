# Local Development Guide

## Overview

This document describes recommended workflows for local development within the Wallet-as-a-Service platform.

Because the platform uses distributed asynchronous services, local development prioritizes:

* isolated service testing
* event visibility
* reproducibility
* debugging simplicity

---

# Development Philosophy

The platform encourages:

* service isolation
* modular development
* reproducible environments
* incremental feature development

Each service should remain independently runnable wherever possible.

---

# Recommended Workflow

## Step 1 — Start Infrastructure

```bash
docker-compose up -d
```

Infrastructure includes:

* PostgreSQL
* Redis
* RabbitMQ

---

## Step 2 — Start Services Individually

Example:

```bash
cd services/wallet-service

npm run dev
```

This allows focused debugging and faster iteration.

---

# Event Visibility

RabbitMQ Management UI is used to:

* inspect queues
* inspect exchanges
* debug event routing
* monitor retries
* inspect dead-letter queues

---

# Database Inspection

Recommended tools:

* TablePlus
* DBeaver
* pgAdmin

Useful for:

* transaction inspection
* reconciliation debugging
* event correlation analysis

---

# Logging Strategy

Local development uses structured logs for:

* request tracing
* event correlation
* debugging asynchronous workflows

Logs should include:

* request IDs
* correlation IDs
* transaction references
* event names

---

# Hot Reloading

Services use development reload tooling for faster iteration.

Example:

* nodemon
* ts-node-dev

---

# Recommended Development Order

Suggested implementation order:

1. API Gateway
2. Wallet Service
3. Transaction Service
4. RabbitMQ Integration
5. Redis Integration
6. Notification Service
7. Reconciliation Workflows

---

# Local Development Challenges

Distributed systems introduce:

* asynchronous debugging complexity
* event ordering concerns
* retry visibility challenges
* eventual consistency behavior

The platform intentionally embraces these realities during development.

---

# Testing Philosophy

Developers should validate:

* retries
* duplicate events
* partial failures
* queue backlogs
* consumer crashes
* delayed processing

These scenarios are normal in production distributed systems.

---

# Local Development Goals

The local environment exists to simulate:

* production-like workflows
* distributed coordination
* async processing behavior
* infrastructure interactions
