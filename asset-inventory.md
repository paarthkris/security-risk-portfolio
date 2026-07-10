# HarborPay Asset Inventory

## Overview

HarborPay is a fictional Boston-based fintech company with about 120 employees. The company helps small businesses accept payments, manage invoices, and view customer transaction activity.

I created this asset inventory as the starting point for the HarborPay security risk portfolio. Before I can talk about risks, controls, or monitoring, I need to understand what the company actually depends on.

For this first version, I focused on 10 assets that seem realistic for a small fintech company and important from a cybersecurity/GRC perspective: identity, email, cloud, customer data, applications, code, endpoints, vendors, and security monitoring.

## My Assumptions

- HarborPay is a small but growing fintech company, so it uses common modern tools instead of a large enterprise stack.
- The company is hybrid, so employees access systems from different locations and devices.
- The company handles sensitive customer and payment-related data, so identity, cloud security, and vendor risk matter a lot.
- This is a learning portfolio, not a real audit, so the assets and controls are realistic examples that I can explain and build on.

## Asset Inventory

| Asset ID | Asset Name | Category | Owner | Description | Data Sensitivity | Business Criticality | Internet-Facing | Main Risks | Existing Controls | Evidence to Review |
|---|---|---|---|---|---|---|---|---|---|---|
| HP-AST-001 | Okta | Identity and Access Management | IT / Security | Central identity provider used for employee single sign-on into company applications. | High | Critical | Yes | Account takeover, weak MFA, excessive admin privileges, inactive users retaining access. | MFA, SSO, admin roles, login alerts, access reviews. | User list, MFA enrollment report, admin role list, sign-in logs, access review records. |
| HP-AST-002 | Google Workspace | Email and Documents | IT | Company email, shared drives, documents, spreadsheets, calendar, and internal collaboration. | High | High | Yes | Phishing, mailbox compromise, overshared documents, sensitive files shared externally. | MFA through Okta, sharing settings, email security, user access controls. | External sharing report, mailbox security settings, admin audit logs, shared drive permissions. |
| HP-AST-003 | AWS Account | Cloud Infrastructure | Engineering | Primary cloud environment hosting HarborPay systems, databases, storage, and infrastructure. | Critical | Critical | Yes | Misconfigured cloud resources, exposed services, excessive IAM permissions, weak logging. | IAM roles, security groups, CloudTrail, encryption, least privilege policies. | IAM policy report, CloudTrail logs, security group rules, public resource scan, encryption settings. |
| HP-AST-004 | Customer Database | Data Store | Engineering | Database containing customer account records, business details, invoice data, and transaction-related information. | Critical | Critical | No | Unauthorized access, data leakage, weak encryption, excessive employee access, poor backup controls. | Database access controls, encryption, backups, logging, role-based permissions. | Access list, database audit logs, backup records, encryption settings, data retention policy. |
| HP-AST-005 | HarborPay Web App | Customer-Facing Application | Engineering / Product | Public web application used by customers to log in, manage invoices, and view payment activity. | High | Critical | Yes | OWASP Top 10 vulnerabilities, broken authentication, input validation issues, session hijacking. | HTTPS, authentication, code review, dependency scanning, app logging. | Vulnerability scan results, dependency report, authentication design, application logs, secure coding review. |
| HP-AST-006 | Admin Dashboard | Internal Application | Operations / Engineering | Internal tool used by HarborPay staff to support customers, review accounts, and handle operational tasks. | Critical | Critical | Limited | Excessive admin access, unauthorized customer record changes, weak activity logging, privilege abuse. | RBAC, admin approvals, audit logs, Okta SSO, restricted access. | Admin user list, role matrix, activity logs, approval records, access review evidence. |
| HP-AST-007 | GitHub Repositories | Source Code | Engineering | Repositories containing HarborPay application code, infrastructure code, documentation, and development workflows. | High | High | Yes | Exposed secrets, vulnerable code, weak branch protection, unreviewed changes, dependency risk. | Branch protection, code review, secret scanning, Dependabot, limited repository access. | Repo access list, branch protection settings, secret scanning alerts, dependency alerts, pull request history. |
| HP-AST-008 | Employee MacBooks | Endpoint Devices | IT | Company-issued laptops used by employees and developers to access HarborPay systems and data. | Medium / High | High | No | Lost devices, malware, weak local security, outdated software, unmanaged developer tools. | Device management, disk encryption, screen lock, endpoint protection, patching. | MDM inventory, encryption status, patch status, endpoint alerts, lost device process. |
| HP-AST-009 | Stripe | Payment Processing Vendor | Finance / Product | Third-party payment processor used to handle payment activity and payment-related workflows. | High | Critical | Yes | Vendor outage, payment workflow disruption, poor access control, sensitive data exposure through vendor access. | Vendor security review, restricted admin access, MFA, vendor monitoring. | Vendor security documentation, SOC 2 report, admin user list, access logs, incident notification terms. |
| HP-AST-010 | Wazuh | Security Monitoring | Security / IT | Security monitoring platform used to collect endpoint and system logs, generate alerts, and support investigations. | Medium | High | Limited | Missing logs, alert fatigue, poor rule tuning, lack of response process, incomplete endpoint coverage. | Agents, alert rules, dashboards, log retention, investigation notes. | Agent coverage report, alert history, rule configuration, log retention settings, incident notes. |

