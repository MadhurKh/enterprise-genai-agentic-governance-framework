# Week 8 — Implementation Blueprint: Circuit Breaker + Safe Fallback

## Purpose

Week 6 introduced operational assurance and the "red-button" drill concept.  
Week 8 makes the control enforceable: the system must auto-trip when safety or sovereignty conditions fail.

This file defines:
- circuit breaker triggers (auto-trip)
- degrade modes (safe fallback)
- kill switch relationship
- testing requirements and separation of duties

---

## Definitions

### Circuit breaker
An automated control that stops or degrades AI execution when risk signals exceed thresholds.

### Kill switch ("red button")
A manual emergency control used when humans decide to immediately neutralize AI behavior.

Relationship:
- circuit breaker is automatic
- kill switch is manual
- both degrade the system to an approved safe mode

---

## Where Circuit Breakers Run

Circuit breakers should execute:
- in the Tool Router (for agent tool calls)
- in the Model Gateway (for sovereignty/quality failures)
- in the Output Validator (for schema/evidence failures)

The breaker must be always-on for Tier 2/3.

---

## Safe Degrade Modes (Fallback)

Define explicit safe fallback behaviors:

1. manual_mode
   - disable AI generation
   - revert to non-AI baseline process

2. read_only_mode
   - allow retrieval/summaries only
   - block tool calls and execution

3. limited_scope
   - restrict to a subset of use cases or contract types
   - enforce lower-risk paths only

4. shadow_mode
   - AI runs but outputs are not shown to users
   - used for testing after incident

Each use case must declare which degrade modes are permitted.

---

## Circuit Breaker Triggers (Tier 2/3)

### A) Policy and control failures
Auto-trip when:
- policy decision = deny due to missing controls
- tool call violates schema or policy boundaries
- unauthorized user/role attempts high-risk action

### B) Sovereignty violations
Auto-trip when:
- region routing fails (EU-only request processed outside EU)
- provider not on allowlist is selected
- sovereignty metadata missing for Tier 2/3 output

### C) Evidence and audit failures
Auto-trip when:
- decision-impacting outputs lack evidence references
- logging pipeline fails redaction confirmation
- audit record cannot be written (evidence store unavailable)

### D) Quality and safety failures
Auto-trip when:
- repeated hallucination indicators above threshold
- spike in user overrides (HITL override rate)
- repeated safety policy violations (disallowed output patterns)
- repeated tool errors / retries beyond threshold

### E) Availability and performance
Auto-trip when:
- model latency breaches SLA persistently
- provider outage detected
- cost/tokens exceed guardrails for a use case

---

## Trigger Threshold Guidance (Illustrative)

These are examples; enterprises should calibrate thresholds:

- sovereignty metadata missing: 1 event -> trip (zero tolerance for Tier 3, near-zero for Tier 2)
- policy deny due to missing controls: 1 event -> trip (Tier 3)
- evidence missing for decision-impacting output: >= 2 events in 10 requests -> trip
- override rate spike: > 30% increase vs baseline -> trip and investigate
- tool schema violations: >= 1 event -> trip (Tier 3)

### Cost / Budget Breach Trigger (Financial Guardrail)

Agentic loops can create runaway spend even without safety violations. The circuit breaker must include a financial threshold trigger.

Illustrative triggers:
- tokens or cost per minute exceeds approved use-case limit
- daily budget threshold exceeded for a use case or workspace
- repeated 429/rate-limit errors causing retries that inflate spend

Example threshold framing:
- Tier 2: trip if spend exceeds **2x expected baseline** within a sliding window
- Tier 3: trip if spend exceeds **approved cap** (near-zero tolerance) and degrade immediately

---

## Circuit Breaker Decisioning

When a trigger fires, breaker returns:
- breaker_status: open | closed | half_open
- degrade_mode selected
- reason codes (triggered rules)
- duration (cooldown window)
- required remediation (P0/P1)

### Half-open recovery
After cooldown:
- allow limited traffic (shadow_mode or limited_scope)
- require passing validation tests before full restore

---

## Kill Switch (Manual) Requirements

- must be callable by defined roles (EPO, AIPO, Incident Commander)
- must take effect within defined time (for example, < 60 seconds)
- must force a safe degrade mode
- must be logged with:
  - who triggered
  - why
  - what mode applied
  - duration and restoration approval

### Kill switch drills (Tier 3)
- required quarterly
- evidence must be captured in the audit packet

---

## Testing and Separation of Duties

### Mandatory tests (Tier 2)
- fallback simulation (provider outage -> manual mode)
- schema validation failure -> breaker trip
- logging pipeline redaction failure -> breaker trip
- cost/budget breach simulation -> breaker trip (financial guardrail)

### Mandatory tests (Tier 3)
- circuit breaker auto-trip simulation (policy + sovereignty)
- kill switch drill (quarterly)
- rollback test for reversible actions (where applicable)
- cost/budget breach simulation -> breaker trip (zero tolerance for cap breach)

### Separation of duties (required)
- tests executed by: Platform/Engineering Owner (EPO)
- evidence validated by: Risk/Compliance or Independent AI Auditor (Tier 3)

---

## Implementation Checklist

- [ ] breaker triggers defined and mapped to signals (including cost/budget)
- [ ] degrade modes declared per use case
- [ ] breaker status persisted and observable
- [ ] half-open recovery path defined
- [ ] kill switch implemented and role-restricted
- [ ] drills scheduled + evidenced (Tier 3)
- [ ] incident runbooks updated
