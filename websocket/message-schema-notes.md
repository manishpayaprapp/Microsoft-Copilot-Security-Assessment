# Chathub Message Schema Notes

## Captured frame characteristics

The supplied Burp WebSockets history shows multiple client-to-server and server-to-client frames on a single Chathub WebSocket connection.

The selected server/client traffic includes structured JSON with fields such as:

- `type`
- `target`
- `arguments`
- `messages`
- message text/content fields
- timestamps
- `messageId`
- `requestId`
- `messageType`
- progress/content-origin indicators

## Example observed semantic pattern

A server-to-client frame contains an update structure with:

- `target: "update"`
- an `arguments` array
- a `messages` collection
- progress/message metadata

This is useful for understanding how the UI receives streamed conversation state.

## Security relevance

The presence of conversation/session identifiers in the surrounding WebSocket handshake and message flow makes Chathub an independent authorization surface. The assessment therefore treats WebSocket authorization separately from ordinary HTTP API authorization.

## Evidence

See:
- `screenshots/02-burp-websocket-history-chathub.png`
- `evidence/websocket/handshake.md`
- `websocket/websocket-authorization-testing.md`
