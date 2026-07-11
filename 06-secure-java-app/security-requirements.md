# Access Request Tracker - Security Requirements

## Purpose

These requirements define what the first Java version must enforce. A requirement is not complete because code exists; it is complete when a test or review artifact supports it.

## Roles

| Role | Allowed scope | Explicit restriction |
|---|---|---|
| Requester | Create requests and view their own request history | Cannot approve or view another user's request |
| Manager | View and decide requests for direct reports | Cannot decide their own request or manage system definitions |
| Administrator | Manage system definitions and decide privileged requests after manager approval | Cannot approve their own request or rewrite audit history |
| Auditor | Read all requests, decisions, and audit events | Cannot create, approve, reject, or edit records |

## Requirements

| ID | Requirement | Acceptance evidence |
|---|---|---|
| AUTHZ-01 | Every service operation must receive an authenticated-actor object from the application boundary and make an explicit authorization decision. | Unit tests for each role/action pair; denied action returns a controlled error |
| AUTHZ-02 | A requester may view only requests they created. | Test proves own request is returned and another user's request is denied |
| AUTHZ-03 | A manager may decide only requests from their configured direct reports. | Tests for direct report, unrelated user, and missing manager relationship |
| AUTHZ-04 | No user may approve or reject their own request, even if they also have a manager or admin role. | Self-approval tests for both manager and administrator paths |
| AUTHZ-05 | Only an administrator may create, disable, or change a system resource or its risk tier. | Requester, manager, and auditor tests are denied; admin test succeeds |
| AUTHZ-06 | An auditor is read-only. | Tests deny every write operation and allow authorized reporting views |
| FLOW-01 | A new valid request starts in `SUBMITTED`; callers cannot choose the initial status. | Constructor or factory test and direct-status-injection test |
| FLOW-02 | Standard and sensitive requests require a manager decision; privileged requests require manager approval followed by an administrator decision. | State-transition tests for each risk tier |
| FLOW-03 | Rejected and approved requests are terminal in version 1. | Tests deny approval, rejection, or resubmission from terminal states |
| FLOW-04 | Every decision requires a nonblank reason and an eligible reviewer. | Validation and authorization tests |
| INPUT-01 | Identifiers must match the expected format and refer to an existing object. | Invalid, unknown, and valid identifier tests |
| INPUT-02 | Justification and decision text must be trimmed, length limited, and treated as data rather than executable content. | Boundary tests; output is safely displayed; no command or markup interpretation |
| INPUT-03 | Enum-backed fields must reject values outside the allowed set. | Deserialization or parser tests for unknown values |
| INPUT-04 | Errors must explain the safe next step without exposing stack traces or internal object state to the user. | Test expected public error and separate developer log behavior |
| AUDIT-01 | Submit, approve, reject, resource change, and denied sensitive action must create an audit event. | Tests assert action, actor, target, result, reason, and timestamp |
| AUDIT-02 | Application services must not expose an update or delete operation for existing audit events. | Interface review and test that returned collections cannot modify stored events |
| AUDIT-03 | Audit events must not contain passwords, tokens, or full secret-like input. | Review logging calls and test redaction of a seeded secret pattern |
| DATA-01 | Version 1 must use synthetic users and systems only. | Seed-data review; no real employee or account data in Git history |
| DATA-02 | Sensitive fields must not be written through `toString`, exception, or debug output. | Output tests and code review |
| TEST-01 | Security-relevant allowed and denied paths must have automated tests. | Test inventory maps each `AUTHZ`, `FLOW`, and `AUDIT` requirement to at least one test |
| SUPPLY-01 | Dependencies must be pinned through the build file and reviewed with an automated dependency scan. | Committed build file and dated scan result |
| SUPPLY-02 | The repository must be scanned for committed secrets before release. | Dated secret-scan result and documented false-positive review |

## Security Test Matrix

| Actor | Action | Target | Expected result |
|---|---|---|---|
| Requester A | Create request | Own identity | Allow and audit |
| Requester A | View request | Requester B's request | Deny and audit |
| Requester A | Approve request | Any request | Deny and audit |
| Manager A | Approve request | Direct report | Allow if state and tier permit |
| Manager A | Approve request | Own request | Deny and audit |
| Manager A | Approve request | Unrelated employee | Deny and audit |
| Administrator A | Approve privileged request | Manager-approved request | Allow and audit |
| Administrator A | Approve privileged request | Own request | Deny and audit |
| Auditor | View records | All request and audit records | Allow |
| Auditor | Change record | Any record | Deny and audit |

## Out Of Scope For Version 1

- Production authentication or password storage
- Real account provisioning
- Email notifications
- A database or distributed concurrency
- A graphical interface
- Regulatory certification

The out-of-scope list keeps the first version understandable. Each item can become a later security design decision instead of hidden complexity.
