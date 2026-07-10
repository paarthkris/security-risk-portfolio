# HarborPay Control Mapping

## Overview

This document maps HarborPay's first 10 cybersecurity risks to practical controls, NIST Cybersecurity Framework categories, and CIS Controls themes.

I created this control map to understand how security risks connect to real control areas. The risk register explains what could go wrong. This file explains what HarborPay should check, improve, or collect as evidence.

The goal is to practice how a security or GRC team can move from:

1. Asset inventory
2. Risk register
3. Control mapping
4. Evidence review
5. Recommendations

This is a key part of the portfolio because it shows that risks are not just theoretical. Each risk should connect to a control that can be reviewed, improved, and explained to the business.

## My Assumptions

- I am using NIST CSF and CIS Controls as learning references, not claiming this is a full compliance assessment.
- I am mapping at a practical level first, so I can understand the purpose of each control before going deeper.
- I am focusing on evidence because GRC work often comes down to proving that a control exists and works.
- I expect to update this file as I learn more about Wazuh, IAM, Java security, and vendor risk.

## How To Read This

- **Risk ID** connects back to the risk register.
- **Control Objective** explains the security goal in plain English.
- **NIST CSF Mapping** connects the risk to a professional framework.
- **CIS Controls Theme** connects the risk to common security control areas.
- **Evidence To Collect** lists what an auditor, GRC analyst, or security team would ask for.
- **Recommended Improvement** explains what HarborPay should do next.

## Control Map

| Risk ID | Related Asset | Control Objective | NIST CSF Mapping | CIS Controls Theme | Evidence To Collect | Recommended Improvement |
|---|---|---|---|---|---|---|
| HP-RISK-001 | Okta | Ensure only approved users can access company systems using strong authentication. | PR.AA: Identity Management, Authentication, and Access Control; DE.CM: Continuous Monitoring | Account Management; Access Control Management | User list, MFA enrollment report, admin role list, sign-in logs, access review records | Review MFA settings, reduce admin access, add conditional access rules, and perform quarterly access reviews. |
| HP-RISK-002 | Google Workspace | Protect sensitive company documents, email, and shared files from unauthorized access or accidental exposure. | PR.DS: Data Security; PR.AT: Awareness and Training; DE.CM: Continuous Monitoring | Data Protection; Email and Web Browser Protections; Security Awareness Training | External sharing report, shared drive permissions, mailbox audit logs, phishing training records | Review external sharing, create sensitive data handling rules, and train employees on phishing and file sharing risk. |
| HP-RISK-003 | AWS Account | Protect cloud infrastructure from misconfiguration, excessive permissions, and unauthorized changes. | PR.AA: Identity and Access Control; PR.DS: Data Security; DE.CM: Continuous Monitoring | Cloud Security; Account Management; Audit Log Management | IAM policy report, CloudTrail logs, security group rules, public resource scan, encryption settings | Review IAM policies, remove overly broad permissions, check public exposure, and monitor cloud configuration changes. |
| HP-RISK-004 | Customer Database | Restrict access to customer data and ensure sensitive records are encrypted, monitored, and backed up. | PR.DS: Data Security; PR.AA: Identity and Access Control; DE.CM: Continuous Monitoring | Data Protection; Access Control Management; Audit Log Management | Database access list, database audit logs, encryption settings, backup records, retention policy | Create a formal database access review, validate encryption, monitor unusual queries, and document retention requirements. |
| HP-RISK-005 | HarborPay Web App | Reduce web application security weaknesses before they affect customers or expose data. | PR.PS: Platform Security; PR.DS: Data Security; DE.CM: Continuous Monitoring | Application Software Security; Vulnerability Management | Vulnerability scan results, dependency report, authentication design, application logs, secure coding review | Perform OWASP Top 10 review, add threat modeling, scan dependencies, and document secure coding practices. |
| HP-RISK-006 | Admin Dashboard | Ensure internal users only have the admin permissions they need and that sensitive actions are logged. | PR.AA: Identity and Access Control; GV.RR: Roles and Responsibilities; DE.CM: Continuous Monitoring | Access Control Management; Account Management; Audit Log Management | Admin user list, role matrix, activity logs, approval records, access review evidence | Create a role matrix, require approval for admin access, review admin actions, and remove unnecessary privileges. |
| HP-RISK-007 | GitHub Repositories | Protect source code and development workflows from unauthorized access, leaked secrets, and insecure changes. | PR.PS: Platform Security; PR.DS: Data Security; DE.CM: Continuous Monitoring | Application Software Security; Account Management; Vulnerability Management | Repo access list, branch protection settings, secret scanning alerts, dependency alerts, pull request history | Enforce branch protection, require code review, review secret scanning alerts, and track dependency fixes. |
| HP-RISK-008 | Employee MacBooks | Ensure employee laptops are encrypted, patched, monitored, and recoverable if lost or compromised. | PR.PS: Platform Security; PR.DS: Data Security; DE.CM: Continuous Monitoring | Endpoint Security; Inventory and Control of Enterprise Assets; Malware Defenses | MDM inventory, encryption status, patch report, endpoint alerts, lost device process | Track device compliance, require disk encryption, review endpoint alerts, and document lost-device response steps. |
| HP-RISK-009 | Stripe | Manage vendor risk for payment processing and ensure HarborPay understands Stripe's security and availability posture. | GV.SC: Cybersecurity Supply Chain Risk Management; ID.RA: Risk Assessment; RC.RP: Recovery Planning | Service Provider Management; Data Protection; Incident Response Management | SOC 2 report, vendor security docs, admin user list, access logs, contract terms, incident notification terms | Complete vendor review, restrict Stripe admin access, document outage response, and verify incident notification terms. |
| HP-RISK-010 | Wazuh | Ensure security logs are collected, alerts are reviewed, and suspicious activity can be investigated. | DE.CM: Continuous Monitoring; RS.AN: Analysis; RS.MI: Mitigation | Audit Log Management; Incident Response Management; Endpoint Security | Agent coverage report, alert history, rule configuration, log retention settings, incident notes | Track agent coverage, define alert triage steps, tune noisy alerts, and create basic investigation playbooks. |

