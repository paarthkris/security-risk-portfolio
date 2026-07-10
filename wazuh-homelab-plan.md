# HarborPay Wazuh Homelab Plan

## Purpose

This lab will be the first major hands-on security monitoring project for HarborPay.

The goal is to set up Wazuh, collect logs, trigger simple suspicious events, review alerts, and write clear investigation notes.

## Why Wazuh

Wazuh is useful for this portfolio because it helps me learn:

- What a SIEM does
- How endpoint logs are collected
- What security alerts look like
- How to investigate suspicious activity
- How monitoring connects back to business risk

## Project Connection

This lab connects to:

- HP-AST-010: Wazuh
- HP-AST-008: Employee MacBooks
- HP-RISK-010: Incomplete logging or poor alert review
- HP-RISK-008: Endpoint device compromise or loss

## First Version Setup

The first version should stay simple.

Recommended setup:

- Run Wazuh locally or in Docker.
- Add one monitored endpoint or test log source.
- Generate a few safe test events.
- Capture screenshots of alerts and dashboard views.
- Write a short investigation note for each event.

## Test Events

| Test Event | Why It Is Useful |
|---|---|
| Multiple failed login attempts | Simulates brute force or account guessing behavior. |
| New local user created | Shows possible persistence or unauthorized account creation. |
| File integrity change | Shows how monitoring can detect important file changes. |
| Suspicious command run | Helps practice reviewing endpoint activity. |
| Missing endpoint/log source | Shows why monitoring coverage matters. |

## Planned Deliverables

- `wazuh-homelab-notes.md`
- Wazuh setup notes
- Alert screenshots
- Event timeline
- Investigation notes
- Recommendations
- Lessons learned

## What I Should Capture

- Dashboard screenshot
- Agent/endpoint status screenshot
- Alert details screenshot
- Rule or alert name
- Event timestamp
- What triggered the alert
- Why it matters
- What I would recommend

## Stretch Goals

After the basic lab works, possible expansions include:

- Add Suricata for network IDS practice.
- Add more endpoints or containers.
- Map alerts to MITRE ATT&CK.
- Create a simple incident response playbook.
- Use the n8n AI GRC workflow to summarize Wazuh alerts into risk notes.

## What I Would Explain In An Interview

I would explain that I set up Wazuh to understand how monitoring and alert review work in practice.

The key point is not just installing the tool. The important part is showing that I can trigger events, read alerts, explain what happened, and connect the finding back to risk and controls.

## Build Status

Planned. The next step is to choose the setup method and install Wazuh.

