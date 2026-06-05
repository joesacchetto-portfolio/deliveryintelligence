# Human-in-the-Loop Design
## AI-Assisted Project Delivery Framework

**Author:** Project Manager / Framework Architect
**Version:** 1.0
**Date:** 2026

---

## Why This Document Exists

The phrase "human-in-the-loop" is used loosely in most AI discussions. It can mean anything from "a human presses the approve button" to "a human reads a summary before acting on it." In a project management context, that looseness is a problem. PM work involves consequential, often irreversible decisions — scope commits, go-live approvals, escalations, stakeholder communications. Getting the division of labor wrong between AI and human judgment has real project consequences.

This document describes how the human-in-the-loop principle was operationalized in this framework — not as an abstract policy, but as a set of specific structural choices about when AI produces, when the PM reviews, and when a gate must be passed before work continues.

---

## The Core Principle

The AI in this framework is a drafting engine, not a decision engine. Every output the AI produces — every risk item, every stakeholder assignment, every project plan milestone — is a draft until a PM has reviewed it and accepted it, modified it, or rejected it.

This is not a hedge or a disclaimer. It is the architectural premise of the framework. The AI is designed to accelerate the creation of structured project documentation. The PM is designed to supply judgment, authority, and accountability. Neither role substitutes for the other.

---

## The Three-Module Structure and Where Humans Sit

The framework is organized in three sequential modules: intake, delivery, and simulation. Each module has a defined AI role and a defined PM role. Between modules, there are formal human review gates that must be passed before the next module begins.

```
[Project Input Document]
        |
    PM INTAKE MODULE
    (AI produces 3 analysis outputs)
        |
    [HUMAN GATE 1 — PM Reviews Intake Outputs]
        |
    PM DELIVERY MODULE
    (AI produces 4 delivery artifacts)
        |
    [HUMAN GATE 2 — PM Reviews Delivery Artifacts]
        |
    PM SIMULATION MODULE
    (AI tested under controlled disruption)
        |
    [PM Documents Supervision Observations]
```

The gates are not optional checkpoints. They are the mechanism by which the PM validates that what the AI produced in the prior module is accurate, complete, and appropriate before using it as input to the next module. Garbage in, garbage out — if the intake analysis contains fabricated assumptions, those assumptions will propagate into the delivery artifacts unless the PM catches them at Gate 1.

---

## Human Gate 1: Intake Review

After the AI completes the five-layer intake analysis, the PM reviews three documents:

1. **Analysis** — five-layer breakdown of scope, dependencies, constraints, stakeholders, and risk concentration
2. **Open items log** — consolidated list of every unresolved item from the analysis
3. **Stakeholder map** — identified stakeholders with roles, authority, and engagement level

At this gate, the PM is looking for:

**Fabricated specifics.** The AI may have filled gaps in the input with plausible-sounding details. Common examples: inventing a stakeholder name, describing a process that doesn't appear in the input, or assigning an owner to a task where ownership was not stated. These need to be corrected or flagged before moving to delivery.

**Inferred items presented as confirmed.** The AI is designed to label inferences as INFERRED — but this guardrail must be verified, not assumed. The PM should check that every item labeled OPEN is genuinely unresolved, and every risk labeled INFERRED is not being treated as fact elsewhere in the output.

**Missing gaps.** The AI works from what is in the input document. It does not know what it does not know. A PM with domain experience may recognize risks or constraints the document doesn't mention. Gate 1 is the moment to add those before they're absent from the entire delivery phase.

**PM decision:** After review, the PM either accepts the intake outputs as ready for delivery input, returns the AI to revise specific items, or manually edits the documents directly.

---

## Human Gate 2: Delivery Artifact Review

After the AI produces the four delivery artifacts (kickoff agenda, project plan, RAID log, stakeholder matrix), the PM reviews before using any of them externally.

At this gate, the PM is looking for:

**Date fabrication in the project plan.** The AI is instructed to use TBD for unknown dates — but this discipline degrades under ambiguity. The PM should verify that every date in the plan is either derived from a stated project date or explicitly marked TBD/OPEN.

**RAID log quality.** The AI should have carried OPEN items from the intake analysis forward into the RAID log. If OPEN items from intake are absent from the RAID log, they have been silently resolved without authorization. The PM reconciles the two documents.

