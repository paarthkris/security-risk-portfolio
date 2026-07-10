# HarborPay Executive Summary

## Summary

HarborPay is a fictional Boston-based fintech company that relies on cloud infrastructure, identity systems, payment vendors, employee devices, source code repositories, customer data, and security monitoring.

I created this project to practice thinking like a cybersecurity, GRC, and technology risk analyst. The documentation work gives the project a realistic business context, while the technical labs will show hands-on work with IAM investigation, Wazuh monitoring, secure Java development, and AI-assisted GRC workflows.

## Scope

The first version of the project focuses on 10 core HarborPay assets:

1. Okta
2. Google Workspace
3. AWS Account
4. Customer Database
5. HarborPay Web App
6. Admin Dashboard
7. GitHub Repositories
8. Employee MacBooks
9. Stripe
10. Wazuh

These assets were selected because they represent realistic areas of corporate security risk: identity, email, cloud, customer data, applications, code, endpoints, vendors, and monitoring.

## Highest Priority Risks

The highest priority risks identified so far are:

| Risk | Why It Matters |
|---|---|
| Okta account takeover | A compromised identity account could open access to many company systems. |
| AWS misconfiguration | Cloud permission or exposure mistakes could affect sensitive systems or data. |
| Customer database unauthorized access | Customer data exposure would create major business and trust impact. |
| Web app vulnerabilities | The public-facing app is directly reachable by customers and attackers. |
| Admin dashboard excessive access | Internal privileged tools can expose or modify sensitive customer records. |
| Incomplete logging in Wazuh | If logs or alerts are missing, suspicious activity may not be detected quickly. |

## Key Control Themes

The project currently focuses on these control areas:

- Identity and access management
- Least privilege
- MFA and suspicious login review
- Cloud configuration and permissions
- Data protection
- Application security
- Vendor risk management
- Endpoint security
- Logging, monitoring, and investigation
- Human-reviewed AI assistance for GRC work

## Technical Build Direction

The documentation is intentionally lightweight support material. The main value of this portfolio will come from the technical work:

1. **IAM Investigation Lab**
   Simulate suspicious login activity, review evidence, and recommend controls.

2. **Wazuh Homelab**
   Set up Wazuh, collect logs, trigger test alerts, and write investigation notes.

3. **Secure Java App**
   Build an access request tracker with roles, approvals, input validation, logging, and security review.

4. **AI GRC n8n Workflow**
   Use n8n and AI to turn incident or vendor notes into structured risks, controls, evidence requests, and recommendations with human review.

## What I Want To Be Able To Explain

By the end of this project, I want to be able to explain:

- Why asset inventory comes before risk analysis
- How identity risk can turn into business risk
- How logs support investigation and control testing
- How vendor risk connects to access, availability, contracts, and evidence
- How secure application design connects to least privilege and OWASP concepts
- How AI can support GRC work without replacing human judgment

## Current Recommendation

The project should now move from documentation into hands-on build work.

Recommended build order:

1. IAM Investigation Lab
2. Wazuh Homelab
3. Secure Java Access Request App
4. AI GRC n8n Workflow

