# HarborPay Wazuh Lab Notes

## Lab Purpose

This lab is part of my HarborPay security risk portfolio. The goal is to learn how Wazuh collects endpoint information, shows security events, and maps activity to frameworks like MITRE ATT&CK.

For the first version, I deployed a Wazuh agent to my Mac and connected it to the local Wazuh manager running in Docker.

## Lab Setup

| Component | Details |
|---|---|
| Wazuh manager | Running locally through Docker |
| Wazuh dashboard | Running locally at `https://localhost` |
| Wazuh agent | Installed on my Mac |
| Agent name | `harborpay-macbook-01` |
| Agent status | Active |
| Operating system | macOS |

## Initial Observation

After deploying the Wazuh agent to `harborpay-macbook-01`, the endpoint appeared as active in the Wazuh dashboard.

The dashboard started showing:

- Agent status
- System inventory
- Operating system details
- Compliance information
- MITRE ATT&CK mappings
- Event activity

## MITRE ATT&CK Observation

During the setup process, Wazuh showed MITRE ATT&CK tags including:

- Defense Evasion
- Privilege Escalation

My interpretation:

> In my Wazuh lab, I observed that legitimate administrative setup activity can still map to MITRE ATT&CK tactics like Privilege Escalation or Defense Evasion. This helped me understand why analysts need to review context before deciding whether an alert is actually malicious.

## Why This Happened

The MITRE tags likely appeared because I performed normal administrator actions while setting up the Wazuh agent.

Examples of setup activity that may look security-relevant:

- Installing the Wazuh agent
- Running commands with `sudo`
- Loading a background service with `launchctl`
- Starting the Wazuh agent service

These actions are legitimate in this lab, but they are still worth monitoring because attackers may use similar behavior during real incidents.

## Key Lesson

MITRE ATT&CK tags are context labels, not automatic proof of compromise.

For example:

| Activity | Why Wazuh Cares |
|---|---|
| `sudo` command used | Administrator privileges were used. |
| Agent installed | A system-level change occurred. |
| `launchctl` loaded a service | A background service was started. |
| MITRE tag appeared | The behavior resembles a known attacker technique. |

The important analyst skill is understanding the difference between:

- Legitimate administrative activity
- Suspicious activity
- Malicious activity

## Screenshot

![Wazuh dashboard showing endpoint overview and MITRE ATT&CK mappings](screenshots/wazuh/wazuh-agent-mitre-overview.png)

Caption:

> Wazuh dashboard showing `harborpay-macbook-01` as an active endpoint with MITRE ATT&CK mappings for Defense Evasion and Privilege Escalation.

What this screenshot shows:

- The endpoint `harborpay-macbook-01` is active.
- Wazuh collected basic system inventory from the endpoint.
- Wazuh identified MITRE ATT&CK tactic mappings.
- The dashboard shows compliance and vulnerability sections that can be explored later.

## Interview Talking Point

I would explain this lab by saying:

> I deployed a Wazuh agent to a local endpoint and observed that legitimate administrative activity during setup was mapped to MITRE ATT&CK tactics. This helped me understand that security alerts need context. A tag like Privilege Escalation does not automatically mean compromise, but it tells the analyst what type of behavior to review.

## Next Steps

Next, I want to generate controlled test events and document how Wazuh records them.

Possible next test events:

- Sudo/admin command activity
- File creation or modification
- New test user creation
- Failed login attempt
- Custom HarborPay log file event
