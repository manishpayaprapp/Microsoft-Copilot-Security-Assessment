# Raw Observations

This file records observations that are directly supported by the supplied captures and existing assessment notes.

## Reconnaissance

- Subfinder output contained 11 discovered subdomains under `m365.cloud.microsoft`.
- HTTPX output contained 10 observed HTTP hosts/responses.
- `chat.svc.m365.cloud.microsoft` returned HTTP 302 in the supplied output and was prioritized for deeper review.

## HTTP application traffic

- `/chat` returned HTTP 200.
- `/chat` response state included conversation entries containing `conversationId` and, for applicable entries, `threadId`.
- `/resources/app-shell-action` returned HTTP 200 for observed application-shell actions.
- Observed application-shell actions include `RefreshNavPane`, `GetUserPinnedApps`, and `GetAppLauncherCoreApps`.

## WebSocket

- Chathub upgrade returned HTTP 101 Switching Protocols.
- Burp WebSockets history shows traffic in both directions.
- Captured message content uses structured JSON.

## Authorization

- User A could access an A-owned conversation.
- User B could access a B-owned conversation.
- Controlled cross-account conversation checks did not demonstrate unauthorized access.
- Fresh User A-dependent Chathub cross-account validation remains pending.

## Important distinction

These are observations, not vulnerability claims. A security issue requires a demonstrated violation of the intended authorization boundary.
