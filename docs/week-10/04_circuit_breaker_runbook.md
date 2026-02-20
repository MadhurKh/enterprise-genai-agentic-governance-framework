# Week 10 — Circuit Breaker Runbook (Operational)

**Goal:** Provide a practical incident runbook for auto-tripping circuit breakers and manual kill switches in Tier 2/3 GenAI/Agentic systems.

---

## Definitions

- **Circuit Breaker (Auto):** Automatically trips when safety/sovereignty/cost/quality thresholds are violated.
- **Kill Switch (Manual):** Human-initiated “red button” to stop/disable AI execution.
- **Safe Degrade Modes:** manual_mode / read_only / limited_mode / shadow_mode / fail_closed

---

## Triggers (Non-Exhaustive)

Trip breaker if any of these exceed thresholds:

1. **Safety / Policy Violations**
   - jailbreak detected rate above threshold
   - policy denies spike (unexpected)
2. **Sovereignty Bound Breach**
   - non-approved provider or region selection
3. **Operational Failure**
   - provider error rate spikes; repeated timeouts
   - repeated tool-call failures
4. **Rate/Token Limits**
   - sustained HTTP 429; quotas exhausted
5. **Cost/Budget Breach**
   - cost per minute or cost per request exceeds budget (runaway loops)
6. **Quality Degradation**
   - anomaly signals: hallucination rate, user override spikes

---

## Immediate Actions (When Breaker Trips)

1. **Switch Mode**
   - Tier 2: degrade to **manual_mode** or **read_only**
   - Tier 3: **fail_closed** unless explicitly authorized break-glass
2. **Stop Writes**
   - disable write tools (if any) at gateway/tooling layer
3. **Notify**
   - on-call engineering + AIPO + Risk/Compliance
   - Tier 3: Independent AI Auditor notified
4. **Preserve Evidence**
   - snapshot audit events, policy decisions, routing metadata
   - confirm redaction applied before immutability

---

## Investigation Checklist

- What trigger fired? (safety/sovereignty/cost/429/quality)
- What changed recently? (model/prompt/tool/data/context drift)
- Is this confined to one region/provider?
- Are we seeing malicious attempts (prompt injection patterns)?
- Are guardrails/policy rules functioning as designed?

---

## Recovery Criteria

Returning from **Half-Open** to **Closed (full production)** requires explicit sign-off:
- **Tier 2:** AI Product Owner (AIPO)
- **Tier 3:** AI Product Owner (AIPO) **and** Risk/Compliance (or Independent AI Auditor, as defined in Week 6 decision rights)

Breaker can be reset only when:
- root cause identified
- remediation applied (policy update, prompt patch, routing fix, tooling change)
- validation tests re-run for relevant category
- Tier 3: independent validation completed + decision record logged

---

## Post-Incident Requirements

- incident report (timeline + blast radius)
- gate/control failure analysis
- corrective actions with owners and due dates
- update exception register if temporary waiver used
- add “lesson learned” to validation test plan (new test cases)

---

## Kill Switch Drills (Tier 3)

- Frequency: quarterly (minimum)
- Evidence: drill record + success criteria + time-to-disable metric
- Separation of duties:
  - executed by Platform/Engineering Owner
  - validated by Risk/Compliance or Independent AI Auditor
