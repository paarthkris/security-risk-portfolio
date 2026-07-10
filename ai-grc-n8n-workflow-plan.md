# AI GRC n8n Workflow Plan

## Purpose

This project will add an AI and automation layer to the HarborPay security portfolio.

The goal is to use **n8n** as a workflow tool that takes messy security or GRC notes and turns them into structured outputs:

- Risks
- Related assets
- Control gaps
- Evidence requests
- Recommended next steps
- Human review notes

## Why n8n

n8n is useful because it lets me build a visual workflow instead of only writing code.

For this portfolio, n8n can act as the automation layer between:

- A form input
- An AI model
- A structured risk/control template
- A human review step
- A final output document or spreadsheet

## Important Principle

The AI should not be treated as the final decision-maker.

The workflow should clearly show:

> AI can assist with drafting risk analysis, but a human must review the output before it is trusted.

That is important for AI governance and responsible use.

## Example Inputs

The workflow should accept inputs like:

- Suspicious login summary
- Wazuh alert summary
- Vendor risk finding
- Policy excerpt
- Admin access concern
- Java app security finding

## Example Workflow

1. User submits an incident or finding through a form.
2. n8n sends the text to an AI model.
3. AI extracts the main issue.
4. AI identifies related HarborPay assets.
5. AI drafts possible risks.
6. AI suggests NIST/CIS control areas.
7. AI lists evidence to request.
8. AI drafts recommendations.
9. Human reviews and edits the output.
10. Final output is saved as Markdown, Google Docs, Notion, or a spreadsheet row.

## First Use Case

The first use case should be:

**Turn an IAM suspicious login summary into a GRC risk note.**

Example input:

> A HarborPay employee account had a successful login from Boston at 9:04 AM, followed by a failed login from an unusual location at 9:22 AM. The account later attempted to access the Admin Dashboard.

Expected output:

- Related assets: Okta, Admin Dashboard
- Risk: Possible account takeover
- Control gaps: conditional access, alert triage, admin access review
- Evidence needed: sign-in logs, MFA status, device details, admin role list
- Recommendations: investigate session, reset password if needed, review MFA, review admin access
- Human review: required

## Planned Deliverables

- n8n workflow diagram or exported workflow
- `ai-grc-assistant/README.md`
- Example input and output
- Human review checklist
- Notes on limitations
- Screenshot of workflow

## Human Review Checklist

Before accepting AI output, review:

- Are the related assets correct?
- Is the risk realistic?
- Are the controls relevant?
- Is the evidence request practical?
- Are recommendations too vague?
- Did the AI invent facts?
- Is anything sensitive included that should be removed?

## Stretch Goals

- Connect the workflow to Google Sheets.
- Connect the workflow to GitHub Issues.
- Create a reusable risk note template.
- Add a confidence field.
- Add a human approval step.
- Use local AI for privacy-focused testing.
- Use Wazuh alert summaries as inputs.

## What I Would Explain In An Interview

I would explain that I built this workflow to explore how AI can support GRC work without replacing human judgment.

The strongest point is that the workflow creates structure from messy security notes, but still requires human review before the output is used.

## Build Status

Planned. The next step is to install or access n8n and design the first workflow around the IAM investigation lab.

