# Dimension-Level Scoring Anchors

## Purpose of Scoring Anchors

Scoring anchors ensure that a score of “3” or “4” means the **same level of maturity across teams, reviewers, and time**.

Each evaluation dimension is assessed using consistent anchors on a 0–5 scale.

---

## 1. Business Value & ROI

| Score | Anchor Description |
|-----|-------------------|
| 0 | No clear business problem or value case |
| 1 | Problem identified but value not estimated |
| 2 | Indicative value with weak assumptions |
| 3 | Clear value hypothesis with reasonable estimates |
| 4 | Quantified value supported by data |
| 5 | Demonstrated or realized business value |

---

## 2. Risk & Compliance Exposure

| Score | Anchor Description |
|-----|-------------------|
| 0 | High, unmanaged legal or regulatory risk |
| 1 | Risks identified but not mitigated |
| 2 | Partial mitigation; material gaps remain |
| 3 | Risks mitigated to an acceptable baseline |
| 4 | Strong controls; low residual risk |
| 5 | Continuous risk monitoring and active controls |

---

## 3. Reliability & Determinism

| Score | Anchor Description |
|-----|-------------------|
| 0 | Unpredictable behavior; no error handling |
| 1 | Frequent failures; no fallback logic |
| 2 | Basic stability; weak edge-case handling |
| 3 | Acceptable consistency with **defined manual fallback procedures** |
| 4 | High reliability with **automated graceful degradation** |
| 5 | Deterministic behavior with automated recovery and resilience testing |

---

## 4. Governance & Auditability

| Score | Anchor Description |
|-----|-------------------|
| 0 | No logs, traceability, or ownership |
| 1 | Minimal logging; ownership unclear |
| 2 | Partial audit trail; gaps remain |
| 3 | End-to-end traceability with accountable owners |
| 4 | Strong auditability with structured governance reviews |
| 5 | Enterprise-grade governance with independent oversight |

---

## 5. Security & Data Handling

| Score | Anchor Description |
|-----|-------------------|
| 0 | Uncontrolled data access or leakage risk |
| 1 | Basic controls; major gaps |
| 2 | Partial compliance with security policies |
| 3 | Acceptable enterprise security baseline |
| 4 | Strong data protection and access control |
| 5 | Continuous security monitoring and assurance |

---

## 6. Agentic Safety & Control

| Score | Anchor Description |
|-----|-------------------|
| 0 | Unbounded autonomy; no safeguards |
| 1 | Weak autonomy controls; opaque logic |
| 2 | Partial bounds; unclear escalation |
| 3 | Defined autonomy limits with mandatory HITL checkpoints |
| 4 | Policy-bound autonomy enforced through independent control layers |
| 5 | Mature agentic control with continuous monitoring and pre-emptive kill-switches |

---

## 7. Operational Readiness

| Score | Anchor Description |
|-----|-------------------|
| 0 | No operational ownership or support |
| 1 | Ad-hoc operational handling |
| 2 | Partial monitoring and support |
| 3 | Defined operational model |
| 4 | Strong monitoring and incident response |
| 5 | Production-grade operations with SLAs |

---

## 8. Vendor & Model Sovereignty

| Score | Anchor Description |
|-----|-------------------|
| 0 | Single-vendor dependency with no fallback |
| 1 | High lock-in risk; switching impractical |
| 2 | Limited alternatives; fallback poorly defined |
| 3 | Viable exit or fallback strategy defined |
| 4 | Multiple provider options with tested fallback |
| 5 | Vendor-agnostic design with seamless portability |

---

## Scoring Discipline

- Scores must be justified with documented evidence or rationale
- Conservative scoring is preferred in ambiguous cases
- Over-scoring is treated as a governance risk
