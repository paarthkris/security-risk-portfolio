# HarborPay Asset Inventory

## Objective

This inventory identifies the systems HarborPay depends on, who would own them, what information they handle, how exposed they are, and what evidence would be useful in a security review.

All entries are fictional scenario assumptions. "Expected controls" means controls I would expect to review; it does not mean I verified that they work.

## Inventory

| ID | Asset | Owner | Data class | Criticality | Exposure | Primary dependency | Main risk | Expected controls | Evidence request |
|---|---|---|---|---|---|---|---|---|---|
| HP-AST-001 | Okta | IT / Security | Restricted | Critical | Internet-facing | Employee directory and connected applications | Account takeover or privileged-role misuse | MFA, SSO, role separation, session policy, access reviews | User export, MFA enrollment, admin roles, sign-in logs, review records |
| HP-AST-002 | Google Workspace | IT | Confidential | High | Internet-facing | Okta and employee devices | Phishing, mailbox compromise, or external oversharing | SSO, sharing restrictions, audit logs, email protection, DLP | Sharing report, admin logs, drive permissions, DLP rules |
| HP-AST-003 | AWS account | Engineering / Security | Restricted | Critical | Mixed | Okta, IAM roles, and GitHub deployment workflows | Public exposure, excessive permissions, or unauthorized change | Least privilege, CloudTrail, security groups, encryption, configuration monitoring | IAM policies, CloudTrail status, public-resource report, security-group rules |
| HP-AST-004 | Customer database | Engineering | Restricted | Critical | Private service | AWS and HarborPay applications | Unauthorized record access, leakage, or unmonitored queries | RBAC, encryption, backups, audit logging, retention controls | Access list, audit logs, encryption configuration, backup test, retention rule |
| HP-AST-005 | HarborPay web app | Product / Engineering | Restricted | Critical | Internet-facing | AWS, customer database, and Stripe | Broken access control, injection, session abuse, or vulnerable dependency | Secure SDLC, authentication, validation, logging, dependency scanning | Architecture, threat model, scan results, test results, application logs |
| HP-AST-006 | Admin dashboard | Operations / Engineering | Restricted | Critical | Restricted web access | Okta and customer database | Excessive access or unauthorized customer-record changes | RBAC, approval, audit trail, session controls, periodic recertification | Role matrix, access list, approval records, activity logs, review evidence |
| HP-AST-007 | GitHub repositories | Engineering | Confidential | High | Internet service | Okta and developer endpoints | Secret exposure, unauthorized changes, or vulnerable dependencies | MFA/SSO, branch rules, code review, secret scanning, dependency alerts | Collaborator list, branch rules, scan alerts, pull-request history |
| HP-AST-008 | Employee MacBooks | IT | Confidential | High | Endpoint | Identity, device management, and patching | Device loss, malware, stale software, or stolen sessions | MDM, disk encryption, screen lock, endpoint monitoring, patching | Device inventory, encryption status, patch report, endpoint alerts |
| HP-AST-009 | Stripe | Finance / Product | Restricted | Critical | Internet service | HarborPay web app and authorized admins | Vendor outage, account misuse, or unclear incident obligations | Vendor review, MFA, least-privilege roles, audit logs, continuity plan | Contract, assurance report, user list, MFA setting, audit logs, SLA |
| HP-AST-010 | Wazuh | Security / IT | Confidential | High | Limited | Agents, manager, indexer, and dashboard | Missing telemetry, noisy alerts, or unsupported investigation decisions | Coverage tracking, protected configuration, retention, triage process | Agent list, configuration, alert history, retention setting, triage notes |

## Priority Rationale

The first six assets receive the highest attention because they directly affect identity, infrastructure, customer data, customer access, privileged operations, and payments. GitHub and MacBooks are important attack paths into those systems. Wazuh is important because weak telemetry would make problems harder to detect and explain.

## Maintenance Rules

- Add an asset only when it supports a clear business process or technical lab.
- Give every asset an owner and evidence request.
- Update criticality when dependencies change.
- Never record credentials, tokens, real customer data, serial numbers, or private configuration in this inventory.
- Revisit the inventory after each completed technical build.

## What I Learned

An asset list becomes useful when it includes business context. Naming AWS or Okta is not enough; I also need to know what depends on the asset, who would be accountable for it, what data it touches, and what evidence could support a review.
