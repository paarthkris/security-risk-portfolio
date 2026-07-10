# HarborPay Asset Inventory Brainstorm

## Goal

Build a realistic asset inventory for **HarborPay**, a fictional Boston fintech company.

This list should include normal business systems, but it should also focus on assets that are commonly vulnerable in real corporate environments.

The point is to make the portfolio feel practical, not like a generic classroom example.

## Research-Informed Risk Themes

Recent breach and security guidance points toward a few major risk areas:

- Public-facing systems and unpatched software are major initial access points.
- Identity systems and stolen credentials remain a common path into companies.
- Cloud storage and cloud permissions are easy to misconfigure.
- Code repositories and CI/CD pipelines can expose secrets or become deployment attack paths.
- Third-party vendors create real supply chain and data handling risk.
- Weak logging makes attacks harder to detect and investigate.
- AI tools create new data leakage and governance questions.

## High-Priority Vulnerable Corporate Assets

These are the assets HarborPay should include because they are realistic, vulnerable, and useful for a strong cybersecurity/GRC portfolio.

| Priority | Asset | Category | Why It Is Vulnerable In Real Life | Portfolio Angle |
|---|---|---|---|---|
| Critical | Okta | Identity | If attackers compromise SSO, they may reach many connected systems | IAM risk, MFA, conditional access, access reviews |
| Critical | Admin Accounts | Identity | Admin accounts can change settings, create users, and bypass normal limits | Privileged access management |
| Critical | AWS IAM Roles | Cloud Identity | Overly broad cloud permissions can expose data or infrastructure | Least privilege and cloud risk |
| Critical | Customer Database | Data | Customer data is one of the highest-value targets | Data classification and access control |
| Critical | Public Web App | Application | Public-facing apps can be attacked through vulnerabilities | OWASP Top 10 and secure coding |
| Critical | Admin Dashboard | Application | Internal admin panels can expose customer or payment data | RBAC and sensitive function protection |
| High | GitHub Repositories | Code | Secrets, API keys, and vulnerable code can leak through repos | Secret scanning and code review |
| High | GitHub Actions / CI-CD | Code Pipeline | Build pipelines can be abused to deploy malicious code or steal secrets | CI/CD security controls |
| High | AWS S3 Buckets | Cloud Storage | Misconfigured storage can accidentally expose data publicly | Cloud storage permissions |
| High | VPN / Remote Access | Network Access | Remote access systems are often targeted and must be patched quickly | Patch management and access monitoring |
| High | Employee MacBooks | Endpoints | Lost, infected, or unmanaged laptops can expose data and credentials | Endpoint security and device compliance |
| High | Email / Google Workspace | Communication | Email is a major phishing and account takeover target | Phishing, MFA, mail security |
| High | Slack | Communication | Sensitive info and tokens may be shared casually | Data leakage and retention |
| High | Stripe | Payments Vendor | Payment platforms are critical third-party dependencies | Vendor risk and payment data handling |
| High | Payroll / HR System | HR Vendor | Contains employee personal and tax data | Sensitive data and vendor controls |
| High | Logging Platform / Wazuh | Security Monitoring | If logs are missing or ignored, attacks are harder to catch | Detection and investigation |
| Medium/High | Jira | Work Management | Tickets may reveal vulnerabilities, incidents, and system details | Access control and data minimization |
| Medium/High | Google Drive | Documents | Oversharing can expose contracts, customer data, or security docs | Sharing controls and DLP |
| Medium/High | Password Manager | Secrets | A compromise can expose many credentials | Vault access and MFA |
| Medium/High | AI Tools | AI / Productivity | Employees may paste sensitive data into tools without realizing the risk | AI governance and acceptable use |
| Medium/High | Vendor List / GRC Tracker | GRC | Poor vendor tracking makes third-party risk invisible | Vendor risk management |
| Medium/High | Backup Storage | Resilience | Weak backup protection can worsen ransomware impact | Recovery and business continuity |
| Medium/High | Security Policies | Governance | Policies that are outdated or ignored do not reduce real risk | Policy review and control evidence |
| Medium | Zoom | Communication | Recordings can contain sensitive discussions | Meeting security and retention |
| Medium | Developer Laptops | Endpoints | Developers often have code, credentials, and cloud access | Endpoint and developer access risk |

