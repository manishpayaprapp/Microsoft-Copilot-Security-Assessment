# Subdomain Enumeration

## 1. Objective

The objective of this reconnaissance phase was to identify publicly discoverable subdomains associated with the authorized Microsoft 365 target domain.

Subdomain enumeration was performed to establish an initial attack-surface inventory before proceeding with live-host validation, application/API reconnaissance, authorization testing, and WebSocket analysis.

---

## 2. Target

**Root Domain:**

```text
m365.cloud.microsoft
```

**Assessment:** Microsoft Copilot Security Assessment

**Assessment Type:** Authorized security research / bug bounty testing

---

## 3. Tool Information

| Property | Details |
|---|---|
| Tool | Subfinder |
| Version | v2.16.0 |
| Provider | ProjectDiscovery |
| Purpose | Passive subdomain enumeration |
| Target | `m365.cloud.microsoft` |

---

## 4. Command Used

```bash
subfinder -d m365.cloud.microsoft/
```

---

## 5. Command Output

```text
[INF] Current subfinder version v2.16.0 (latest)
[INF] Loading provider config from /home/manish/.config/subfinder/provider-config.yaml
[INF] Enumerating subdomains for m365.cloud.microsoft
assets.offer.m365.cloud.microsoft
chat.svc.m365.cloud.microsoft
connectivity.m365.cloud.microsoft
df.workforceinsights.m365.cloud.microsoft
endpoints.m365.cloud.microsoft
workforceinsights.m365.cloud.microsoft
scuprodprv.m365.cloud.microsoft
connectivity-ppe.m365.cloud.microsoft
offer.m365.cloud.microsoft
signup.m365.cloud.microsoft
df.knowyourteam.m365.cloud.microsoft
[INF] Found 11 subdomains for m365.cloud.microsoft in 2 minutes 13 seconds
```

---

## 6. Discovered Subdomains

Subfinder identified **11 subdomains**:

| # | Discovered Subdomain |
|---:|---|
| 1 | `assets.offer.m365.cloud.microsoft` |
| 2 | `chat.svc.m365.cloud.microsoft` |
| 3 | `connectivity.m365.cloud.microsoft` |
| 4 | `df.workforceinsights.m365.cloud.microsoft` |
| 5 | `endpoints.m365.cloud.microsoft` |
| 6 | `workforceinsights.m365.cloud.microsoft` |
| 7 | `scuprodprv.m365.cloud.microsoft` |
| 8 | `connectivity-ppe.m365.cloud.microsoft` |
| 9 | `offer.m365.cloud.microsoft` |
| 10 | `signup.m365.cloud.microsoft` |
| 11 | `df.knowyourteam.m365.cloud.microsoft` |

---

## 7. Relevant Host

Because this assessment focuses on Microsoft Copilot application and API security, the following hostname was prioritized for further reconnaissance:

```text
chat.svc.m365.cloud.microsoft
```

The hostname appears relevant to chat-related functionality. This prioritization does not indicate that the host is vulnerable.

---

## 8. Reconnaissance Workflow

```text
Target Domain
     |
     v
m365.cloud.microsoft
     |
     v
Subfinder
     |
     v
Subdomain Enumeration
     |
     v
11 Discovered Hosts
     |
     v
HTTP Validation
     |
     v
httpx
```

---

## 9. Next Phase

The discovered subdomains were passed to `httpx` for live-host validation and basic technology identification.

The next phase is documented in:

```text
reconnaissance/live-host-discovery.md
```

---

## 10. Evidence

Recommended screenshot:

```text
screenshots/subfinder-m365-enumeration.png
```

The screenshot should include:

- Subfinder version
- Target domain
- Executed command
- Discovered subdomains
- Final count
- Enumeration duration

---

## 11. Result

**Status:** Completed

Subfinder v2.16.0 identified:

```text
11 subdomains
```

for:

```text
m365.cloud.microsoft
```

The discovered hosts established the initial externally visible attack-surface inventory and were used as input for the subsequent live-host validation phase.

---

## 12. Security Conclusion

Subdomain enumeration is a reconnaissance activity and does not by itself demonstrate a security vulnerability.

The identified hosts were retained for authorized follow-up analysis based on their relevance to the assessment scope.
