# Week 8 — Implementation Blueprint: Internal Model Gateway (Sovereignty Abstraction Layer)

## Purpose

For Tier 2/3 systems, application code should never call a vendor model API directly (for example, "OpenAI", "Anthropic").  
Instead, all calls route through an **Internal Model Gateway** that enforces:

- sovereignty rules (region, residency, approved providers)
- availability + fallback routing
- model version governance
- safety controls and policy checks
- audit metadata capture (provider, region, model version)

This file defines the pattern, inputs/outputs, and required behaviors.

---

## Why the Model Gateway Matters (Enterprise View)

Without a gateway:
- sovereignty is implemented inconsistently across apps
- vendor lock-in is baked into product code
- model upgrades happen without governance
- auditors cannot prove residency or model version used

With a gateway:
- sovereignty is centrally enforceable
- fallback is standardized and tested
- provider switching is feasible
- audit evidence is consistent across all use cases

---

## Placement in the Architecture

The Model Gateway sits in the Execution Plane and is called by the Orchestrator.

Conceptually:

- App/Orchestrator -> Model Gateway -> Provider(s)

---

## Model Gateway Responsibilities

### 1) Provider abstraction
Expose a unified interface:
- generate()
- embed()
- classify() (optional)
- moderate() (optional)

### 2) Sovereignty routing
Route requests based on:
- region_requirement (EU-only, etc.)
- data classification
- approved provider list per tier
- client-specific constraints

### 3) Fallback strategy
Define fallback types:
- provider fallback (Provider A -> Provider B in same region)
- model fallback (Model vX -> vY)
- manual fallback (degrade to non-AI baseline)

Fallback rules must be explicit and testable.

### 4) Policy integration
Model Gateway should invoke Policy-as-Code:
- pre-flight: verify tier and controls
- enforce deny/degrade decisions
- log policy outcomes

### 5) Audit metadata capture
Every response must carry sovereignty metadata:
- provider_id
- provider_region
- model_id
- model_version
- gateway_version
- request_id
- policy_decision_id

---

## Gateway Input Contract (Minimal)

- use_case_id
- tier
- environment
- user_context (id, role)
- region_requirement
- data_classification
- prompt (or messages)
- output_schema_id (if structured output)
- safety_profile_id (tier-based)
- controls_declared (logging, redaction, circuit breaker enabled)

---

## Gateway Output Contract (Minimal)

- response_text (or structured JSON)
- evidence (if applicable)
- sovereignty_metadata
  - provider_id
  - provider_region
  - model_id
  - model_version
  - gateway_version
- latency_ms
- tokens_in / tokens_out (or equivalents)
- request_id
- policy_decision_id
- error/fallback flags

---

## Recommended Routing Rules (Examples)

### Rule A — EU-only residency
IF region_requirement == EU-only  
THEN route to providers approved for EU region only  
ELSE deny or degrade to manual mode.

### Rule B — Tier-based provider allowlist
- Tier 1: broader allowlist
- Tier 2/3: restricted allowlist with explicit residency assurances and contracts

### Rule C — Data classification constraints
IF data_classification == restricted  
THEN require:
- approved provider contract
- encryption and key management policy
- logging redaction enabled  
If not satisfied -> deny or degrade.

---

## Fallback Patterns (Enterprise)

### 1) Provider outage fallback
- detect provider outage / SLA breach
- route to approved alternate provider (same region)
- if none exists -> degrade to manual mode

### 2) Token limit / rate limit fallback (quota-aware)
Vendor APIs may be healthy but unavailable due to enterprise quota controls (for example, HTTP 429 Too Many Requests).

The gateway must:
- detect rate limit/quota errors reliably
- apply throttling/backoff policies
- route to an approved backup model/provider (same region) **or** degrade to manual mode
- log the event as an operational control signal (cost and availability governance)

### 3) Quality fallback (confidence failure)
- detect repeated low-quality or policy violations
- trip circuit breaker
- degrade to manual mode for duration

### 4) Governance fallback (policy deny)
- policy denies request due to missing controls
- gateway returns deny response with reason codes
- optionally: allow_with_controls for pilot only

---

## Audit Requirements (Non-negotiable for Tier 2/3)

The gateway must emit logs/evidence for:
- sovereignty metadata per request
- routing decision reasoning (which rule matched)
- fallback events (what triggered, what was used)
- policy decision id + rule version
- redaction status (confirmed pre-immutability)

This enables an auditor to prove months later:
- which provider/model processed the request
- where it was processed (region)
- which policy rules were enforced

---

## Implementation Checklist

- [ ] Unified gateway API for all apps
- [ ] Tier-based allowlists
- [ ] Region routing enforcement
- [ ] Fallback logic implemented and tested (including quota-aware fallback)
- [ ] Policy-as-code integrated (pre-flight)
- [ ] Sovereignty metadata logged + stored
- [ ] Circuit breaker integration
