# 06 - Secure Java App

## Project

**HarborPay Access Request Tracker**

This will be a small Java application where employees request access to HarborPay systems and authorized reviewers approve or reject those requests. I chose this idea because it connects object-oriented design to IAM, least privilege, separation of duties, approval evidence, and audit logging.

## Honest Status

The design and security requirements are complete. No application code or test result exists yet. I will build the code myself in small milestones so I can explain the classes, decisions, mistakes, and security checks.

## Version 1 Scope

The first version will be a console application with in-memory data and automated tests. It will demonstrate **authorization and workflow logic**, not production authentication. Users will be seeded test identities, and the README will not claim that choosing a user from a menu securely proves identity.

After the console version is correct and tested, I can decide whether to add a Spring Boot API, a database, and real authentication.

## Business Rules

- A requester can submit and view their own access requests.
- A manager can review requests for people on their team.
- Nobody can approve their own request.
- An administrator manages system definitions and gives final approval for privileged access.
- An auditor can read requests, decisions, and audit events but cannot change them.
- Every submit, approve, reject, and denied attempt creates an audit event.
- Rejected or completed requests cannot silently return to an earlier state.

## Suggested Domain Model

| Class or enum | Responsibility |
|---|---|
| `User` | Stores identity, department, manager, and role information for the lab. |
| `Role` | Defines requester, manager, administrator, and auditor capabilities. |
| `SystemResource` | Describes an application or platform and its access-risk tier. |
| `RiskTier` | Distinguishes standard, sensitive, and privileged access. |
| `AccessRequest` | Holds requester, resource, requested level, justification, state, and timestamps. |
| `RequestStatus` | Controls valid workflow states and transitions. |
| `Decision` | Records reviewer, outcome, reason, and timestamp. |
| `AuditEvent` | Records actor, action, target, result, reason, and timestamp. |
| `AuthorizationService` | Answers whether an actor may perform an action. |
| `AccessRequestService` | Validates and creates requests. |
| `ApprovalService` | Applies approval rules and state changes. |
| `AuditService` | Writes append-only security events. |

## Planned Workflow

```text
SUBMITTED
   |
   +-- rejected by manager -----------------> REJECTED
   |
   +-- standard/sensitive manager approval -> APPROVED
   |
   +-- privileged manager approval --------> PENDING_ADMIN
                                                |
                                                +-- admin approves -> APPROVED
                                                +-- admin rejects  -> REJECTED
```

An approved request means the workflow approved access; version 1 will not provision access in a real system.

## Build Milestones

### Milestone 1 - Java model

- [ ] Create a Maven project and run one test.
- [ ] Implement enums and immutable identifiers.
- [ ] Implement `User`, `SystemResource`, and `AccessRequest`.
- [ ] Write tests for required fields and valid states.

### Milestone 2 - Authorization

- [ ] Implement role checks in one `AuthorizationService`.
- [ ] Restrict request viewing by ownership, team, and auditor role.
- [ ] Deny self-approval.
- [ ] Write allowed and denied tests before adding the menu.

### Milestone 3 - Approval workflow

- [ ] Implement manager approval and rejection.
- [ ] Add administrator approval for privileged access.
- [ ] Reject invalid state transitions.
- [ ] Require a decision reason.

### Milestone 4 - Auditability

- [ ] Record successful and denied sensitive actions.
- [ ] Keep audit events append-only through the service interface.
- [ ] Do not log credentials, secrets, or full sensitive input.
- [ ] Test event fields and ordering.

### Milestone 5 - Review

- [ ] Complete the design threat model with implemented details.
- [ ] Run unit tests, dependency scanning, and secret scanning.
- [ ] Complete the security review checklist.
- [ ] Save sanitized terminal output or a short demo.
- [ ] Document one design mistake and how I fixed it.

## Files

- [Security requirements](security-requirements.md)
- [Design-stage threat model](design-threat-model.md)
- [Security review checklist](security-review-checklist.md)
- [Project-wide roadmap](../PROJECT_ROADMAP.md)

## Definition Of Done

This app is complete when the repository contains working code, tests that prove the important allowed and denied paths, scan output, an updated threat model, and a short explanation I can give without reading from the file.

## Planned Interview Explanation

After I build and test the application, I should be able to say:

> I built an access-request workflow in Java to connect object-oriented design with IAM. The key security rules were least privilege, no self-approval, controlled state transitions, and an audit record for both successful and denied actions. I wrote tests around the security decisions instead of treating the user interface as the main result.
