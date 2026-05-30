# Rate Limit Example

## Example Policy

```txt id="p70mh5"
100 requests per minute
```

---

# Example Response

```http id="c11wfw"
HTTP 429 Too Many Requests
```

---

# Response Body

```json id="ybpk11"
{
  "error": "RATE_LIMIT_EXCEEDED"
}
```

---

# Architectural Goals

The strategy prioritizes:

* infrastructure protection
* operational stability
* abuse prevention
