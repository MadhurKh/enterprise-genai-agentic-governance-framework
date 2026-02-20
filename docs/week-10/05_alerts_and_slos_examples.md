# Week 10 — Alerts and SLOs (Examples)

**Goal:** Provide examples of operational alerts for Tier 2/3 systems aligned with governance gates.

---

## SLO Examples (Illustrative)

- **Sovereignty compliance:** 99.99% (Tier 2), **100% (Tier 3)**  
- **Breaker response time:** < 60 seconds to safe degrade mode  
- **Policy decision logging:** 100% of requests in Tier 2/3  
- **Redaction-before-immutability:** 100% for Restricted/Confidential data  
- **Jailbreak block effectiveness:** > 99% of detected attempts denied and logged  

---

## Alert Examples

### A) Sovereignty Violation (Critical)
- Condition: provider/region not in allowed list for EU-only request
- Severity: P0 for Tier 3, P1 for Tier 2
- Action: trip breaker → fail_closed/manual_mode; page on-call; notify Risk

### B) Policy Engine Unhealthy (Critical for Tier 2/3)
- Condition: policy engine health check fails
- Action: fail-closed for Tier 2/3; alert on-call; status update to governance

### C) Rate Limit / Token Quota (Major)
- Condition: sustained HTTP 429 over 5 minutes
- Action: throttle; failover if permitted; if not, degrade to manual_mode

### D) Cost/Budget Breach (Critical)
- Condition: cost_per_minute exceeds threshold OR budget per request exceeded repeatedly
- Action: trip breaker; investigate loops/tool misconfig

### E) Jailbreak Attempt Spike (Major)
- Condition: jailbreak_detected rate > threshold
- Action: increase deny enforcement; add WAF rules; investigate source; notify security

### F) HITL Override Spike (Major)
- Condition: override rate increases beyond baseline (quality regression)
- Action: hold expansion; trigger out-of-cycle review; rerun validation tests

---

## Ownership (Separation of Duties)

- Alerts are actioned by **Platform/Engineering Owner**
- Evidence for Tier 3 is validated by **Independent AI Auditor** or Risk/Compliance
