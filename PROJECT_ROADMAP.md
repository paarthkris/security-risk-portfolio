# HarborPay Project Roadmap

Last updated: July 2026

## Why This File Exists

This is the one file I can return to whenever I am unsure what the project is, what is finished, or what I should do next.

The project has two goals:

1. Show that I can think clearly about security risk, controls, evidence, and business impact.
2. Build technical experience that I can demonstrate and explain without overstating what I have done.

I do not need to complete everything at once. Each technical phase should produce one small, defensible result before I add more tools or complexity.

## Project Story

HarborPay is a fictional Boston fintech company with approximately 120 employees. It uses Okta, Google Workspace, AWS, GitHub, Stripe, employee MacBooks, customer-facing applications, an internal admin dashboard, and Wazuh.

The portfolio follows a practical sequence:

```text
Company context -> Assets -> Risks -> Controls -> Evidence -> Investigation -> Remediation -> Lessons learned
```

The documentation establishes the scenario. The technical labs test parts of that scenario and create evidence I can discuss in interviews.

## Current Status

| Workstream | What Exists Now | Status | What Is Still Needed |
|---|---|---|---|
| Company context | Company profile, scope, assumptions, data classes | Complete | Update only if the scenario changes |
| Asset inventory | Ten core assets with owners, exposure, and evidence needs | Complete | Add assets only when a lab requires them |
| Risk register | Ten scored risk scenarios with treatments and owners | Complete | Reassess after technical findings exist |
| Control mapping | NIST CSF 2.0 and CIS Controls v8.1 category mapping | Complete | Add exact test results after labs |
| Executive summary | Business-level summary and priorities | Complete | Rewrite at final portfolio completion |
| Vendor risk | Simulated Stripe pre-assessment and evidence plan | Complete as a scenario | Do not present it as a real Stripe audit |
| IAM case | Simulated events and tabletop investigation | Complete as a tabletop | Rebuild with real lab evidence later |
| Wazuh | Docker stack, dashboard, and Mac agent connection documented | Setup complete | Generate, investigate, and document controlled alerts |
| Secure Java app | Scope, roles, requirements, and design-stage threat model | Specification complete | Build and test the application |
| Local AI GRC assistant | Architecture, schema, safety controls, and evaluation cases | Specification complete | Build locally and evaluate outputs |
| Portfolio reporting | Triage, evidence, and lab-report templates | Complete | Fill them with technical evidence |

## What Counts As Complete

### Documentation completion

A documentation artifact is complete when it:

- states whether the content is real, simulated, assumed, or planned;
- names the asset, risk, control, owner, and evidence involved;
- explains the business impact in plain language;
- uses a consistent structure and terminology;
- includes sources when a framework or tool is referenced; and
- avoids claiming that an untested control works.

### Technical completion

A technical lab is complete only when I can provide:

- the objective and environment;
- commands or configuration I personally used;
- timestamped evidence, logs, or screenshots;
- actions I took during the investigation;
- findings supported by that evidence;
- a decision and recommendations;
- limitations and mistakes; and
- a short explanation in my own words.

## Build Order

### Phase 1 - Wazuh controlled-event investigations

Goal: move from "I installed Wazuh" to "I investigated specific activity."

- [x] Install Docker Desktop.
- [x] Run the Wazuh manager, indexer, and dashboard locally.
- [x] Connect the Mac endpoint as `harborpay-macbook-01`.
- [x] Capture one setup screenshot locally.
- [ ] Add a sanitized replacement; the original exposed a device serial number and is not publishable.
- [ ] Restart the environment and confirm all components are healthy.
- [ ] Record exact versions and non-sensitive configuration details.
- [ ] Generate one safe file-integrity event.
- [ ] Generate one safe privilege/admin event.
- [ ] Find the related alerts or log records.
- [ ] Complete one triage note per event.
- [ ] Capture screenshots that show the relevant evidence, not only the dashboard.
- [ ] Write one final mini-incident report.
- [ ] Map the observed behavior to the correct MITRE ATT&CK technique only when supported.

Definition of done: two controlled events, two triage notes, one concise incident report, and evidence I can explain without reading a script.

