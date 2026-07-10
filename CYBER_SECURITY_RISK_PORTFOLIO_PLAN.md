# Security Risk Portfolio Project Plan

## Project Name

**HarborPay Security Risk Portfolio**

## Simple Version

We are building a realistic cybersecurity and GRC portfolio around a fake company called **HarborPay**, a Boston-based fintech startup.

The goal is not to become a hardcore security engineer overnight. The goal is to become a strong **technical security risk candidate** who can:

- Understand basic systems, identity, logs, and cloud tools
- Explain business and security risk clearly
- Build simple technical demos
- Map risks to real frameworks like NIST CSF and CIS Controls
- Talk confidently in interviews about how security teams think

This project should become something you can put on:

- GitHub
- LinkedIn
- Resume
- Internship and co-op applications

## Target Role Fit

This project is designed for roles like:

- Cybersecurity intern
- GRC intern
- Technology risk intern
- IT audit intern
- Security operations intern
- IAM intern
- Risk advisory intern
- Business technology intern
- AI governance or AI risk intern

It is not mainly focused on software engineering roles, although it will include some coding through a secure Java app.

## Fictional Company: HarborPay

**HarborPay** is a fictional Boston fintech company with about 120 employees.

It helps small businesses accept payments, manage invoices, and view customer transaction data.

### Why This Company Works Well

Fintech is a strong project setting because it naturally includes:

- Customer data
- Payment data
- Vendors
- Cloud infrastructure
- Employee accounts
- Compliance pressure
- Security monitoring
- Business risk

That gives us enough realism to create a portfolio that feels professional without needing access to a real company.

## Main Project Sections

### 1. Asset Inventory

This is the starting point.

An asset inventory is a list of the important things a company uses and needs to protect.

For HarborPay, example assets include:

| Asset | What It Is | Why It Matters |
|---|---|---|
| Google Workspace | Email, docs, files | Stores company communication and documents |
| Okta | Login and identity system | Controls employee access |
| AWS | Cloud infrastructure | Hosts company systems and data |
| GitHub | Code storage | Contains application code |
| Slack | Team messaging | May contain sensitive internal conversations |
| Stripe | Payment processor | Handles payment activity |
| Jira | Project tracking | Shows internal engineering and business work |
| Customer Database | Customer and payment-related records | High-value sensitive data |
| Employee MacBooks | Work laptops | Used to access company systems |
| Vendor List | Third-party tools and partners | Creates vendor risk |
| Wazuh | Security monitoring tool | Collects logs and alerts |
| ChatGPT/Codex | AI tools used by employees | Creates data handling and AI governance questions |

### 2. Risk Register

A risk register is a table of possible security or business risks.

Each risk should explain:

- What could go wrong
- Why it matters
- How likely it is
- How bad the impact would be
- What controls reduce the risk
- Who owns the risk

Example risks:

| Risk | Example |
|---|---|
| Weak MFA enforcement | Employees may access systems without strong login protection |
| Phishing | An employee could give away credentials |
| Over-permissioned accounts | People may have more access than they need |
| Vendor breach | A third-party tool could expose company data |
| Poor logging | Suspicious activity may go unnoticed |
| AI data leakage | Employees may paste sensitive company data into AI tools |
| Insecure Java app | Poor validation or access control could expose data |

### 3. NIST CSF and CIS Controls Mapping

This section connects the risks to real cybersecurity frameworks.

The goal is to show that you can translate real-world problems into professional security language.

Examples:

| Risk | NIST CSF Area | CIS Control |
|---|---|---|
| Weak MFA | Protect | Account Management / Access Control |
| Poor logging | Detect | Audit Log Management |
| Vendor breach | Identify / Protect | Service Provider Management |
| Phishing | Protect | Security Awareness and Skills Training |
| Insecure app | Protect | Application Software Security |

### 4. Vendor Risk Questionnaire

This section simulates reviewing a vendor before HarborPay uses it.

Example vendor: a fake AI note-taking tool or payments analytics vendor.

Questions to include:

- What data does the vendor collect?
- Does the vendor support MFA?
- Does the vendor encrypt data?
- Does the vendor have SOC 2 or ISO 27001?
- Where is customer data stored?
- How does the vendor handle incidents?
- Can HarborPay delete its data?
- Does the vendor train AI models on customer data?

### 5. IAM Investigation Lab

IAM means Identity and Access Management.

This lab will show that you understand logins, accounts, suspicious access, and recommended controls.

Scenario idea:

An employee account logs in from Boston at 9:00 AM, then from another country 20 minutes later. The account then tries to access a sensitive finance system.

You will document:

- Normal login flow
- Suspicious login timeline
- What logs would matter
- What risks exist
- What controls should be added
- What you would tell a manager

Controls could include:

- MFA
- Conditional access
- Stronger password policy
- Login alerts
- Device trust
- Least privilege access
- Account lockout rules

### 6. Wazuh Homelab

A homelab is a practice environment you build yourself.

For this project, the homelab will use **Wazuh**, a security monitoring tool. Wazuh works like a beginner-friendly SIEM, meaning it collects logs and helps detect suspicious activity.

Beginner version:

- Install Wazuh locally or in a small virtual environment
- Add one test machine or log source
- Generate simple suspicious activity
- Capture alerts
- Write what happened in plain English

Possible suspicious activity examples:

- Failed login attempts
- New user created
- Suspicious command run
- File integrity change
- Unusual admin activity

Advanced later version:

- Add Suricata as a network IDS
- Use Emerging Threats rules
- Add cloud logs
- Build dashboards
- Map alerts to MITRE ATT&CK

### 7. Secure Java App

This ties directly into your Java and object-oriented design learning.

