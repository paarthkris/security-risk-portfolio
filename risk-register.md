# HarborPay Risk Register

## Overview

This risk register identifies the first set of cybersecurity and technology risks for **HarborPay**, a fictional Boston-based fintech company.

The risks are based on the first 10 assets in the HarborPay asset inventory:

1. Okta
2. Google Workspace
3. AWS Account
4. Customer Database
5. HarborPay Web App
6. Admin Dashboard
7. GitHub Repositories
8. Employee MacBooks
9. Stripe
10. Wazuh

I created this risk register to practice turning a list of business systems into specific security concerns. My goal is to show that I can look at an asset, think through what could realistically go wrong, estimate the business impact, and recommend practical next steps.

This is not meant to claim that HarborPay is a real company or that I performed a real audit. It is a portfolio exercise that helps me practice how a GRC, cybersecurity, or technology risk analyst would think.

## My Approach

For each risk, I tried to answer a few simple questions:

- What asset is involved?
- What could realistically go wrong?
- How would that scenario affect the business?
- What controls might already exist?
- What gaps would I want to review?
- What evidence would I ask for if I were checking this risk?

I kept the first version to 10 risks so I can explain each one clearly in an interview.

## Risk Rating Method

### Likelihood

| Rating | Meaning |
|---|---|
| Low | Unlikely, but possible |
| Medium | Realistic and should be monitored |
| High | Likely enough to require active attention |

### Impact

| Rating | Meaning |
|---|---|
| Low | Limited disruption or low sensitivity |
| Medium | Moderate operational or data impact |
| High | Major business, customer, security, or compliance impact |
| Critical | Severe impact to customer trust, payments, identity, or core operations |

### Overall Priority

| Priority | Meaning |
|---|---|
| Low | Track and revisit later |
| Medium | Address through normal planning |
| High | Needs planned remediation |
| Critical | Needs urgent attention and leadership visibility |

## Risk Register

