# Database Relationships

```mermaid
erDiagram

    WALLET ||--o{ TRANSACTION : contains

    TRANSACTION ||--o{ LEDGER_ENTRY : generates

    WALLET {
        uuid wallet_id
        uuid user_id
        string currency
        string status
    }

    TRANSACTION {
        uuid transaction_id
        decimal amount
        string transaction_type
        string status
    }

    LEDGER_ENTRY {
        uuid ledger_entry_id
        decimal amount
        string entry_type
    }
```

---

# Overview

The persistence layer prioritizes:

* auditability
* immutable financial history
* transactional integrity
* reconciliation support

---

# Wallet Entity

Wallets represent:

* account ownership
* wallet state
* balance coordination

---

# Transaction Entity

Transactions represent immutable financial operations.

Examples:

* funding
* debits
* transfers
* reversals

---

# Ledger Entries

Ledger entries provide:

* accounting traceability
* replay capability
* reconciliation support
