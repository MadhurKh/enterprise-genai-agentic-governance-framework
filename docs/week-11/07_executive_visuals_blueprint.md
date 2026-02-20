# Week 11 — Executive Visuals Blueprint (Carousel Outline)

**Goal:** Provide a clear structure for a LinkedIn-friendly PDF carousel that summarizes Weeks 1–11.

---

## Carousel Structure (5 slides)

### Slide 1 — The Problem
“Readiness is not permission.”  
Most GenAI programs stall in POC purgatory because Risk/Legal can’t approve safely.

### Slide 2 — Tier Model
Tier 1 (assist) → Tier 2 (decision support) → Tier 3 (decision execution)

### Slide 3 — Permission Model
Hard gates override score.  
(HITL, auditability, sovereignty, privacy redaction, breaker readiness)

### Slide 4 — Enforcement Architecture
Internal Model Gateway + Policy-as-Code + Circuit Breaker = enforceable governance

### Slide 5 — What’s Included (Proof)
Templates (Week 5), Operating Model (Week 6), Examples (Week 7), Policy/Gateway/Breaker (Weeks 8–10), Packaging + MVI walkthroughs (Week 11)

---

## Optional Slide 6 (If You Want)
“Week 10–11 = Implementation Kit”  
OpenAPI gateway contract, policy samples, breaker runbook, JSONL audit examples, tiered release checklist.

---

## Visual Tips (LinkedIn)
- Use short sentences and whitespace
- Use 1 key diagram (gateway/breaker flow)
- Avoid dense tables; show “checklists” instead

---

## Suggested Diagram (for Slide 4 — Enforcement Architecture)

Use a single, clean flow diagram that shows **where enforcement happens** (gateway + policy + breaker) and where evidence is captured.

**Diagram elements (recommended):**
```
[User/App]
   |
   v
[Experience Layer]
(UI/API Gateway + RBAC + Consent)
   |
   v
[Orchestration Layer]
(Prompts + Tools + RAG)
   |
   +-------------------------------+
   |                               |
   v                               v
[Policy Engine (OPA)]
(Pre/In/Post-flight checks)     [Internal Model Gateway]
(Deny / Degrade / Fail-closed)  (Provider routing + fallback)
   |                               |
   +---------------+---------------+
                   |
                   v
          [Execution Plane]
     (LLM(s) + Tools + Data)
                   |
                   v
     [Circuit Breaker / Safe Fallback]
 (Auto-trip → safe_degrade_mode; manual kill switch)
                   |
                   v
         [Evidence + Audit Layer]
   (Redaction → immutable logs → replay)
```

**Design tip:** Visually emphasize the three enforcement controls:
- Policy Engine
- Internal Model Gateway
- Circuit Breaker
