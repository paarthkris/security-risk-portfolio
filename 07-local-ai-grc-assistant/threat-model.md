# Local AI GRC Assistant - Threat Model

## Status

Design-stage model. Update it after the program, prompt, model, and file-handling behavior exist.

## Security Objective

Use a local model to create useful drafts without allowing untrusted input or generated output to become an unsupported finding, expose sensitive data, or trigger an external action.

## Assets

- Source incident and vendor notes
- HarborPay risk and control documents
- Local model and runtime configuration
- Prompt and schema versions
- Generated drafts and human decisions
- Run metadata and evaluation results

## Trust Boundaries

| Boundary | Risk |
|---|---|
| User-selected file to loader | Unexpected file type, excessive size, or sensitive content |
| Source text to prompt | Embedded instructions may attempt to override the task |
| Python program to local Ollama API | Wrong endpoint, unavailable runtime, timeout, or untrusted model output |
| Model response to validator | Malformed JSON, extra fields, fabricated sources, or unsafe content |
| Validated draft to human reviewer | Automation bias and confident but unsupported recommendations |
| Approved output to disk | Sensitive data, misleading provenance, or overwrite of original evidence |

## Priority Risks And Controls

| ID | Risk | Planned control | Test evidence |
|---|---|---|---|
| AI-01 | A source document contains prompt injection that tells the model to ignore instructions or approve a result. | Delimit source content, state that source instructions are untrusted, constrain output schema, prevent tools/actions, and require source-backed human review. | Injection case produces no external action and any unsupported instruction is rejected or flagged. |
| AI-02 | Sensitive or secret-like data is sent to the model or saved in output. | Local-only endpoint allowlist, input classification, basic secret detection/redaction, safe logging, and test data only. | Secret-like test value is blocked or redacted and absent from logs/output. |
| AI-03 | The model invents a risk fact, control citation, or evidence result. | Require source IDs, allow `not_enough_information`, validate references against the source registry, and require human review. | Fabricated source or unsupported claim is detected during automated or human review. |
| AI-04 | Schema-valid output is treated as correct. | Separate structural validation from factual review; show assumptions, uncertainty, and source text beside each draft. | Reviewer checklist catches a deliberately plausible unsupported claim. |
| AI-05 | Generated text causes code execution, file overwrite, or an external action. | No tool execution, no shell interpolation, fixed output directory, generated filename, and explicit approve step. | Adversarial output remains data and cannot select a command or arbitrary path. |
| AI-06 | A local model or dependency changes and results are no longer reproducible. | Record model identifier/digest, runtime, prompt hash, schema version, parameters, and dependency lockfile. | Two run records can be compared and differences are explained. |
| AI-07 | A reviewer accepts output too quickly because it sounds confident. | Require a decision reason, source check, uncertainty review, and at least one editable field before approval. | Review record contains decision, edits, and reviewer rationale. |
| AI-08 | Retrieval later returns irrelevant or manipulated chunks. | Keep retrieval out of version 1; later evaluate chunk provenance, relevance, and conflicting sources. | Retrieval evaluation records precision and unsupported-claim outcomes. |

## Design Decisions

1. The model receives no tools and cannot update another system.
2. The application accepts only explicit local files, not arbitrary URLs.
3. The Ollama base URL defaults to localhost and rejects a nonlocal host unless a future design review changes the rule.
4. Schema validation is necessary but does not count as factual validation.
5. Approved output is a draft with provenance, not evidence or a final risk acceptance.
6. The original input remains unchanged.

## Review Triggers

Repeat the threat model before adding a web interface, retrieval, multiple users, cloud models, ticket creation, email, database storage, or any autonomous action.
