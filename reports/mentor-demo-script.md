# Mentor Walkthrough Script

## 1. Start with the project register

Open `01-assessment-register.md`.

Explain the progression:

1. Attack-surface mapping
2. API inventory
3. Resource mapping
4. Application actions
5. Event traffic
6. Event Listener
7. Chathub WebSocket reconnaissance
8. Controlled authorization testing

## 2. Show reconnaissance

Open:

- `reconnaissance/subdomain-enumeration.md`
- `reconnaissance/live-host-discovery.md`

Then show:

- `07-subfinder-command.png`
- `08-subfinder-results-count.png`
- `09-httpx-live-hosts.png`
- `10-httpx-priority-host.png`

Key numbers:

- 11 discovered subdomains
- 10 HTTP observations
- `chat.svc.m365.cloud.microsoft` prioritized for deeper review

## 3. Show API evidence

Open:

- `api-analysis/api-inventory-practical.md`
- `api-analysis/chat-analysis.md`
- `api-analysis/app-shell-analysis.md`

Show:

- `11-burp-chat-history.png`
- `12-burp-chat-response.png`
- `13-burp-chat-repeater-baseline.png`
- `14-burp-events-history.png`
- `15-burp-events-response.png`
- `16-burp-app-shell-history.png`
- `17-refresh-nav-pane.png`
- `19-pinned-apps-response.png`
- `20-event-listener-client.png`

Explain that normal application behavior was used to identify authenticated endpoints, parameters and resource identifiers.

## 4. Show resource mapping and authorization

Open:

- `api-analysis/resource-boundary-analysis.md`
- `authorization/authorization-matrix.md`
- `authorization/authorization-testing.md`

Point out:

- `conversationId`
- `threadId`
- `X-SessionId`
- `chatsessionid`
- `clientrequestid`

Explain:

- A → A: allowed
- B → B: allowed
- A → B: no unauthorized access demonstrated
- B → A: no unauthorized access demonstrated

Do not describe normal same-owner access as a vulnerability.

## 5. Show WebSocket evidence

Open:

- `websocket/chathub-analysis.md`
- `websocket/message-schema-notes.md`

Then show:

- `22-chathub-handshake.png`
- `23-chathub-client-message.png`
- `24-chathub-server-message.png`
- `25-chathub-message-sequence.png`
- `26-chathub-message-detail.png`

Point out:

- WebSocket upgrade
- `101 Switching Protocols`
- one connection
- both client/server directions
- multiple structured JSON frames
- message/request/conversation context

## 6. Show supplementary Burp captures

Show:

- `01-burp-http-history-browser-events.png`
- `02-burp-websocket-history-chathub.png`
- `03-burp-repeater-microsoft-endpoint.png`

These demonstrate the actual Burp workflow and supporting Microsoft traffic. They are not presented as independent vulnerability proof.

## 7. Finish with results

Open:

- `results/testing-matrix.md`
- `results/findings.md`
- `results/coverage-summary.md`
- `evidence/evidence-index.md`

Final statement:

> The assessment has evidence for reconnaissance, authenticated API mapping, resource analysis, controlled conversation authorization, application-shell analysis and WebSocket reconnaissance. No confirmed vulnerability is claimed from the completed evidence. The remaining Chathub cross-account authorization check is explicitly pending because it requires a fresh controlled User A session.
