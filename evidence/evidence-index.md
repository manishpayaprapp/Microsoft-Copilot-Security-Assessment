# Evidence Index

| Evidence ID | Evidence | What it supports | Source |
|---|---|---|---|
| E-01 | Subfinder enumeration | 11 discovered subdomains | `reconnaissance/subdomain-enumeration.md`, `screenshots/07-subfinder-command.png` |
| E-02 | HTTPX live-host output | 10 HTTP observations and technology/status mapping | `reconnaissance/live-host-discovery.md`, `screenshots/09-httpx-live-hosts.png` |
| E-03 | `/chat` capture | Authenticated 200 response and conversation/thread state | `evidence/api/chat.md`, screenshots `11–13` |
| E-04 | `/events` capture | Representative event request/response structure | `evidence/api/events.md`, screenshots `14–15` |
| E-05 | App-shell captures | Observed application-shell actions and successful responses | `evidence/api/app-shell-actions.md`, screenshots `16`, `17`, `19` |
| E-06 | Chathub handshake | WebSocket upgrade with HTTP 101 | `evidence/websocket/handshake.md`, `screenshots/22-chathub-handshake.png` |
| E-07 | Authorization matrix | Controlled A/B same-owner and cross-owner checks | `authorization/authorization-matrix.md` |
| E-08 | Chathub message evidence | Bidirectional structured JSON frames | screenshots `23–26` |
| E-09 | Event Listener evidence | Supporting client event endpoint observed | `screenshots/20-event-listener-client.png` |
| E-10 | Config/Fluid evidence | Supporting endpoint observed in Burp | `screenshots/21-config-fluid-endpoint.png` |
| E-11 | Burp workflow evidence | Direct Burp UI captures from the supplied session | screenshots `01/01a`, `02/02a`, `03/03a` |

## Evidence rule

A screenshot supports an observed behavior. A vulnerability conclusion requires the corresponding controlled test, comparison and reproducible result. No screenshot in this package is treated as a vulnerability finding by itself.
