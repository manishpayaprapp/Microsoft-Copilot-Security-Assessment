# Final Practical Testing Matrix

| ID | Component | Practical action | Evidence | Result |
|---|---|---|---|---|
| RECON-01 | Subfinder | Enumerate target subdomains | `reconnaissance/subdomain-enumeration.md` | Completed |
| RECON-02 | HTTPX | Validate reachable hosts | `reconnaissance/live-host-discovery.md` | Completed |
| API-01 | `/chat` | Inspect authenticated request/response and resource metadata | `evidence/api/chat.md`, screenshots 11–13 | Completed — observed behavior documented |
| API-02 | `/events` | Inspect event request/response structure | `evidence/api/events.md`, screenshots 14–15 | Completed — representative traffic documented |
| API-03 | App Shell | Inspect `RefreshNavPane`, `GetUserPinnedApps` and related actions | `evidence/api/app-shell-actions.md`, screenshots 16, 17, 19 | Completed — observed actions documented |
| RES-01 | Resource mapping | Map conversationId/threadId/session identifiers | `api-analysis/resource-boundary-analysis.md` | Completed |
| AUTHZ-01 | Conversation | A → A | `authorization/authorization-matrix.md` | PASS |
| AUTHZ-02 | Conversation | B → B | `authorization/authorization-matrix.md` | PASS |
| AUTHZ-03 | Conversation | A → B | `authorization/authorization-matrix.md` | No confirmed unauthorized access |
| AUTHZ-04 | Conversation | B → A | `authorization/authorization-matrix.md` | No confirmed unauthorized access |
| WS-01 | Chathub | WebSocket handshake | `evidence/websocket/handshake.md` | HTTP 101 observed |
| WS-02 | Chathub | Bidirectional frame inspection | `websocket/message-schema-notes.md` | Completed |
| WS-03 | Chathub | Cross-account authorization | `websocket/websocket-authorization-testing.md` | Pending |

## Overall security position

**No confirmed BOLA/IDOR vulnerability is demonstrated by the completed evidence.**

Pending items remain explicitly marked as pending.
