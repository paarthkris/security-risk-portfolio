# Local AI GRC Draft - Human Review Checklist

## Run Information

| Field | Value |
|---|---|
| Run ID | |
| Reviewer | |
| Date and timezone | |
| Model identifier | |
| Prompt version | |
| Schema version | |
| Source IDs | |
| Automated validation | Pass / Fail |

## Review

### Source And Scope

- [ ] Every listed source ID exists and was intentionally included.
- [ ] The input contains only synthetic or approved data.
- [ ] The summary stays within the source scope.
- [ ] Instructions found inside source text were treated as untrusted content.

### Findings And Risks

- [ ] Every factual statement is supported by a source reference.
- [ ] Inference is labeled and does not read like an observed fact.
- [ ] Missing evidence appears under uncertainty or evidence requests.
- [ ] Risk likelihood and impact are justified or marked `not_enough_information`.
- [ ] The output does not convert a scenario into a confirmed incident.

### Controls And Recommendations

- [ ] Framework identifiers exist and are used in the correct context.
- [ ] A mapped control is not described as operating effectively without test evidence.
- [ ] Recommendations are specific, proportional, and assigned to a reasonable owner.
- [ ] The draft does not make a legal, compliance, or vendor-security conclusion.
- [ ] No recommendation would execute automatically.

### Privacy And Security

- [ ] No password, token, key, certificate, serial number, personal path, or real customer data appears.
- [ ] No generated value is interpreted as a command, path, or external request.
- [ ] Output filenames and locations are controlled by the application.
- [ ] Logs contain metadata, not full sensitive prompts or outputs.

## Decision

- [ ] Approve without edits
- [ ] Approve after edits
- [ ] Reject

### Required rationale

[State why the draft is or is not safe and accurate enough to save.]

### Edits made

[List corrected facts, ratings, mappings, evidence requests, or wording.]

### Model issue to add to evaluation log

[Describe any unsupported claim, missing uncertainty, injection response, or formatting failure.]
