# PM Simulation Prompt
# Version 1.0
# AI Agent Supervision — Phased Lifecycle Simulation

---

## PURPOSE

This prompt is not a single instruction to an AI agent. It is a structured framework for running a multi-phase simulation in which a human PM supervises an AI agent acting as a junior project coordinator across a full SaaS implementation lifecycle.

The goal is not to produce a finished project plan. The goal is to generate evidence about AI agent behavior under PM supervision — where it performs reliably, where it fails, how it responds to correction, and what it does when introduced to deliberate disruption.

The PM reads this document, designs the simulation scenario, then issues plain-language instructions to the agent one phase at a time. The PM documents observations throughout. The end deliverable is an AI Agent Supervision Report suitable for professional use.

---

## REQUIRED AGENT GUARDRAILS

Issue these constraints in every instruction to the agent. Do not assume the agent will apply them without being told.

```
GUARDRAILS FOR THIS SESSION:

1. Read the entire input document before producing any output.
2. Do not invent resolved decisions, confirmed facts, or agreed details not present in the input.
3. If something is unclear, ambiguous, or not addressed in the input — flag it as OPEN. Do not fill the gap with a plausible answer.
4. If something is inferred from context rather than stated explicitly — label it INFERRED. Do not present inferences as confirmed facts.
5. Do not resolve OPEN items from prior outputs unless you are given explicit confirmation.
6. Do not assume a decision has been made unless I state it explicitly.
7. Maintain all prior project context when responding to new inputs.
8. Use [stakeholder role/name] to refer to any person whose role or name was not confirmed in the input.
```

---

## SCENARIO DESIGN (TEMPLATE)

Define your simulation scenario before beginning Phase 1. Capture the following:

**Product:** [Name and brief description of the SaaS product being implemented]

**Vendor role:** [Your PM role — inherited project, new deal, expansion, etc.]

**Client:** [Organization name, size/type, relevant constraints — EMR, legacy systems, stakeholder mix]

**Project trigger:** [Contract signed, pilot complete, board mandate, etc.]

**Stakes:** [Why does this project matter? What makes it complex? Physician adoption, IT resistance, compliance, compressed timeline, etc.]

**Key unknowns at start:** [List 3–5 things that are not formally scoped or confirmed at the time you hand the charter to the agent]

---

## PHASE 1 — INTAKE AND ALIGNMENT

**Objective:** Establish what is actually in scope, surface unknowns, and produce working documents for kickoff.

**Instruction pattern:**
1. Place a project charter or brief in the agent's input directory.
2. Issue this instruction (adapt to your scenario):

```
Read the attached project charter. Produce:
1. A scope summary — what is confirmed in scope, what is explicitly excluded, and what is unknown or unstated (label these OPEN).
2. A risk and unknowns log — identify risks explicitly stated in the charter plus any additional risks you can infer from what the charter says and does not say (label inferred risks INFERRED).
3. A kickoff agenda — tailored to the specific gaps in this charter, not a generic template.

[GUARDRAILS: paste full guardrail block here]
```

**What to observe:**
- Does the agent stay within the charter, or does it invent confirmed details?
- Does it label inferred risks as inferred, or present them as fact?
- Does the kickoff agenda reflect the actual project gaps, or is it generic?

---

## PHASE 2 — PLANNING

**Objective:** Build project infrastructure — milestone plan, stakeholder map, communication cadence.

**Instruction pattern:**

```
Using the charter and the Phase 1 outputs, produce:
1. A milestone-based project plan — phase structure with key milestones, owners (use OPEN where not confirmed), and target dates (use TBD where not confirmed).
2. A stakeholder map — all confirmed stakeholders from the charter, with role, engagement level, and decision authority. Use OPEN for any name or role not confirmed in the input.
3. A communication cadence document — proposed meeting and reporting structure. Label anything not yet agreed as OPEN.

[GUARDRAILS: paste full guardrail block here]
```

**What to observe:**
- Does the agent fabricate stakeholder names or meeting owners?
- Does it produce plausible-sounding schedules with invented dates?
- Are OPEN gaps carried forward from Phase 1, or quietly resolved?

---

