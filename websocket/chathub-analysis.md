# WS-01 — Chathub WebSocket

## Captured handshake

```http
GET /m365Copilot/Chathub/[REDACTED]?...&ConversationId=[REDACTED]&access_token=[REDACTED] HTTP/2
Host: substrate.office.com
Connection: Upgrade
Upgrade: websocket
Origin: https://m365.cloud.microsoft
Sec-WebSocket-Version: 13
Sec-WebSocket-Key: [REDACTED]

HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Vary: Origin
X-BackEndHttpStatus: 101,101
X-Proxy-BackendServerStatus: 101
Sec-WebSocket-Accept: [REDACTED]
Strict-Transport-Security: max-age=31536000; includeSubDomains
```

## Meaning

The `101 Switching Protocols` response confirms that the application established a WebSocket transport.

The request also contained conversation/session parameters and an access token in the original capture. Those values are redacted here.

A WebSocket handshake alone does not establish a vulnerability.
