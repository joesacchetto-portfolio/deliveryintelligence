# AI Agent Supervision Report
## VoiceRx Cloud Implementation — Northgate Regional Health System

**Project type:** Simulated SaaS implementation (ambient clinical documentation)
**Simulation period:** February 2026
**Agent used:** OpenClaw (Claude-backed local agent, Docker sandbox)
**Supervisor role:** PM / Workflow Architect
**Report version:** 1.0

---

## 1. Objective

The objective of this simulation was to operate an AI agent as a junior project coordinator across a full healthcare SaaS implementation lifecycle — intake through controlled disruption — and to document where the agent added value, where it required correction, and what that tells you about the practical use of AI in a PM delivery environment.

This was not a technology evaluation. It was a governance experiment. The question was not "what can the AI do?" but "how does it behave when supervised, how does it fail, and what does a PM need to do to keep it reliable?"

The secondary objective was to produce a set of AI-generated project artifacts — risk logs, stakeholder maps, project plans, escalation summaries — that could demonstrate both the capability and the limitations of AI-assisted PM work.

---

## 2. Scenario and Agent Setup

**Scenario:** VoiceRx Cloud implementation for Northgate Regional Health System. Three-campus hospital network, 85 physicians, Epic EMR, 10-week compressed timeline, PM inheriting the project post-signature. Nothing formally scoped at the start.

The agent was given a project charter and a single guiding instruction per phase. No master prompt was used in this simulation — instructions were issued as plain-language messages with embedded constraints. Key guardrails included:

- Do not invent resolved decisions or confirmed facts
- Flag anything unresolved or assumed as OPEN
- Label any inferred risk as INFERRED — not confirmed
- Do not produce output that implies a decision has been made by the sponsor or client unless explicitly stated
- Maintain all prior context when responding to new inputs

The agent had no persistent memory between sessions. Each session required a brief re-orientation to project context before the agent could produce reliable output.

---

## 3. Tasks Assigned Across Phases

| Phase | Tasks assigned to agent |
|-------|------------------------|
| Phase 1 — Intake | Read charter; produce scope summary; generate risk and unknowns log; draft internal alignment agenda; draft discovery call agenda; draft kickoff agenda |
| Phase 2 — Planning | Generate milestone-based project plan; produce stakeholder map with engagement levels; draft communication cadence; document dependency assumptions |
| Phase 3 — Execution Support | Draft status update template; draft UAT plan; draft go-live readiness checklist; draft hypercare stability report template; draft executive status update |
| Phase 4 — Change Event | Receive three simultaneous change events; produce change event summary; update risk log; draft escalation document with options; produce revised project plan reflecting confirmed slip |

---

## 4. Where the Agent Performed Well

**Structured analysis from sparse input.** Given only a project charter, the agent produced a 15-item risk log that separated explicit charter risks from inferred risks, labeled each category clearly, and surfaced open unknowns that a PM would need to resolve before kickoff. The output was usable as a working document on day one.

**Consistent OPEN/INFERRED discipline.** When given clear guardrails, the agent maintained the distinction between confirmed facts and inferred risks throughout all four phases. It did not resolve OPEN items on its own. When it was told "Epic integration has slipped 3 weeks," it updated the plan to reflect the confirmed slip and explicitly left the go-live decision as OPEN rather than auto-resolving it.

**Template quality.** Status update template, UAT plan, go-live checklist, and hypercare report template were all produced at a quality level that a PM could use with minor edits. The structure was logical, the fields were correct, and the placeholder language was appropriate.

**Change event adaptation.** When three change events were introduced simultaneously, the agent produced a coherent multi-event summary, updated the risk log, drafted an escalation document with three explicitly labeled options, and produced a revised project plan reflecting only the confirmed change (the integration slip) while leaving the unconfirmed items as OPEN. This was the highest-quality output of the simulation.

---

## 5. Failure Patterns Observed

