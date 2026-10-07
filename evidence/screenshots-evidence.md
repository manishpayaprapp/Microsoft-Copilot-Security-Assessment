# Screenshot Evidence Notes

The screenshot set contains direct captures from the supplied research session plus focused evidence captures. Full-screen Burp images have had only the Ubuntu desktop top panel (system date/time) cropped out.

## Reconnaissance

- `07-subfinder-command.png` — Subfinder enumeration command and discovered hosts.
- `08-subfinder-results-count.png` — focused enumeration result/count.
- `09-httpx-live-hosts.png` — HTTPX live-host validation.
- `10-httpx-priority-host.png` — focused prioritized-host evidence.

## HTTP/API

- `11-burp-chat-history.png` — Burp HTTP history around Copilot `/chat` and related traffic.
- `12-burp-chat-response.png` — focused `/chat` response.
- `13-burp-chat-repeater-baseline.png` — Repeater baseline.
- `14-burp-events-history.png` — `/events` traffic in HTTP history.
- `15-burp-events-response.png` — `/events` response.
- `16-burp-app-shell-history.png` — application-shell traffic.
- `17-refresh-nav-pane.png` — `RefreshNavPane`.
- `19-pinned-apps-response.png` — `GetUserPinnedApps`.
- `20-event-listener-client.png` — `/m365Copilot/EventListener/Client`.
- `21-config-fluid-endpoint.png` — observed Config/Fluid supporting endpoint.

## WebSocket

- `22-chathub-handshake.png` — Chathub upgrade / `101 Switching Protocols`.
- `23-chathub-client-message.png` — client-to-server frame.
- `24-chathub-server-message.png` — server-to-client frame.
- `25-chathub-message-sequence.png` — multiple bidirectional frames.
- `26-chathub-message-detail.png` — detailed message structure.
- `02-burp-websocket-history-chathub.png` and `02a-chathub-message-history.png` — original/focused Chathub captures supplied in the archive.

## Supplementary Burp captures

- `01-burp-http-history-browser-events.png` / `01a-http-history-request-response.png` — Microsoft browser/application telemetry capture.
- `03-burp-repeater-microsoft-endpoint.png` / `03a-repeater-request-response.png` — Microsoft application-service Repeater capture.

These supplementary captures demonstrate the actual Burp workflow and supporting Microsoft traffic. They are not presented as independent Copilot vulnerability proof.

## Evidence hygiene

The screenshots may contain identifiers, cookies, session metadata or correlation values. Keep them private and do not publish raw authentication material.
