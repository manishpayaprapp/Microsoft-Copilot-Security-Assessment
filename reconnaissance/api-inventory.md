# Microsoft Copilot API Inventory

> **Purpose:** Document the API surface observed in Burp Suite during normal, authorized application use.
>
> **Scope:** This inventory is based only on the captured requests provided for this assessment. No endpoint purpose or security issue is assumed unless supported by the observed request/response.

## 1. Inventory

| # | Method | Host | Endpoint | Status | Content Type | Purpose | Auth | Parameters | Resource |
|---|---|---|---|---:|---|---|---|---|---|
| 1 | POST | `m365.cloud.microsoft` | `/chat?fromcode=cmmyr718qsb&es=Click` | 200 | JSON | To be determined from request/response body | Authenticated | `fromcode`, `es` | To be determined |
| 2 | POST | `m365.cloud.microsoft` | `/events` | 200 | JSON | To be determined from request/response body | Authenticated | None visible in URL | To be determined |
| 3 | POST | `substrate.office.com` | `/m365Copilot/EventListener/Client?...` | 200 | JSON | Event/action processing endpoint observed during Copilot activity | Authenticated | `EventId=ExecuteAction`, `variants=...` | Session/action |
| 4 | GET | `substrate.office.com` | `/m365Copilot/Chathub/{identifier}` | 101 | — | Chathub request associated with a Copilot conversation/session | Authenticated | `chatsessionid`, `XRoutingParameterSessionKey`, `clientrequestid`, `X-SessionId`, `ConversationId`, `access_token`, `variants`, `source`, `product`, `agentHost`, `licenseType`, `isEdu`, `agent`, `scenario` | Conversation / session |
| 5 | POST | `m365.cloud.microsoft` | `/resources/app-shell-action?fromcode=cmmyr718qsb&es=Click` | 200 | JSON | Application shell action; exact purpose to be determined from body | Authenticated | `fromcode`, `es` | Application/session |
| 6 | GET | `ecs.office.com` | `/config/v1/Fluid/0.0.0.1?...` | 200 | JSON | Fluid configuration retrieval | Authenticated | `agents`, `audience`, `userId`, `tenantId`, `hostName` | User / tenant configuration |
| 7 | GET | `go.trouter.skype.com` | `/` | 200 | text | Trouter connectivity/request associated with BizChat | Authenticated | `check`, `cor_id`, `epid`, `tc` | Session / connection |
| 8 | GET | `go.trouter.skype.com` | `/v4/c?...` | 101 | — | Trouter connection/stream request | Authenticated | `tc`, `timeout`, `epid`, `ccid`, `dom`, `cor_id`, `con_num` | Session / connection |

## 2. Key Requests to Inspect Further

The following requests are the highest-priority candidates for deeper manual inspection because they are directly associated with Copilot chat, events, actions, or conversation/session state:

### A. `POST /chat`

**Host:** `m365.cloud.microsoft`

**Observed:**
- Method: `POST`
- Status: `200`
- Response type: JSON
- Query parameters: `fromcode`, `es`

**Next step:** Inspect the full request and response body in Burp to determine what operation is performed and which identifiers are sent.

---

### B. `POST /events`

**Host:** `m365.cloud.microsoft`

**Observed:**
- Method: `POST`
- Status: `200`
- Response type: JSON
- Multiple requests were observed.

**Observed request IDs:** 419, 437, 454, 520, 525, 527, 535, 539, 669, 681, 689, 697, 702, 703, 704, 705, 706, 707, 708, 709, 710, 711, 712, 714.

**Next step:** Compare several `/events` requests to determine which fields change between user actions, messages, or UI events.

---

### C. `GET /m365Copilot/Chathub/{identifier}`

**Host:** `substrate.office.com`

**Observed identifiers/parameters include:**
- `ConversationId`
- `X-SessionId`
- `chatsessionid`
- `XRoutingParameterSessionKey`
- `clientrequestid`

**Important note:** The captured request also contains an `access_token` query parameter. Do **not** copy live tokens into this repository. Redact credentials/tokens in screenshots and notes.

**Next step:** Determine which identifiers are session-scoped, conversation-scoped, tenant-scoped, or user-scoped from repeated normal application requests.

---

### D. `POST /m365Copilot/EventListener/Client`

**Host:** `substrate.office.com`

**Observed:**
- `EventId=ExecuteAction`
- Large `variants` query parameter
- Status `200`
- JSON response

**Next step:** Compare the request body and response for different normal Copilot actions to identify the action schema.

---

## 3. Repeated Endpoints

### `/events`

This endpoint appeared repeatedly during the captured session. Record each distinct request body rather than creating a new inventory row for every identical request.

Useful comparison fields:

- Event/action type
- Conversation/session identifier
- User identifier
- Client request identifier
- Timestamp
- Any resource/object identifier
- Response fields
- Whether the response changes after a specific UI action

