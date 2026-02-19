# RACI and Decision Rights

## Purpose

Define clear ownership for:
- classification, scoring, and gating
- approval decisions
- control implementation
- audit evidence and assurance
- incident response and kill-switch authority
- policy exceptions and waivers

---

## Roles (Definitions)

- **Business Owner (BO):** accountable for business outcome and acceptable risk posture
- **AI Product Owner (AIPO):** accountable for governance adherence, documentation, lifecycle control
- **Engineering / Platform Owner (EPO):** accountable for architecture, controls, observability, runtime stability
- **Risk & Compliance (RISK):** accountable for risk interpretation, gates, exceptions, regulatory alignment
- **Legal (LEGAL):** accountable for legal/regulatory exposure, contract and liability posture (Tier 2/3)
- **Security (SEC):** accountable for security posture, pen-tests, access control standards
- **Domain SME (SME):** consulted for domain correctness, operational realism, sampling review
- **Independent AI Auditor (AUD):** independent assurance for Tier 3; sampling and systemic drift/bias review

---

## RACI by Activity

**R = Responsible, A = Accountable, C = Consulted, I = Informed**

| Activity | BO | AIPO | EPO | RISK | LEGAL | SEC | SME | AUD |
|---|---|---|---|---|---|---|---|---|
| Use-case intake completion | A | R | C | C | C | C | C | I |
| Tier classification (proposal) | A | R | C | C | C | C | C | C (Tier 3) |
| Tier classification (approval) | A | A | C | A | A (Tier 2/3) | C | C | C (Tier 3) |
| Scorecard scoring | A | R | C | C | C | C | C | C (Tier 3) |
| Evidence maturity validation | I | A | R | C | C | C | C | A (Tier 3) |
| Hard gates evaluation | A | R | R | A | A (Tier 2/3) | A (security gate) | C | C (Tier 3) |
| Minimum controls implementation | I | A | R | C | C | R | C | C (Tier 3) |
| **Policy exception approval (waivers)** | I | R | C | **A** | **A (Tier 2/3)** | **A (security-related)** | C | C (Tier 3) |
| Pilot approval | A | A | C | A | A (Tier 2/3) | C | C | C (Tier 3) |
| Production approval | A | A | A | A | A (Tier 2/3) | A | C | A (Tier 3) |
| Incident response ownership | A | C | A | C | C | A | I | I |
| Kill-switch authority (manual) | A | A | A | C | C | A | I | I |
| Circuit breaker (auto) policy | I | A | A | A | C | A | C | C |
| Re-certification decision | A | A | A | A | A (Tier 2/3) | A | C | A (Tier 3) |

---

## Notes on Policy Exception Accountability

- In practice, **ARCC** is the forum where exceptions are reviewed and approved.  
- This matrix expresses ARCC accountability through **RISK/LEGAL/SEC** roles (depending on exception type).
- Exceptions must be time-bound and tied to compensating controls, recorded in the exception register.

---

## Decision Rights by Tier

### Tier 1
- Approval: **AIPO + BO**
- Risk/Legal: consulted for regulated contexts
- Evidence requirements: lightweight

### Tier 2
- Approval: **BO + AIPO + RISK**, Legal required when regulated or contractual exposure exists
- Evidence requirements: scorecard + gates + controls + evidence packet

### Tier 3
- Approval: **Executive BO + RISK + LEGAL + EPO + AUD**
- Evidence requirements: full packet + circuit breaker tests + kill-switch drills + auditor plan
