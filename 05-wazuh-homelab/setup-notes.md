# Wazuh Homelab Setup Notes

## Classification

This report describes a real local learning environment that I set up on July 9, 2026. HarborPay is fictional, and this environment is not a production SIEM.

## Summary

I ran a Wazuh 4.14.6 single-node stack through Docker Desktop on an Apple-silicon Mac. The stack included the Wazuh manager, indexer, and dashboard. I then installed the macOS agent, named it `harborpay-macbook-01`, and confirmed that it appeared as active in the dashboard.

This proves that the basic components communicated in my local environment at the time of setup. It does not prove that logging coverage, alert quality, retention, or incident-response procedures are effective.

## Objective

Learn how the main parts of a SIEM environment connect:

```text
Mac endpoint -> Wazuh agent -> Wazuh manager -> Wazuh indexer -> Wazuh dashboard
```

- The **agent** collects supported endpoint information and events.
- The **manager** receives and analyzes agent data against configured rules.
- The **indexer** stores searchable event and alert data.
- The **dashboard** provides the interface used to review endpoints, alerts, inventory, and security views.

## Environment

| Component | Observed setup |
|---|---|
| Host | Personal Apple-silicon Mac used only for the local lab |
| Container runtime | Docker Desktop |
| Wazuh deployment | Local single-node Docker stack |
| Wazuh version | 4.14.6 at setup time |
| Wazuh components | Manager, indexer, dashboard |
| Endpoint agent | Wazuh macOS agent |
| Agent name | `harborpay-macbook-01` |
| Agent status | Active when verified in the dashboard |
| Dashboard address | Localhost over HTTPS |

Credentials, personal paths, hardware identifiers, and generated certificates are intentionally excluded.

## Actions Taken

1. Installed the correct Apple-silicon release of Docker Desktop.
2. Confirmed Docker could pull and run test containers.
3. Started the Wazuh single-node Docker services.
4. Opened the local Wazuh dashboard.
5. Installed the Wazuh macOS agent with administrator approval.
6. Started the agent service and enrolled it with the local manager.
7. Verified `harborpay-macbook-01` appeared as an active endpoint.
8. Reviewed the endpoint summary, including inventory, security-configuration, vulnerability, compliance, and MITRE ATT&CK panels.

## Findings

### Verified observations

- The manager, indexer, and dashboard containers ran together during the setup session.
- The macOS agent enrolled successfully and reported as active.
- Wazuh collected basic endpoint inventory and displayed security-related views.
- The endpoint page displayed MITRE ATT&CK tactic labels for Defense Evasion and Privilege Escalation after administrative setup activity.

### Interpretation

The MITRE labels are context for behaviors associated with an alert or rule; they are not proof that an attacker evaded defenses or escalated privileges. During setup I used administrator privileges and started a background service, which are legitimate actions that can resemble behavior worth monitoring.

The correct analyst response is to open the underlying alert, identify its rule and source event, review the command or process context, and decide whether the activity is expected. The dashboard summary alone is not enough for an incident conclusion.

## Decision

**Setup milestone accepted; investigation milestone remains open.**

The environment was functional enough to move forward, but I need controlled events and alert-level evidence before describing the lab as a security-monitoring investigation.

## Evidence Status

The original endpoint-overview screenshot included a real device serial number, so it is not stored in the portfolio. A publishable replacement must be cropped or redacted and should show the relevant rule, event fields, timestamp, and endpoint name instead of broad hardware inventory.

## Limitations

- I have not recorded a clean restart and health check.
- I have not documented the exact configuration changes in a reproducible runbook.
- I have not completed an alert search, timeline, or triage decision.
- I have not measured log coverage, delay, retention, or false-positive rate.
- I have not tested restoration of the Wazuh services or data.
- The lab runs on the same Mac it monitors, so it does not represent production isolation.

## Next Steps

1. Record a restart and component-health check.
2. Complete the controlled File Integrity Monitoring event.
3. Complete one controlled administrative-authentication event.
4. Use the same triage-note structure for both.
5. Compare what Wazuh displayed with the original endpoint evidence.
6. Write a short conclusion about coverage, context, and remaining gaps.

## References

- [Wazuh architecture and Docker documentation](../SOURCES.md#security-monitoring)
- [HarborPay control mapping](../02-risk-and-controls/control-mapping.md)

## What I Learned

Docker made it possible to run several Wazuh components together without configuring each one directly on macOS. More importantly, I learned that a security dashboard is only the starting point. An analyst still has to trace a label back to the underlying event and explain why the activity is expected, suspicious, or malicious.

## Interview Explanation

> I deployed a Wazuh single-node environment with Docker and connected my Mac as an endpoint. During setup, Wazuh showed MITRE ATT&CK tactic labels around legitimate administrator activity. That taught me not to treat a framework label as proof of compromise. My next milestone is to generate two controlled events and document the event source, alert, decision, and limitations.
