# Microsoft Copilot Security Assessment — Updated Mentor Evidence Package

**Assessment type:** Authorized application security research  
**Primary tools:** Burp Suite Community Edition, Subfinder, HTTPX, Browser DevTools  
**Assessment focus:** attack-surface mapping, authenticated API inventory, resource mapping, authorization analysis, application-shell actions, event traffic, Event Listener analysis, and Chathub WebSocket reconnaissance.

## What is included

- reconnaissance records with command/output evidence
- API inventory and endpoint analysis
- resource and identifier mapping
- controlled User A/User B authorization matrix
- application-shell action analysis
- event and Event Listener analysis
- Chathub WebSocket handshake and message analysis
- **25 screenshot captures** in `screenshots/`
- focused Burp/WebSocket evidence captures
- evidence register and evidence-to-file mapping
- assessment activity register
- final findings and limitations
- mentor walkthrough script

## Current evidence-backed results

- Subfinder: **11 subdomains** observed.
- HTTPX: **10 HTTP observations** recorded.
- `/chat`: authenticated **HTTP 200** observed.
- `/events`: representative successful traffic captured and analyzed.
- `/resources/app-shell-action`: successful application-shell actions observed.
- `/m365Copilot/EventListener/Client`: supporting endpoint observed.
- Chathub: **HTTP 101 Switching Protocols** observed.
- Multiple Chathub client/server JSON frames captured.
- Controlled conversation authorization: no confirmed BOLA/IDOR demonstrated.
- Chathub cross-account authorization: **pending** where a fresh controlled User A session is required.

## Screenshot handling

Full-screen Burp screenshots have had the **Ubuntu desktop top panel containing the system date/time cropped out**. Burp content remains intact. Terminal-focused captures that did not contain the desktop panel were left unchanged.

The supplied numbering contains no `18-*` screenshot. It has not been fabricated or duplicated. The capture previously named `19-app-launcher-response.png` is actually a `GetUserPinnedApps` response, so it has been renamed to `19-pinned-apps-response.png`.

## Evidence integrity

Screenshots are evidence of observed traffic and workflow. They are not, by themselves, vulnerability findings. Vulnerability conclusions require controlled testing and reproducible results.

Keep screenshots and raw session material private. Do not publish authentication cookies, access tokens, session IDs or other sensitive values.

## Review order

1. `01-assessment-register.md`
2. `reconnaissance/subdomain-enumeration.md`
3. `reconnaissance/live-host-discovery.md`
4. `api-analysis/api-inventory-practical.md`
5. `api-analysis/chat-analysis.md`
6. `api-analysis/app-shell-analysis.md`
7. `authorization/authorization-matrix.md`
8. `websocket/chathub-analysis.md`
9. `websocket/message-schema-notes.md`
10. `results/testing-matrix.md`
11. `results/findings.md`
12. `evidence/evidence-index.md`
13. `screenshots/`

## Final security position

No confirmed vulnerability is claimed from the completed evidence. The report separates observed behavior, security-relevant observations, completed authorization checks and pending validation.