---

## 4. Request-Level Capture Template

Use this template for every endpoint that becomes interesting:

```text
### Endpoint: METHOD /path

Host:
Method:
Full Path:
Query Parameters:

Authentication:
- Cookie:
- Authorization:
- Other auth/session headers:

Request Headers:
- Content-Type:
- X-*:
- Other relevant headers:

Request Body:
```json
{
  "REPLACE_WITH_CAPTURED_BODY": "..."
}
```

Response Status:
Response Headers:
Response Body:

Observed Purpose:
Resource Identifier(s):
User-Specific:
Conversation-Specific:
Session-Specific:
Tenant-Specific:

Notes:
```

## 5. Resource / Identifier Mapping

| Identifier | Where Observed | Initial Classification | Confirmed? | Notes |
|---|---|---|---|---|
| `ConversationId` | Chathub request | Conversation identifier | No | Confirm by comparing multiple conversations |
| `X-SessionId` | Chathub request | Session identifier | No | Compare across sessions |
| `chatsessionid` | Chathub request | Chat/session identifier | No | Compare during one conversation and across conversations |
| `XRoutingParameterSessionKey` | Chathub request | Routing/session identifier | No | Determine lifetime |
| `clientrequestid` | Chathub request | Client request identifier | No | Compare across requests |
| `userId` | Fluid config request | User identifier | No | Confirm scope using normal requests |
| `tenantId` | Fluid config request | Tenant identifier | No | Confirm scope using normal requests |
| `epid` | Trouter requests | Session/connection-related identifier | No | Determine relationship to chat session |

## 6. What Is Not Yet Determined

The captured traffic alone does **not** establish:

- Whether any endpoint is vulnerable.
- Whether an identifier can be substituted successfully.
- Whether an identifier is user-specific or merely session-specific.
- Whether an endpoint permits access to another user's resource.
- Whether an endpoint exposes authorization weaknesses.
- The exact semantic purpose of every `/events` or `/resources/app-shell-action` request.

These should be determined from additional normal application traffic and controlled testing using accounts/resources you are authorized to test.

## 7. Evidence Checklist

For each important endpoint, capture:

- [ ] Burp request
- [ ] Burp response
- [ ] Method and host
- [ ] Full path
- [ ] Query parameters
- [ ] Relevant request headers
- [ ] Request body
- [ ] Response status
- [ ] Response headers
- [ ] Response body
- [ ] Resource/conversation/session identifiers
- [ ] Redacted screenshot
- [ ] Explanation of observed purpose
- [ ] Whether the behavior is user-, conversation-, session-, or tenant-specific

## 8. Security / Privacy Notes

- Use only accounts and resources you are authorized to test.
- Do not commit live access tokens, cookies, session identifiers, or other credentials.
- Redact tokens before adding Burp screenshots to `evidence/` or `screenshots/`.
- Do not label an endpoint as vulnerable based only on its existence or on a successful `200` response.
- Keep the inventory factual and separate **observation** from **hypothesis**.

## 9. Source Capture

This inventory was prepared from the supplied Burp capture. The capture showed the identified `/chat`, `/events`, Copilot Chathub, EventListener, application-shell, Fluid, and Trouter requests. fileciteturn0file0L13-L16

---
**Status:** Reconnaissance / API inventory in progress


## POST `/chat` — API Analysis

### Overview

The `/chat` endpoint was observed as an authenticated `POST` request to `m365.cloud.microsoft`. The endpoint is associated with processing a Copilot conversation and returning conversation state and metadata.

### Request Details

| Field | Observed Value |
|---|---|
| Method | `POST` |
| Host | `m365.cloud.microsoft` |
| Path | `/chat` |
| Query Parameters | `fromcode=cmmyr718qsb`, `es=Click` |
| Content-Type | `application/json` |
| Authentication | Authenticated browser session |
| Session Identifier | `X-Session-Id` |
| Request Body | JSON |
| Origin | `https://m365.cloud.microsoft` |
| Referer | Conversation-specific `/chat/conversation/{conversationId}` URL |

> **Security note:** Authentication cookies, tokens, and session values have been redacted and should not be committed to the repository.

### Response Details

The endpoint returned an HTTP `200 OK` response with a JSON body.

The response contained the following top-level fields:

```text
action
conversationId
traceId
isNewChat
conversationTitle
turnState
state
chatType
agentList
```

The observed response action was:

```text
ConversationResponseComplete
```

The conversation was marked as:

```text
turnState: Completed
```

and the response indicated:

```text
isNewChat: true
```

### Conversation Metadata Observed

The response contained conversation-related records with fields including:

```text
conversationId
chatName
createTimeUtc
updateTimeUtc
expiryTimeUtc
plugins
threadLevelGptId
isMessageless
isUnread
retentionPolicyEffect
threadId
isScheduledPromptThread
mostRecentGptIds
hasLoopPages
isLegacyWebChat
hasCopilotTasks
turnState
path
```

