# 07 - Local AI GRC Assistant

## Project

This will be a local command-line assistant that turns a security incident note or vendor-review note into a structured **draft** containing risks, control mappings, evidence requests, recommendations, assumptions, and uncertainties.

The model will run through Ollama on my Mac. A small Python program will prepare the input, request JSON that matches a defined schema, validate the response, require human review, and then create a Markdown draft.

## Honest Status

The architecture, output schema, threat model, human-review checklist, and evaluation cases are complete. The application has not been implemented or tested. No sample in this folder should be described as model-generated until I run and record the actual local workflow.

## Why Local

- I can learn how a model runtime and local API work instead of hiding the flow behind an automation platform.
- HarborPay test notes can stay on the local machine during processing.
- I can record the exact model, prompt, parameters, latency, and output.
- I can test failure cases without giving the model authority to change another system.

Local processing reduces some data-sharing risk, but it does not make the output accurate or the software automatically secure.

## Version 1 Boundary

Version 1 will:

- accept one Markdown or plain-text case file;
- accept an allowlist of HarborPay source documents;
- enforce file type and size limits;
- send a structured request to a local Ollama API;
- require output that matches [output-schema.json](output-schema.json);
- reject or quarantine invalid output;
- show source pointers, assumptions, and uncertainties;
- require a person to approve, edit, or reject the draft; and
- save approved JSON and Markdown locally.

Version 1 will **not**:

- send email, update the risk register, open tickets, or call external services;
- browse the web;
- ingest secrets or real customer data;
- treat model output as evidence;
- automatically approve a risk decision; or
- use retrieval or a vector database.

Retrieval with local embeddings is a later milestone after the basic structured workflow is reliable and understandable.

## Architecture

```text
Case file + allowlisted sources
            |
            v
Input validation and basic redaction
            |
            v
Prompt builder with source IDs
            |
            v
Local Ollama API and local model
            |
            v
JSON Schema validation
       |                 |
    invalid            valid
       |                 |
 quarantine        human review
                         |
              approve / edit / reject
                         |
                 local JSON + Markdown
```

## Suggested Components

| Component | Responsibility |
|---|---|
| `CaseLoader` | Read only allowed file types and enforce size limits. |
| `SourceRegistry` | Assign stable source IDs and provide allowlisted content. |
| `Redactor` | Flag or remove obvious secret-like values before inference. |
| `PromptBuilder` | Separate instructions from untrusted source content. |
| `OllamaClient` | Call only the configured local endpoint with a timeout. |
| `OutputValidator` | Validate the JSON response and reject extra or missing fields. |
| `ReviewSession` | Display the draft, sources, assumptions, and uncertainty for a human decision. |
| `ReportWriter` | Save only reviewed output with provenance metadata. |

## Model Output Rule

The assistant creates a draft, not a finding. Every risk, mapping, evidence request, and recommendation must point to one or more source IDs or be labeled as an assumption. The model must also state uncertainty instead of filling missing information with a confident guess.

## Build Milestones

### Milestone 1 - Local runtime

- [ ] Install or verify Ollama.
- [ ] Choose one model that fits the local machine.
- [ ] Record the exact model name, digest or version, and license notes.
- [ ] Make one local API request and prove no cloud API is required.

### Milestone 2 - Validated JSON

- [ ] Create a small Python project and configuration file.
- [ ] Load [output-schema.json](output-schema.json).
- [ ] Ask Ollama for structured output using the schema.
- [ ] Reject malformed JSON and schema violations.
- [ ] Add automated tests for valid, invalid, incomplete, and extra-field responses.

### Milestone 3 - Traceability And Review

- [ ] Assign a source ID to every input document.
- [ ] Require source references on claims.
- [ ] Display assumptions and uncertainty prominently.
- [ ] Implement approve, edit, and reject decisions.
- [ ] Save model and prompt metadata with each reviewed output.

### Milestone 4 - Security Tests

- [ ] Run the prompt-injection evaluation case.
- [ ] Run missing-context and conflicting-source cases.
- [ ] Test secret-like input and confirm it is blocked or redacted.
- [ ] Test a fabricated control citation.
- [ ] Confirm the program cannot call external actions.
- [ ] Document incorrect output and the control that caught or missed it.

### Milestone 5 - Optional Retrieval

- [ ] Add local embeddings only after version 1 passes its tests.
- [ ] Retrieve small source chunks with stable source IDs.
- [ ] Record the embedding model and chunk settings.
- [ ] Evaluate whether retrieval improves source accuracy instead of assuming it does.

## Required Run Record

| Field | Example format |
|---|---|
| Run ID | `AIGRC-YYYYMMDD-001` |
| Date and timezone | ISO 8601 |
| Input type | Incident or vendor review |
| Model | Exact local model identifier |
| Model digest/version | Runtime-reported value |
| Prompt version | Git commit or prompt file hash |
| Schema version | From validated output |
| Parameters | Temperature and other non-default settings |
| Latency | Measured locally |
| Validation result | Pass or rejected with reason |
| Human decision | Approved, edited, or rejected |
| Source IDs | Exact documents used |

## Files

- [Output schema](output-schema.json)
- [Threat model](threat-model.md)
- [Human review checklist](human-review-checklist.md)
- [Evaluation cases](evaluation-cases.md)
- [Primary references](../SOURCES.md#local-ai-security)

## Definition Of Done

The project is complete when I can run the workflow locally from a clean setup, produce schema-valid output, trace claims to sources, show at least one rejected or corrected model response, and explain why human review remains necessary.

## Planned Interview Explanation

After I build and evaluate the assistant, I should be able to say:

> I built a local AI assistant that converts security notes into structured GRC drafts. I used an output schema, source IDs, validation, adversarial tests, and a required human decision because the model's output is untrusted. It cannot update systems or approve risk on its own.
