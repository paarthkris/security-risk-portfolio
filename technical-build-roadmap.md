# HarborPay Technical Build Roadmap

## Why This Roadmap Exists

The documentation pieces in this project are useful because they create the business and risk context:

- Asset inventory
- Risk register
- Control mapping
- Vendor risk review

But the main focus of this portfolio should be the hands-on technical work.

My goal is to use the documentation as the setup, then build labs and technical artifacts that I can talk about in interviews. I want to show that I understand security risk, but also that I can work with real tools, logs, code, and investigation workflows.

## Main Technical Projects

### 1. Wazuh Security Monitoring Homelab

This will be the first major technical lab.

The goal is to set up Wazuh, collect logs, trigger suspicious activity, review alerts, and write up what happened.

What I want to learn:

- What a SIEM does
- How logs are collected
- What endpoint alerts look like
- How to investigate suspicious activity
- How detection connects back to risk and controls

Possible scenarios:

- Multiple failed login attempts
- New local user created
- Suspicious command execution
- File integrity change
- Endpoint missing from monitoring

Portfolio deliverables:

- `wazuh-homelab-notes.md`
- Screenshots of Wazuh dashboard and alerts
- Short investigation writeups
- Mapping from alerts back to HarborPay risks

Why this helps for interviews:

I can explain how I set up monitoring, generated test events, reviewed alerts, and connected them to business risk.

### 2. IAM / Suspicious Login Investigation Lab

This lab will simulate an identity-related investigation.

The goal is to understand how account takeover and suspicious login activity would be investigated.

Scenario idea:

An employee logs in from Boston, then shortly after there is a suspicious login attempt from another location. The account then tries to access sensitive systems.

What I want to learn:

- How authentication works at a high level
- What login logs show
- Why MFA matters
- What conditional access means
- How to recommend controls after an incident

Portfolio deliverables:

- `iam-investigation-report.md`
- Login timeline
- Evidence table
- Risk and control recommendations

Why this helps for interviews:

I can explain identity risk in a practical way, which is useful for cybersecurity, GRC, IAM, SOC, and technology risk roles.

### 3. Secure Java Application

This connects directly to my Java and object-oriented design learning.

The goal is to build a small HarborPay-style internal app and then analyze its security.

Best app idea:

**Access Request Tracker**

Employees request access to systems like GitHub, AWS, Stripe, or the admin dashboard. Managers or admins approve or deny requests.

Why this app fits the project:

- It connects directly to IAM and least privilege.
- It is realistic for a business/security environment.
- It lets me practice Java, OOP, roles, validation, and logging.
- It connects to the risk register and control mapping.

Security features to include:

- Role-based access control
- Input validation
- Basic logging
- Approval workflow
- User roles like requester, manager, admin, auditor
- Dependency scanning
- OWASP Top 10 review
- Short threat model

Portfolio deliverables:

- Java app source code
- `java-secure-app/README.md`
- `threat-model.md`
- `owasp-review.md`
- Screenshots or demo flow

Why this helps for interviews:

I can show that I understand how access decisions work and how application design can create or reduce risk.

### 4. AI GRC Assistant With n8n

This should come after the first labs and Java app.

The goal is to build a simple AI-supported workflow, likely using n8n, that helps turn an incident, vendor issue, or policy into risks, controls, evidence requests, and recommendations.

What I want to learn:

- How AI can support GRC work
- How n8n can automate a repeatable GRC workflow
- Why human review still matters
- How to structure prompts and outputs
- How to avoid over-trusting AI-generated security advice

Possible use case:

Paste in a short incident summary and have the assistant draft:

- Related assets
- Possible risks
- Control gaps
- Evidence to request
- Recommended next steps
- Human review notes

Portfolio deliverables:

- `ai-grc-assistant/README.md`
- n8n workflow export or screenshot
- Example inputs and outputs
- Human review checklist
- Notes on limitations

Why this helps for interviews:

I can talk about AI governance and practical AI use in security/risk work without pretending AI replaces human judgment.

## Recommended Build Order

### Phase 1: Finish The Setup

Already started:

- Asset inventory
- Risk register
- Control mapping
- Stripe vendor review

Keep these simple. They support the technical work, but they are not the main show.

### Phase 2: Build Wazuh Homelab

This should be the first hands-on technical milestone.

Start simple:

1. Decide whether Wazuh runs locally, in Docker, or in a virtual machine.
2. Install Wazuh.
3. Add one monitored endpoint or test log source.
4. Trigger simple events.
5. Take screenshots.
6. Write investigation notes.

### Phase 3: Build IAM Investigation Lab

Use the HarborPay Okta risk as the story.

Create a fake but realistic investigation:

- Login timeline
- Suspicious behavior
- Evidence review
- Risk explanation
- Recommended controls

### Phase 4: Build Secure Java App

Build the Access Request Tracker.

Start small:

- Users
- Roles
- Access requests
- Approvals
- Logs

Then add security review:

- Threat model
- OWASP review
- Dependency scan

### Phase 5: Build AI GRC Assistant

Use the earlier documentation and lab outputs as sample inputs.

The assistant should help draft security/risk analysis, but the project should clearly show human review.

## What I Should Be Able To Say In Interviews

By the end of this project, I want to be able to say:

> I built a security risk portfolio around a fictional fintech company. I started by identifying critical assets and risks, then built hands-on labs around monitoring, IAM investigation, and secure Java application design. The project helped me understand how technical controls, business risk, and evidence collection connect in real security work.

More specific talking points:

- I used Wazuh to learn how endpoint monitoring and alert review work.
- I created an IAM investigation scenario to practice suspicious login analysis.
- I built a Java access request app to connect OOP concepts with least privilege and RBAC.
- I mapped technical findings back to risks, controls, and business impact.
- I explored how AI can support GRC work while still requiring human review.

## Immediate Next Step

Move into the Wazuh homelab.

Before installing anything, create a simple lab plan:

- What machine will run Wazuh?
- What endpoint or logs will be monitored?
- What events will be tested?
- What screenshots should be captured?
- What final writeup should be created?
