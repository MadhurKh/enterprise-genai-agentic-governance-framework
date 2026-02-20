# Week 10 — Release Readiness Checklist (Tiered)

**Goal:** A tier-aware “Definition of Done” that ties together gates, minimum controls, evidence, and enforcement patterns.

---

## Tier 1 (Assistive) — Release Checklist

- [ ] Tier 1 classification rationale documented
- [ ] No write tools; read-only scope enforced
- [ ] Basic logging enabled (request_id, use_case_id, model metadata)
- [ ] Privacy checks completed for data used
- [ ] User disclosures included (limitations + safe use)
- [ ] Sample audit plan defined (quarterly)

---

## Tier 2 (Decision Support) — Release Checklist

- [ ] Tier 2 classification rationale documented
- [ ] Scorecard completed with evidence maturity per dimension
- [ ] Hard gates checklist passed (or pass-with-conditions with owners/dates)
- [ ] HITL roles defined + training record captured
- [ ] Internal Model Gateway integrated (no direct vendor calls)
- [ ] Sovereignty routing enforced + metadata captured
- [ ] Circuit breaker enabled + tested safe degrade mode (manual/read-only)
- [ ] Redaction before immutability verified
- [ ] Prompt injection / jailbreak tests executed and documented
- [ ] Incident response runbook prepared
- [ ] Change control triggers registered; recert cadence assigned

---

## Tier 3 (Decision Execution) — Release Checklist

- [ ] Tier 3 classification and autonomy bounds approved (conditional autonomy only)
- [ ] Independent AI Auditor assigned
- [ ] Threat model and pen-test results completed
- [ ] Policy-as-code enforcement enabled (pre/in/post flight)
- [ ] Tool permissions constrained (schemas + least privilege)
- [ ] Circuit breaker auto-trip tested (safety/sovereignty/cost)
- [ ] Kill switch drill executed (current quarter) + evidence stored
- [ ] Fail-closed behavior verified when policy engine unavailable
- [ ] Break-glass procedure documented and approved
- [ ] Replayability evidence prepared (post-redaction)
- [ ] Executive sign-off recorded + next review date set

---

## Final Release Record (All Tiers)

- [ ] Decision record stored in system of record (GRC/Jira SecOps)
- [ ] Evidence packet assembled (Week 5 template)
- [ ] Exceptions (if any) logged with expiry and compensating controls
