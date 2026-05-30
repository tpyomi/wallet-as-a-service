# Setup Guide

## Overview

This document explains how to set up the Wallet-as-a-Service platform locally for development and testing purposes.

The platform is designed using containerized microservices architecture with Docker Compose orchestration.

---

# Prerequisites

The following tools must be installed:

* Docker
* Docker Compose
* Node.js
* Git

Optional:

* Postman
* TablePlus / DBeaver
* RabbitMQ Management UI

---

# Repository Structure

```txt
wallet-as-a-service/
├── services/
├── architecture/
├── docs/
├── diagrams/
├── docker/
├── api/
└── examples/
```

---

# Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/wallet-as-a-service.git

cd wallet-as-a-service
```

---

# Install Dependencies

Each service manages its own dependencies.

Example:

```bash
cd services/wallet-service

npm install
```

Repeat for all services.

---

# Environment Variables

Copy example environment files:

```bash
cp .env.example .env
```

Update values as needed.

---

# Start Infrastructure

From project root:

```bash
docker-compose up -d
```

This starts:

* PostgreSQL
* Redis
* RabbitMQ
* supporting infrastructure

---

# Start Services

Example:

```bash
cd services/wallet-service

npm run dev
```

Repeat for all services.

---

# Verify Infrastructure

RabbitMQ Management UI:

```txt
http://localhost:15672
```

PostgreSQL:

* localhost:5432

Redis:

* localhost:6379

---

# Common Development Ports

| Service              | Port  |
| -------------------- | ----- |
| API Gateway          | 3000  |
| Wallet Service       | 3001  |
| Transaction Service  | 3002  |
| Notification Service | 3003  |
| RabbitMQ Management  | 15672 |
| PostgreSQL           | 5432  |
| Redis                | 6379  |

---

# Local Development Goals

The local setup supports:

* isolated service development
* event-driven workflow testing
* distributed debugging
* infrastructure simulation
* asynchronous processing validation

---

# Development Philosophy

The platform favors:

* reproducible environments
* infrastructure consistency
* containerized development
* isolated service boundaries
* operational parity between local and deployment environments
