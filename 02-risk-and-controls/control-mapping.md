# HarborPay Control Mapping

## Purpose

This document connects HarborPay's risk scenarios to control objectives, NIST Cybersecurity Framework 2.0 categories, CIS Controls v8.1 areas, and evidence I would request.

The mapping is learning-oriented and category-level. It does not establish compliance, certification, or control effectiveness. A framework reference tells me where an objective fits; evidence and testing tell me whether the objective is actually met.

## Control Objectives

| Objective | Related risks | NIST CSF 2.0 | CIS Controls v8.1 | Example test | Evidence |
|---|---|---|---|---|---|
| Maintain accountable owners and an accurate inventory of systems, software, data, and dependencies. | All | GV.RR, ID.AM | 1, 2 | Select in-scope assets and confirm owner, purpose, classification, and inventory coverage. | Asset records, software inventory, ownership records, data-flow notes |
| Assess and track security risks using defined criteria and review triggers. | All | ID.RA | 7 | Recalculate selected scenarios and confirm that new evidence changes the register when appropriate. | Risk method, register history, vulnerability results, review notes |
| Require strong authentication and controlled recovery for workforce and privileged identities. | 001, 002, 003, 006, 007, 009 | PR.AA | 5, 6 | Sample privileged users and verify approved role, strong MFA, and protected recovery methods. | User list, role export, MFA methods, sign-in policy, recovery configuration |
| Apply least privilege, role separation, and periodic access review. | 001, 003, 004, 006, 007, 009 | PR.AA | 5, 6 | Compare a user sample with job need, approval, current access, and latest review. | Role matrix, approval ticket, access list, review sign-off, removal record |
| Protect restricted data in storage, transit, use, backup, and disposal. | 002, 003, 004, 005, 008, 009 | PR.DS | 3 | Trace one restricted-data flow and inspect access, encryption, backup, and retention settings. | Data-flow diagram, encryption configuration, access list, backup test, retention rule |
| Configure and maintain endpoints, cloud resources, and applications securely. | 003, 005, 007, 008, 010 | PR.PS | 4, 7, 16 | Compare selected configurations and dependencies with approved baselines and investigate exceptions. | Baseline, configuration export, patch report, dependency results, exception record |
| Develop and test application security requirements throughout the software lifecycle. | 005, 006, 007 | PR.PS | 16, 18 | Test access-control, validation, logging, and dependency requirements in the Java application. | Threat model, unit tests, review checklist, scan output, change approval |
| Collect protected, usable logs for identity, endpoint, cloud, application, and privileged activity. | 001, 003, 004, 005, 006, 007, 008, 009, 010 | DE.CM | 8 | Generate a known event, locate it, confirm useful fields, and document any coverage gap. | Source configuration, event record, timestamp, alert, retention setting, coverage report |
| Analyze alerts consistently and separate facts, inferences, and unknowns. | 001, 006, 008, 010 | RS.AN | 8, 17 | Complete a triage note from controlled evidence and peer-check the decision. | Alert, timeline, actions, findings, decision, evidence links, limitations |
| Prepare recovery actions for identity, cloud, application, data, and monitoring failures. | 001, 003, 004, 005, 009, 010 | RC.RP | 11, 12, 17 | Walk through or test one recovery procedure and record time, outcome, and gaps. | Recovery plan, backup result, test record, action owner, lessons learned |
| Evaluate critical service providers and define security, incident, and continuity expectations. | 009 and vendor dependencies across other risks | GV.SC | 15 | Review a vendor evidence package against documented requirements and track unanswered items. | Questionnaire, contract clauses, assurance report, incident terms, SLA, remediation record |
| Train users and administrators for phishing, privileged actions, reporting, and secure development. | 001, 002, 003, 005, 006, 007, 008 | PR.AT | 14 | Sample role-based training records and compare content with responsibilities. | Completion report, training content, secure-development guidance, exception follow-up |

## How I Will Record Test Results

When I test a control, I will add a separate result instead of changing this objective into a claim. Each result should include:

1. **Scope:** the exact user, system, event, or configuration tested.
2. **Procedure:** what I did and in what order.
3. **Evidence:** a file, screenshot, log, or command output with sensitive data removed.
4. **Result:** passed, failed, partially met, or not tested.
5. **Finding:** the difference between the requirement and the observed state.
6. **Decision:** what should happen next and who would own it.
7. **Limitation:** what the test did not prove.

## Current Evidence Status

| Area | Current evidence | Status |
|---|---|---|
| Company, assets, and risk | Scenario documents in this repository | Documentation evidence only |
| Vendor risk | Simulated questionnaire and evidence plan | No real vendor evidence reviewed |
| IAM | Simulated event dataset and tabletop analysis | No real identity-provider evidence |
| Wazuh | Local Docker setup and connected Mac agent observed during setup | Setup observed; original screenshot withheld for privacy and control operation not yet tested through documented investigations |
| Java application | Requirements and design-stage threat model | Not implemented or tested |
| Local AI assistant | Architecture, schema, review checklist, and evaluation cases | Not implemented or tested |

## What I Learned

Framework mapping is useful for organizing work, but a control number is not evidence. The most important part of this exercise was defining a test and the artifact that would support a conclusion.
