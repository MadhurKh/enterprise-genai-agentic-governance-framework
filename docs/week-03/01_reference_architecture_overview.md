# Reference Architecture Overview (Week 3)

## Purpose

Week 3 closes the loop between **governance policy** (Weeks 1–2) and **technical enforcement** (architecture and controls).

This reference architecture defines where enterprise controls live across the GenAI / Agentic AI lifecycle:

- Input handling and data protection
- Prompting, retrieval, and reasoning boundaries
- Tool/action execution (agentic control)
- Auditability and evidence capture
- Monitoring, incident response, and kill-switch patterns
- Vendor/model sovereignty and fallback strategies

The outcome is a **buildable blueprint** that allows engineering teams to implement governance requirements consistently.

---

## Scope

This architecture applies to:

- Tier 1–3 GenAI and Agentic AI use cases
- Internal and client-facing enterprise deployments
- Regulated and high-impact workflows requiring auditability

It is intentionally **vendor-agnostic** and can map to common enterprise stacks.

---

## Architecture Principles (EU Enterprise Lens)

1) **Policy must be enforceable**
Governance controls must map to enforceable technical mechanisms (not “process-only” controls).

2) **Readiness is not permission**
A system can score well but still be blocked by permission gates; architecture must implement these gates.

3) **Auditability by design**
Every material output must be reconstructable: inputs, prompts/templates, evidence, model versions, tool calls, and human decisions.

4) **Controlled autonomy**
Autonomy must be bounded by:
- policy constraints
- schema constraints
- tool permissions
- explicit kill-switch capability

5) **Sovereignty-first engineering**
Design must reduce single-vendor dependency via abstraction, portability patterns, and tested fallback routes.

---

## Reference Architecture Building Blocks

Week 3 introduces six core building blocks:

1) **Experience Layer**
UI / API entry points; authentication; user roles; consent and disclosure.

2) **Orchestration Layer**
Prompt templates, routing, retrieval, structured outputs, agent loops (if any).

3) **Control Plane (Guardrails)**
Policy engine, safety constraints, tool permissions, tier-based enforcement, kill-switch.

4) **Execution Plane**
Model calls, retrieval calls, tool/action calls, integrations.

5) **Evidence + Audit Layer**
Event log schema, evidence store, decision trace, replayability.

6) **Operations Layer**
Monitoring, alerting, incident response, drift detection, cost controls, change management.

---

## Deliverables (Week 3 Files)

1. `01_reference_architecture_overview.md` (this file)
2. `02_genai_reference_architecture.md`
3. `03_agentic_ai_reference_architecture.md`
4. `04_guardrails_and_control_plane.md`
5. `05_schema_contracts.md`
6. `06_audit_logging_and_evidence_store.md`

---

## How Week 3 Connects to the Framework

Week 3 is the implementation companion to:

- **Week 1 Risk Tiers:** what controls are required
- **Week 2 Scoring + Gates:** what must be technically provable
- **Week 4 Worked Example:** how a system would implement audit logging and permission gates

This ensures the framework is not only “decision-ready” but also “implementation-ready.”