## Notes On Sensitivity And Criticality

**Data Sensitivity** describes how sensitive the information inside or connected to the asset is.

- Low: Public or low-impact business information.
- Medium: Internal company information.
- High: Sensitive business, employee, customer, or operational information.
- Critical: Customer data, payment-related data, privileged access, or systems that could create major harm if compromised.

**Business Criticality** describes how important the asset is to HarborPay's ability to operate.

- Low: Minimal operational impact if unavailable.
- Medium: Some team disruption.
- High: Major business disruption.
- Critical: Customer-facing, payment-related, identity-related, or security-critical system.

## Initial Observations

The highest-risk assets are:

1. Okta
2. AWS Account
3. Customer Database
4. HarborPay Web App
5. Admin Dashboard
6. Stripe

These assets are high priority because they connect directly to identity, cloud infrastructure, customer data, application security, internal privileged access, and payment operations.

## Why I Started With These 10

I started with these assets because they give me a balanced picture of how a real company creates security risk.

- **Okta** shows identity and access risk.
- **Google Workspace** shows phishing, email, and document-sharing risk.
- **AWS** shows cloud configuration and permission risk.
- **Customer Database** shows sensitive data protection risk.
- **HarborPay Web App** shows application security risk.
- **Admin Dashboard** shows privileged internal access risk.
- **GitHub** shows source code, secrets, and dependency risk.
- **Employee MacBooks** show endpoint and device management risk.
- **Stripe** shows vendor and payment dependency risk.
- **Wazuh** shows detection, logging, and investigation risk.

This gives me enough variety to build a strong risk register without making the project too broad at the beginning.

## What I Would Explain In An Interview

I would explain that I started with asset inventory because security risk needs context. A company cannot prioritize risk well if it does not know which systems are most important, who owns them, what data they touch, and how exposed they are.

I would also explain that I intentionally chose assets that map to common internship and co-op areas: IAM, cloud, GRC, app security, vendor risk, endpoint security, and SIEM/logging.

## Next Step

Use this asset inventory to build the first HarborPay risk register. Each risk should connect back to one or more assets from this inventory.

Example:

| Risk ID | Related Asset | Risk |
|---|---|---|
| HP-RISK-001 | Okta | Employee account takeover due to weak MFA or phishing. |
| HP-RISK-002 | AWS Account | Cloud data exposure due to misconfigured access controls. |
| HP-RISK-003 | Admin Dashboard | Excessive admin privileges leading to unauthorized customer record access. |
