# Environment Variables

## Overview

The Wallet-as-a-Service platform uses environment variables for configuration management across environments.

Configuration includes:

* infrastructure connectivity
* credentials
* service ports
* feature toggles
* deployment-specific values

---

# Configuration Philosophy

The platform prioritizes:

* environment isolation
* deployment flexibility
* secret separation
* reproducible deployments

---

# Example Variables

## API Gateway

```env id="h14r7r"
PORT=3000
JWT_SECRET=example_secret
RATE_LIMIT_WINDOW=60
RATE_LIMIT_MAX=100
```

---

## PostgreSQL

```env id="l8rvdo"
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_USER=postgres
POSTGRES_PASSWORD=password
POSTGRES_DB=wallet_db
```

---

## Redis

```env id="df1m1v"
REDIS_HOST=localhost
REDIS_PORT=6379
```

---

## RabbitMQ

```env id="csc21f"
RABBITMQ_HOST=localhost
RABBITMQ_PORT=5672
RABBITMQ_USER=guest
RABBITMQ_PASSWORD=guest
```

---

# Secrets Management

Sensitive values should:

* never be committed to source control
* remain environment-specific
* use secret management solutions in production

---

# Environment Isolation

Each environment maintains isolated:

* credentials
* queues
* databases
* infrastructure configuration

---

# Configuration Validation

Services should validate:

* required environment variables
* missing configuration
* invalid configuration values

during startup.

---

# Operational Philosophy

The architecture favors:

* explicit configuration
* deployment portability
* infrastructure reproducibility
