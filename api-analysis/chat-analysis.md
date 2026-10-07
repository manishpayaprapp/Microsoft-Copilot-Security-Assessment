# API-01 — POST /chat

## Captured request/response

```http
POST /chat?fromcode=cmmyr718qsb&es=SSR HTTP/2
Host: m365.cloud.microsoft
Content-Type: application/json
X-Session-Id: [REDACTED]
Origin: https://m365.cloud.microsoft
Referer: https://m365.cloud.microsoft/chat/conversation/[REDACTED]

[JSON request body captured; secrets redacted]

HTTP/2 200 OK
Content-Type: application/json

{
  "action": "ConversationResponseComplete",
  "conversationId": "[REDACTED]",
  "traceId": "[REDACTED]",
  "isNewChat": true,
  "turnState": "Completed",
  "state": {
    "conversationPageHistoryList": {
      "chats": [
        {
          "conversationId": "[REDACTED]",
          "threadId": "[REDACTED]",
          "turnState": "Completed"
        }
      ]
    }
  },
  "chatType": "web",
  "agentList": []
}
```

## Observed fields
- `ConversationResponseComplete`
- `conversationId`
- `traceId`
- `isNewChat`
- `turnState`
- `threadId`
- `chatType`

## Security interpretation

This proves practical conversation-state handling. It does not by itself prove an authorization weakness.
