# Findings

## Confirmed vulnerabilities

**None.**

## Security-relevant observations

### OBS-01 — Conversation and thread identifiers are exposed in normal application state
`/chat` responses contain conversation/thread state. These identifiers are security-relevant because they represent application resources and therefore require authorization enforcement.

**Status:** Observed. No unauthorized access demonstrated.

### OBS-02 — Application-shell actions return structured account/application state
`/resources/app-shell-action` supports multiple named actions and returns structured application/navigation state.

**Status:** Observed. No security impact demonstrated.

### OBS-03 — Chathub is a separate real-time authorization surface
The application establishes a WebSocket connection and exchanges structured JSON frames. Session and conversation context appear in the surrounding handshake/request state.

**Status:** Observed. Cross-account authorization validation remains pending.

## Authorization conclusion

Controlled User A/User B conversation testing did not demonstrate BOLA/IDOR. The assessment does not label normal successful same-owner access as a finding.

## Limitations

A fresh User A authentication session was not consistently available for the remaining Chathub cross-account test. This is documented as a limitation rather than filled with an assumed result.
