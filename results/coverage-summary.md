# Coverage Summary

| Area | Coverage | Status |
|---|---|---|
| Subdomain enumeration | 11 discovered hosts recorded | Complete |
| Live-host validation | 10 HTTP observations recorded | Complete |
| `/chat` request/response analysis | Authenticated 200 response and resource-state fields | Complete |
| Resource identifier mapping | conversationId/threadId/session identifiers | Complete |
| App-shell actions | RefreshNavPane, GetUserPinnedApps and related observed actions | Complete — observed actions |
| Event traffic | Representative `/events` structure and successful responses | Complete — representative traffic |
| Event Listener | `/m365Copilot/EventListener/Client` observed and documented | Complete — observed endpoint |
| Conversation BOLA/IDOR | A→A, B→B, A→B, B→A controlled checks | No issue demonstrated |
| Chathub handshake | 101 upgrade captured | Complete |
| Chathub message analysis | Bidirectional JSON frames and message structures | Complete |
| Chathub cross-account authorization | Requires fresh controlled A/B validation | Pending |

## Evidence coverage

The current screenshot directory contains **25 PNG captures**. The supplied numbering is `01–17`, `19–26`; there is no fabricated `18` capture. The former `19-app-launcher-response.png` capture has been renamed to `19-pinned-apps-response.png` because the actual request shown is `GetUserPinnedApps`.

## Coverage statement

The package is strongest on reconnaissance, authenticated API inventory, resource mapping, conversation authorization, application-shell analysis and WebSocket reconnaissance. It intentionally does not claim complete coverage of every Copilot backend route or complete WebSocket cross-account authorization until the remaining controlled test is performed.
