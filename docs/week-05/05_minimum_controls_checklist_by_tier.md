# Minimum Controls Checklist by Risk Tier

## Purpose

This checklist operationalizes minimum controls by tier.  
It is designed to prevent “tier inflation” (high-risk behavior in low-control deployments).

---

## Tier 1 — Assistive / Low Risk (Minimum Controls)

Governance + Process:
- [ ] Business owner and AI product owner identified
- [ ] User disclosure present (“AI-assisted”)
- [ ] Feedback loop exists (user can report issues)

Technical:
- [ ] RBAC enforced
- [ ] Prompt templates versioned
- [ ] Basic output filtering (safety baseline)
- [ ] Logging enabled (request metadata + prompt template version + output hash)

Operational:
- [ ] Rate limits and cost controls defined
- [ ] Incident response contact defined

---

## Tier 2 — Decision Support / Medium Risk (Minimum Controls)

Governance + Process:
- [ ] Tier classification documented and approved
- [ ] HITL role defined (end-user verification or SME review)
- [ ] Decision accountability documented
- [ ] Pilot scope defined (duration, users, blast radius)

Technical:
- [ ] Structured output schema validation (material outputs)
- [ ] Evidence capture (citations/refs/hashes)
- [ ] Internal Model Gateway used (sovereignty abstraction)
- [ ] Tool registry enforced for any tool usage
- [ ] Manual fallback runbook exists (provider outage / failure mode)

Operational:
- [ ] Monitoring baseline (latency, errors, quality signals)
- [ ] Alerting thresholds defined
- [ ] Change control required for prompt/model updates
- [ ] Periodic review cadence defined

---

## Tier 3 — Decision Execution / High Risk (Minimum Controls)

Governance + Process:
- [ ] Executive business owner named
- [ ] Risk + Legal sign-off captured
- [ ] Independent AI auditor defined (sampling plan)
- [ ] Explicit approval checkpoints for out-of-bounds actions
- [ ] Kill-switch drill schedule defined (e.g., quarterly)

Technical:
- [ ] Policy engine (policy-as-code) enforced
- [ ] Least-privilege tool permissions + scopes
- [ ] Schema-bound actions (inputs/outputs/action contracts)
- [ ] Rollback strategy for reversible actions
- [ ] Circuit breaker auto-trip configured (policy/safety failures)
- [ ] Immutable/append-only logging for action events (redacted)
- [ ] Privacy & redaction layer before immutability
- [ ] Multi-provider fallback or manual mode validated

Operational:
- [ ] Runbooks for incidents + escalations
- [ ] Drift monitoring and behavior anomaly signals
- [ ] Access reviews for privileged roles
- [ ] Re-certification triggers defined (model/tool/policy changes)
