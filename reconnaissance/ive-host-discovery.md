# Live Host Discovery and Technology Identification

## 1. Objective

The objective of this phase was to validate the subdomains identified during reconnaissance and determine which hosts responded over HTTP/HTTPS.

The assessment also collected:

- HTTP status codes
- Page titles
- Technologies detected from HTTP responses
- Redirect behavior
- Responsive services

This information was used to prioritize hosts for subsequent application and API reconnaissance.

---

## 2. Target

**Root Domain:**

```text
m365.cloud.microsoft
```

**Assessment:** Microsoft Copilot Security Assessment

**Assessment Type:** Authorized security research / bug bounty testing

---

## 3. Tools Used

### Subfinder

**Version:** v2.16.0

**Purpose:** Subdomain enumeration.

### httpx

**Purpose:** HTTP/HTTPS validation, status-code collection, page-title collection, and basic technology fingerprinting.

---

## 4. Command Used

```bash
echo "m365.cloud.microsoft" | subfinder -silent | httpx -silent -status-code -title -tech-detect
```

---

## 5. Command Workflow

```text
m365.cloud.microsoft
        |
        v
    Subfinder
        |
        v
Discovered Subdomains
        |
        v
      httpx
        |
        +----------------------+
        |          |           |
        v          v           v
     Status     Title     Technology
      Code
```

---

## 6. Raw Command Output

```text
https://chat.svc.m365.cloud.microsoft [302] [Azure,Azure Front Door,Microsoft ASP.NET]
https://connectivity-ppe.m365.cloud.microsoft [200] [Microsoft 365 network connectivity test] [Azure,Azure Monitor,HSTS,Microsoft ASP.NET]
https://connectivity.m365.cloud.microsoft [200] [Microsoft 365 network connectivity test] [Azure,Azure Monitor,HSTS,Microsoft ASP.NET]
https://endpoints.m365.cloud.microsoft [200] [HSTS,Microsoft ASP.NET]
https://assets.offer.m365.cloud.microsoft [404] [Page not found] [Azure,Azure Front Door]
https://df.knowyourteam.m365.cloud.microsoft [404] [Page not found] [Azure,Azure Front Door]
https://df.workforceinsights.m365.cloud.microsoft [200] [Workforce Insights] [Azure,Azure Front Door,HSTS]
https://workforceinsights.m365.cloud.microsoft [200] [Workforce Insights] [Azure,Azure Front Door,HSTS]
https://offer.m365.cloud.microsoft [200] [Microsoft 365] [Azure,Azure Front Door,Azure Monitor,HSTS]
https://scuprodprv.m365.cloud.microsoft [302] [HSTS]
```

---

## 7. Live Host Results

| # | Host | HTTP Status | Page Title | Technologies |
|---:|---|---:|---|---|
| 1 | `chat.svc.m365.cloud.microsoft` | 302 | — | Azure, Azure Front Door, Microsoft ASP.NET |
| 2 | `connectivity-ppe.m365.cloud.microsoft` | 200 | Microsoft 365 network connectivity test | Azure, Azure Monitor, HSTS, Microsoft ASP.NET |
| 3 | `connectivity.m365.cloud.microsoft` | 200 | Microsoft 365 network connectivity test | Azure, Azure Monitor, HSTS, Microsoft ASP.NET |
| 4 | `endpoints.m365.cloud.microsoft` | 200 | — | HSTS, Microsoft ASP.NET |
| 5 | `assets.offer.m365.cloud.microsoft` | 404 | Page not found | Azure, Azure Front Door |
| 6 | `df.knowyourteam.m365.cloud.microsoft` | 404 | Page not found | Azure, Azure Front Door |
| 7 | `df.workforceinsights.m365.cloud.microsoft` | 200 | Workforce Insights | Azure, Azure Front Door, HSTS |
| 8 | `workforceinsights.m365.cloud.microsoft` | 200 | Workforce Insights | Azure, Azure Front Door, HSTS |
| 9 | `offer.m365.cloud.microsoft` | 200 | Microsoft 365 | Azure, Azure Front Door, Azure Monitor, HSTS |
| 10 | `scuprodprv.m365.cloud.microsoft` | 302 | — | HSTS |

---

## 8. HTTP Status Analysis

### HTTP 200

The following hosts returned HTTP 200:

```text
connectivity-ppe.m365.cloud.microsoft
connectivity.m365.cloud.microsoft
endpoints.m365.cloud.microsoft
df.workforceinsights.m365.cloud.microsoft
workforceinsights.m365.cloud.microsoft
offer.m365.cloud.microsoft
```

These hosts were retained in the live-host inventory.

### HTTP 302

The following hosts returned HTTP 302:

```text
chat.svc.m365.cloud.microsoft
scuprodprv.m365.cloud.microsoft
```

HTTP 302 indicates redirect behavior. A redirect by itself does not represent a vulnerability.

### HTTP 404

The following hosts returned HTTP 404:

```text
assets.offer.m365.cloud.microsoft
df.knowyourteam.m365.cloud.microsoft
```

HTTP 404 indicates that the requested resource was not found at the tested location. The response itself was not treated as a vulnerability.

---

## 9. Technology Fingerprinting

The scan identified the following technologies and infrastructure components:

```text
Azure
Azure Front Door
Azure Monitor
Microsoft ASP.NET
HSTS
```

These observations are informational and do not independently establish a vulnerability.

---

## 10. Host Prioritization

The following host was prioritized for further Copilot-focused reconnaissance:

```text
chat.svc.m365.cloud.microsoft
```

### Reason

The hostname contains `chat.svc` and therefore appears potentially relevant to chat-related application functionality.

The service returned:

```text
HTTP 302
```

with technology fingerprints including:

```text
Azure
Azure Front Door
Microsoft ASP.NET
```

This does not establish that the host is vulnerable. It identifies the host as a candidate for further authorized application/API analysis.

---

## 11. Reconnaissance Workflow

```text
Subdomain Enumeration
        |
        v
     Subfinder
        |
        v
Live Host Discovery
        |
        v
       httpx
        |
        v
Technology Identification
        |
        v
Host Prioritization
        |
        v
Application/API Reconnaissance
        |
        v
Authorization Testing
        |
        v
WebSocket Analysis
```

---

## 12. Evidence

Recommended screenshot:

```text
screenshots/subfinder-httpx-m365.png
```

The screenshot should clearly show:

- Executed command
- Subfinder output being piped into httpx
- HTTP status codes
- Page titles
- Technology detection results

---

## 13. Result

**Status:** Completed

The Subfinder + httpx workflow successfully:

- Enumerated target subdomains.
- Validated HTTP/HTTPS responses.
- Identified responsive services.
- Recorded HTTP status codes.
- Collected available page titles.
- Performed basic technology fingerprinting.
- Identified `chat.svc.m365.cloud.microsoft` as a relevant candidate for subsequent Copilot-focused application/API reconnaissance.

---

## 14. Security Conclusion

No vulnerability is claimed from the live-host discovery or technology fingerprinting results alone.

The purpose of this phase was to establish and prioritize the externally observable application attack surface.

The resulting host inventory was used to guide subsequent authorized API, authentication, authorization, and WebSocket analysis.
