# Stripe Vendor Risk Pre-Assessment

## Classification

**Simulated HarborPay exercise.** This is not a real review of Stripe, and it does not make claims about Stripe's controls. I selected Stripe because HarborPay's fictional payment workflow depends on it. Every unanswered question below is an evidence need, not a vendor deficiency.

## Summary

HarborPay would treat its payment provider as a critical service provider because account misuse, integration failure, or service interruption could affect revenue, customer activity, and trust. The review should focus on the specific service HarborPay uses, the data exchanged, HarborPay's own account configuration, incident obligations, and continuity options.

## Scope

| Item | HarborPay scenario |
|---|---|
| Service | Payment-processing integration for customer transactions |
| Business owner | Head of Product |
| Risk owner | CFO |
| Technical owner | Product Engineering Manager |
| Data assumption | Customer and transaction metadata; HarborPay does not store full card numbers |
| Access | Limited HarborPay finance, support, and engineering roles |
| Integration | HarborPay web application and backend services |
| Criticality | Critical |
| Review type | Initial security and continuity pre-assessment |

## Inherent Risk Summary

| Risk area | Scenario | Initial rating | Why it matters |
|---|---|---|---|
| Account access | A compromised or overprivileged HarborPay user could view or change sensitive payment settings. | High | The account supports payment-related operations and sensitive business actions. |
| Integration secrets | An exposed API credential or webhook secret could allow unauthorized requests or false events. | High | Application trust depends on protected credentials and validation. |
| Availability | A service or integration outage could prevent or delay customer transactions. | High | HarborPay's revenue and customer workflows depend on payment processing. |
| Incident coordination | Unclear notice, evidence, or escalation paths could delay HarborPay's response. | High | HarborPay needs enough time and information to assess customer impact. |
| Data handling | Unclear data flows, retention, or subprocessors could create privacy and contractual risk. | High | Restricted data should have documented purpose, location, access, and retention. |

These are HarborPay's inherent scenarios, not observations about the vendor.

## Questionnaire And Evidence Plan

| ID | Question | Why I would ask | Evidence requested | Current status |
|---|---|---|---|---|
| VR-01 | Which exact service, regions, data types, and subprocessors are in scope for HarborPay? | Defines the boundary of the review. | Data-flow description, service documentation, subprocessor list | Not reviewed |
| VR-02 | What independent security assurance applies to the in-scope service and period? | Provides an external view of control design and operation. | Current SOC report, certification scope, bridge letter if needed | Not reviewed |
| VR-03 | How is HarborPay customer data encrypted in transit and at rest? | Tests the data-protection expectation. | Architecture or control statement, encryption standard, key-management description | Not reviewed |
| VR-04 | How are vendor workforce and privileged accounts approved, authenticated, reviewed, and removed? | Privileged access can affect customer data and service operation. | Access-control policy, MFA requirement, review procedure, termination process | Not reviewed |
| VR-05 | Which security logs and account audit events are available to HarborPay? | HarborPay needs evidence for misuse and incident analysis. | Event catalog, retention period, export or API options, sample redacted log | Not reviewed |
| VR-06 | What incident-notification timeline and information commitments apply? | Supports timely impact assessment and communication. | Contract language, incident procedure, escalation contacts | Not reviewed |
| VR-07 | How are vulnerabilities identified, prioritized, remediated, and independently tested? | Shows how technical weaknesses enter the risk process. | Vulnerability policy, remediation targets, summary test evidence | Not reviewed |
| VR-08 | How are software changes reviewed, tested, approved, and monitored? | Changes can affect security and availability. | Secure-development summary, change-control process, test description | Not reviewed |
| VR-09 | What availability target, recovery objective, and service-credit terms apply? | Connects service resilience to HarborPay's business needs. | SLA, recovery summary, status-history source, continuity terms | Not reviewed |
| VR-10 | How are backups and recovery procedures tested for the in-scope service? | Supports recoverability after operational or security events. | Recovery-control description and latest test summary | Not reviewed |
| VR-11 | How can HarborPay restrict its users by role, MFA, network, or approval workflow? | HarborPay remains responsible for its side of access control. | Product role documentation, MFA options, account settings, admin guide | Not reviewed |
| VR-12 | How should HarborPay create, rotate, store, scope, and revoke integration credentials? | Reduces credential misuse and improves incident response. | Credential-management guidance and supported restrictions | Not reviewed |
| VR-13 | How are webhook messages authenticated, replay-protected, and monitored? | Prevents HarborPay from trusting forged or repeated events. | Webhook security documentation and implementation guidance | Not reviewed |
| VR-14 | What happens to HarborPay data at contract end, and how is deletion confirmed? | Addresses retention and exit risk. | Retention schedule, deletion process, confirmation method | Not reviewed |
| VR-15 | What are the escalation, support, and exit options if risk is not acceptable? | Defines accountability and a practical response path. | Support model, remediation process, termination and data-export terms | Not reviewed |

## HarborPay-Side Controls To Verify

A vendor review should not ignore the customer's own responsibilities. In this scenario, I would verify that HarborPay:

- uses individual accounts and least-privilege roles;
- requires strong MFA for every interactive user;
- separates routine support work from sensitive administration;
- stores integration secrets outside source code;
- scopes and rotates credentials;
- validates webhook signatures and rejects replayed events;
- logs privileged actions and reviews unusual activity;
- documents outage handling and a manual customer-communication path; and
- removes access promptly when a role or employment status changes.

## Preliminary Findings

Because no evidence was reviewed, the only supportable findings are process gaps in the fictional exercise:

1. **Evidence not yet collected:** HarborPay cannot conclude that external control requirements are met without an in-scope evidence package.
2. **Shared responsibility needs definition:** HarborPay must document which access, credential, logging, and integration controls it owns.
3. **Continuity criteria need an owner:** The business should define acceptable interruption and escalation thresholds before an outage.
4. **Exit requirements need to be explicit:** Data return, deletion, integration replacement, and access removal should be planned before termination is needed.

## Tabletop Decision

**Decision: conditional approval within the fictional scenario, pending evidence and HarborPay-side configuration review.**

This is not an approval of Stripe. It is the decision I would document for the exercise: the business need can continue through due diligence only if the risk owner accepts the interim uncertainty, required evidence has named owners and dates, and critical HarborPay-side controls are verified before production use.

## Recommended Follow-Up

| Priority | Action | Owner | Completion evidence |
|---:|---|---|---|
| 1 | Confirm service scope, data flow, and HarborPay responsibilities. | Product Engineering | Approved data-flow and responsibility matrix |
| 2 | Review current assurance, incident, privacy, and continuity evidence. | Security / Legal | Review notes with exceptions and expiration dates |
| 3 | Test HarborPay account roles, MFA, credential storage, and webhook validation. | IT / Engineering | Configuration evidence and test results |
| 4 | Document outage, security escalation, and customer-communication procedures. | Product / Operations | Approved runbook and tabletop result |
| 5 | Track unanswered questions and accepted exceptions through closure. | Vendor Risk Owner | Dated issue log with owner and decision |

## Framework Connection

This exercise supports NIST CSF 2.0 supply-chain risk management (`GV.SC`) and CIS Control 15, Service Provider Management. Framework labels organize the review; they do not replace contracts, technical testing, or evidence.

## What I Learned

Vendor risk is not a checklist about whether a famous company is secure. The useful questions are what HarborPay depends on, what data and access are involved, which controls HarborPay owns, what evidence supports the vendor's commitments, and what the business will do if the service fails.
