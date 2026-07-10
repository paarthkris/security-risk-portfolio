# HarborPay Secure Java App Plan

## Purpose

This project will connect my Java and object-oriented design learning to cybersecurity and GRC.

The goal is to build a small HarborPay internal application, then review it from a security perspective.

## App Idea

**HarborPay Access Request Tracker**

Employees use the app to request access to systems like:

- GitHub
- AWS
- Stripe
- Admin Dashboard
- Google Workspace shared drives

Managers or admins can approve, reject, or review requests.

## Why This App Fits

This app fits the portfolio because it connects directly to:

- Least privilege
- Role-based access control
- Access reviews
- Admin approvals
- Audit logging
- IAM and GRC workflows

It also gives me a realistic way to practice Java, classes, objects, validation, and basic application design.

## Core Features

| Feature | Security Concept |
|---|---|
| User accounts | Identity and authentication |
| Roles | Role-based access control |
| Access requests | Least privilege and approval workflow |
| Approval/rejection | Governance and accountability |
| Request history | Audit trail |
| Input validation | Secure coding |
| Basic logging | Monitoring and investigation |

## Suggested Roles

| Role | What The Role Can Do |
|---|---|
| Requester | Submit access requests and view own requests. |
| Manager | Approve or reject team requests. |
| Admin | Manage users, systems, and requests. |
| Auditor | View request history and logs without making changes. |

## First Version Scope

The first version should be simple:

- Console app or basic web app
- Hardcoded users at first
- Create request
- Approve request
- Reject request
- View request history
- Basic logging

## Security Features To Add

- Role checks before sensitive actions
- Input validation for request fields
- Logging for approvals and rejections
- Simple audit trail
- Dependency scanning
- OWASP Top 10 review
- Threat model

## Planned Deliverables

- `java-secure-app/README.md`
- Java source code
- `threat-model.md`
- `owasp-review.md`
- Screenshots or demo output
- Short reflection on what I learned

## Threat Model Questions

- Who can submit a request?
- Who can approve a request?
- Can someone approve their own request?
- Can a user view someone else's request?
- What happens if bad input is entered?
- Are actions logged?
- What data should not be exposed?

## What I Would Explain In An Interview

I would explain that I built this app to connect secure coding and GRC.

Instead of building a random Java app, I chose access requests because it connects to real security work: least privilege, approvals, audit trails, role-based access, and evidence collection.

## Build Status

Planned. The next step is to decide whether the first version should be a console app or a simple web app.