### Phase 2 - IAM investigation with real lab evidence

Goal: use the current simulated case as preparation, then perform a reproducible identity-focused investigation.

- [x] Create the simulated Maya Chen login dataset.
- [x] Complete a tabletop analysis of the simulated evidence.
- [ ] Choose the lab source: generated authentication logs, an identity lab, or Wazuh custom logs.
- [ ] Document the authentication flow in my own words.
- [ ] Generate known-good and suspicious test events.
- [ ] Compare user, time, location, device, MFA, and access context.
- [ ] Decide whether to close, contain, or escalate the case.
- [ ] Replace unsupported assumptions with observed evidence.
- [ ] Complete the investigation note template.

Definition of done: a reproducible scenario, evidence table, defensible decision, and clear distinction between what the logs show and what I infer.

### Phase 3 - Secure Java Access Request Tracker

Goal: connect Java and object-oriented design to IAM, least privilege, approval, and auditability.

- [ ] Create the Java project and confirm the build runs.
- [ ] Model users, roles, systems, access requests, and decisions as classes.
- [ ] Implement requester, manager, admin, and auditor permissions.
- [ ] Prevent self-approval.
- [ ] Validate required fields and allowed values.
- [ ] Create an append-only audit record for sensitive actions.
- [ ] Write unit tests for allowed and denied actions.
- [ ] Run dependency and secret scanning.
- [x] Complete the design-stage threat model.
- [ ] Update the threat model against the implemented code.
- [ ] Complete an OWASP ASVS-based review of the implemented features.
- [ ] Add screenshots or a short demo.

Definition of done: working code, tests for security rules, scan results, threat model, and a README that explains design choices and limitations.

### Phase 4 - Local AI GRC Assistant

Goal: use a local model to structure security notes while treating its output as untrusted analysis that requires human review.

- [ ] Install and verify a local model runtime.
- [ ] Make one local API request with no cloud dependency.
- [ ] Define the structured output schema in code.
- [ ] Parse an incident or vendor note into the schema.
- [ ] Validate every response before displaying or saving it.
- [ ] Add citations or source pointers to HarborPay documents.
- [ ] Test prompt injection, missing context, and sensitive-data handling.
- [ ] Add a human approve/reject/edit step.
- [ ] Record model, prompt version, latency, and test result.
- [ ] Document limitations and examples of incorrect output.

Definition of done: a local, reproducible workflow that produces schema-valid drafts, preserves source traceability, and cannot take external actions.

### Phase 5 - Final portfolio polish

- [ ] Replace remaining placeholders with evidence.
- [ ] Remove failed experiments that do not teach anything useful.
- [ ] Verify every internal link.
- [ ] Confirm that screenshots contain no passwords, tokens, private IP details, or personal information.
- [ ] Rewrite the executive summary using final technical results.
- [ ] Add a short architecture diagram for each completed build.
- [ ] Record a two-minute project explanation.
- [ ] Add the project to my resume and LinkedIn only after I can defend the claims.

## Interview Preparation Checklist

For every completed technical artifact, I should be able to answer:

- What problem was I trying to solve?
- Why did I choose this tool or design?
- What did I personally configure or write?
- What evidence did I review?
- What did I initially misunderstand?
- What did the evidence support?
- What did it not prove?
- What decision did I make?
- What would I improve in a real environment?
- How does the work connect to business risk?

## Explanation For Recruiters Or Family

> HarborPay is a fictional fintech company I use to learn cybersecurity in a structured way. I first documented what the company depends on and what could go wrong. I then mapped those risks to controls and evidence. The hands-on part is where I use Wazuh, Java, identity logs, and a local AI model to test specific ideas. Every technical claim is supported by something I configured, observed, or built myself.

## Rules I Will Follow

1. I will not describe a plan as completed work.
2. I will label all fictional data and simulated incidents.
3. I will keep secrets, credentials, and personal information out of GitHub.
4. I will favor two well-explained investigations over many shallow screenshots.
5. I will keep the first version of each build small enough to understand.
6. I will record mistakes and limitations because they demonstrate real learning.
7. I will update this roadmap whenever a phase changes status.
