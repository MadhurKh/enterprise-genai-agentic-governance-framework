# POLICY.md — Policy-as-Code Governance (Starter Template)

**Purpose:** Define how policy rules are authored, reviewed, approved, tested, deployed, and audited.

---

## Scope

This file applies to:
- OPA/Rego policy bundles
- any policy engine rules that gate Tier 2/3 execution
- sovereignty routing rules and tool permission rules
- circuit breaker obligations (deny vs. degrade vs. fail-closed)

---

## Policy Change Principles

- **Readiness is not permission.** Policies enforce permission.
- Tier 2/3 must **fail-closed** if policy engine is unavailable.
- Policies are version-controlled and auditable.
- Policy exceptions must be explicit, time-bound, and recorded in the SoR.

---

## Ownership and Approvals

| Change Type | Examples | Required Approvals |
|---|---|---|
| Minor | wording, comments, non-functional refactor | Policy Owner + Reviewer |
| Material | rule logic change, sovereignty allowlist change, tool permission change | Policy Owner + Risk/Compliance |
| High Risk | Tier 3 autonomy scope expansion, break-glass policy changes | Policy Owner + ARCC + Independent AI Auditor |

---

## Testing Requirements (Before Merge)

- Unit tests for policy rules
- Simulation tests using representative inputs
- Negative tests (jailbreak, tool escalation, region mismatch)
- For Tier 3: **fail-closed tests** (policy engine unhealthy/unreachable)

---

## Deployment Controls

- Deploy policies via CI/CD
- Record policy version and policy_decision_id in audit events
- Maintain rollback plan (previous policy bundle)

---

## Audit Requirements

For each policy release:
- policy version
- commit hash
- approver list
- test evidence links
- effective date/time
- list of active policy exceptions (if any)
