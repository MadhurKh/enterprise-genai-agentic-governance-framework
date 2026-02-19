# Governance Cadence and Review Cycles

## Purpose

Define repeatable review cycles so governance is:
- continuous (not one-time approvals)
- proportional to risk
- audit-ready by design

This file includes both:
- scheduled review cadence, and
- out-of-cycle triggers for immediate re-evaluation (especially Tier 3).

---

## Cadence by Tier

### Tier 1 — Assistive
- **Operational review:** monthly
- **Scorecard refresh:** quarterly or upon change control triggers
- **Sampling / QA:** lightweight (spot checks)

### Tier 2 — Decision Support
- **Pilot review:** weekly during pilot
- **Operational review:** monthly post-pilot
- **Scorecard + gates re-check:** quarterly
- **Sampling / QA:** monthly sampling plan (SME + AIPO)

### Tier 3 — Decision Execution
- **Pilot review:** weekly (mandatory)
- **Operational review:** bi-weekly or monthly depending on criticality
- **Scorecard + gates re-check:** every 60–90 days
- **Auditor review:** monthly sampling + quarterly systemic review
- **Kill-switch drills:** quarterly (minimum)
- **Access review for privileged roles:** quarterly

---

## Out-of-Cycle Re-Certification Triggers (Mandatory for Tier 3)

Tier 3 systems require an immediate review when any of the following occur:

1. **Regulatory / policy change**
   - new EU AI Act guidance, enforcement interpretations, sector rules, privacy changes

2. **Known base model vulnerability or major model behavior change**
   - provider incident, model regression, jailbreak pattern, safety degradation, vendor “silent” update

3. **Sovereignty risk event**
   - provider outage, region routing failure, residency assurance cannot be proven, fallback failure

4. **Material incident or near-miss**
   - P0/P1 incident, repeated circuit breaker trips, suspicious override spikes

5. **Scope creep**
   - expanded user group, increased decision criticality, new data class introduced (PII/PHI/PCI)

**Outcome of out-of-cycle review:** Continue / restrict / rollback / block until controls are restored.

---

## Standard Review Agenda (Tier 2/3)

1. **Incidents & near-misses**
2. **Gate breaches / circuit breaker trips**
3. **Override statistics** (HITL accept/override rates)
4. **Quality and drift signals**
5. **Sovereignty compliance** (routing/regions, provider stability)
6. **Cost and performance** (latency, spend)
7. **Change control log** (what changed and why)
8. **Open remediation items** (P0/P1/P2)

---

## Required Review Outputs

- meeting record (date, attendees)
- decisions made (approve / continue pilot / pause / block)
- action items (owner + due date)
- evidence links updated (scorecard, gates, exception register)
