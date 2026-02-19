# Change Control and Re-Certification (Template)

## Purpose

GenAI and agentic systems change frequently (models, prompts, tools, data, policies).  
Change control prevents silent risk drift and ensures approvals remain defensible.

---

## What Triggers Re-Certification

Re-certification is required when any of the following change:

### Model and Provider
- model provider changes
- model version changes (including “silent” vendor upgrades)
- region/routing changes (EU-only vs global)
- fallback model changes

### Prompting and Orchestration
- prompt templates change (system prompt, guardrails, scoring prompts)
- retrieval strategy changes (RAG sources, ranking, chunking)
- tool selection logic changes

### Tooling and Integrations
- new tools added to registry
- tool permissions/scopes change
- write authority added or expanded
- rollback strategy changed

### Policy and Governance
- tier classification changes
- gate rules change
- circuit breaker conditions change
- logging/redaction rules change

### Data and Security
- new data class introduced (PII/PHI/PCI)
- retention policy changes
- access roles change

---

## Change Request Record

- Use case name / ID:
- Current tier:
- Environment affected: dev/pilot/prod
- Change type: Model / Prompt / Tool / Policy / Data / Security / Other
- Change description:
- Reason for change:
- Owner:
- Date submitted:

---

## Risk Impact Assessment (Required)

- Does this change alter tier classification? Yes/No  
  - If yes: re-run Week 1 classification and approvals
- Which dimensions are impacted? (1–8 list)
- Which hard gates are impacted? (Gate 1–7 list)
- Does this change affect sovereignty (provider/region/version)? Yes/No
- Does this change affect autonomy scope or tool permissions? Yes/No

---

## Required Actions

- [ ] Update schema contracts (if affected)
- [ ] Update audit logging (if affected)
- [ ] Re-run scorecard (Week 2)
- [ ] Re-run gates checklist (Week 5)
- [ ] Execute regression tests (policy + schema)
- [ ] Execute replayability test (Tier 2–3)
- [ ] Execute circuit breaker simulation (if relevant)
- [ ] Execute kill-switch drill evidence capture (Tier 3)

---

## Re-Approval and Sign-Off (Tier-Based)

### Tier 1
- AI product owner
- business owner

### Tier 2
- AI product owner
- business owner
- risk/compliance
- domain SME (as applicable)

### Tier 3
- executive business owner
- legal
- risk management
- AI platform owner
- independent AI auditor

---

## Outcome

- Decision: Approved / Approved with Conditions / Blocked
- Conditions:
- Next review date:
- Version updated to:
