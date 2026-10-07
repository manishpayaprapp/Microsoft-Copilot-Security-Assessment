# Practical Reconnaissance

## Subfinder

```text
$ subfinder -d m365.cloud.microsoft/
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

## HTTPX

```text
$ echo "m365.cloud.microsoft" | subfinder -silent | httpx -silent -status-code -title -tech-detect

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

These are the captured outputs supplied for the assessment.
