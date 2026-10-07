# Resource Boundary Analysis

## Purpose

The main authorization question is whether identifiers visible in normal Copilot traffic are enforced against the authenticated account that owns the resource.

## Identifiers observed

| Identifier | Where observed | Security relevance |
|---|---|---|
| `conversationId` | `/chat` response and Chathub query | Conversation ownership boundary |
| `threadId` | `/chat` response/state | Thread/session relationship |
| `traceId` / response trace identifiers | `/chat` metrics | Correlation/debugging, not treated as an authorization key |
| `requestId` | `/chat` metrics | Request correlation |
| `clientrequestid` | Chathub query | Client/request correlation |
| `X-SessionId` | Chathub query | Session boundary |
| `chatsessionid` | Chathub query | Chat session boundary |
| `XRoutingParameterSessionKey` | Chathub query | Routing/session context |

## Analysis approach

1. Establish a normal resource under User A.
2. Establish a normal resource under User B.
3. Capture the identifiers generated for each resource.
4. Test the resource using its owning account.
5. Test the opposite account only within the controlled test setup.
6. Compare HTTP status, response body, returned resource metadata and observable application behavior.

## Result

The completed conversation-level A/B testing did not demonstrate unauthorized access. No BOLA/IDOR vulnerability is claimed.

## Remaining work

Fresh User A authentication is required for the remaining Chathub cross-account validation. This is recorded as pending rather than inferred.
