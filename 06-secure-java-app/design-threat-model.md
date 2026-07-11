# Access Request Tracker - Design-Stage Threat Model

## Status

This model covers the planned console version. It must be updated against the actual code before the application is described as complete.

## Security Objective

Ensure that access requests follow an authorized, reviewable workflow and that one role cannot silently bypass approval or rewrite the evidence.

## Assets To Protect

- User and reporting-line data
- System and risk-tier definitions
- Access-request content and status
- Approval and rejection decisions
- Audit events
- Authorization and workflow rules
- Build and dependency integrity

## Trust Boundaries

| Boundary | What crosses it | Main concern |
|---|---|---|
| Console input to application | Actor selection, request fields, commands | Untrusted or malformed input |
| User interface to services | Requested action and actor context | Authorization bypass if checks exist only in the menu |
| Services to in-memory repositories | Domain objects and state changes | Direct mutation or invalid transitions |
| Application to console/log output | Errors, request data, audit information | Sensitive-data exposure or misleading output |
| Developer environment to dependency repository | Build tools and third-party packages | Vulnerable or tampered dependency |

## Important Design Rule

The console menu is not a security boundary. Authorization must be enforced inside the service that performs the action. Hiding an option from a role is useful for usability, but it does not prove that the action is protected.

## STRIDE Review

| Category | Abuse case | Planned protection | Evidence needed |
|---|---|---|---|
| Spoofing | A caller selects another seeded user and acts as them. | Clearly state that version 1 has simulated identity; pass one actor object through the application boundary; do not claim production authentication. | README limitation and actor-context tests |
| Tampering | A caller changes a request status directly or rewrites an audit record. | Encapsulated state transitions; immutable identifiers and audit events; no public setters for protected state. | Unit tests and code review |
| Repudiation | A reviewer denies taking an approval action. | Record actor, action, target, result, reason, and timestamp for every decision. | Audit-event tests and demo output |
| Information disclosure | One requester reads another user's justification or internal error details. | Ownership and team authorization; safe public errors; controlled `toString` output. | Denied-access and output tests |
| Denial of service | Extremely long input or repeated requests exhausts memory in the console app. | Input length and collection limits appropriate for the lab. | Boundary tests and stated limitation |
| Elevation of privilege | A manager approves their own request, reviews another team, or skips administrator approval. | Central authorization service, no self-approval rule, and enforced state machine. | Role/action matrix tests |

## Priority Abuse Cases

### TM-01 - Self-approval

- **Attempt:** A manager submits a request and then approves it using the manager role.
- **Expected result:** Denied before state change; denied attempt is audited.
- **Why it matters:** Separation of duties is the main security value of the app.

### TM-02 - Direct state manipulation

- **Attempt:** Code creates a request already marked approved or changes a terminal request.
- **Expected result:** Constructors and services reject the invalid transition.
- **Why it matters:** A protected menu is ineffective if domain objects allow bypass.

### TM-03 - Cross-user disclosure

- **Attempt:** A requester supplies another request ID to view its justification.
- **Expected result:** Service returns a safe denial and records the attempt.
- **Why it matters:** Request text may reveal business systems and job responsibilities.

### TM-04 - Audit suppression

- **Attempt:** A sensitive action fails after a state change or bypasses event creation.
- **Expected result:** The service design keeps state change and audit creation together; version 1 limitations are documented if atomicity cannot be guaranteed.
- **Why it matters:** A workflow without reliable evidence is difficult to govern or investigate.

### TM-05 - Secret exposure through logs

- **Attempt:** A user pastes a token-like value into justification and the app logs it.
- **Expected result:** Input is treated as untrusted and sensitive-looking values are not included in security logs.
- **Why it matters:** Auditability should not create a second data leak.

## Open Decisions For The Build

| Decision | Options to compare | Record after implementation |
|---|---|---|
| Domain mutability | Immutable records vs controlled methods | |
| Service error model | Exceptions vs result type | |
| Audit write order | Before action, after action, or paired result | |
| Repository interface | Generic repository vs domain-specific methods | |
| Time source | Direct system clock vs injected clock for testing | |
| Secret-pattern handling | Reject, redact, or warn | |

## Review Trigger

Update this model whenever the app adds a web API, database, authentication, external notification, or real provisioning. Those features create new trust boundaries that the console model does not cover.
