# 05 - Wazuh Homelab

This is the first hands-on part of the HarborPay portfolio. I installed a local Wazuh environment with Docker, connected my Mac as an endpoint, and confirmed that the agent appeared as active. The next milestone is to generate and investigate controlled events.

## Files

- [Setup notes](setup-notes.md): what I actually configured, observed, and learned.
- [Controlled-event plan](controlled-event-plan.md): two safe investigations I still need to perform.
- [Evidence guidance](evidence/README.md): rules for adding useful, sanitized proof.
- [Shared triage template](../08-report-templates/triage-note-template.md): report structure for each event.

## Status

**Setup complete; investigations pending.** Installing the platform and connecting an agent is a real milestone, but it is not the same as investigating an alert. I will consider this section technically complete after I document two controlled events, the evidence behind them, and one final mini-incident report.

## Project Connection

- Assets: HP-AST-008 Employee MacBooks and HP-AST-010 Wazuh
- Risks: HP-RISK-008 endpoint compromise and HP-RISK-010 incomplete monitoring
- Control areas: secure configuration, vulnerability management, audit logging, continuous monitoring, and incident analysis

## Next Action

Restart the lab, confirm the manager, indexer, dashboard, and agent are healthy, then complete **Test 1 - File Integrity Monitoring** in the controlled-event plan with guidance.
