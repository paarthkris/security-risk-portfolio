# HarborPay Security Risk Portfolio

HarborPay is a fictional Boston fintech company I created as a learning environment for cybersecurity, GRC, IAM, security monitoring, secure application design, and AI governance.

I am building this portfolio as a Northeastern student who is still developing hands-on experience. The completed documents show how I approach assets, risks, controls, evidence, and business impact. The technical folders show what I have set up, what I have not completed yet, and what I plan to build myself.

This is not a real audit, and none of the fictional findings describe Stripe, Okta, AWS, or any other real company. Simulated evidence and unverified assumptions are labeled throughout the repository.

## Start Here

Read [PROJECT_ROADMAP.md](PROJECT_ROADMAP.md) for the current project status, build order, interview goals, and detailed checklist.

## Suggested Reading

| Reader or goal | Best path |
|---|---|
| One-minute overview | This README, then the [executive summary](02-risk-and-controls/executive-summary.md) |
| GRC or technology-risk review | [Risk register](02-risk-and-controls/risk-register.md), [control mapping](02-risk-and-controls/control-mapping.md), and [vendor review](03-vendor-risk/stripe-pre-assessment.md) |
| Security or technical review | [Wazuh setup notes](05-wazuh-homelab/setup-notes.md), [Java design](06-secure-java-app/), and [local AI design](07-local-ai-grc-assistant/) |
| Current progress and next steps | [Project roadmap](PROJECT_ROADMAP.md) |

## Repository Guide

| Section | Purpose | Current State |
|---|---|---|
| [01 - Company Context](01-company-context/) | HarborPay profile, scope, assumptions, and asset inventory | Documentation complete |
| [02 - Risk and Controls](02-risk-and-controls/) | Risk register, NIST CSF 2.0/CIS Controls mapping, and executive summary | Documentation complete |
| [03 - Vendor Risk](03-vendor-risk/) | Simulated Stripe pre-assessment and evidence request plan | Documentation complete |
| [04 - IAM Investigation](04-iam-investigation/) | Simulated identity case study plus future hands-on lab plan | Tabletop complete; technical lab pending |
| [05 - Wazuh Homelab](05-wazuh-homelab/) | Local SIEM setup evidence and guided investigation plan | Setup complete; investigations pending |
| [06 - Secure Java App](06-secure-java-app/) | Access Request Tracker design and security requirements | Specification complete; code pending |
| [07 - Local AI GRC Assistant](07-local-ai-grc-assistant/) | Local-model architecture, output schema, tests, and human review | Specification complete; build pending |
| [08 - Report Templates](08-report-templates/) | Consistent templates for labs, evidence, and alert triage | Ready to use |
| [Sources](SOURCES.md) | Primary references used across the project | Maintained |

## What This Project Demonstrates

- Translating business systems into specific security risks
- Prioritizing risk with a documented scoring method
- Mapping risks to NIST CSF 2.0 and CIS Controls v8.1
- Defining evidence that could validate a control
- Separating assumptions from verified technical evidence
- Explaining findings in language useful to both technical and business teams
- Planning hands-on work without claiming results before they exist

## Technical Build Path

The hands-on work will be completed in this order:

1. Generate and investigate controlled Wazuh events.
2. Rebuild the IAM scenario with real lab-generated evidence.
3. Build the Java Access Request Tracker.
4. Build the local AI GRC assistant with Ollama-compatible models.
5. Replace templates and sample data with screenshots, commands, logs, tests, and reflections from my own work.

## Honest Status Statement

The documentation foundation and simulated IAM tabletop are complete. I also installed Wazuh locally through Docker and connected my Mac as an endpoint. I have not yet completed the alert investigations, Java application, or local AI assistant. Those are the technical parts I will build and learn step by step.

## Target Roles

This project is designed to support internship and co-op applications in:

- Cybersecurity
- GRC and technology risk
- IAM
- Security operations
- IT audit and risk advisory
- Business technology
- AI governance and AI risk

## Short Explanation

> I built a security risk portfolio around HarborPay, a fictional fintech company. I completed the business context, asset, risk, control, and vendor-risk documentation, then used that foundation to plan hands-on labs in IAM, Wazuh, secure Java development, and local AI governance. I clearly separate simulated analysis from technical work I have personally completed so I can explain every part honestly in an interview.