**Gap-filling without flagging.** In early phases before guardrails were tightened, the agent would fill scope gaps with plausible-sounding assumptions presented as confirmed. In one instance it described a UAT sign-off process in detail — naming a responsible party and a process flow — that did not appear anywhere in the charter. When challenged, it acknowledged the gap and reissued the output with proper OPEN flags. The guardrail "do not invent resolved decisions" had to be stated explicitly to stop this pattern.

**Soft confirmation language.** The agent occasionally used phrasing like "the CMO will likely want to see weekly updates" or "the standard approach for Epic integrations typically includes..." — language that sounds authoritative but is inference, not project fact. This is a subtle failure mode because the output passes a quick read but embeds assumptions that can harden over time into the project record.

**Context degradation across session length.** In longer sessions, the agent's output began to drift toward generic healthcare implementation content rather than Northgate-specific content. By the third or fourth task in a single session, outputs occasionally dropped Northgate-specific constraints (3-campus complexity, the CMO's high visibility expectations, the ED scheduling challenge) in favor of boilerplate. Re-stating "this is specific to Northgate" in the instruction helped but did not fully eliminate it.

**Stakeholder fabrication tendency.** When asked to produce a stakeholder map with named contacts, the agent had a tendency to complete the OPEN fields with plausible names if not explicitly told to leave them blank. This was corrected by adding "use OPEN for any role or name not confirmed in the input" to the instruction — but it required explicit instruction, not just the spirit of the guardrail.

---

## 6. Drift Examples

**Example 1: Fabricated sign-off process**
*Instruction:* Draft UAT plan for the Northgate implementation.
*Agent behavior:* Produced a UAT plan that included "UAT sign-off to be confirmed by Kerry Shaw (Project Manager)" — a name that appeared in a different example project, not in the Northgate charter. The agent cross-contaminated context from a different session.
*Correction:* Cleared session context; re-stated that all stakeholder names not confirmed in the Northgate charter should be OPEN. Reissued instruction. Output was clean.

**Example 2: Assumed go-live decision**
*Instruction:* Update the project plan to reflect the Epic integration slip.
*Agent behavior (first attempt):* Produced a revised plan with go-live moved to 2026-05-15 as if a decision had been made.
*Correction:* Instructed the agent: "The go-live date decision has NOT been made. Reflect the integration slip in the plan but mark the go-live as AT RISK and OPEN. Present the options — do not pick one."
*Result:* Revised plan correctly reflected AT RISK status with OPEN decision flag. The escalation document produced alongside it also presented three options without recommending one, which is the correct behavior.

**Example 3: Generic risk vs project-specific risk**
*Instruction:* Produce a risk log for this project.
*Agent behavior (no guardrail):* Produced a risk log that included standard implementation risks (change management, training readiness, timeline) but framed them generically — not anchored to the specific context of Northgate (first-time AI documentation tool, CMO visibility, 3-campus coordination, ED variable schedules).
*Correction:* Re-stated the specific project context in the instruction. Output was substantially stronger — risks were labeled with Northgate-specific drivers rather than generic categories.

---

## 7. Corrections Applied

| Issue observed | Correction applied | Outcome |
|---|---|---|
| Agent inventing resolved decisions | Added explicit guardrail: "Do not invent resolved decisions or confirmed facts" | Reliable compliance when stated explicitly |
| Soft confirmation language | Added: "If something is inferred, label it INFERRED — not confirmed" | Improved; some residual soft language remained in longer sessions |
| Context degradation | Re-stated project-specific context at top of instruction in each new session | Effective; session restart with context summary is necessary |
| Stakeholder fabrication | Added: "Use OPEN for any role or name not confirmed in the input document" | Reliable compliance when stated explicitly |
| Cross-session contamination | Cleared session context before each new phase | Prevented recurrence |
| Generic rather than specific output | Included key project constraints in every instruction | Substantially improved specificity |

---

## 8. Lessons Learned

**The guardrails are the governance model.** The quality of AI output in a PM context is almost entirely determined by how well the PM defines what the AI is and is not permitted to do. The agent did not apply OPEN/INFERRED discipline on its own — it applied it when explicitly instructed to. This is not a flaw; it is the expected behavior. The PM's job is to design the instructions, not to hope the AI defaults to PM-appropriate behavior.

