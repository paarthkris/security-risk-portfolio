# Simulated IAM Case Study - Maya Chen

## Classification

**Tabletop exercise using fictional data.** The people, systems, events, and decisions in this report are invented for HarborPay. The source CSV is not an export from Okta, Google Workspace, or a production system.

## Summary

The simulated dataset contains a successful normal-workday sign-in for Maya Chen from a known MacBook in Boston, followed 18 minutes later by a failed sign-in attempt and failed MFA challenge from an unusual location and unknown device. Eight minutes after that, the account was denied access to the HarborPay Admin Dashboard from the known Boston device.

The events justify prompt validation and containment steps, but they do not prove that the account was compromised. The dataset lacks IP addresses, session identifiers, authentication-factor details, device identifiers, and user confirmation.

## Scope

| Field | Scenario value |
|---|---|
| User | Maya Chen, Customer Operations |
| Normal location | Boston, Massachusetts |
| Normal device | Company-issued MacBook using Chrome |
| Expected access | Google Workspace and customer-support tools |
| Sensitive access | No stated business need for the Admin Dashboard |
| Related assets | HP-AST-001 Okta; HP-AST-006 Admin Dashboard |
| Related risks | HP-RISK-001 identity takeover; HP-RISK-006 improper privileged activity |
| Evidence source | [simulated-login-events.csv](simulated-login-events.csv) |

## Actions Taken

For this tabletop, I:

1. ordered all six events by timestamp;
2. compared location, device, event type, and result;
3. compared the dashboard request with the user's fictional access profile;
4. separated direct observations from interpretations and missing evidence;
5. selected an investigation decision based only on the available fields; and
6. identified the additional evidence needed before calling the event an account takeover.

I did not contact a user, revoke a session, reset a password, or query a real system.

## Timeline

| Time | Event | Context | Result | Analyst note |
|---|---|---|---|---|
| 09:04:12 | Okta login | Boston; known MacBook and Chrome | Success | Matches the fictional baseline. |
| 09:07:33 | Google Workspace access | Boston; known MacBook and Chrome | Success | Expected activity after the successful sign-in. |
| 09:22:08 | Okta login attempt | Unusual location; unknown device | Failed | Requires validation because context differs from baseline. |
| 09:23:01 | MFA challenge | Unusual location; unknown device | Failed | Shows an unsuccessful challenge; does not show why it failed or whether the password was valid. |
| 09:31:45 | Admin Dashboard access | Boston; known MacBook and Chrome | Denied | Sensitive and outside the stated access need; session correlation is missing. |
| 09:34:18 | Okta risk alert | System generated | Generated | Simulated alert based on unusual location and failed MFA. |

## Findings

### Observed facts

- The normal and unusual sign-in events are 18 minutes apart.
- The unusual sign-in and MFA challenge both failed.
- The unusual activity used an unknown device label and different location label.
- The Admin Dashboard request was denied.
- The fictional user profile states that Maya does not normally require dashboard access.

### Reasonable inferences

- The unusual login sequence could represent mistyped credentials, a user traveling or using a privacy service, credential testing, phishing, or an account-takeover attempt.
- The denied dashboard request deserves correlation because it targets a sensitive system outside the user's expected access.
- MFA may have prevented access, but the available fields are not enough to confirm which authentication stage stopped the attempt.

### Unknowns

- Whether Maya recognizes either unusual event
- Source and destination IP addresses
- Session, request, or correlation identifiers
- Whether the password was accepted before the MFA challenge
- Which MFA method was used and whether any prompt reached the user
- Device fingerprint, browser version, network owner, and reputation
- Whether the dashboard request used the original Boston session
- Whether similar attempts affected other users
- Whether the account's roles or group memberships recently changed

## Decision

**Tabletop disposition: escalate for user validation and short-term containment; do not label as confirmed compromise.**

The combination of unusual authentication context and a sensitive access attempt creates enough risk to act quickly. At the same time, the failed results and missing correlation data do not support a definitive incident conclusion.

## Recommended Response

### Immediate actions

1. Ask Maya through a trusted channel whether she recognizes the sign-in, MFA prompt, and dashboard request.
2. Review active sessions and revoke sessions that cannot be tied to known activity.
3. Reset the password if the activity is unrecognized or credential exposure is suspected.
4. Review MFA method enrollment and recent changes.
5. Confirm that Maya has no Admin Dashboard role or group assignment.
6. Search for the same IP, device, location, or failure pattern across other users.

### Control improvements

- Require phishing-resistant authentication for privileged roles where practical.
- Alert on unusual context combined with failed MFA or sensitive-resource access.
- Maintain role-based access and recurring recertification for the Admin Dashboard.
- Preserve identity, application, and endpoint fields needed for session correlation.
- Define a response procedure that includes user validation, session revocation, role review, and evidence preservation.

## Evidence Needed For A Technical Version

| Evidence | Purpose |
|---|---|
| Raw authentication event with event and session IDs | Correlate attempts and determine authentication stage |
| MFA event details | Identify factor, prompt, result, and enrollment changes |
| IP and network context | Compare geography, provider, reputation, and other affected accounts |
| Device details | Distinguish managed, known, new, or spoofed device context |
| Admin Dashboard authorization log | Identify requested action, session, policy, and denial reason |
| User and group history | Confirm expected access and recent changes |
| User validation record | Establish whether the activity was recognized |

## Limitations

- The location labels are generic and cannot support an impossible-travel calculation.
- A failed MFA field alone does not prove that MFA blocked an attacker.
- A denied dashboard request does not prove malicious intent.
- No source is available to validate event completeness or timestamp accuracy.
- The response actions are recommendations only; none were performed.

## References

- [HarborPay risk register](../02-risk-and-controls/risk-register.md)
- [HarborPay control mapping](../02-risk-and-controls/control-mapping.md)
- [NIST CSF 2.0 and other primary sources](../SOURCES.md)

## What I Learned

The most important lesson was to avoid turning a suspicious pattern into a confirmed story. A junior analyst still needs to be decisive, but the decision can be "contain and investigate" while clearly stating what the evidence proves, what it suggests, and what remains unknown.

## Interview Explanation

> I created a six-event IAM tabletop for a fictional fintech user. I built a timeline, separated facts from inferences, identified missing correlation fields, and chose to escalate for validation without calling it a confirmed compromise. My next step is to reproduce a similar scenario with lab-generated authentication evidence.
