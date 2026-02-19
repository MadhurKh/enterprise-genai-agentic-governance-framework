# Exception Management and Policy Waivers

## Purpose

Exceptions are inevitable in enterprises. This process ensures exceptions are:
- explicit (never implicit)
- risk-assessed
- time-bound
- backed by compensating controls
- audit-defensible

---

## Key Rule

If a control from **Week 5 Minimum Controls** or a **Hard Gate requirement** is not met, it must be:
1) remediated before approval, **or**
2) raised as a documented exception and approved by the right authority.

---

## What Requires an Exception

- reduced retention periods due to PII considerations
- inability to use a secondary model provider (vendor lock-in unavoidable)
- delayed implementation of circuit breaker automation (interim manual controls)
- partial evidence maturity due to pilot constraints
- temporary access broadenings during controlled rollout

---

## Exception Record (Minimum Fields)

- Exception ID
- Control / policy referenced
- Description of deviation
- Risk introduced
- Compensating control(s)
- Owner
- Approver(s)
- Expiry / review date
- Evidence references

**System of Record:**  
All exceptions must be centrally logged in the enterprise **GRC (Governance, Risk, and Compliance) platform** or an access-controlled registry (e.g., **Jira SecOps**) to ensure they are tracked for expiration, renewal, and audit.

---

## Approval Authority

### Tier 1
- AIPO + BO

### Tier 2
- AIPO + BO + RISK  
- LEGAL if regulated/contractual exposure

### Tier 3
- Executive BO + RISK + LEGAL + SEC + AUD  
- EPO required if architecture/control-plane impacted

---

## Exception Closure

Exceptions must be closed by:
- remediation completion, or
- explicit risk acceptance renewal (time-bound), or
- decommissioning / rollback if risk cannot be controlled

No exception is “permanent by default.”
