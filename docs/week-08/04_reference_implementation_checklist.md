# Week 8 — Implementation Blueprint: Reference Implementation Checklist (By Tier)

## Purpose

This checklist operationalizes Weeks 1–7 into a build-ready engineering contract.  
A system is not production eligible until this checklist is satisfied.

Use this during:
- solution design reviews
- architecture reviews
- pilot exit criteria
- production readiness reviews

---

## Tier 1 (Assistive AI) — Minimum Implementation

### Product + Governance
- [ ] Use case intake completed (Week 5)
- [ ] Tier 1 classification justified (Week 1)
- [ ] Owner named (Business Owner + AIPO)
- [ ] Disclosure and usage boundaries documented

### Security + Data
- [ ] RBAC enforced
- [ ] Data classification confirmed (no restricted data unless approved)
- [ ] Retention policy documented (pilot vs prod)

### Technical Controls
- [ ] Output schema validation for structured outputs (where applicable)
- [ ] Basic logging (non-sensitive metadata)
- [ ] Safe fallback defined (manual process exists)

### Evidence
- [ ] Evidence packet created for at least sampled outputs (recommended)

---

## Tier 2 (Decision Support) — Production Eligibility Checklist

### Governance and Permission
- [ ] Tier 2 classification justified (Week 1)
- [ ] Scorecard completed with evidence maturity (Week 5/7 example)
- [ ] Hard gates passed (Week 5)
- [ ] HITL defined (end-user verification) + training completion evidence
- [ ] Decision rights and cadence defined (Week 6)

### Sovereignty and Vendor
- [ ] Internal Model Gateway enforced (Week 8)
- [ ] Sovereignty routing tests executed (EU-only where required)
- [ ] Sovereignty metadata logged (provider, region, model version)

### Technical Enforcement
- [ ] Policy-as-code integrated for key enforcement points
- [ ] Tool permissions enforced (no write tools)
- [ ] Output schema contracts implemented
- [ ] Evidence references required for decision-impacting claims

### Auditability and Privacy
- [ ] Redaction before immutability implemented and tested
- [ ] Replayability metadata captured (prompt template version, model version, input hashes)
- [ ] Evidence store available with access controls

### Operations
- [ ] Monitoring dashboards created (quality, overrides, cost, latency)
- [ ] Incident runbooks published
- [ ] Circuit breaker enabled + fallback mode tested

---

## Tier 3 (Decision Execution) — High-Risk Eligibility Checklist

### Governance and Permission (Non-negotiable)
- [ ] Tier 3 classification justified (Week 1)
- [ ] Scorecard + gates approved by required roles (Week 1/6 decision rights)
- [ ] Independent AI Auditor assigned
- [ ] Exception management process defined (Week 6)
- [ ] Out-of-cycle recertification triggers configured (Week 6)

### Autonomy Boundaries
- [ ] Conditional autonomy boundaries defined (policy-bound and reversible)
- [ ] Transaction limits or scope caps implemented (where applicable)
- [ ] Human escalation path defined for out-of-bounds actions

### Policy-as-Code Enforcement
- [ ] Tool schema enforcement for every tool call
- [ ] Policy enforcement on every execution step (pre-flight + in-flight)
- [ ] Deny/degrade decisions tested

### Sovereignty and Platform
- [ ] Internal Model Gateway required and audited
- [ ] Multi-provider or explicit manual fallback strategy proven
- [ ] Region enforcement validated (zero tolerance for sovereignty breach)

### Circuit Breaker + Kill Switch
- [ ] Circuit breaker auto-trip simulation executed and evidenced
- [ ] Kill switch implemented and role-restricted
- [ ] Quarterly kill switch drills executed and evidenced
- [ ] Rollback tested for reversible actions

### Audit Evidence (High maturity)
- [ ] Evidence packet includes policy decision logs, routing decisions, and replay tests
- [ ] Privacy/redaction evidence included (GDPR-aware)
- [ ] Auditor sampling plan executed

---

## Pilot Exit Criteria (Recommended)

A pilot should not exit to production unless:
- all Tier baseline items are complete
- all P0 remediation items are closed
- evidence maturity upgraded for high-risk dimensions (security, sovereignty, auditability)
- operating model cadence and KPIs are active

---

## Notes

- This checklist should be embedded into the enterprise SDLC (architecture review, change control, release process).
- Tier reclassification is mandatory if tool permissions, data class, or autonomy posture changes.