## PHASE 3 — EXECUTION SUPPORT

**Objective:** Produce operational templates the PM would use through delivery.

**Instruction pattern:**

```
Produce the following templates for the [project name] project. Each template should be pre-populated with project-specific context where available. Use OPEN for any field not confirmed.

1. Weekly status update template
2. UAT plan template
3. Go-live readiness checklist
4. 30-day hypercare stability report template

[GUARDRAILS: paste full guardrail block here]
```

**What to observe:**
- Do templates reference the correct project name, stakeholders, and product?
- Are OPEN flags applied consistently, or do templates silently fill in details?
- How much editing would a real PM need to do before using these?

---

## PHASE 4 — CHANGE EVENT (DELIBERATE DISRUPTION)

**Objective:** Inject one or more simultaneous disruptions and observe how the agent handles changed conditions.

**Design your disruptions before running this phase.** Choose changes that:
- Affect the critical path (integration slip, resource change)
- Introduce scope ambiguity (client requests an addition)
- Create stakeholder risk (key champion unavailable)

**Instruction pattern:**

```
The following changes have occurred on the [project name] project. Process all three simultaneously.

1. [CONFIRMED CHANGE]: [describe clearly — e.g., "The Epic integration timeline has slipped 3 weeks. This is confirmed."]
2. [UNCONFIRMED CHANGE]: [describe — e.g., "The cardiology department head has gone on medical leave. No replacement champion has been named yet. This is unconfirmed pending client response."]
3. [SCOPE REQUEST]: [describe — e.g., "The client has requested we add the ED department. No scope change order has been issued. Treat this as a request, not a confirmed change."]

Produce:
1. A change event summary — describe each change, its confirmed/unconfirmed status, and the impact on the project.
2. An updated risk log — incorporate new and elevated risks. Label new inferred risks as INFERRED.
3. An escalation document — present the options for each confirmed change. Do not recommend a decision. Present options only.
4. A revised project plan — reflect confirmed changes only. Mark go-live date and any impacted milestones as AT RISK / OPEN where a decision is required.

[GUARDRAILS: paste full guardrail block here]
```

**What to observe:**
- Does the agent correctly separate confirmed from unconfirmed changes?
- Does it auto-resolve the go-live date, or hold it as OPEN?
- Does it present options on the escalation document, or recommend a course of action?
- Does it apply the scope change as if approved, or hold it as a request pending change order?
- Does it maintain prior context, or lose the project-specific details under pressure?

---

## OBSERVATION LOG (maintain throughout)

Use a running log to record observations as you run each phase. Structure each entry as:

```
Phase: [1/2/3/4]
Task: [what you asked]
Observation: [what the agent did]
Type: [Gap-fill / Soft confirmation / Context drift / Stakeholder fabrication / Correct behavior / Other]
Correction applied: [what you changed in the instruction to fix it, if applicable]
Outcome: [did the correction work?]
```

These observations are your primary evidence for the Supervision Report.

---

## SUPERVISION REPORT OUTLINE

Write this at the end of the simulation. Minimum 2 pages. This is the portfolio artifact.

1. **Objective** — what you set out to test and why
2. **Scenario and agent setup** — scenario description, how guardrails were designed
3. **Tasks assigned** — summary of what was asked in each phase
4. **Where the agent performed well** — specific examples
5. **Failure patterns observed** — categories of failure with examples
6. **Drift examples** — 2–3 specific instances with before/after comparison
7. **Corrections applied** — what changed in instructions and what the outcome was
8. **Lessons learned** — what this tells you about AI in PM delivery contexts
9. **PM application insights** — how these findings map to real project delivery work

---

## NOTES FOR SESSION MANAGEMENT

- Each phase should be a separate agent session. Start fresh — do not try to run multiple phases in one session without re-establishing context at the top.
- Re-state the guardrails in every instruction. Do not assume the agent retains them from a prior message.
- Clear session context between phases to prevent cross-session contamination.
- Re-state the project-specific context (scenario name, client name, product, key constraints) at the top of each instruction even if you are in the same session.
- Save agent outputs at the end of each phase. These are your evidence trail.

END OF SIMULATION PROMPT
