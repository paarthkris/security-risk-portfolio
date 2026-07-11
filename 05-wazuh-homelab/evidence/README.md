# Wazuh Evidence Folder

Add only sanitized evidence that supports a specific statement in a report.

## Naming Convention

`YYYY-MM-DD_case-id_evidence-id_short-description.ext`

Example: `2026-07-15_fim-001_ev-02_wazuh-alert-detail.png`

## Capture Checklist

- [ ] The image or export shows the relevant timestamp, rule, event, or setting.
- [ ] The related report explains why the evidence matters.
- [ ] Passwords, tokens, certificates, serial numbers, personal paths, and unrelated identifiers are removed.
- [ ] The evidence is from my lab or is clearly labeled simulated.
- [ ] The original is retained locally if cropping or redaction changes context.
- [ ] The filename matches the evidence table in the report.

## Current Status

No publishable image is stored here yet. The first endpoint-overview screenshot was excluded because it displayed a real hardware serial number. A sanitized, alert-focused replacement is part of the next lab milestone.
