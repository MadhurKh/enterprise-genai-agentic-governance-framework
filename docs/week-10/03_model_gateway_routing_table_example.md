# Week 10 — Internal Model Gateway Routing Table (Example)

**Goal:** Provide a practical routing table that supports sovereignty, tier-based controls, and resilient fallback patterns.

---

## Routing Keys (Inputs)

- Tier: 1/2/3
- Region constraint: EU-only / global / client-specific
- Data classification: Public/Internal/Confidential/Restricted
- Capability: reasoning vs summarization vs extraction
- Runtime state: provider health, latency, rate limits, token quota, cost budget

---

## Standard Providers (Illustrative)

- **internal-eu-llm** (EU-hosted, enterprise-controlled)
- **azure-openai-eu** (EU region deployments)
- **aws-bedrock-eu** (EU region)
- **internal-global-llm** (global but controlled)
- **vendor-x-global** (fallback, only when allowed by policy)

---

## Fallback Patterns (Enterprise)

1. **Health fallback:** provider down → failover to approved secondary
2. **429 rate/token limit fallback:** quota reached → throttle or failover if policy permits
3. **Latency fallback:** above SLA → switch to smaller model / cached answer / manual mode
4. **Cost/budget fallback:** spend breach → trip breaker → safe degrade mode
5. **Safety fallback:** jailbreak/safety failure → deny + log + safe response template

---

## Example Routing Table

| Rule | Conditions | Primary | Secondary | Safe Degrade Mode |
|---|---|---|---|---|
| R1 | Tier 1, Public/Internal, Global | internal-global-llm | vendor-x-global (if allowed) | limited_mode |
| R2 | Tier 2, EU-only, Confidential+ | internal-eu-llm | azure-openai-eu | manual_mode |
| R3 | Tier 2, EU-only, 429 on primary | azure-openai-eu | aws-bedrock-eu | throttle_then_manual |
| R4 | Tier 3, EU-only, Restricted | internal-eu-llm | (none unless explicitly approved) | fail_closed |
| R5 | Tier 3, cost breach or loop detected | (n/a) | (n/a) | circuit_breaker_trip → manual_mode |
| R6 | Any tier, jailbreak detected | (deny) | (deny) | safe_response + log + alert |

---

## Notes for Implementation

- All routing decisions must be logged with **sovereignty metadata**:
  - provider, region, model, version, policy_decision_id
- Tier 2/3 must **fail-closed** if:
  - policy engine unavailable, or
  - no approved EU provider available for EU-only constraint
- 429 handling should include:
  - throttle limits
  - queue/backoff strategy
  - optional failover only if policy permits
- Treat sustained **token/quota exhaustion (HTTP 429)** as a **governance signal**, not only a reliability issue:
  - log it as a cost-control event,
  - trigger throttling/queuing,
  - and if sustained or excessive, consider a **cost-based circuit breaker trip** to safe fallback mode.
