# Schema Contracts (Inputs, Outputs, Actions, Evidence)

## Purpose

Schema contracts make GenAI and Agentic AI systems **auditable, reliable, and enforceable** by design.

They enable:
- **Deterministic integrations:** downstream systems receive structured, validated payloads
- **Safety controls:** tools/actions cannot run without schema compliance
- **Auditability:** decisions can be reconstructed from captured artifacts
- **Consistent governance:** reviewers can score and gate systems using the same evidence structure

Schema contracts are the technical backbone of:
- **Week 2:** scoring anchors, readiness computation, and hard gates
- **Week 3:** control-plane enforcement (validation + permissions)
- **Week 4:** worked example evidence capture and remediation plans

---

## Contract Types (Minimum Set)

1. **Input Contract** (request context and constraints)
2. **Model Output Contract** (structured model output)
3. **Tool Call Contract** (tool input + tool output)
4. **Evidence Contract** (citations / snippets / references)
5. **Decision Contract** (human-in-the-loop action)
6. **Policy Decision Contract** (allow/deny/conditions)

---

## Guiding Rules

1) **Validate everything material**
- Model outputs that influence decisions
- Any tool call (especially write actions)
- Any approval/override decision

2) **Prefer references + hashes over raw data**
- Store evidence pointers and integrity hashes
- Avoid dumping PII into logs

3) **Version your contracts**
- Schema changes are governance events
- Version in a registry, not in ad-hoc prompts

4) **Fail safe**
- Schema validation failure triggers:
  - constrained retry
  - degrade-to-manual
  - escalation (Tier 3)

---

## 1) Input Contract (Example)

Minimum fields:
- request_id
- use_case_id
- tier
- user_id and role
- data_classification
- document references (not raw PII)
- purpose_of_use
- environment (dev/pilot/prod)

Example JSON shape:

{
  "request_id": "uuid",
  "use_case_id": "contract_risk_analyzer",
  "tier": 2,
  "environment": "pilot",
  "user": { "id": "u123", "role": "end_user" },
  "data_classification": "anonymized",
  "document_refs": [{ "doc_id": "d001", "version": "v3" }],
  "purpose_of_use": "contract triage"
}

Validation rules:
- tier must be in {1,2,3}
- user.role must match RBAC permissions
- document_refs required for RAG-based systems
- purpose_of_use required for audit defensibility

---

## 2) Model Output Contract (Example)

A structured contract risk output (illustrative). Includes **Sovereignty Metadata** to prove jurisdictional and version bounds months later.

{
  "overall_risk_score": 0.0,
  "risk_level": "low|medium|high",
  "flags": [
    {
      "category": "liability|termination|privacy|pricing|sla|jurisdiction",
      "severity": "low|medium|high",
      "summary": "string",
      "evidence_refs": ["e001", "e002"],
      "recommended_action": "string"
    }
  ],
  "confidence": 0.0,
  "needs_human_review": true,
  "sovereignty": {
    "provider": "string",
    "model_id": "string",
    "model_version": "string",
    "region": "string",
    "processing_boundary": "EU-only|global|on-prem"
  }
}

Validation rules:
- confidence must be between 0.0 and 1.0
- if severity == high then evidence_refs must be non-empty
- if tier >= 2 then needs_human_review is required (policy sets threshold)
- sovereignty.provider/model_id/model_version/region are required for Tier 2–3
- if schema validation fails:
  - retry with constrained prompt template
  - if still fails: manual mode + incident counter increment

---

## 3) Tool Call Contract (Input + Output)

### Tool Input Contract

{
  "request_id": "uuid",
  "tool_name": "clm_search",
  "tool_version": "1.0",
  "inputs": { "query": "string", "filters": { "contract_type": "msa" } }
}

### Tool Output Contract

{
  "request_id": "uuid",
  "tool_name": "clm_search",
  "tool_version": "1.0",
  "status": "success|fail",
  "outputs": { "results": [{ "id": "c01", "title": "..." }] },
  "error": "optional"
}

Validation rules:
- tool_name must exist in Tool Registry
- tool inputs must pass Policy Engine constraints (tier + role + scopes)
- any write-tool output must include a rollback_hint or rollback_id (Tier 3)
- tool I/O must be logged to the audit layer

---

## 4) Evidence Contract

Evidence is stored as references (with integrity), not raw dumps.

{
  "evidence_id": "e001",
  "doc_id": "d001",
  "doc_version": "v3",
  "location": { "type": "page|section|chunk", "value": "Section 4.2" },
  "snippet_hash": "sha256",
  "snippet_preview": "short preview string (redacted)"
}

Validation rules:
- snippet_hash required for integrity
- snippet_preview must be redacted (no unnecessary PII)
- access to raw snippet content is RBAC-controlled

---

## 5) Decision Contract (Human-in-the-loop)

Captures what the human did with the AI output.

{
  "request_id": "uuid",
  "reviewer": { "id": "u123", "role": "end_user|sme|auditor" },
  "decision": "accept|override|escalate|reject",
  "notes": "string",
  "timestamp": "ISO-8601"
}

Validation rules:
- Tier 2: at least End-User Verification (accept/override/escalate)
- Tier 3: Independent AI Auditor sampling must be recorded (policy-defined cadence)
- notes required if decision in {override, reject}

---

## 6) Policy Decision Contract (Allow / Deny / Conditions)

Records the control-plane decision for a given action.

{
  "request_id": "uuid",
  "policy_id": "tier_policy_v1",
  "decision": "allow|deny|allow_with_conditions",
  "conditions": [
    "requires_human_approval",
    "max_tool_calls=3",
    "restricted_tool_scope=refund<=50"
  ],
  "timestamp": "ISO-8601"
}

Validation rules:
- deny must include a reason code
- allow_with_conditions must include at least one condition
- policy_id and version must be captured for audit replay

---

## Contract Governance

Contracts must be:
- **Versioned:** each schema has an explicit version (e.g., v1, v1.1)
- **Registered:** maintained in a single registry (repo folder or schema store)
- **Tested:** validated via CI checks (schema linting + sample payload tests)
- **Backward compatible:** or migrated with explicit change control

A change to any contract is treated as a governance event and triggers:
- re-evaluation of scores (Week 2)
- re-certification review for Tier 2–3
