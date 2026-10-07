# WebSocket Authorization Matrix

| ID | Session | Target | Expected | Status |
|---|---|---|---|---|
| WS-01 | A | A-owned | Allow | Baseline |
| WS-02 | B | B-owned | Allow | Baseline |
| WS-03 | A | B-owned | Deny/isolate | Pending fresh A session |
| WS-04 | B | A-owned | Deny/isolate | Pending complete A-side validation |

No vulnerability is claimed for pending tests.
