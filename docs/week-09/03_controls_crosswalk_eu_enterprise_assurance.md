# Week 9 — Controls Crosswalk (EU Governance Themes + Enterprise Assurance)

**Purpose:** Help executives, auditors, and procurement/security teams see “coverage” at a glance.  
**Note:** This is a practical mapping to common enterprise expectations (not legal advice).  
**Repository:** https://github.com/MadhurKh/enterprise-genai-agentic-governance-framework

---

## How to Use This Crosswalk

- Start with a use case (Week 5 intake)
- Identify its Tier (Week 1)
- Apply scoring + gates (Week 2/5)
- Validate architecture enforcement (Week 3/8)
- Capture evidence (Week 5/6)
- Track exceptions (Week 6)

---

## Crosswalk Table

| Governance Theme (Common EU / Enterprise Expectation) | What We Require in This Framework | Where It Lives (Repo Weeks) | Evidence Artifact |
|---|---|---|---|
| **Accountability & Ownership** | Named Business Owner + AIPO; tier-based approval rights; independent auditor for Tier 3 | W1, W6 | RACI, decision record, approval log |
| **Risk Proportionality** | Tier 1/2/3 classification; tier-specific weights and minimum controls | W1, W2, W5 | Tier rationale, weighting matrix, controls checklist |
| **Human Oversight** | HITL roles defined (end-user/SME/auditor); training record required | W1, W5, W6, W7 | Gate checklist + training evidence |
| **Transparency** | Disclosure and bounded claims; decision-impacting outputs require evidence references | W1, W3, W5 | Output schema, evidence snippets, user acceptance log |
| **Technical Robustness** | Reliability anchors; graceful degradation; incident runbooks | W2, W6, W8 | Validation tests, breaker logs, runbooks |
| **Security** | RBAC; least privilege tool access; threat model / pen-test evidence maturity | W2, W3, W5, W6, W8 | Security test report, access logs |
| **Data Protection / Privacy** | PII redaction before immutability; retention controls; replay without raw PII | W3, W6, W8 | Redaction report, log samples, retention policy |
| **Auditability / Traceability** | Immutable event schema; replayability metadata; policy decision logs | W3, W5, W6, W8 | Evidence packet, policy logs, replay report |
| **Sovereignty / Residency** | Internal model gateway; provider/region routing; sovereignty metadata captured per response | W2, W3, W8 | Gateway logs, metadata fields, routing tests |
| **Agentic Safety** | Conditional autonomy only; tool schemas; circuit breaker auto-trip + kill switch drills | W1, W3, W6, W8 | Breaker tests, drill record, tool call logs |
| **Change Control** | Triggers include model/prompt/tool changes + context/regulatory drift; recertification required | W5, W6, W7 | Change ticket, recert record |
| **Exception Management** | Time-bound waivers with compensating controls; system of record in GRC/Jira SecOps | W6, W7 | Exception register + approvals |

---

## Quick “Audit Narrative” (What an Auditor Will Ask)

1. **What is the use case and why AI?** (intake + baseline)  
2. **What tier and why?** (tier rationale)  
3. **How did you measure readiness?** (scorecard + evidence maturity)  
4. **What gates prevent unsafe release?** (gates checklist)  
5. **How is it enforced technically?** (architecture + policy-as-code + gateway + breaker)  
6. **How do you prove it after the fact?** (logs, evidence store, replay)  
7. **What changed since approval?** (change control, recertification)  
8. **Any exceptions?** (exception register, expiry, compensating controls)
