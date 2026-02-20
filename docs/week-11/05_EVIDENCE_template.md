# EVIDENCE.md — Evidence Capture Guide (Starter Template)

**Purpose:** Standardize how teams capture and store evidence required for Tier 2/3 governance and audits.

---

## Evidence Categories

1. **Classification Evidence**
   - tier rationale, autonomy bounds, scope definition

2. **Readiness Evidence**
   - scorecard + weights snapshot
   - evidence maturity justification per dimension

3. **Permission Evidence**
   - gates checklist
   - HITL training record references
   - policy exceptions / waivers (if any)

4. **Technical Enforcement Evidence**
   - gateway contract version
   - policy bundle version
   - circuit breaker configuration and safe fallback mode

5. **Validation Evidence**
   - sovereignty tests
   - jailbreak attempt tests
   - redaction tests
   - breaker trip simulations

6. **Runtime Evidence**
   - alerts and SLOs
   - drill records (Tier 3)
   - incidents and postmortems

---

## Minimum Required Fields (All Evidence Items)

- use_case_id
- release_id
- owner
- date
- link/path to artifact
- correlation_id (where applicable)

---

## Policy Exception Register (Enterprise Reality)

If the release requires any deviation from minimum controls:
- record the exception in the SoR (GRC / Jira SecOps)
- include compensating controls and expiry date
- add the exception ID to the audit packet and evidence index

---

## Redaction Rule (EU Reality)

No raw PII prompts are allowed in immutable logs.
- store redacted prompt versions, hashed references, or secured “vault” links
- prove redaction via a `redaction_summary` audit event
