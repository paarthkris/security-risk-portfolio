# HarborPay IAM Investigation Report

## Purpose

This is the first hands-on investigation writeup for the HarborPay security portfolio.

I created this lab to practice investigating suspicious login activity from an identity and access management perspective. The goal is to understand what evidence matters, how to explain the risk, and what controls I would recommend.

This is a simulated lab, not a real incident.

## Scenario Summary

A HarborPay employee account showed unusual sign-in activity.

The employee successfully logged in from Boston during normal work hours. Shortly after, there was a failed login attempt from an unusual location. Later, the same account attempted to access the HarborPay Admin Dashboard.

This scenario connects to:

- HP-AST-001: Okta
- HP-AST-006: Admin Dashboard
- HP-RISK-001: Okta account takeover
- HP-RISK-006: Admin dashboard excessive access

## Simulated User

| Field | Value |
|---|---|
| Employee Name | Maya Chen |
| Department | Customer Operations |
| Normal Location | Boston, MA |
| Normal Device | Company-issued MacBook |
| Normal Access | Google Workspace, Slack, customer support tools |
| Sensitive Access | No regular admin dashboard access |
| MFA Status | Enrolled |

## Investigation Timeline

| Time | Event | Location | Device | Result | Notes |
|---|---|---|---|---|---|
| 9:04 AM | Okta login | Boston, MA | Known MacBook | Success | Normal login pattern. |
| 9:07 AM | Google Workspace access | Boston, MA | Known MacBook | Success | Expected after login. |
| 9:22 AM | Okta login attempt | Unusual foreign location | Unknown browser/device | Failed | Suspicious because it is soon after a Boston login. |
| 9:23 AM | MFA challenge | Unusual foreign location | Unknown browser/device | Failed | MFA appears to have blocked access. |
| 9:31 AM | Admin Dashboard access attempt | Boston, MA | Known MacBook | Denied | User does not normally need admin dashboard access. |
| 9:34 AM | Okta risk alert generated | System event | N/A | Alert | Flagged for unusual location and failed MFA. |

## Evidence Reviewed

| Evidence | What I Looked For | What I Found |
|---|---|---|
| Okta sign-in logs | Login time, location, device, result | Normal Boston login followed by suspicious failed login attempt. |
| MFA logs | Whether MFA was completed | MFA failed during the unusual login attempt. |
| Device details | Known vs unknown device | Suspicious login came from an unknown browser/device. |
| Admin Dashboard access logs | Whether sensitive access was attempted | Access was attempted but denied. |
| User access profile | Whether user needed admin access | User does not normally require admin dashboard access. |

## Initial Assessment

This looks like a possible account takeover attempt or credential stuffing attempt.

The suspicious login did not succeed because MFA failed. However, the event is still important because it suggests that the employee's password may have been known, guessed, reused, or phished.

The admin dashboard access attempt also matters because the user does not normally need that access. Even though access was denied, it creates a reason to review whether the account, session, or device activity should be investigated further.

## Risk Statement

If an attacker compromises an employee identity account, they may be able to access connected systems, view sensitive data, or attempt privileged actions through internal applications.

For HarborPay, this could affect customer trust, internal operations, and sensitive customer information.

## Risk Rating

| Category | Rating | Reason |
|---|---|---|
| Likelihood | Medium | The suspicious login failed, but the attempt was realistic and identity attacks are common. |
| Impact | High | Account compromise could affect multiple connected systems. |
| Priority | High | The account should be reviewed quickly, especially because of the admin dashboard access attempt. |

## Recommended Immediate Actions

| Action | Why |
|---|---|
| Confirm with the employee whether they recognize the activity. | Helps determine if the login attempt was legitimate or suspicious. |
| Reset the user's password if activity is not recognized. | Reduces risk if the password was exposed. |
| Review active sessions and revoke suspicious sessions. | Prevents continued access from risky sessions. |
| Review MFA logs and device details. | Confirms whether MFA protected the account. |
| Check whether the user should have any admin dashboard permissions. | Supports least privilege. |
| Monitor the account for additional suspicious activity. | Helps detect continued attack attempts. |

## Recommended Control Improvements

| Control | Recommendation |
|---|---|
| MFA | Keep MFA required for all users and evaluate stronger MFA for privileged users. |
| Conditional Access | Add rules for unusual locations, impossible travel, and unknown devices. |
| Access Reviews | Review admin dashboard access on a regular schedule. |
| Alerting | Generate alerts for failed MFA attempts from unusual locations. |
| User Awareness | Remind users how to report suspicious login prompts or phishing attempts. |
| Logging | Retain sign-in logs and admin dashboard access logs for investigations. |

## Business Explanation

The main business issue is not just that someone tried to log in. The bigger issue is that one employee account can become a doorway into multiple HarborPay systems.

Okta connects to tools like Google Workspace, internal apps, and possibly engineering or support tools. If identity controls are weak, the company could lose control over who is accessing sensitive systems.

## What I Learned

This lab helped me understand why IAM is such an important part of security.

The suspicious login itself was simple, but it connected to multiple areas:

- MFA
- Login monitoring
- Device trust
- Access reviews
- Least privilege
- Admin dashboard protection
- User awareness

I also learned that a failed login can still be worth investigating if it shows signs of password exposure or account targeting.

## Interview Talking Point

I would explain this lab by saying:

> I created a simulated IAM investigation for a fictional fintech company. I reviewed a suspicious login timeline, looked at MFA and device evidence, connected the activity to business risk, and recommended controls like conditional access, session review, access recertification, and stronger monitoring.

## Next Steps

This IAM scenario can be reused in two future technical builds:

1. **Wazuh Homelab**
   Create or simulate related log events and practice alert review.

2. **AI GRC n8n Workflow**
   Feed this incident summary into an AI workflow that drafts related risks, controls, evidence requests, and recommendations for human review.