## Recommended First Version

Start with 20 assets instead of trying to document everything at once.

### Core 10

| Asset ID | Asset | Category | Why It Belongs |
|---|---|---|---|
| HP-AST-001 | Okta | Identity | Main login system for employees |
| HP-AST-002 | Google Workspace | Communication / Documents | Email, files, and company docs |
| HP-AST-003 | AWS Account | Cloud | Main cloud environment |
| HP-AST-004 | Customer Database | Data | Stores sensitive customer records |
| HP-AST-005 | HarborPay Web App | Application | Public-facing customer application |
| HP-AST-006 | Admin Dashboard | Application | Internal tool with sensitive access |
| HP-AST-007 | GitHub Repositories | Code | Stores code and possible secrets |
| HP-AST-008 | Employee MacBooks | Endpoints | Main employee devices |
| HP-AST-009 | Stripe | Payments Vendor | Handles payment processing |
| HP-AST-010 | Wazuh | Security Monitoring | SIEM/log monitoring tool |

### Add These 10 To Make It More Realistic

| Asset ID | Asset | Category | Why It Belongs |
|---|---|---|---|
| HP-AST-011 | AWS IAM Roles | Cloud Identity | Common source of over-permissioning |
| HP-AST-012 | AWS S3 Buckets | Cloud Storage | Common source of accidental data exposure |
| HP-AST-013 | GitHub Actions / CI-CD | Code Pipeline | Can expose secrets or affect deployments |
| HP-AST-014 | VPN / Remote Access | Network Access | Frequently targeted access path |
| HP-AST-015 | Admin Accounts | Identity | High-impact privileged access |
| HP-AST-016 | Password Manager | Secrets | Stores sensitive credentials |
| HP-AST-017 | Slack | Communication | Informal sensitive data exposure risk |
| HP-AST-018 | Payroll / HR System | HR Vendor | Stores employee personal data |
| HP-AST-019 | AI Tools | AI / Productivity | Raises data leakage and governance concerns |
| HP-AST-020 | Backup Storage | Resilience | Critical for ransomware recovery |

## Best Assets For The First Risk Register

These are the strongest first assets to turn into risks:

1. Okta
2. Admin accounts
3. AWS IAM roles
4. Customer database
5. Public web app
6. Admin dashboard
7. GitHub repositories
8. GitHub Actions / CI-CD
9. AWS S3 buckets
10. VPN / remote access
11. Employee MacBooks
12. Google Workspace
13. Wazuh/logging
14. Stripe
15. AI tools

## Beginner-Friendly Risk Examples

| Asset | Risk Example | Plain-English Meaning |
|---|---|---|
| Okta | Weak MFA or risky login rules | Someone could log in as an employee |
| Admin Accounts | Too many admins | Too many people can make dangerous changes |
| AWS IAM Roles | Over-permissioned roles | Cloud accounts can access more than they should |
| S3 Buckets | Public data exposure | Files could accidentally become public |
| GitHub | Secrets in code | API keys or passwords could leak |
| CI/CD | Pipeline secret theft | Build tools could expose production credentials |
| VPN | Unpatched remote access tool | Attackers could exploit the doorway into the company |
| Customer Database | Excessive access | Employees may see data they do not need |
| Wazuh | Missing logs | The company may not notice an attack |
| AI Tools | Sensitive prompt leakage | Employees may paste private data into AI tools |

## Next Step

Turn the recommended 20 assets into a formal `asset-inventory.md` with these columns:

- Asset ID
- Asset Name
- Category
- Owner
- Description
- Data Sensitivity
- Business Criticality
- Internet-Facing
- Main Risks
- Existing Controls
- Notes

