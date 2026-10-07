# API-03 — App Shell Actions

## Captured actions

```http
POST /resources/app-shell-action?fromcode=cmmyr718qsb&es=SSR HTTP/2
Host: m365.cloud.microsoft
X-Route-Id: app-shell-action
X-Session-Id: [REDACTED]
Content-Type: application/json

{"action":"GetUserPinnedApps"}

HTTP/2 200 OK
Content-Type: application/json

{"store":{"pinnedAppIds":["Mail","SkypeTeams","WordOnline","ExcelOnline","PowerPointOnline","OneNoteOnline","Clipchamp","Documents","Sites"]}}

---

POST /resources/app-shell-action?fromcode=cmmyr718qsb&es=SSR HTTP/2
Host: m365.cloud.microsoft
X-Route-Id: app-shell-action
X-Session-Id: [REDACTED]
Content-Type: application/json

{"action":"GetAppLauncherCoreApps"}

HTTP/2 200 OK
Content-Type: application/json

{"store":{"appLauncherCoreAppsContent":[{"id":"[captured]","label":"Create","path":"/create"}]}}

---

POST /resources/app-shell-action?fromcode=cmmyr718qsb&es=SSR HTTP/2
Host: m365.cloud.microsoft
X-Route-Id: app-shell-action
X-Session-Id: [REDACTED]
Content-Type: application/json

{"action":"RefreshNavPane","conversationHistoryFilter":null,"skipNotebooks":true,"skipAgentListCache":true,"enableLastMessage":false,"state":{"accountInfo":"[REDACTED]"}}

HTTP/2 200 OK
Content-Type: application/json

[structured navigation/account application state captured; identifiers redacted]
```

### Actions observed
1. `GetUserPinnedApps`
2. `GetAppLauncherCoreApps`
3. `RefreshNavPane`

These are real application-shell requests from the supplied Burp capture, with secrets and account data redacted.