| Risk ID | Related Asset | Risk Description | Threat Scenario | Likelihood | Impact | Priority | Existing Controls | Control Gaps | Recommended Treatment | Owner | Status | Evidence to Review | Framework Mapping | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HP-RISK-001 | Okta | Employee account takeover due to phishing, weak MFA settings, or risky login behavior. | An employee enters their credentials into a fake login page, allowing an attacker to access Okta-connected tools. | High | Critical | Critical | MFA, SSO, login alerts, admin roles. | Need stronger conditional access, phishing-resistant MFA review, and regular access reviews. | Mitigate | IT / Security | Open | MFA enrollment report, sign-in logs, admin role list, access review records. | NIST CSF PR.AA, DE.CM; CIS Account Management | Identity compromise can create access to many other systems. |
| HP-RISK-002 | Google Workspace | Sensitive documents or emails may be exposed through phishing or external sharing. | A finance spreadsheet or customer support export is shared outside the company by mistake. | High | High | High | Okta SSO, sharing settings, email security, user permissions. | Need external sharing review, stronger DLP rules, and employee training. | Mitigate | IT | Open | External sharing report, shared drive permissions, mailbox audit logs. | NIST CSF PR.DS, PR.AT; CIS Data Protection | Google Workspace is both a productivity tool and a sensitive data store. |
| HP-RISK-003 | AWS Account | Misconfigured AWS resources or overly broad permissions could expose infrastructure or customer data. | A cloud resource is accidentally exposed to the internet or an IAM role has more permissions than needed. | Medium | Critical | Critical | IAM roles, security groups, CloudTrail, encryption settings. | Need least privilege review, public resource scanning, and stronger cloud configuration monitoring. | Mitigate | Engineering / Security | Open | IAM policy report, CloudTrail logs, security group rules, public resource scan. | NIST CSF PR.AA, PR.DS, DE.CM; CIS Cloud Security | Cloud misconfiguration is one of the most realistic risks for a fintech startup. |
| HP-RISK-004 | Customer Database | Unauthorized access to customer data due to weak permissions, poor logging, or insecure queries. | An employee or compromised account accesses customer records beyond their job responsibilities. | Medium | Critical | Critical | Database access controls, encryption, backups, logging. | Need formal data access review, stronger query monitoring, and documented data retention rules. | Mitigate | Engineering | Open | Database access list, audit logs, encryption settings, backup records. | NIST CSF PR.DS, PR.AA, DE.CM; CIS Data Protection | This is one of HarborPay's most sensitive assets. |
| HP-RISK-005 | HarborPay Web App | Web application vulnerabilities could expose customer accounts or disrupt customer access. | An attacker uses broken authentication, injection, or insecure session handling to access customer data. | Medium | Critical | Critical | HTTPS, authentication, code review, dependency scanning, app logging. | Need structured OWASP Top 10 review, threat model, and repeatable vulnerability testing. | Mitigate | Engineering / Product | Open | Vulnerability scan results, dependency report, authentication design, application logs. | NIST CSF PR.PS, PR.DS, DE.CM; CIS Application Software Security | This risk will connect directly to the secure Java app portion of the portfolio. |
| HP-RISK-006 | Admin Dashboard | Excessive admin privileges could allow staff to view or change customer records without proper need. | A support user has more access than required and accidentally or intentionally modifies sensitive customer information. | Medium | Critical | Critical | RBAC, Okta SSO, audit logs, restricted access. | Need role matrix, approval workflow, admin activity review, and periodic access recertification. | Mitigate | Operations / Engineering | Open | Admin user list, role matrix, activity logs, approval records. | NIST CSF PR.AA, GV.RR, DE.CM; CIS Access Control Management | Good risk for showing least privilege and GRC thinking. |
| HP-RISK-007 | GitHub Repositories | Source code, secrets, or vulnerable dependencies may be exposed through poor repository controls. | A developer accidentally commits an API key or merges insecure code without review. | Medium | High | High | Branch protection, code review, secret scanning, Dependabot. | Need consistent branch rules, secret scanning review process, and dependency remediation tracking. | Mitigate | Engineering | Open | Repo access list, branch protection settings, secret scanning alerts, dependency alerts. | NIST CSF PR.PS, PR.DS; CIS Application Software Security | This is a strong bridge between software basics and security risk. |
| HP-RISK-008 | Employee MacBooks | Lost, infected, or poorly managed laptops could expose accounts, local files, or cloud access. | An employee loses a laptop that contains cached sessions or sensitive downloaded files. | Medium | High | High | Device management, disk encryption, screen lock, endpoint protection, patching. | Need device compliance reporting, lost-device procedure, and endpoint alert review. | Mitigate | IT | Open | MDM inventory, encryption status, patch report, endpoint alerts, lost device process. | NIST CSF PR.PS, PR.DS, DE.CM; CIS Endpoint Security | Endpoint risk is realistic because employees use laptops to access almost everything. |
| HP-RISK-009 | Stripe | Payment processing disruption or vendor security issue could affect HarborPay's customers and operations. | Stripe has an outage, access issue, or security incident that disrupts payment workflows. | Low | Critical | High | Vendor security review, restricted admin access, MFA, vendor monitoring. | Need documented vendor risk review, incident notification terms, and business continuity plan. | Transfer / Mitigate | Finance / Product | Open | SOC 2 report, vendor security docs, admin user list, access logs, contract terms. | NIST CSF GV.SC, ID.RA, RC.RP; CIS Service Provider Management | This is important because HarborPay depends on Stripe for payment workflows. |
| HP-RISK-010 | Wazuh | Incomplete logging or poor alert review could delay detection of suspicious activity. | A suspicious login or endpoint event occurs, but logs are missing or alerts are not reviewed in time. | Medium | High | High | Wazuh agents, dashboards, alert rules, log retention. | Need alert triage process, agent coverage tracking, and documented investigation playbooks. | Mitigate | Security / IT | Open | Agent coverage report, alert history, rule configuration, incident notes. | NIST CSF DE.CM, RS.AN; CIS Audit Log Management | This risk connects directly to the Wazuh homelab. |

## Highest Priority Risks

The first risks to focus on are:

1. **HP-RISK-001: Okta account takeover**
2. **HP-RISK-003: AWS misconfiguration or excessive permissions**
3. **HP-RISK-004: Customer database unauthorized access**
4. **HP-RISK-005: HarborPay web app vulnerabilities**
5. **HP-RISK-006: Admin dashboard excessive access**

These are the most important because they connect to identity, cloud infrastructure, customer data, customer-facing systems, and privileged internal access.

## What I Learned From This Register

The biggest thing I noticed is that many risks connect back to identity and access. If an attacker gets into Okta, GitHub, AWS, or the admin dashboard, the issue is not only technical. It becomes a business risk because customer data, payment workflows, and trust could all be affected.

I also noticed that some controls are technical, like MFA, logging, encryption, and vulnerability scanning. Other controls are process-based, like access reviews, vendor reviews, approval workflows, and incident response steps. That mix is exactly why I am interested in the space between cybersecurity, business technology, and GRC.

## Interview Talking Point

This risk register shows how I moved from an asset inventory to practical risk management.

Instead of saying "cybersecurity is important" in a general way, this register identifies specific systems, realistic threat scenarios, current controls, missing controls, owners, evidence, and framework mappings.

In an interview, I would use Okta, AWS, or the admin dashboard as examples because they are easy to explain and show how one weak control can create a larger business risk.

## Next Step

The next project artifact should be a **control mapping** file that connects each risk to NIST CSF and CIS Controls in more detail.
