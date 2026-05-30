# Pagination Strategy

Pagination improves:

* scalability
* query efficiency
* predictable API behavior

---

# Recommended Strategy

Cursor-based pagination is preferred over offset pagination for large datasets.

---

# Example

```http id="fw56xv"
GET /api/v1/transactions?cursor=abc123&limit=20
```

---

# Design Goals

The pagination architecture prioritizes:

* deterministic ordering
* scalable querying
* operational efficiency
