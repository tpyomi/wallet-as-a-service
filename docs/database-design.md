# Database Design

## Overview

PostgreSQL acts as the primary system of record within the Wallet-as-a-Service platform.

The database layer prioritizes:

* consistency
* auditability
* transactional safety
* reconciliation support
* historical traceability

---

# Database Philosophy

The architecture treats the database as:

* the authoritative financial state
* the source of truth
* the reconciliation foundation

Caches and projections are considered secondary representations.

---

# Core Entities

## Wallets

Represents user wallet accounts.

Example fields:

* wallet_id
* user_id
* currency
* status
* created_at

---

## Transactions

Represents immutable financial transaction records.

Example fields:

* transaction_id
* wallet_id
* amount
* transaction_type
* status
* reference
* created_at

---

## Ledger Entries

Stores accounting-style immutable balance operations.

Benefits:

* auditability
* replayability
* reconciliation support

---

## Idempotency Records

Tracks processed operations to prevent duplicate execution.

---

## Audit Logs

Stores operational events and traceability metadata.

---

# Transactional Integrity

Critical financial writes use:

* database transactions
* atomic operations
* consistency constraints

---

# Immutable Financial Records

Financial transaction records should remain immutable wherever practical.

Instead of modifying records:

* reversal transactions are preferred
* corrective ledger entries are preferred

---

# Indexing Strategy

Indexes should support:

* transaction lookup
* wallet lookup
* reconciliation queries
* idempotency checks

---

# Partitioning Considerations

As transaction volume grows:

* ledger tables may require partitioning
* archival workflows may become necessary

---

# Database Constraints

Constraints improve:

* data correctness
* duplicate prevention
* operational safety

Examples:

* unique transaction references
* foreign key constraints
* not-null constraints

---

# Database Tradeoffs

The architecture prioritizes:

* correctness
* traceability
* auditability

over:

* overly simplified schemas
* write shortcuts
* denormalized financial mutations