## Control Themes

The first 10 HarborPay risks mostly fall into these themes:

| Theme | Related Risks | Why It Matters |
|---|---|---|
| Identity and access | HP-RISK-001, HP-RISK-006, HP-RISK-003 | Many breaches begin with compromised credentials or excessive permissions. |
| Cloud security | HP-RISK-003 | Cloud misconfiguration can expose systems or data quickly. |
| Data protection | HP-RISK-002, HP-RISK-004, HP-RISK-009 | HarborPay handles sensitive customer, business, and payment-related data. |
| Application security | HP-RISK-005, HP-RISK-007 | Vulnerable apps and code can create direct security issues. |
| Endpoint security | HP-RISK-008, HP-RISK-010 | Employee devices generate risk and also provide useful logs. |
| Vendor risk | HP-RISK-009 | HarborPay depends on Stripe for payment workflows. |
| Detection and response | HP-RISK-010 | Without good logging, the company may not know when something is wrong. |

## What I Would Explain In An Interview

I would explain that this file helped me connect business risk to specific security controls. For example, "Okta account takeover" is not just a vague cyber risk. It connects to MFA, admin role review, sign-in logs, conditional access, and access review evidence.

I would also explain that evidence is important because a control is only useful if the company can show it is actually working. For example, saying "we use MFA" is weaker than showing an MFA enrollment report, admin list, and sign-in logs.

## Evidence Checklist

These are the first evidence items HarborPay should collect:

- Okta user list
- Okta MFA enrollment report
- Okta admin role list
- Google Workspace external sharing report
- AWS IAM policy report
- AWS CloudTrail logs
- Customer database access list
- Customer database audit logs
- Web app vulnerability scan
- Web app dependency scan
- Admin dashboard role matrix
- GitHub branch protection settings
- GitHub secret scanning alerts
- Employee MacBook MDM inventory
- Employee MacBook encryption status report
- Stripe SOC 2 report
- Stripe admin access list
- Wazuh agent coverage report
- Wazuh alert history
- Wazuh log retention settings

## Beginner-Friendly Explanation

The asset inventory answers:

> What does HarborPay have?

The risk register answers:

> What could go wrong?

The control map answers:

> What should HarborPay have in place to reduce the risk, and what evidence would prove it?

## Next Step

The next artifact should be a **vendor risk questionnaire** for Stripe or a fictional AI vendor.

Recommended next choice:

Start with **Stripe** because it is already one of the top 10 assets and it connects directly to fintech, payment processing, third-party risk, and business continuity.
