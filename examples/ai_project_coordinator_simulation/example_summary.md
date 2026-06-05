# Example Summary: AI Project Coordinator Simulation

---

## Scenario

Full-lifecycle simulation of a healthcare AI SaaS implementation. A vendor PM inherits a signed contract for a clinical documentation platform deployment at a three-campus hospital network. Eighty-five physicians in scope across primary care, cardiology, and emergency medicine. Epic EMR integration required. Compressed 10-week timeline. The PM inherits the project post-contract-signature with nothing formally scoped.

The simulation ran four phases: intake and alignment, planning, execution support, and deliberate disruption. Phase 4 introduced three simultaneous change events to test AI adaptability under real delivery conditions.

---

## Objective

Operate an AI agent as a junior project coordinator across a full implementation lifecycle and document what the supervision experience reveals about AI reliability, failure patterns, and the governance design required to use AI productively in a delivery context.

---

## My Role

Simulation designer, PM supervisor, and documentation lead. Designed the scenario and all four phases. Wrote every instruction issued to the agent. Reviewed all outputs before advancing to the next phase. Designed and introduced the Phase 4 change events deliberately, with defined hypotheses about what behavior they would test. Documented observations throughout in a running log. Corrected AI behavior when it drifted. Wrote the final AI Agent Supervision Report.

---

## Input

Project charter created for the simulation. Plain-language scenario brief covering project scope, client organization, integration requirements, known risks at contract signature, and vendor resource structure. Approximately 400 words.

---

## Outputs Produced

**Phase outputs (8 files):**
- Scope summary, risk log (15 items), stakeholder map, project plan (Phase 0–6)
- Change event summary, updated risk log, escalation document (3 options), revised project plan (AT RISK)

**Templates (4 files):**
- Weekly status update, UAT plan, go-live readiness checklist, 30-day hypercare report

**Supervision report (1 file):**
- AI Agent Supervision Report — 9-section professional report documenting objective, setup, tasks assigned, strong performance areas, failure patterns, specific drift examples, corrections applied, lessons learned, and PM application insights

---

## Key Observation

The Phase 4 change event test was the most instructive part of the simulation. Introducing three simultaneous disruptions — one confirmed (integration timeline slip), one unconfirmed (stakeholder unavailability), one pending (scope expansion request) — revealed the AI's tendency to auto-resolve OPEN items downstream of the confirmed change. On first run, the revised project plan moved the go-live date to a new confirmed date even though the go-live decision had not been made. Correcting this required an explicit instruction: "reflect confirmed changes only — mark the go-live date as AT RISK and OPEN." After correction, the output was correct. The failure mode was predictable; the correction was simple; but it would not have been caught without active review.