These fields indicate that the response provides metadata associated with conversations and their corresponding threads.

### Identifiers Observed

The following identifiers were observed during analysis:

| Identifier | Observation |
|---|---|
| `conversationId` | Identifies the conversation associated with the response |
| `X-Session-Id` | Session identifier supplied in the request header |
| `traceId` | Request/operation tracing identifier returned by the endpoint |
| `threadId` | Identifier associated with an individual conversation thread |

### Observed Relationship

The captured traffic shows a relationship between the authenticated session, the `/chat` request, and conversation resources:

```text
Authenticated Browser Session
          │
          │ X-Session-Id
          ▼
       POST /chat
          │
          │
          ▼
    conversationId
          │
          ▼
       threadId
```

This relationship is documented only as an observation of the captured traffic. It does not by itself demonstrate an authorization weakness.

### Observed Purpose

Based on the captured request and response, `/chat` is involved in **Copilot conversation response processing and conversation state handling**. The response identifies the conversation and returns associated conversation metadata.

### Security Assessment Status

At this stage, no vulnerability is being claimed.

The endpoint has been documented to establish:

- HTTP method and endpoint
- Authentication context
- Session identifier
- Conversation identifier
- Thread identifier
- Response structure
- Conversation metadata
- Conversation state

Further authorization analysis should be based on controlled testing with authorized accounts and resources.

**Assessment status:** `Reconnaissance — Documented`


# POST /events

## Endpoint Overview

**Host:** `m365.cloud.microsoft`  
**Method:** `POST`  
**Path:** `/events`  
**Purpose:** Client-side event/telemetry ingestion associated with the Copilot web application.

## Authentication

The observed requests were made from an authenticated browser session and included:

- Authenticated browser cookies
- `Authorization: Bearer [REDACTED]`
- `X-Session-Id: [REDACTED]`

All authentication material should be redacted from stored evidence.

## Request Characteristics

### Request Headers

Relevant application headers observed include:

```text
Authorization: Bearer [REDACTED]
X-Session-Id: [REDACTED]
X-Host-Context: {"clientPlatform":"web","hostName":"officeweb"}
X-Client-Eligibility: [REDACTED]
Content-Type: application/json
Origin: https://m365.cloud.microsoft
Referer: https://m365.cloud.microsoft/chat/...
```

### Request Body

The request contains an `events` array and a `context` object.

Example event types observed:

```text
InputFocused
IdleTimerStopped
```

The event properties include application telemetry information such as:

```text
eventId
agentExtensionId
chatType
agent
routeId
clientCorrelationId
eventScope
timestamp
level
```

The context contains session/application configuration information including:

```text
sessionId
officeHomeEcsRing
featureFlags
```

The exact captured request body should be preserved separately as evidence with authentication tokens and sensitive identifiers redacted.

## Response

Observed responses:

```http
HTTP/2 200 OK
Content-Type: application/json; charset=utf-8
```

Example response:

```json
{
  "success": true,
  "received": 40
}
```

Another observed response:

```json
{
  "success": true,
  "received": 2
}
```

And:

```json
{
  "success": true,
  "received": 1
}
```

## Observed Behavior

The endpoint accepts batches of client-generated events and returns a successful acknowledgement indicating the number of events received.

The endpoint appears to function primarily as an event/telemetry ingestion mechanism rather than as a conversation-management API.

## Identifiers Observed

The requests contained identifiers such as:

- Session ID
- Client correlation ID
- Trace ID
- Event ID
- Route ID

These identifiers should be treated as evidence/context rather than as proof of an authorization boundary.

## Security-Relevant Observations

No vulnerability is inferred from the observed requests or `200 OK` responses alone.

The following areas may be relevant for authorized security assessment:

1. Whether authentication is consistently enforced.
2. Whether event submission is correctly associated with the authenticated session.
3. Whether server-side validation exists for event/context fields.
4. Whether user-controlled event metadata can influence security-sensitive application state.
5. Whether identifiers accepted by the endpoint provide access to resources belonging to another user.

Any authorization testing should use only accounts and resources that are owned or explicitly authorized for the assessment.

## Assessment Status

**Endpoint discovered:** Yes  
**Authentication observed:** Yes  
**Successful request:** Yes  
**Telemetry/event ingestion confirmed:** Yes  
**Conversation resource directly manipulated:** No  
**Authorization vulnerability identified:** No

## Conclusion

`POST /events` is currently classified as a **telemetry/event ingestion endpoint**. The observed behavior demonstrates successful authenticated event submission but does not, by itself, demonstrate an authorization weakness or security vulnerability.

For the current assessment, this endpoint should be documented and deprioritized unless further testing demonstrates that event data can affect security-sensitive state or cross-user resources.
