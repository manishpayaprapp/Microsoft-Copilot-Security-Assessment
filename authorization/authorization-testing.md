# Authorization — Practical A/B Record

## Controlled accounts
- User A
- User B

## Completed conversation tests

| ID | Session | Resource owner | Expected | Observed | Result |
|---|---|---|---|---|---|
| AUTH-01 | A | A | Allow | Legitimate access | Pass |
| AUTH-02 | B | B | Allow | Legitimate access | Pass |
| AUTH-03 | A | B | Deny/isolate | No confirmed unauthorized access demonstrated | Pass |
| AUTH-04 | B | A | Deny/isolate | No confirmed unauthorized access demonstrated | Pass |

## Conclusion

No confirmed BOLA/IDOR vulnerability was demonstrated in the completed conversation-level testing.

Remaining fresh User A-dependent API/WebSocket tests should remain **Pending** rather than being fabricated.
