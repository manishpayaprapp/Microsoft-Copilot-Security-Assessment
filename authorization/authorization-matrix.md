# Authorization Matrix

## Controlled account matrix

| Test ID | Resource owner | Requesting account | Operation | Expected | Actual | Result |
|---|---|---|---|---|---|---|
| AUTHZ-01 | User A | User A | Access A-owned conversation | Allowed | Allowed | PASS |
| AUTHZ-02 | User B | User B | Access B-owned conversation | Allowed | Allowed | PASS |
| AUTHZ-03 | User B | User A | Access B-owned conversation | Denied / isolated | No confirmed unauthorized access | NO ISSUE DEMONSTRATED |
| AUTHZ-04 | User A | User B | Access A-owned conversation | Denied / isolated | No confirmed unauthorized access | NO ISSUE DEMONSTRATED |
| AUTHZ-05 | User A | User A | Chathub cross-resource validation | Controlled | Fresh A session unavailable | PENDING |

## Interpretation

The matrix separates legitimate same-owner access from cross-owner authorization checks. A successful response to a same-owner request is not treated as a vulnerability. A cross-owner test would require observable unauthorized access before a BOLA/IDOR finding could be raised.
