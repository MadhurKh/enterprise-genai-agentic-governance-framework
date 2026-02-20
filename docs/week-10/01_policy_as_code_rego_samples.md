# Week 10 — Policy-as-Code (OPA/Rego) Sample Policies

**Goal:** Provide starter policies that map directly to Weeks 1–9 governance (tiers, gates, sovereignty, evidence, and operational controls).  
**Pattern:** Use these as templates for OPA (Open Policy Agent) or compatible policy engines.

---

## Policy Execution Modes

- **Pre-flight:** Validate inputs, tier, required controls, tool permissions **before** model call.
- **In-flight:** Enforce tool-call allowlists, write permissions, rate/cost thresholds during execution.
- **Post-flight:** Verify evidence capture, audit metadata, redaction, and required decision capture.

---

## Fail-Open vs Fail-Closed (Critical)

If the **policy engine is unavailable**:

- **Tier 1:** may fail-open (optional, risk-accepted) if no restricted data and no write tools.
- **Tier 2/3:** **must fail-closed** (deny) to prevent ungoverned execution.

---

## Input Contract (Representative)

Assume a policy input object like:

- `input.use_case.tier` ∈ {1,2,3}
- `input.request.region` (e.g., "EU", "US", "APAC")
- `input.request.data_classification` (e.g., "Public", "Internal", "Confidential", "Restricted")
- `input.request.tools[]` with `{name, permission}`
- `input.controls` (flags like `hitl_defined`, `audit_enabled`, `redaction_enabled`, `breaker_enabled`)
- `input.evidence` (artifacts references)
- `input.runtime` (rate, cost, failure counters)

---

## Rego Samples

> These samples illustrate patterns; adapt names/structures to your internal schema.

### 1) Deny If Policy Engine Health Unknown (Tier 2/3 Fail-Closed)

```rego
package genai.policy

default allow = false

# If policy engine health is unknown/unavailable, enforce fail-closed for Tier 2/3
deny[msg] {
  input.system.policy_engine_healthy == false
  input.use_case.tier >= 2
  msg := "Policy engine unhealthy: Tier 2/3 must fail-closed."
}

allow {
  not deny[_]
  input.system.policy_engine_healthy == true
  preflight_passed
}

preflight_passed {
  not preflight_deny[_]
}

preflight_deny[msg] { deny[msg] }
```

---

### 2) Tier 1 Must Be Read-Only (No Write Tools)

```rego
package genai.tier1

deny[msg] {
  input.use_case.tier == 1
  some t
  tool := input.request.tools[t]
  tool.permission == "write"
  msg := sprintf("Tier 1 cannot request write tools: %v", [tool.name])
}
```

---

### 3) Tier 2 Requires HITL + Audit Enabled

```rego
package genai.tier2

deny[msg] {
  input.use_case.tier == 2
  input.controls.hitl_defined != true
  msg := "Tier 2 requires defined Human-in-the-Loop roles."
}

deny[msg] {
  input.use_case.tier == 2
  input.controls.audit_enabled != true
  msg := "Tier 2 requires audit logging enabled."
}
```

---

### 4) Tier 3 Requires Independent Auditor + Breaker + Drill Currency

```rego
package genai.tier3

deny[msg] {
  input.use_case.tier == 3
  input.controls.independent_auditor_assigned != true
  msg := "Tier 3 requires Independent AI Auditor assignment."
}

deny[msg] {
  input.use_case.tier == 3
  input.controls.breaker_enabled != true
  msg := "Tier 3 requires circuit breaker enabled."
}

deny[msg] {
  input.use_case.tier == 3
  input.controls.killswitch_drill_current != true
  msg := "Tier 3 requires current kill-switch drill evidence."
}
```

---

### 5) Sovereignty Routing: EU Data Must Use EU-Allowed Providers/Regions

```rego
package genai.sovereignty

eu_allowed_providers := {"internal-eu-llm", "azure-openai-eu", "aws-bedrock-eu"}
eu_allowed_regions := {"eu-west-1", "westeurope", "northeurope"}

deny[msg] {
  input.request.region == "EU"
  not eu_allowed_providers[input.gateway.selected_provider]
  msg := sprintf("EU request routed to non-approved provider: %v", [input.gateway.selected_provider])
}

deny[msg] {
  input.request.region == "EU"
  not eu_allowed_regions[input.gateway.selected_region]
  msg := sprintf("EU request routed to non-approved region: %v", [input.gateway.selected_region])
}
```

---

### 6) Evidence Required for Decision-Impacting Outputs

```rego
package genai.evidence

deny[msg] {
  input.request.decision_impacting == true
  count(input.evidence.citations) == 0
  msg := "Decision-impacting output requires at least one evidence citation."
}
```

---

### 7) Redaction Must Precede Immutability (Privacy-by-Design)

```rego
package genai.privacy

deny[msg] {
  input.controls.audit_enabled == true
  input.controls.redaction_enabled != true
  msg := "Audit enabled but redaction disabled: must redact before immutable evidence store."
}
```

---

### 8) Block Prompt Injection / Jailbreak Attempts (Pattern)

```rego
package genai.security

deny[msg] {
  input.request.user_prompt_risk == "jailbreak_detected"
  msg := "Prompt injection/jailbreak attempt detected: request denied and logged."
}
```

---

### 9) Cost/Budget Circuit Breaker Trigger (Policy Output)

```rego
package genai.cost

breaker_trip := true {
  input.runtime.cost_per_minute_usd > input.runtime.cost_threshold_usd_per_minute
}

deny[msg] {
  breaker_trip
  msg := "Cost threshold exceeded: circuit breaker should trip to safe fallback."
}
```

---

## Suggested Outputs

A policy engine typically returns:

- `allow: true/false`
- `deny_reasons[]`
- `obligations[]` (e.g., “log policy decision”, “require HITL confirmation”)
- `break_glass: true/false` (for emergency operations)

---

## Minimal “Obligations” Examples

- Require HITL confirmation step (Tier 2/3)
- Require evidence citation for decision-impacting outputs
- Require sovereignty metadata capture in every model call
- Require redaction summary event before writing to immutable log