**Supervision is not optional.** Every output required review before use. In most cases the output was directionally correct. In a meaningful minority of cases it contained fabricated specifics, assumed decisions, or cross-session contamination that would have created real problems if accepted without review. Passive acceptance of AI output is a governance failure.

**The AI does not know what it does not know.** The agent would produce complete, confident-looking output in areas where the input was silent. This is the most dangerous failure mode in a PM context — not obvious hallucination, but plausible-sounding gap-filling. The OPEN discipline guardrail is specifically designed to counter this, but it must be stated, not assumed.

**Session length matters.** Context quality degrades in longer sessions. For a production PM workflow, each phase should be a fresh session with a clear context summary at the top. Trying to run multiple phases in a single session without re-establishing context produces lower-quality, less specific output.

**The change event was the most informative test.** Introducing three simultaneous disruptions — and watching the agent handle them — revealed more about its reliability characteristics than any structured phase. The agent correctly compartmentalized confirmed vs. unconfirmed changes, maintained OPEN discipline under pressure, and produced a structured options analysis rather than a false resolution. This is the behavior you want. It only happened because the guardrails were in place.

**AI is a documentation accelerant, not a decision engine.** Every meaningful decision in this simulation — go-live strategy, scope change acceptance, champion replacement, risk acceptance — required human judgment. The AI surfaced the decision clearly, structured the options, and preserved the ambiguity. The PM made the call. That is the right division of labor.

---

## 9. PM Application Insights

**This maps directly to managing a junior coordinator.** The supervision skills used here — defining scope, setting guardrails, reviewing output for accuracy, correcting errors, re-briefing after context drift — are the same skills used to manage a junior PM or coordinator. The primary difference is that the AI requires more explicit instruction and has no persistent memory between sessions.

**Prompt design is a PM competency.** The ability to write a clear, constrained, unambiguous instruction that produces reliable AI output is a skill. It overlaps with scope definition, requirements writing, and acceptance criteria design — all existing PM competencies. PMs who already write tight scope statements adapt quickly to prompt design.

**Governance frameworks work.** The OPEN/INFERRED labeling discipline, the explicit no-fabrication guardrail, and the structured output formats produced significantly more reliable output than unguarded instructions. The discipline that makes PM documentation useful — tracking what is confirmed vs. assumed, separating facts from inferences — translates directly into AI guardrail design.

**AI reduces documentation lag.** In a real delivery context, the time between "PM absorbs new information" and "that information appears in updated project artifacts" is often measured in days. With AI assistance and proper guardrails, that lag can be reduced to minutes. The value is not in removing the PM — it is in freeing the PM from the transcription work so more time is available for judgment.

**The failure modes are predictable and manageable.** Gap-filling, soft confirmation language, context degradation, and cross-session contamination are consistent patterns. They do not require the PM to be an AI expert to manage them. They require the PM to review outputs carefully, maintain clear instructions, and restart sessions cleanly. These are manageable with process discipline.

---

## Appendix: Simulation Outputs

The following artifacts were produced during this simulation and are archived in the `outputs/` and `templates/` directories of this example:

- `scope_summary.md` — Phase 1 intake output
- `risk_log.md` — 15-item risk log (explicit + inferred)
- `stakeholder_map.md` — Named stakeholders with engagement levels and OPEN gaps
- `project_plan.md` — Milestone-level delivery plan (Phase 0–6)
- `change_event_summary.md` — Three-event change summary with impact assessment
- `updated_risk_log.md` — Risk log after change events (5 new/elevated risks)
- `escalation_draft.md` — Escalation document with three structured options
- `revised_project_plan.md` — Revised plan reflecting confirmed integration slip
- `status_update_template.md` — Weekly status update template
- `uat_plan_template.md` — UAT plan template
- `go_live_checklist.md` — Go-live readiness checklist
- `hypercare_report_template.md` — 30-day hypercare stability report template
