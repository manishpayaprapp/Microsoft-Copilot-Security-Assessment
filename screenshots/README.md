# Screenshot Evidence

This directory contains screenshots supplied/collected during the research session and focused evidence captures.

## Screenshot handling

For full-screen Burp captures, the **Ubuntu desktop top panel containing the system date/time has been cropped out**. The Burp application content itself was not intentionally removed by this crop. Terminal-focused screenshots that already excluded the desktop panel were left unchanged.

The supplied numbering contains no `18-*` capture. It was not invented or duplicated. The previous `19-app-launcher-response.png` filename was corrected to `19-pinned-apps-response.png` because the actual Burp request shown is `GetUserPinnedApps`.

## Captures

- `01-burp-http-history-browser-events.png` — Burp Proxy → HTTP history; supplied Microsoft browser/application telemetry capture.
- `01a-http-history-request-response.png` — Focused Burp HTTP request/response capture supplied from the research session.
- `02-burp-websocket-history-chathub.png` — Burp Proxy → WebSockets history; Chathub connection with client/server traffic.
- `02a-chathub-message-history.png` — Focused Chathub WebSocket message-history capture.
- `03-burp-repeater-microsoft-endpoint.png` — Burp Repeater request/response capture supplied from the research session.
- `03a-repeater-request-response.png` — Focused Repeater request/response capture.
- `07-subfinder-command.png` — Subfinder command and discovered m365.cloud.microsoft subdomains.
- `08-subfinder-results-count.png` — Focused Subfinder result/count evidence.
- `09-httpx-live-hosts.png` — HTTPX live-host validation and technology/status output.
- `10-httpx-priority-host.png` — Focused evidence for the prioritized Copilot-related host.
- `11-burp-chat-history.png` — Burp HTTP history showing authenticated Copilot traffic including /chat and related requests.
- `12-burp-chat-response.png` — Focused /chat response evidence and resource-state fields.
- `13-burp-chat-repeater-baseline.png` — Burp Repeater baseline capture for an observed Copilot request.
- `14-burp-events-history.png` — Burp HTTP history filtered around /events traffic.
- `15-burp-events-response.png` — Focused /events response evidence.
- `16-burp-app-shell-history.png` — Burp HTTP history filtered around /resources/app-shell-action.
- `17-refresh-nav-pane.png` — Application-shell RefreshNavPane request/response capture.
- `19-pinned-apps-response.png` — GetUserPinnedApps request/response capture.
- `20-event-listener-client.png` — m365Copilot/EventListener/Client request/response capture.
- `21-config-fluid-endpoint.png` — Observed Config/Fluid endpoint capture from the supplied Burp session.
- `22-chathub-handshake.png` — Chathub WebSocket handshake / 101 Switching Protocols evidence.
- `23-chathub-client-message.png` — Chathub client-to-server structured JSON frame.
- `24-chathub-server-message.png` — Chathub server-to-client structured JSON frame.
- `25-chathub-message-sequence.png` — Chathub WebSocket history showing multiple bidirectional frames.
- `26-chathub-message-detail.png` — Detailed Chathub message/schema capture.

## Evidence hygiene

These captures are intended for private mentor review. Some may contain identifiers, cookies, session metadata, correlation IDs, or other live-looking values. Do not publish this directory or commit raw authentication material to a public repository.

A screenshot supports an observation; it does not by itself establish a vulnerability. Security conclusions remain tied to the corresponding controlled test and documented result.
