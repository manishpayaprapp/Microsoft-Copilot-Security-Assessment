# Supplementary Burp Observations

The three supplied screenshots include Microsoft traffic that is useful for demonstrating hands-on Burp workflow but is not all part of the Copilot API surface.

## Capture 01 — Browser telemetry

- Host shown: `browser.events.data.microsoft.com`
- Method: `POST`
- HTTP result: `HTTP/2 200 OK`
- Response: small JSON acknowledgement
- CORS headers are visible.

**Use:** demonstrates captured Microsoft-origin telemetry traffic and request/response inspection.

**Do not classify as:** Copilot `/events` endpoint evidence.

## Capture 02 — Chathub

- Host: `substrate.office.com`
- Path family: `/m365Copilot/Chathub/...`
- Burp WebSockets history shows both directions.
- Structured JSON frames are visible.

**Use:** direct Chathub WebSocket evidence.

## Capture 03 — Instrument/logclient

- Host: `admin.microsoft.com`
- Method: `POST`
- Path: `/api/instrument/logclient`
- Result: `HTTP/2 200 OK`
- Request contains structured client instrumentation records.

**Use:** demonstrates additional authenticated Microsoft application traffic observed while using the environment.

**Do not classify as:** Copilot vulnerability evidence.

## Why these are included

They show the actual research workflow: traffic was captured, filtered, inspected, and separated into relevant Copilot surfaces versus supplementary Microsoft-origin traffic.
