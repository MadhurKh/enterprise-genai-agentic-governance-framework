# Filled Example — Policy Exception Register (Sample)

## System of Record (Example)

All exceptions must be logged in:
- Enterprise GRC platform **or**
- an access-controlled registry (e.g., Jira SecOps project: `AI-GRC`)

This example shows how exceptions should be documented for audit.

---

## Exception Register (Sample Entries)

| Exception ID | Policy / Control Referenced | Deviation Description | Risk Introduced | Mitigation / Compensating Control | Approver (Role/Name) | Expiry / Review Date | Evidence Ref |
|---|---|---|---|---|---|---|---|
| EX-001 | Week 3/5 Logging: retention duration | Logs retained for **12 months** instead of 24 due to PII risk and minimization posture. | Reduced investigation window for long-tail incidents. | Increase sampling frequency; retain hashed evidence metadata for 24 months; store redacted summaries only. | Risk (A) + Legal (A) | Review in 90 days | Retention policy doc |
| EX-002 | Week 2/3 Sovereignty: multi-provider fallback | No secondary LLM provider available for EU-only deployment during pilot. | Vendor outage could reduce availability. | Manual mode fallback; outage runbook; SLA monitoring; plan to onboard alternate provider by Q3. | Risk (A) + Platform (C) | Review in 60 days | Gateway design + runbook |

---

## Exception Closure Plan (Template)

For each exception:
- define closure target
- define owner
- confirm compensating control evidence exists
- close or renew with explicit approval before expiry
