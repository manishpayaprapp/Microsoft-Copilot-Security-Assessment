# API-02 — POST /events

## Captured request/response

```http
POST /events HTTP/2
Host: m365.cloud.microsoft
Authorization: Bearer [REDACTED]
X-Session-Id: [REDACTED]
Content-Type: application/json
Origin: https://m365.cloud.microsoft

{
  "events": [
    {
      "eventId": "InputFocused",
      "clientCorrelationId": "[REDACTED]",
      "eventScope": "[captured]",
      "timestamp": "[captured]",
      "level": "[captured]"
    }
  ],
  "context": {
    "sessionId": "[REDACTED]",
    "officeHomeEcsRing": "[captured]",
    "featureFlags": "[captured]"
  }
}

HTTP/2 200 OK
Content-Type: application/json; charset=utf-8

{"success":true,"received":1}
```

The supplied API analysis records multiple `/events` requests returning HTTP 200 and responses such as `{"success":true,"received":1}`.

## Security interpretation

The endpoint behaves as authenticated event/telemetry ingestion. A successful 200 response alone is not evidence of an authorization flaw.
