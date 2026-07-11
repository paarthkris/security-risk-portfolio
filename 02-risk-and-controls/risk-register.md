# HarborPay Risk Register

## Purpose And Limitations

This register prioritizes ten fictional security scenarios based on HarborPay's assets and business model. It is an exercise in risk reasoning, not a report about a real company. The ratings represent **inherent risk**, meaning the exposure before I rely on any assumed control.

I intentionally leave residual risk unscored. A residual rating would imply that I had tested the control design and operation, which I have not done.

## Scoring Method

Likelihood and impact are scored from 1 to 5.

| Score | Likelihood | Impact |
|---|---|---|
| 1 | Rare in this scenario | Negligible disruption or data effect |
| 2 | Unlikely | Limited, recoverable effect |
| 3 | Possible | Material team or customer effect |
| 4 | Likely | Major operational, financial, or trust effect |
| 5 | Very likely | Severe or widespread effect |

`Risk score = likelihood x impact`

| Score | Rating |
|---|---|
| 1-4 | Low |
| 5-9 | Moderate |
| 10-15 | High |
| 16-25 | Critical |

The scores are prioritization tools, not precise predictions. Each one should be reconsidered when technical evidence becomes available.

## Register

| ID | Risk scenario | Asset(s) | L | I | Score | Rating | Response | Risk owner | Evidence needed before relying on controls |
|---|---|---|---:|---:|---:|---|---|---|---|
| HP-RISK-001 | If a workforce or administrator account is taken over through phishing, MFA abuse, or a weak recovery path, an unauthorized person could access connected systems and restricted data, causing broad business and customer impact. | Okta and connected applications | 4 | 5 | 20 | Critical | Mitigate | Head of IT | MFA enrollment and method report, admin-role export, sign-in policy, recovery settings, access-review records, selected sign-in logs |
| HP-RISK-002 | If an employee mailbox or shared drive is compromised or overshared, confidential information could be stolen or used for further impersonation, causing fraud, privacy, and trust impact. | Google Workspace | 4 | 4 | 16 | Critical | Mitigate | Head of IT | External-sharing report, admin audit logs, email security configuration, DLP rules, high-risk user events |
| HP-RISK-003 | If an AWS role, key, policy, or network rule is misconfigured or abused, an unauthorized person could change infrastructure or expose data, causing service interruption and a serious data event. | AWS account | 4 | 5 | 20 | Critical | Mitigate | VP of Engineering | IAM policies, privileged-role list, CloudTrail status, public-resource report, security-group review, selected configuration history |
| HP-RISK-004 | If customer database access is excessive, exposed, or insufficiently logged, customer records could be viewed, changed, or removed without timely detection, causing legal, operational, and trust impact. | Customer database | 4 | 5 | 20 | Critical | Mitigate | VP of Engineering | Access list, database roles, audit-log configuration, encryption settings, retention rule, backup and restore test |
| HP-RISK-005 | If the customer web application contains broken access control, injection, session, or dependency weaknesses, an attacker could access customer functions or data, causing fraud, downtime, and loss of trust. | HarborPay web app | 4 | 5 | 20 | Critical | Mitigate | Head of Product Engineering | Architecture, threat model, security tests, dependency results, access-control tests, relevant application logs |
| HP-RISK-006 | If admin-dashboard roles are too broad or sensitive actions are not approved and logged, an authorized or compromised user could make improper customer changes, causing fraud and difficult investigations. | Admin dashboard | 3 | 5 | 15 | High | Mitigate | Head of Customer Operations | Role matrix, current access list, approval records, action logs, session policy, latest access review |
| HP-RISK-007 | If a repository secret is exposed or a code change bypasses review, an attacker could gain system access or introduce insecure code, affecting applications and infrastructure. | GitHub repositories | 3 | 4 | 12 | High | Mitigate | Engineering Manager | Collaborator list, branch protection, SSO settings, secret and dependency alerts, sample pull-request approvals |
| HP-RISK-008 | If an employee MacBook is lost, compromised, or left unpatched, stored data and active sessions could be exposed and used to reach HarborPay services. | Employee MacBooks | 3 | 4 | 12 | High | Mitigate | IT Manager | Managed-device inventory, disk-encryption status, patch compliance, endpoint coverage, screen-lock policy, selected alerts |
| HP-RISK-009 | If access to the payment provider is misused or the service becomes unavailable, HarborPay could experience unauthorized payment activity or an inability to process transactions. | Stripe | 3 | 5 | 15 | High | Mitigate and transfer | CFO / Head of Product | Contract and SLA, assurance report, user and role list, MFA settings, audit logs, incident terms, continuity procedure |
| HP-RISK-010 | If endpoint telemetry is missing, delayed, or too noisy to investigate, HarborPay could make late or unsupported incident decisions and overlook activity affecting other assets. | Wazuh and connected endpoints | 3 | 4 | 12 | High | Mitigate | Security Lead | Agent coverage, manager configuration, alert history, rule exceptions, retention setting, triage notes, recovery test |

## Priority Decisions

The first technical attention should go to identity, cloud access, customer data, and the customer-facing application because they connect to several other assets and have the largest potential customer impact. The admin dashboard and Stripe also deserve early review because they support privileged or payment-related actions.

Wazuh is a different type of priority. It does not directly process customer payments, but weak telemetry would make every other scenario harder to detect and investigate. That is why the first hands-on phase focuses on proving that useful events can be generated, found, and explained.

## Review Triggers

I should update this register when:

- a technical lab produces evidence that changes likelihood or impact;
- an asset, owner, dependency, or data classification changes;
- a control is tested and residual risk can be supported;
- a new vendor or privileged workflow enters scope; or
- a simulated assumption is replaced with an observed result.

## What I Learned

A strong risk statement needs more than a threat name. Writing each scenario as a cause, event, and business consequence made it easier to choose an owner, request evidence, and explain why the risk matters.
