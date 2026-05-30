# Caching Strategy

## Overview

Redis is used within the Wallet-as-a-Service platform as a distributed caching and coordination layer.

Caching is primarily used to:

* reduce database load
* improve response latency
* support distributed workflows
* enable temporary state management

Redis is intentionally treated as a non-authoritative system.

The platform remains functionally correct even if Redis becomes unavailable.

---

# Caching Principles

The caching strategy follows several principles:

* financial correctness must not depend on cache availability
* cache entries are disposable
* stale cache data must not compromise consistency
* cache invalidation must be predictable
* sensitive financial state should not rely solely on cache persistence

---

# Redis Use Cases

## Wallet Metadata Caching

Frequently accessed wallet metadata may be cached to reduce repetitive database lookups.

Examples:

* wallet status
* wallet configuration
* account preferences

---

## Idempotency Key Tracking

Redis stores temporary idempotency records to support:

* duplicate request detection
* retry safety
* replay prevention

---

## Rate Limiting

The API Gateway uses Redis-backed distributed rate limiting to:

* prevent abuse
* protect downstream services
* control operational load

---

## Distributed Locking

Redis may be used for lightweight distributed coordination where temporary locking is required.

Examples:

* reconciliation workflows
* scheduled jobs
* duplicate processing prevention

---

## Session Management

Redis can temporarily store:

* authentication sessions
* temporary authorization state
* API session metadata

---

# Cache Expiration Policies

Cache entries use explicit TTL (time-to-live) policies.

This prevents:

* stale long-lived cache entries
* memory exhaustion
* outdated operational state

---

# Cache Invalidation Strategy

Cache invalidation occurs through:

* event-driven updates
* TTL expiration
* explicit invalidation after writes

---

# Read-Through Caching

The platform primarily uses read-through caching patterns.

Workflow:

1. Request checks Redis.
2. Cache miss falls back to PostgreSQL.
3. Database result populates Redis.

---

# Cache Failure Handling

Redis failures must not compromise financial correctness.

Fallback strategy:

* bypass cache
* retrieve directly from PostgreSQL
* continue operating with degraded performance if necessary

---

# Caching Tradeoffs

Caching introduces:

* invalidation complexity
* temporary state divergence
* operational coordination overhead

However, these tradeoffs are accepted for:

* improved performance
* reduced database pressure
* scalability improvements

---

# Financial Consistency Considerations

Critical financial state is never trusted exclusively from cache.

Authoritative financial records remain within:

* transaction ledgers
* PostgreSQL persistence layer
* reconciliation workflows

Cache layers exist strictly for optimization purposes.