**Stakeholder matrix gaps.** The AI will attempt to complete a RACI matrix with the stakeholders it knows from the intake analysis. Any role that appears as OPEN in the matrix is a real gap — someone is unassigned to a critical deliverable or decision. The PM decides whether to fill the gap or escalate.

**Kickoff agenda fit.** The agenda should reflect the actual open items from the intake analysis, not a generic kickoff structure. The PM validates that the priority open questions are present in the agenda and that the right owners are flagged to answer them.

**PM decision:** After review, the PM confirms which artifacts are ready to use, which require modification, and whether any issues require resolution before kickoff.

---

## The Simulation Module: Supervised Evaluation

The simulation module does not produce client-facing artifacts. Its purpose is to test the AI under conditions closer to real delivery — including deliberate disruption — and to document what the supervision experience reveals about AI reliability in a PM context.

Human involvement in this module is continuous, not gated. The PM:
- Designs the simulation scenario and the disruption events
- Issues one instruction per phase (not a master prompt)
- Reviews every output before moving to the next phase
- Introduces the change events deliberately, with awareness of what behavior they are designed to test
- Documents observations throughout in a running log
- Writes the Supervision Report at the end

The simulation module produces the most valuable learning output in the framework precisely because the human PM is most actively engaged. The AI is not running on autopilot — it is being supervised, tested, and evaluated by someone who knows what correct project behavior looks like and is looking for deviations.

---

## What PMs Decide That AI Does Not

To be explicit about the division of labor, this is what the PM decides in this framework that the AI does not decide:

| Decision | Who decides | Notes |
|---|---|---|
| Whether intake analysis is accurate | PM | AI produces; PM validates |
| Which open items are blockers vs. watch items | PM | AI surfaces; PM prioritizes |
| Go/no-go at kickoff | PM | AI may draft agenda; PM runs the meeting |
| Scope change acceptance | PM | AI may summarize request; PM approves or rejects |
| Risk acceptance or mitigation strategy | PM | AI logs the risk; PM decides the response |
| Go-live readiness | PM | AI may draft checklist; PM signs off |
| Escalation path and options | PM | AI may draft options; PM decides who to escalate to and what to recommend |
| Whether AI output is ready to use externally | PM | Always — no AI output in this framework goes to a client or stakeholder without PM review |

The AI does not make project decisions. It makes project documentation faster.

---

## OPEN/INFERRED as Governance Mechanism

The most important structural governance tool in this framework is the OPEN/INFERRED labeling discipline. It is not a formatting convention. It is a claim about the state of knowledge.

**OPEN** means: this item is unresolved. No one has confirmed it. It must be resolved before it can drive a project decision.

**INFERRED** means: this item was not stated explicitly in the input. It was derived by the AI from context, pattern, or absence. It may be accurate — but it is not confirmed, and it must not be treated as project fact until someone with authority confirms it.

Without this discipline, AI output in a PM context drifts toward confident-sounding documentation that does not actually represent agreement. A project plan that contains fabricated milestone owners and assumed dates looks like a plan. It is not a plan — it is a hallucinated plan, and if it gets distributed as though it were agreed, it creates real problems downstream.

The OPEN/INFERRED discipline forces the gap to stay visible. The PM cannot ignore an OPEN item because it is still in the record, still in the log, still blocking the next gate. This is the equivalent of requiring a PM to actually resolve their open items rather than hoping they go away.

---

## What This Framework Does Not Do

It does not automate project management. The PM still runs the kickoff, still manages the stakeholders, still makes the calls. The AI reduces documentation time between "PM absorbs new information" and "that information appears in updated project artifacts." It does not replace the PM's judgment, relationships, or accountability.

It does not replace governance processes. If an organization has a formal change control process, this framework does not substitute for it. The AI can draft a change event summary — the PM still runs the change through whatever governance process applies.

It does not make the PM responsible for AI errors they didn't catch. But it does make the PM responsible for reviewing AI output before using it. That is the contract of human-in-the-loop design: the human is in the loop precisely because the AI is not reliable enough to operate without review.

---

## Summary

The human-in-the-loop design in this framework is not aspirational. It is structural. Two formal gates between modules, continuous PM involvement in the simulation, explicit labeling of every unresolved and inferred item, and a clear separation between what the AI produces and what the PM decides. The result is a workflow where AI accelerates the documentation work without replacing the human judgment that makes project documentation meaningful.
