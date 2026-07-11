# HarborPay Security Risk Review - Executive Summary

## Summary

I completed a scenario-based security risk review for HarborPay, a fictional 120-person fintech company. The review covers ten connected assets across identity, collaboration, cloud, customer data, applications, source code, employee endpoints, payments, and monitoring.

The purpose was to practice turning a business environment into clear risk statements, priorities, control objectives, and evidence requests. This was not a real audit. No production environment or real vendor evidence was tested.

## Overall Assessment

HarborPay's highest inherent-risk scenarios involve workforce identity, AWS access, the customer database, and the public web application. These systems are highly connected: one compromised identity or development path could affect infrastructure, code, customer records, and privileged operations.

The scenario also depends heavily on third-party and monitoring capabilities. Payment-provider access and availability have direct business importance, while incomplete Wazuh telemetry would make it harder to detect and defend decisions about the other risks.

## Priority Risks

| Priority | Risk | Why it matters |
|---:|---|---|
| 1 | Identity takeover and privileged-access misuse | Okta connects employees to several important services, so a single account can create broad exposure. |
| 2 | AWS misconfiguration or unauthorized change | Cloud permissions and network settings can affect availability, customer data, and application security. |
| 3 | Customer database access or logging failure | Restricted customer records require tightly controlled, reviewable access and reliable recovery. |
| 4 | Web-application access-control or input weakness | The public application is directly exposed and supports customer activity. |
| 5 | Insufficient monitoring and investigation evidence | Weak coverage can delay detection and produce conclusions that are not supported by facts. |

## Recommended Actions

1. Validate privileged identity controls, including MFA methods, recovery paths, role separation, and access-review evidence.
2. Review AWS public exposure, privileged roles, CloudTrail coverage, and security-group changes.
3. Confirm database roles, query logging, encryption, retention, backup, and restore evidence.
4. Establish application-security requirements and test access control, validation, logging, and dependencies.
5. Prove monitoring value with controlled events, complete triage notes, and documented coverage gaps.
6. Review payment-provider access, assurance evidence, incident terms, and continuity procedures.

## Work Completed

- Defined HarborPay's business context, data classes, scope, and assumptions.
- Inventoried ten assets with owners, dependencies, criticality, and evidence requests.
- Scored ten inherent-risk scenarios using a documented 5-by-5 method.
- Mapped control objectives to NIST CSF 2.0 and CIS Controls v8.1 categories.
- Prepared a simulated vendor-risk review and IAM tabletop.
- Established a Wazuh Docker environment and connected a local Mac endpoint.

## Work Not Yet Completed

- No HarborPay control has been formally tested for operating effectiveness.
- No real Stripe, Okta, AWS, Google, or GitHub evidence was reviewed.
- The Wazuh lab has not yet produced two completed controlled-event investigations.
- The secure Java application and local AI GRC assistant have not been built.

## Decision

The documentation provides a clear starting point, but technical conclusions should wait for evidence. The next priority is to complete two small Wazuh investigations and use the same report structure for each. That will turn the monitoring section from a setup exercise into defensible hands-on work.

## Student Reflection

This review helped me see that GRC and technical security are connected by evidence. A risk register identifies what matters, but logs, tests, configurations, and approvals are what let an analyst decide whether a control is working and what should change.
