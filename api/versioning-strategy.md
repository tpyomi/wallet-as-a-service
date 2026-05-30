# API Versioning Strategy

The platform uses URI-based versioning.

Example:

```http id="9pr6pr"
GET /api/v1/wallets
```

---

# Goals

Versioning supports:

* backward compatibility
* safe evolution
* distributed client support

---

# Deprecation Philosophy

Deprecated versions should:

* remain operational temporarily
* provide migration guidance
* avoid sudden breaking changes
