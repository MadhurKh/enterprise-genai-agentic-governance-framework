# Operational Assurance Plan (Controls That Must Be Proven)

## Purpose

Define what must be **tested, evidenced, and continuously assured** for Tier 2/3 systems.

This prevents “paper governance” by requiring proof that controls work in reality.

---

## Assurance Categories

### 1) Policy and Gate Assurance
- gate checklist passed with evidence
- policy-as-code rules are versioned and tested
- regression tests exist for key policy conditions

### 2) Schema Contract Assurance
- JSON schemas validated at runtime
- schema changes trigger re-certification
- evidence schema supports replayability

### 3) Logging and Privacy Assurance
- PII redaction occurs **before** immutability
- retention policy enforced
- access to evidence store is permissioned and audited

### 4) Sovereignty Assurance
- internal model gateway is used
- region routing/residency rules are testable
- fallback behavior is validated (provider outage simulation)

### 5) Circuit Breaker and Kill Switch Assurance
- circuit breaker trips on repeated violations
- safe fallback mode works
- Tier 3: quarterly kill-switch drills produce evidence

---

## Mandatory Tests (Minimum)

### Tier 2
- replay test (selected cases)
- schema validation tests
- fallback simulation (manual mode)
- gate regression tests (core gates)
- sampling QA (monthly)

### Tier 3
- all Tier 2 tests plus:
- automated fallback simulation
- circuit breaker auto-trip simulation
- kill-switch drill record
- privileged access reviews
- auditor systemic review (quarterly)

---

## Separation of Duties (Execution vs Validation)

To avoid “self-attestation”:

- **Operational tests** (e.g., failover simulation, circuit breaker auto-trip, kill-switch drills) are executed by the **Engineering / Platform Owner (EPO)**.
- **Evidence validation** must be performed by **Risk/Compliance (RISK)** or the **Independent AI Auditor (AUD)** for Tier 3, ensuring independent confirmation that controls worked as intended.

Evidence must include:
- test execution timestamp
- actor (who executed)
- environment
- expected vs observed outcomes
- links to logs/screenshots/artifacts
- reviewer sign-off (RISK/AUD)

---

## Evidence Outputs

- test results (links)
- configuration snapshots
- drill records (Tier 3)
- sampling logs (what was reviewed and what changed)
- incident postmortems and remediation evidence
