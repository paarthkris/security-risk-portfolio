# Access Request Tracker - Security Review Checklist

Complete this against the working application. Link every checked item to a test, code location, scan result, or demo artifact.

## Authorization And Workflow

- [ ] Authorization is enforced in services, not only in the console menu.
- [ ] Requesters cannot read another user's request.
- [ ] Managers cannot decide their own or unrelated users' requests.
- [ ] Privileged access cannot skip administrator review.
- [ ] Auditors cannot change data.
- [ ] Invalid and terminal state transitions are rejected.
- [ ] Denied sensitive actions are audited.

## Input And Output

- [ ] Required values, formats, enum values, and lengths are validated.
- [ ] Untrusted text is never executed or interpreted as a command.
- [ ] User-facing errors contain no stack trace or internal object details.
- [ ] `toString`, debug output, and logs exclude sensitive fields.
- [ ] Tests cover minimum, maximum, empty, unknown, and malformed input.

## Audit Trail

- [ ] Submit, approve, reject, resource change, and denied actions create events.
- [ ] Events identify actor, action, target, result, reason, and timestamp.
- [ ] Existing events cannot be edited or deleted through application services.
- [ ] Audit output contains synthetic data only.
- [ ] Event ordering is deterministic in tests.

## Code And Dependencies

- [ ] Security-relevant methods have focused unit tests.
- [ ] The build succeeds from a clean checkout.
- [ ] Dependency scan output is saved with date and tool version.
- [ ] Secret scan output is saved with false positives reviewed.
- [ ] No credential, API key, private path, or personal data appears in Git history.
- [ ] The design threat model matches the implemented boundaries.

## OWASP ASVS Learning Review

For implemented features, compare the design with relevant OWASP ASVS areas such as architecture, validation, access control, error handling, data protection, and logging. Record the exact ASVS version and requirement references used. Mark a requirement **not applicable** with a reason instead of forcing a pass.

| Reference | Requirement in my words | Applicable? | Evidence | Result | Follow-up |
|---|---|---|---|---|---|
| | | | | | |

## Release Decision

- Decision: [ready for portfolio / needs work]
- Reviewer: [name]
- Date: [YYYY-MM-DD]
- Blocking issues:
- Accepted limitations:
- Next improvement:
