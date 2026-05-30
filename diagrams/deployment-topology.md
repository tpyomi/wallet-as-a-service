# Deployment Topology

```mermaid
flowchart TD

    LB[Load Balancer]

    APIGW1[API Gateway]
    APIGW2[API Gateway]

    Wallet1[Wallet Service]
    Wallet2[Wallet Service]

    RabbitMQ[(RabbitMQ Cluster)]

    Postgres[(PostgreSQL)]

    Redis[(Redis)]

    LB --> APIGW1
    LB --> APIGW2

    APIGW1 --> Wallet1
    APIGW2 --> Wallet2

    Wallet1 --> RabbitMQ
    Wallet2 --> RabbitMQ

    Wallet1 --> Postgres
    Wallet2 --> Postgres

    Wallet1 --> Redis
    Wallet2 --> Redis
```

---

# Overview

The deployment architecture supports horizontally scalable service deployment patterns.

The platform prioritizes:

* independent scaling
* stateless services
* infrastructure resilience
* workload distribution

---

# Scalability Principles

Services remain stateless wherever possible to improve:

* deployment flexibility
* scaling efficiency
* failure recovery

---

# Infrastructure Coordination

Infrastructure components provide:

* messaging coordination
* persistence
* caching
* distributed synchronization
