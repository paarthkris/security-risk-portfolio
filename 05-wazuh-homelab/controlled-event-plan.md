# Wazuh Controlled-Event Plan

## Purpose

These tests will turn the Wazuh setup into evidence-based investigation work. They are intentionally small, local, reversible, and limited to files or actions I create for the lab.

I will complete the commands with guidance rather than copying a finished result into the repository. A test is complete only after I can explain the source event, Wazuh rule or record, timeline, decision, and limitation.

## Safety Rules

- Work only on the local lab and a dedicated test folder.
- Do not disable security controls, create persistence, scan other systems, or use real credentials as test data.
- Review each command before running it with `sudo`.
- Never publish passwords, tokens, certificates, serial numbers, personal paths, or unredacted system identifiers.
- Preserve the original timestamp and timezone when capturing evidence.
- Stop and investigate unexpected behavior before continuing.

## Pre-Test Health Check

- [ ] Docker Desktop is running.
- [ ] Wazuh manager, indexer, and dashboard report healthy/running.
- [ ] `harborpay-macbook-01` reports active.
- [ ] Current date, timezone, and Wazuh version are recorded.
- [ ] The test folder contains no personal or sensitive data.
- [ ] A new triage note has been copied from the template.

## Test 1 - File Integrity Monitoring

### Objective

Configure Wazuh to monitor one dedicated lab directory, make a known file change, and determine what evidence Wazuh records.

### Planned activity

1. Create a folder used only for the HarborPay FIM test.
2. Add that exact folder to the Wazuh agent's File Integrity Monitoring configuration.
3. Restart only the required agent service and confirm it reconnects.
4. Create a harmless text file containing synthetic content.
5. Modify the file once and then delete it.
6. Search the Wazuh dashboard for the three expected actions.

### Questions to answer

- Did Wazuh record creation, modification, and deletion separately?
- Which path, user, timestamp, hash, and rule fields were available?
- How long did collection and display take?
- Did any event become an alert, and why?
- What would make this detection useful for a real HarborPay asset?

### Required evidence

- Redacted configuration excerpt for the single monitored test path
- Timestamped local action log
- Alert or event detail showing relevant fields
- Query or dashboard filter used to find it
- Completed triage note and limitation statement

### Success criteria

At least one file action is visible and can be correlated to the exact action I performed. If no event appears, the test still produces a useful result if I document the troubleshooting steps and coverage gap.

## Test 2 - Administrative Authentication Activity

### Objective

Perform one harmless, approved administrator-authentication action and determine whether Wazuh receives enough context to explain it.

### Planned activity

1. Choose a read-only or no-op command that requires local administrator authentication.
2. Record the intended command, purpose, and start time before running it.
3. Run it once successfully in the local lab.
4. Search macOS and Wazuh records for the matching authentication or process evidence.
5. Compare the underlying event with any MITRE ATT&CK mapping displayed by Wazuh.

### Questions to answer

- Which source log recorded the action?
- Can the user, process, result, and timestamp be correlated?
- Did Wazuh create an alert or only collect an event?
- If a MITRE label appeared, which exact technique or tactic did the rule reference?
- What context proves that the action was authorized in this lab?

### Required evidence

- Planned action statement written before the test
- Redacted source event and Wazuh event or alert
- Rule ID, level, description, and MITRE mapping if present
- Completed triage note that closes the event as authorized test activity
- Explanation of what an attacker could do differently and which extra evidence would matter

### Success criteria

I can connect the intended action to a specific source event and make a supported disposition. A MITRE label by itself does not satisfy the test.

## Final Mini-Incident Report

After both tests, I will write one comparison report that includes:

- what each test was designed to show;
- what Wazuh actually recorded;
- where evidence was complete or missing;
- why each event was closed as authorized lab activity;
- which HarborPay risks and controls the tests relate to; and
- the next monitoring improvement I would make.

## Stretch Work After The Core Tests

Only after the two core investigations are complete:

- add a separate Linux endpoint to compare telemetry;
- add Suricata for network visibility in a controlled lab network;
- write one custom Wazuh rule for a HarborPay-formatted test log;
- create an analyst dashboard based on alert severity, asset, status, and open investigation;
- measure alert delay and document rule-tuning decisions; and
- export a sanitized event for the local AI GRC assistant evaluation.
