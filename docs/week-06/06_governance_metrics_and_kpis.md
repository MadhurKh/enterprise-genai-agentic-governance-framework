# Governance Metrics and KPIs

## Purpose

Governance must be measurable. These KPIs show whether the framework is:
- enabling safe scale
- preventing incidents
- improving audit readiness
- reducing POC-to-production friction

Targets below are illustrative and should be calibrated to enterprise context.

---

## Portfolio-Level KPIs (with illustrative targets)

- **% of use cases classified by tier** (Target: 100%)
- **Time from intake → pilot decision (median)** (Target: < 14 days)
- **Time from pilot → production (median)**  
  - Tier 2 (Target: < 60 days)  
  - Tier 3 (Target: context-dependent; decision forum cadence-bound)
- **% of use cases passing gates on first review** (Target: > 70%)
- **Top failed gates (by frequency)** (Target: trending downward quarter-over-quarter)
- **# of approved exceptions** and **exception closure rate** (Target: > 80% closed before expiry)
- **Re-certification adherence rate** (changes captured vs discovered) (Target: > 95%)

---

## Runtime KPIs (Tier 2/3)

- **HITL acceptance rate** and **override rate** (Target: stable baseline; investigate spikes)
- **Override reasons distribution** (hallucination, wrong evidence, policy breach) (Target: decreasing severe categories)
- **Circuit breaker trip count** and time-to-recovery (Target: trip count low; recovery < SLA)
- **Sovereignty violations** (routing outside allowed region, provider mismatch) (Target: 0)
- **Quality drift signals** (trend) (Target: within control limits)
- **Incident count** (severity P0/P1/P2) and mean time to resolve (Target: P0 = 0 tolerance for Tier 3)

---

## Audit Readiness KPIs (with illustrative targets)

- **% of use cases with complete evidence packets** (Target: Tier 2/3 = 100%)
- **Evidence maturity distribution** across dimensions (Target: majority documentation/test-backed; reduce self-assessed)
- **Replayability success rate** (sampled cases) (Target: > 95%)
- **Logging privacy compliance rate** (redaction checks passed) (Target: 100%)

---

## Tier 3 Governance Health KPIs (Zero-Tolerance Examples)

- **% of Tier 3 systems with current successful kill-switch drills** (Target: 100% — zero tolerance)
- **Circuit breaker auto-trip tested within last 90 days** (Target: 100%)
- **Sovereignty violations** (Target: 0)
- **Unreviewed privileged access changes** (Target: 0)

---

## Governance Health Signals (Interpretation)

- If **gate pass rate is low** → upstream design needs improvement (Week 3/5 adoption)
- If **exceptions trend upward** → policy unclear or controls misaligned to operational reality
- If **overrides spike** → quality drift, retrieval failures, weak HITL SOPs, or unsafe autonomy boundaries
- If **sovereignty violations occur** → model gateway enforcement gaps; treat as high severity
- If **time-to-decision exceeds target** → governance bottleneck; adjust board cadence or standardize intake completeness
