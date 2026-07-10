# HarborPay Vendor Risk Review: Stripe

## Overview

This document is a first vendor risk review for **Stripe**, which HarborPay uses as its payment processing vendor.

I chose Stripe because HarborPay is a fictional fintech company, so payment processing is one of the most important third-party dependencies. If Stripe has an outage, security incident, access control issue, or contract gap, HarborPay's customers and business operations could be affected.

This is not a real audit of Stripe. It is a portfolio exercise to practice how a GRC, cybersecurity, or technology risk analyst might review a critical vendor.

## Why This Vendor Matters

Stripe matters to HarborPay because it supports payment-related workflows. Even if HarborPay does not store full payment card data directly, the company still depends on Stripe for business-critical operations.

The main risks I want to understand are:

- Can HarborPay trust Stripe to protect payment-related data?
- Who at HarborPay has access to Stripe?
- What happens if Stripe has an outage?
- How would HarborPay find out if Stripe had a security incident?
- What evidence would HarborPay collect to prove this vendor is being reviewed?

## My Assumptions

- HarborPay uses Stripe to process payments for small business customers.
- HarborPay employees may access Stripe through an admin console.
- HarborPay does not directly store full card numbers in its own customer database.
- Stripe is a critical vendor because payment disruption could affect customers and revenue.
- This review focuses on vendor risk, access control, incident notification, business continuity, and evidence collection.

## Vendor Profile

| Field | Details |
|---|---|
| Vendor Name | Stripe |
| Vendor Type | Payment Processing Vendor |
| HarborPay Owner | Finance / Product |
| Business Purpose | Supports customer payment workflows |
| Related HarborPay Asset | HP-AST-009: Stripe |
| Related Risk | HP-RISK-009: Payment processing disruption or vendor security issue |
| Data Sensitivity | High |
| Business Criticality | Critical |
| Review Type | Initial vendor risk review |
| Review Status | Draft |

## Key Risk Areas

| Risk Area | Why It Matters |
|---|---|
| Data Protection | Stripe may process payment-related data connected to HarborPay customers. |
| Access Control | HarborPay needs to know who can access the Stripe admin console. |
| Incident Notification | HarborPay needs to know how and when Stripe would report a security issue. |
| Availability | If Stripe is unavailable, HarborPay's payment workflows may be disrupted. |
| Compliance | Payment processing usually involves security and compliance requirements. |
| Vendor Dependency | HarborPay relies on Stripe for a critical business function. |

## Vendor Risk Questionnaire

| Question ID | Question | Why I Am Asking | Expected Evidence |
|---|---|---|---|
| VRQ-001 | What services does Stripe provide to HarborPay? | I need to understand the exact business dependency before judging risk. | Vendor contract, system diagram, product owner notes |
| VRQ-002 | What types of data does Stripe process for HarborPay? | Data type affects sensitivity and control requirements. | Data flow diagram, vendor documentation, privacy terms |
| VRQ-003 | Does Stripe provide a SOC 2 report or similar security assurance report? | A SOC 2 report helps show whether the vendor has reviewed security controls. | SOC 2 Type II report or security documentation |
| VRQ-004 | Who at HarborPay has admin access to Stripe? | Vendor admin access should be limited and reviewed. | Stripe user list, admin role list, access review evidence |
| VRQ-005 | Is MFA required for HarborPay users accessing Stripe? | MFA reduces the chance of account takeover. | MFA settings screenshot or admin security settings |
| VRQ-006 | Are Stripe admin actions logged? | Logs help investigate suspicious changes or payment issues. | Audit logs, admin activity report |
| VRQ-007 | How does Stripe notify customers about security incidents? | HarborPay needs to know how quickly it would learn about a vendor issue. | Contract terms, incident notification policy |
| VRQ-008 | How does Stripe handle outages or service disruptions? | Payment downtime could affect HarborPay customers and revenue. | Status page, SLA, business continuity documentation |
| VRQ-009 | Where is HarborPay's payment-related data stored or processed? | Data location can affect privacy and compliance questions. | Vendor documentation, data processing agreement |
| VRQ-010 | Can HarborPay export or delete its data from Stripe if needed? | Exit planning matters if HarborPay changes vendors. | Data deletion policy, export documentation |
| VRQ-011 | Does Stripe support least-privilege roles for HarborPay users? | Different employees should not all have full admin permissions. | Role documentation, user permission list |
| VRQ-012 | Does HarborPay have a backup process if Stripe is unavailable? | Business continuity matters for critical vendors. | Internal continuity plan, product owner notes |

## Initial Risk Assessment

| Risk ID | Vendor Risk | Likelihood | Impact | Priority | Notes |
|---|---|---|---|---|---|
| VR-STRIPE-001 | Too many HarborPay employees have Stripe admin access. | Medium | High | High | This is a realistic access control risk and easy to explain in interviews. |
| VR-STRIPE-002 | HarborPay lacks a documented process for Stripe outages. | Medium | High | High | Even if Stripe is secure, availability still matters. |
| VR-STRIPE-003 | HarborPay does not regularly review Stripe users and permissions. | Medium | High | High | This connects vendor risk to IAM and access reviews. |
| VR-STRIPE-004 | HarborPay does not have clear incident notification expectations. | Low / Medium | High | Medium / High | Contract and communication terms matter during vendor incidents. |
| VR-STRIPE-005 | HarborPay does not fully understand what customer/payment data Stripe processes. | Medium | High | High | Data flow clarity is important for privacy, compliance, and security. |

## Evidence I Would Collect

- Stripe contract or service agreement
- Stripe SOC 2 report or security documentation
- Stripe admin user list
- Stripe MFA/security settings
- Stripe audit logs or activity logs
- Stripe role and permission documentation
- Incident notification terms
- Stripe status page or outage history
- Internal HarborPay business continuity plan
- Data flow diagram showing how HarborPay uses Stripe

## Initial Recommendations

| Recommendation | Reason |
|---|---|
| Review all HarborPay users with Stripe access. | Confirms that only approved employees can access payment tools. |
| Require MFA for all Stripe users. | Reduces account takeover risk. |
| Limit admin roles to the smallest group possible. | Supports least privilege. |
| Document what to do during a Stripe outage. | Helps HarborPay respond faster during payment disruption. |
| Collect and review Stripe security documentation annually. | Creates evidence that vendor risk is being monitored. |
| Confirm incident notification expectations. | Helps HarborPay know when and how it would be informed of a vendor issue. |
| Build a simple Stripe data flow diagram. | Makes the vendor relationship easier to explain and assess. |

## What I Learned

This vendor review helped me see that vendor risk is not just about whether a vendor is "secure." It is also about how the company uses the vendor, who has access, what data is involved, what happens during an outage, and what evidence the company can collect.

For HarborPay, Stripe is a good example because it connects security, business operations, payments, access control, and customer trust.

## What I Would Explain In An Interview

I would explain that I chose Stripe because fintech companies depend heavily on payment vendors. I would also explain that my review focused on practical questions: access, MFA, logs, SOC 2, incident notification, business continuity, and data flows.

The biggest lesson is that third-party risk is shared risk. HarborPay may not control Stripe's full environment, but HarborPay still needs to manage how it uses Stripe and how it would respond if something went wrong.

## Questions I Want To Decide Next

Before finalizing this section, I want to decide:

1. Should this review stay focused only on Stripe, or should I also create a fictional AI vendor review later?
2. Should I make a simple data flow diagram showing HarborPay, customer, web app, and Stripe?
3. Should I create a shorter executive summary version of this review for non-technical readers?
4. Should I add a vendor risk score using categories like Low, Medium, High, and Critical?

