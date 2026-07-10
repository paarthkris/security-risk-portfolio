# HarborPay Security Portfolio: Next Hands-On Phase

## Why This Phase Matters

The first part of the project was mostly setup:

- Wazuh is running in Docker.
- The Mac endpoint is connected as `harborpay-macbook-01`.
- Wazuh is collecting system inventory.
- MITRE ATT&CK mappings appeared during setup activity.
- Screenshots and lab notes were saved.

That setup matters, but it is not the most interesting part of the project.

The next phase should make the project feel more real by creating a HarborPay incident story that I can investigate, explain, and connect to business risk.

## Main Idea

Instead of only clicking around the Wazuh dashboard, I want to simulate realistic HarborPay security events and use Wazuh as the monitoring/investigation tool.

The goal is to be able to say:

> I configured a Wazuh homelab, connected an endpoint, created simulated HarborPay security events, reviewed the results, and wrote investigation notes that connected endpoint activity to IAM, admin access, and business risk.

## Recommended Next Project Direction

### 1. Custom HarborPay Security Log

Create a fake company security log file, such as:

```text
/var/log/harborpay-security.log
```

This log can include realistic events like:

- Suspicious login attempt
- Failed MFA
- Admin dashboard access denied
- Sudo/admin command used
- Sensitive file modified
- Vendor outage note
- New user created

Example log lines:

```text
2026-07-10T09:15:22Z user=maya.chen event=failed_mfa source=unknown_location asset=Okta risk=possible_account_takeover
2026-07-10T09:18:47Z user=maya.chen event=admin_dashboard_access_denied asset=AdminDashboard reason=unauthorized_role
2026-07-10T09:25:03Z user=it.admin event=sudo_command endpoint=harborpay-macbook-01 command="sudo whoami"
```

### 2. Configure Wazuh To Monitor That Log

Tell Wazuh to watch the custom HarborPay log file.

This is more interesting than only relying on default Mac logs because I can control the scenario and explain exactly what Wazuh is seeing.

What I want to learn:

- How custom log collection works
- How Wazuh reads local log files
- How security events become searchable
- How to turn logs into investigation notes

### 3. Build A Mini Incident Scenario

Scenario:

> A HarborPay customer operations employee has suspicious identity activity. The account fails MFA from an unusual location and later attempts to access the Admin Dashboard without the right role.

Related assets:

- Okta
- Admin Dashboard
- Wazuh
- Employee MacBook

Related risks:

- Okta account takeover
- Excessive admin access
- Poor logging or alert review

### 4. Write A Wazuh Mini-Incident Report

Create a short report with:

- What happened
- Timeline of events
- Evidence reviewed
- Why it mattered
- MITRE ATT&CK mapping if relevant
- Business impact
- Recommended controls

Possible file:

```text
wazuh-mini-incident-report.md
```

### 5. Feed The Incident Into The n8n AI GRC Workflow

Later, use the incident summary as input for the AI GRC assistant.

The workflow should turn the incident into:

- Related assets
- Risks
- Control gaps
- Evidence requests
- Recommendations
- Human review notes

This connects Wazuh, IAM, GRC, and AI into one portfolio story.

## Why This Is More Interesting

This phase gives the lab a story.

Instead of saying:

> I installed Wazuh and clicked around.

I can say:

> I built a simulated security monitoring workflow for a fictional fintech company. I created custom identity and admin-access events, ingested them into Wazuh, reviewed the endpoint context, and wrote an investigation report with risk and control recommendations.

That sounds much more like real security work.

## Project Flow From Here

1. Finish Wazuh setup notes.
2. Create a custom HarborPay security log.
3. Configure Wazuh to monitor it.
4. Generate fake suspicious events.
5. Find/review events in Wazuh.
6. Screenshot the useful views.
7. Write the mini incident report.
8. Feed the report into the n8n AI GRC assistant.
9. Move into the secure Java Access Request Tracker.

## Secure Java App Connection

After the Wazuh mini-incident, the next technical build should be the Java app.

Best app idea:

**HarborPay Access Request Tracker**

The app should include:

- Users
- Roles
- Access requests
- Manager approvals
- Admin approvals
- Audit logs
- Basic input validation
- Role-based access control

This connects directly to the Wazuh/IAM story because the incident involved access control and admin dashboard access.

## n8n AI GRC Layer

The n8n workflow should come after the first incident report exists.

First workflow idea:

**Incident Summary to GRC Risk Note**

Input:

```text
A HarborPay employee had a failed MFA attempt from an unusual location and later attempted to access the Admin Dashboard without the proper role.
```

Output:

- Related assets: Okta, Admin Dashboard, Wazuh
- Risk: possible account takeover or access misuse
- Controls: MFA, conditional access, RBAC, access reviews, alerting
- Evidence: sign-in logs, MFA logs, dashboard access logs, user role list
- Recommendations: review session, reset password if needed, review admin access, tune alerts
- Human review: required

## Interview Talking Point

I would explain the next phase like this:

> After setting up Wazuh, I wanted the lab to be more than just a dashboard. I created a simulated HarborPay security incident involving suspicious identity activity and admin dashboard access. I used Wazuh to support the investigation, documented the evidence, and connected the findings back to IAM controls, least privilege, and business risk.

## Tomorrow's Starting Point

Start with:

1. Restart Docker and Wazuh.
2. Confirm `harborpay-macbook-01` is active.
3. Create the custom HarborPay log file.
4. Configure Wazuh to monitor it.
5. Generate the first fake suspicious event.

