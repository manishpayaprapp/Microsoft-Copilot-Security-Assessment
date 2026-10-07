# Scope and Test Rules

## Scope

The assessment was performed against Microsoft Copilot-related web application traffic within the researcher's authorized testing context.

## Controlled accounts

- **User A** — controlled test account
- **User B** — controlled test account

The authorization work is based on comparing behavior between these two controlled identities.

## Test rules

1. Use normal application functionality to generate requests.
2. Capture traffic in Burp Suite and Browser DevTools.
3. Reuse only researcher-controlled resources for authorization checks.
4. Compare same-user and cross-user behavior.
5. Do not claim a vulnerability unless unauthorized behavior is actually demonstrated.
6. Do not brute-force identifiers or enumerate unrelated users/resources.
7. Do not place live access tokens or session cookies in public repositories.
8. Mark incomplete tests as **Pending** rather than filling them with assumed results.

## Evidence classification

- **Observed** — directly visible in captured traffic.
- **Completed** — the planned controlled test was performed.
- **No confirmed issue** — testing did not demonstrate unauthorized behavior.
- **Pending** — the required authenticated state or additional controlled validation is not currently available.
