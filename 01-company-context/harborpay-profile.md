# HarborPay Profile And Assessment Scope

## Company Summary

HarborPay is a fictional Boston-based fintech company with approximately 120 employees. It provides small businesses with payment, invoice, and transaction-management services through a customer-facing web application.

I created HarborPay to give this portfolio one consistent business setting. A fintech scenario lets me connect identity, cloud, software, customer data, vendors, endpoints, monitoring, and business continuity without claiming access to a real company's systems.

## Operating Model

| Area | Scenario assumption |
|---|---|
| Workforce | Approximately 120 hybrid employees in engineering, product, customer operations, finance, IT, and security |
| Customers | Small businesses using HarborPay to manage invoices and payment activity |
| Identity | Okta provides workforce identity and single sign-on |
| Collaboration | Google Workspace supports email, documents, and shared drives |
| Cloud | AWS hosts application infrastructure and data services |
| Development | GitHub stores application and infrastructure code |
| Payments | Stripe provides payment-processing services |
| Endpoints | Employees use company-managed MacBooks |
| Monitoring | Wazuh collects endpoint and security data in the lab scenario |

## Data Classes

| Classification | Examples | Handling expectation |
|---|---|---|
| Public | Marketing pages and public help content | May be shared publicly after approval |
| Internal | Procedures, project notes, and general operations data | Available to authorized employees |
| Confidential | Employee data, contracts, source code, and non-public business records | Access is limited by role and business need |
| Restricted | Customer records, authentication data, payment-related metadata, and security credentials | Strongest access, logging, encryption, and review requirements |

The portfolio does not contain real customer, payment, employee, or company data.

## Business Priorities

1. Keep customer-facing payment and invoice services available.
2. Protect customer and business information.
3. Restrict privileged access to internal and cloud systems.
4. Detect activity that could affect customer trust or operations.
5. Manage critical third-party dependencies.
6. Produce evidence that security controls are designed and operating as expected.

## Assessment Scope

The current portfolio includes ten assets:

- Okta
- Google Workspace
- AWS account
- Customer database
- HarborPay web application
- Admin dashboard
- GitHub repositories
- Employee MacBooks
- Stripe
- Wazuh

The portfolio evaluates scenario risks and control objectives for those assets. It does not evaluate source code, production infrastructure, real vendor evidence, or a real company's compliance status.

## Explicit Assumptions

- Listed controls are assumed design elements until technical evidence validates them.
- HarborPay does not store full payment-card numbers in its customer database.
- The internal admin dashboard contains sensitive customer-service functions.
- Okta is the primary workforce identity provider.
- Wazuh is a learning environment, not HarborPay's real production monitoring platform.
- Risk ratings reflect the fictional scenario and my documented scoring method.

## Out Of Scope

- Legal or regulatory compliance conclusions
- Penetration testing of real services
- Claims about Stripe, Okta, AWS, GitHub, Google, or Wazuh security performance
- Real customer or employee data
- Production incident response

## Why This Scope Is Useful

The scope is intentionally small. Ten connected assets are enough to show how a single identity issue can affect cloud resources, code, customer data, internal tools, and vendor access. Keeping the scope controlled also makes it easier for me to explain the reasoning behind each risk in an interview.
