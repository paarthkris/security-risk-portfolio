# HarborPay IAM Investigation Lab Plan

## Purpose

This lab will simulate an identity and access management investigation for HarborPay.

The goal is to practice how a security or technology risk analyst would investigate suspicious login activity, collect evidence, identify risk, and recommend controls.

## Scenario

An employee account logs in from Boston during normal work hours. Shortly after, there is a suspicious login attempt from an unusual location. The account then tries to access the HarborPay Admin Dashboard.

This scenario is designed to connect back to:

- HP-AST-001: Okta
- HP-AST-006: Admin Dashboard
- HP-RISK-001: Okta account takeover
- HP-RISK-006: Admin dashboard excessive access

## What I Want To Learn

- How authentication works at a high level
- What suspicious login activity can look like
- What evidence matters during an IAM investigation
- Why MFA and conditional access matter
- How to explain identity risk in business language

## Lab Inputs

The lab will use simulated evidence, such as:

- Fake Okta sign-in logs
- User profile details
- MFA status
- Device information
- Location/IP details
- Admin dashboard access attempt
- Short timeline of events

## Investigation Questions

| Question | Why It Matters |
|---|---|
| Was the login successful or blocked? | Determines whether the account may be compromised. |
| Was MFA completed? | Helps understand whether login controls worked. |
| Was the device known or unknown? | Unknown devices may indicate suspicious access. |
| Was the location unusual? | Impossible travel or unusual geography can indicate account takeover. |
| What system was accessed next? | Shows the possible business impact. |
| Does the user normally need admin dashboard access? | Helps evaluate least privilege. |

## Planned Deliverables

- `iam-investigation-report.md`
- Login timeline
- Evidence table
- Risk summary
- Recommended controls
- Interview talking points

## Draft Control Recommendations

- Enforce MFA for all users.
- Review whether phishing-resistant MFA is needed for admins.
- Create conditional access rules for unusual location or device behavior.
- Review Admin Dashboard access monthly or quarterly.
- Alert on impossible travel or suspicious sign-in patterns.
- Disable or investigate risky sessions quickly.

## What I Would Explain In An Interview

I would explain that identity is one of the most important areas in modern security because one compromised account can create access to many systems.

This lab lets me show how I would move from suspicious login evidence to practical recommendations like MFA review, conditional access, access reviews, and alerting.

## Build Status

Planned. The next step is to create simulated login data and write the first investigation report.