Build a simple Java app for HarborPay, such as:

- Internal employee access request tracker
- Vendor risk review tracker
- Customer support case viewer
- Simple admin portal demo

Security features to include:

- Role-based access control
- Input validation
- Logging
- Basic error handling
- Dependency scanning
- OWASP Top 10 review
- Short threat model

The point is not to build a perfect production app. The point is to show that you understand how code creates security risk.

### 8. AI GRC Assistant

This section shows your interest in AI and security risk.

Build a small AI-assisted workflow that can take a policy, incident, or vendor description and produce:

- Possible risks
- Relevant controls
- Evidence requests
- Questions for a human reviewer
- Draft recommendations

Important: the project should clearly say that AI output is reviewed by a human.

This positions you well for AI governance, GRC, and technology risk roles.

## First Brainstorm: HarborPay Asset Inventory

We should start by creating a simple asset inventory.

Possible categories:

- Identity and access
- Cloud systems
- Employee devices
- Communication tools
- Code and development tools
- Payment and customer systems
- Vendors
- AI tools
- Security tools

First draft assets:

| Category | Asset | Owner | Data Sensitivity | Notes |
|---|---|---|---|---|
| Identity | Okta | IT/Security | High | Main login system |
| Communication | Google Workspace | IT | Medium/High | Email, docs, shared files |
| Communication | Slack | Operations | Medium | Internal messages |
| Cloud | AWS | Engineering | High | Hosts application systems |
| Code | GitHub | Engineering | High | Source code and secrets risk |
| Payments | Stripe | Finance/Product | High | Payment-related processing |
| Data | Customer Database | Engineering | High | Customer and account data |
| Devices | Employee MacBooks | IT | Medium/High | Endpoint security concern |
| Security | Wazuh | Security | Medium | Log monitoring |
| AI | ChatGPT/Codex | Employees | Medium/High | AI data handling risk |
| Vendor | Jira | Engineering/Product | Medium | Project and issue tracking |
| Vendor | Vendor Spreadsheet | GRC/Operations | Medium | Tracks third-party tools |

## What We Should Build First

### Step 1: Create the Asset Inventory

Deliverable:

- `asset-inventory.md`
- Optional spreadsheet-style table

Goal:

Understand what HarborPay has before deciding what can go wrong.

### Step 2: Create the Risk Register

Deliverable:

- `risk-register.md`

Goal:

Turn the asset list into realistic risks.

### Step 3: Map Risks to Controls

Deliverable:

- `control-mapping.md`

Goal:

Connect each risk to NIST CSF and CIS Controls.

### Step 4: Build the Wazuh Homelab

Deliverable:

- `wazuh-homelab-notes.md`
- Screenshots
- Alert writeups

Goal:

Show hands-on security monitoring experience.

### Step 5: Add IAM Investigation Scenario

Deliverable:

- `iam-investigation-report.md`

Goal:

Show that you can investigate suspicious access and explain it clearly.

### Step 6: Build Secure Java App

Deliverable:

- Java app folder
- `threat-model.md`
- `owasp-review.md`

Goal:

Connect coursework to practical security concepts.

### Step 7: Add AI GRC Assistant

Deliverable:

- `ai-grc-assistant.md`
- Simple prototype or workflow

Goal:

Show AI-aware GRC thinking and human review.

## GitHub Repo Structure

Suggested layout:

```text
security-risk-portfolio/
  README.md
  docs/
    asset-inventory.md
    risk-register.md
    control-mapping.md
    vendor-risk-questionnaire.md
    iam-investigation-report.md
    wazuh-homelab-notes.md
    executive-summary.md
  java-secure-app/
    README.md
    src/
    threat-model.md
    owasp-review.md
  ai-grc-assistant/
    README.md
    examples/
  screenshots/
    wazuh/
    diagrams/
```

## Resume Bullet Drafts

Early version:

- Built a cybersecurity and GRC portfolio for a fictional fintech company, including asset inventory, risk register, control mapping, vendor risk review, and executive reporting.

Stronger version after Wazuh:

- Built a Wazuh-based security monitoring homelab to simulate suspicious login activity, review alerts, document risks, and recommend IAM and logging controls.

Stronger version after Java app:

- Developed a secure Java application prototype with role-based access control, input validation, logging, dependency scanning, OWASP Top 10 review, and a written threat model.

Stronger version after AI assistant:

- Created an AI-assisted GRC workflow that maps incidents and vendor findings to risks, controls, evidence requests, and human-reviewed recommendations.

## LinkedIn Post Draft

I am building a cybersecurity and GRC portfolio around a fictional fintech company called HarborPay.

The project includes asset inventory, risk register development, NIST CSF/CIS Controls mapping, vendor risk review, IAM investigation scenarios, a Wazuh security monitoring homelab, and a secure Java application tied to my coursework.

My goal is to develop practical experience at the intersection of cybersecurity, technology risk, business systems, and AI governance.

## Brainstorm Questions

These are the questions we should answer next:

1. What exact HarborPay assets should we include in the first asset inventory?
2. Should HarborPay be more like a payments startup, a banking app, or a B2B fintech tool?
3. Which risks should be the first 10 risks in the risk register?
4. Should the Wazuh homelab run locally on your Mac, inside Docker, or in a virtual machine?
5. What should the Java app be: access request tracker, vendor risk tracker, or admin portal?
6. Should the AI GRC assistant be a simple prompt workflow first, or a small app later?

## Immediate Next Move

Start with the asset inventory.

The first mini-goal is:

> Create a clean list of HarborPay's important systems, who owns them, what data they touch, and how risky they are.

Once that exists, the risk register becomes much easier.

