1. www.solarwinds.com

Type: Public Website
Category: Marketing / Product Platform

Observed URLs:

/blog, /events, /campaign, /service-desk, /sql-sentry, etc.

Description:

Main corporate website
Hosts product info, campaigns, blog content

Security Relevance:
🟢 Low — mostly static/public content
🟡 Medium if forms or tracking endpoints are present

🌐 2. sw.solarwinds.com

Type: Redirect / Short Domain
Category: Likely Marketing or Link Shortener

Description:

Likely used for shortened links or campaign redirects

Security Relevance:
🟡 Medium — test for:

Open redirect vulnerabilities
سوء URL validation
🔐 3. customerportal.solarwinds.com

Type: Login Portal
Category: Customer Account Management

Description:

Customer portal for managing licenses, support, downloads

Security Relevance:
🔴 High — authentication surface:

Session management
Account access controls
MFA enforcement
🔐 4. swo.cloud.solarwinds.com

Type: Login Portal (Cloud Service)
Category: SaaS Authentication (OAuth/OpenID)

Description:

Cloud observability login endpoint
Uses OAuth parameters (client_id, redirect_uri, scope)

Security Relevance:
🔴 High — test for:

OAuth misconfiguration
Token leakage
Redirect URI abuse
🔐 5. hco.demo.solarwinds.com

Type: Demo Environment
Category: Test / Demonstration Instance

Description:

Orion platform demo login page

Security Relevance:
🔴 High — demo environments often:

Use weak credentials
Contain outdated software
Leak internal structure
🧪 6. webdevadmin.solarwinds.com

Type: Development / Admin Environment
Category: Internal / Staging (likely)

Description:

Suggests admin interface for web development systems

Security Relevance:
🚨 Critical target:

Potential misconfiguration
Default credentials
Exposed admin panels
🔗 7. referrer.solarwinds.com

Type: Redirect / Tracking Service
Category: Marketing / Analytics

Description:

Likely handles referral tracking or redirects

Security Relevance:
🔴 High — common issues:

Open redirects
Header injection
SSRF (in rare cases)
🧑‍💻 8. thwack.solarwinds.com

Type: Community Platform
Category: User Forum / Knowledge Base

Description:

Official SolarWinds community (THWACK)

Security Relevance:
🟡 Medium:

User-generated content
Possible XSS or injection vectors
🧑‍💻 9. thwackfeeds.solarwinds.com

Type: Feed Service
Category: Content Syndication / API-like

Description:

Likely RSS or feed backend for THWACK

Security Relevance:
🟡 Medium:

Data exposure
API misconfigurations
🛠 10. support.solarwinds.com

Type: Support Portal
Category: Helpdesk / Ticketing

Description:

Customer support system

Security Relevance:
🔴 High:

Contains user data
Ticket-based access controls
Possible IDOR vulnerabilities
💼 11. jobs.solarwinds.com

Type: Third-Party / Recruitment Portal
Category: Careers Platform

Description:

Job listings and application system

Security Relevance:
🟡 Medium:

Often integrated with third-party HR platforms
Possible data exposure via forms
📥 12. downloads.solarwinds.com

Type: File Distribution Server
Category: Software Delivery

Description:

Hosts downloadable binaries (e.g., Dameware tools)

Security Relevance:
🔴 High:

Version disclosure
Potential supply chain implications
File integrity validation (hash/signature)
☁️ 13. my.na-01.cloud.solarwinds.com (via redirect URI)

Type: Cloud Service Endpoint
Category: SaaS Backend

Description:

Region-specific cloud tenant endpoint

Security Relevance:
🔴 High:

Token handling
Tenant isolation issues
📊 Overall Risk Prioritization
🔴 High Priority Targets
webdevadmin.solarwinds.com
customerportal.solarwinds.com
swo.cloud.solarwinds.com
support.solarwinds.com
downloads.solarwinds.com
hco.demo.solarwinds.com
referrer.solarwinds.com
🟡 Medium Priority
thwack.solarwinds.com
thwackfeeds.solarwinds.com
jobs.solarwinds.com
sw.solarwinds.com
🟢 Low Priority
www.solarwinds.com
🧠 Key Takeaways
Multiple authentication surfaces → strong focus for testing
Presence of dev/demo environments → potential weak points
Redirect + OAuth flows → high-value vulnerability targets
Download infrastructure → relevant for supply chain analysis
