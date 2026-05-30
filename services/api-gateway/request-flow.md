# Request Flow

## Example Flow

1. Client sends request
2. Gateway validates authentication
3. Gateway validates authorization
4. Rate limiting evaluated
5. Correlation ID attached
6. Request forwarded to backend service

---

# Design Goals

The request flow prioritizes:

* centralized infrastructure policies
* operational visibility
* backend simplification
