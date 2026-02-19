# Audit Logging and Evidence Store (Replayability by Design)

## Purpose

Auditability is a foundational requirement for enterprise GenAI and Agentic AI systems.

This layer ensures that for any material output or action, the organization can reconstruct:

- what happened
- why it happened
- who approved it
- what evidence was used
- which model/tool versions were involved

This supports governance reviews, incident investigations, and regulatory readiness.

---

## Audit Objectives

An enterprise audit trail must enable:

1. **Traceability**
   - Reconstruct inputs, prompts/templates, evidence, outputs, and actions.

2. **Accountability**
   - Identify accountable owners and human reviewers, including overrides.

3. **Replayability**
   - Re-run the workflow using stored artifacts (or explain why replay differs).

4. **Integrity**
   - Prevent tampering via append-only logs and integrity hashes.

5. **Privacy**
   - Minimize sensitive data in logs; store references + hashes where possible.

---

## What Must Be Captured (Minimum)

For every request or workflow, capture:

- request metadata (request_id, use_case_id, tier, environment)
- user identity and role (RBAC context)
- policy decisions (allow/deny/conditions)
- prompt template id + version (and system instructions version)
- model provider + model id + version (and region/routing)
- retrieval evidence references (doc refs, chunk ids, snippet hashes)
- tool calls (inputs/outputs) with tool version
- structured output payload + schema version
- human decisions (accept/override/escalate/reject) + notes
- final outcome (approve/pilot/block or action result)
- incident flags (if triggered)

---

## Event Types (Recommended)

Each request produces a sequence of immutable events such as:

- REQUEST_RECEIVED
- INPUT_VALIDATED
- POLICY_EVALUATED
- PROMPT_SELECTED
- CONTEXT_ASSEMBLED
- MODEL_CALLED
- MODEL_OUTPUT_VALIDATED
- TOOL_CALLED
- HUMAN_DECISION_CAPTURED
- OUTCOME_ISSUED
- INCIDENT_FLAGGED

---

## Minimal Event Record Schema (Illustrative)

A single event record should include:

- request_id
- event_id
- event_type
- timestamp
- use_case_id
- tier
- environment
- user_role
- policy_id + policy_version
- decision (allow/deny/conditions)
- prompt_template_id + version
- model_provider + model_id + model_version
- retrieval_refs (evidence ids)
- tool_name + tool_version + tool_status
- output_hash + schema_version
- correlation_id / trace_id

---

## Evidence Store Design

Evidence should be stored as:

- document references (doc_id + version)
- location pointers (page/section/chunk)
- snippet hashes (integrity)
- short redacted previews (optional)

Avoid storing full raw documents in logs. Where raw excerpts are required:
- store in a separate evidence store with RBAC controls
- encrypt at rest
- access only on a need-to-know basis

---

## Storage Separation (Enterprise Pattern)

Recommended separation of stores:

1. **Event Log Store**
   - append-only event stream
   - immutable mode for Tier 3 actions

2. **Evidence Store**
   - references + hashes + controlled excerpts
   - strict RBAC, encryption, retention controls

3. **Decision Store**
   - human approvals, overrides, escalations
   - supports governance reviews and sampling audits

4. **Model/Prompt Registry**
   - model versions, prompt templates, approvals, change history

---

## Retention and Access

Retention should be tier-driven:

- Tier 1: shorter retention acceptable (unless regulated)
- Tier 2: retention aligned with business decision lifecycle
- Tier 3: longer retention + stronger integrity controls are typical

Access should be role-driven:

- End-user: own cases only
- SME: sampling and escalations
- Independent AI Auditor: broader read access for oversight
- Platform admin: operational metadata only (avoid raw evidence access)

---

## Operational Linkages

Audit and evidence stores feed:

- monitoring dashboards (quality, drift, anomalies)
- incident response workflows (alerts + investigation)
- governance re-certification (periodic reviews)
- compliance reporting and audit evidence

---

## Testing Requirements (Control Assurance)

Audit layers must be tested. Minimum recommended tests:

- **Replay test:** reconstruct and explain a material decision end-to-end
- **Integrity test:** verify tamper detection using hashes and append-only logs
- **Access test:** ensure least-privilege RBAC holds for evidence access
- **Outage test:** ensure events persist during provider or tool outages (buffering allowed)
- **Kill-switch drill evidence:** Tier 3 drills must generate audit proof of execution

---

## Governance Note

Auditability is not an optional engineering feature. It is a **permission requirement**:

- A high readiness score does not override missing auditability.
- Absence of decision trace or evidence capture triggers **Block / Redesign** for Tier 2–3.
