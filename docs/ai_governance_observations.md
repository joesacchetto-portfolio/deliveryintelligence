# AI Governance Observations
## Behavioral Patterns Observed During Framework Operation

**Author:** Project Manager / Framework Architect
**Version:** 1.0
**Date:** 2026

---

## About This Document

This document records specific behavioral observations from operating an AI agent (OpenClaw, Claude-backed) across the three modules of the framework — intake, delivery, and simulation. It is not a summary of AI capabilities. It is a governance record: what the AI actually did, where it deviated from expected behavior, how those deviations were corrected, and what the pattern of failures reveals about running AI in a PM context.

These observations are the empirical basis for the framework's design decisions. Where a guardrail exists, it exists because a specific failure pattern was observed. Where a gate exists, it exists because a specific risk of downstream error was demonstrated.

---

## Observation Category 1: Gap-Filling Without Disclosure

**What was observed:**
When the input document was silent on a topic — a stakeholder name, a process step, an approval owner — the AI would produce output that filled the gap with plausible content, presented as though it were derived from the input.

**Example:**
Input: A SOW that named an executive sponsor but did not specify who would sign off on go-live readiness.
AI output: A RAID log that listed "CMO (executive sponsor)" as the go-live sign-off owner.
The CMO was named in the input. The sign-off role was not. The AI connected the two without flagging it as an inference.

**Why this matters:**
In a real project, this kind of gap-filling creates false confidence. The RAID log looks complete. The project plan has owners for everything. The PM may not notice that some of those owners were assigned by inference, not by agreement. When the gap surfaces in execution — when the actual sign-off owner turns out to be the IT Director, not the CMO — it creates friction that the documentation should have prevented.

**Governance response:**
Added explicit guardrail: "Do not invent resolved decisions, confirmed facts, or agreed details not present in the input." Added to every instruction, not assumed as a default. Verified at Gate 1 and Gate 2 that OPEN fields were genuinely OPEN in the output.

---

## Observation Category 2: Soft Confirmation Language

**What was observed:**
Even after the no-fabrication guardrail was in place, the AI produced output using hedged but authoritative-sounding language: "The CMO will likely want weekly executive updates," "The standard Epic integration process typically requires 4–6 weeks," "Change management is generally the highest risk in physician-facing deployments."

**Why this matters:**
This language pattern is harder to catch than outright fabrication because it sounds reasonable. In isolation, each statement might be accurate for a comparable project. But in a project record, "typically" and "likely" can harden over time. If a status update references "the agreed weekly executive cadence," it may have originated from an AI inference about what the CMO "will likely want" — never confirmed, never disputed, now part of the record.

**Specific instance:**
During Phase 3 of the simulation, a status update template included a line referencing "weekly CMO briefings as agreed at kickoff." The CMO briefing cadence had not been agreed — it had been described in an earlier output as "likely expected given the CMO's visibility expectations." Two phases later, that inference had become stated fact in the template.

**Governance response:**
Added guardrail: "If something is inferred from context rather than stated explicitly — label it INFERRED. Do not present inferences as confirmed." Added to review checklist at Gate 2: specifically check status update and communication templates for language that assumes agreement where none was recorded.

---

## Observation Category 3: Context Degradation Across Session Length

**What was observed:**
In longer sessions — more than three or four sequential tasks without a context reset — the AI's output began to drift from project-specific content toward generic implementation content. References to project-specific constraints (three-campus coordination, ED scheduling complexity, CMO visibility expectations) were dropped in favor of standard healthcare SaaS implementation language.

**Example:**
Phase 2 planning output correctly referenced the three-campus phasing challenge multiple times. By the fourth task in the same session — a communication cadence document — the output described a "standard implementation communication approach" with no reference to the specific organizational complexity of the project.

**Why this matters:**
Generic project documentation looks like project documentation. A PM reviewing the communication cadence document might not notice that the ED scheduling challenge — a known constraint that should be driving special coordination decisions — was absent. It would only surface later when scheduling the ED training sessions.

**Governance response:**
Session management protocol: each phase runs as a separate session. Project-specific context (client name, product name, key constraints, campus structure, known risks) is restated at the top of every instruction even within the same session. This is documented in the simulation prompt as required practice.

---

## Observation Category 4: Stakeholder Fabrication

**What was observed:**
When asked to produce a stakeholder map or RACI matrix, the AI had a consistent tendency to complete rows rather than leave them blank. If a role existed in the matrix but no name was available from the input, the AI would produce a plausible name — sometimes a name from a different project context read earlier in the session, sometimes a generic-sounding name.

**Specific instance:**
A UAT plan template produced during simulation included "UAT sign-off: Kerry Shaw (Project Manager)" in the sign-off tracking table. Kerry Shaw was not a character in the simulation scenario. The name appeared to have crossed over from a different context processed earlier in the same session.

**Why this matters:**
Cross-session contamination — where content from one project context bleeds into output for another — is a specific risk when running multiple projects through the same AI session. If a PM is using AI to support multiple concurrent projects, the outputs from one project could contain names, dates, or decisions from another. This is a data integrity issue, not just a quality issue.

**Governance response:**
Added guardrail: "Use OPEN for any name or role not confirmed in the input document." Added session isolation protocol: clear all context before beginning a new project. Added to Gate 2 review: verify all names in stakeholder matrices and RACI tables against the confirmed stakeholder list from intake.

---

## Observation Category 5: Auto-Resolution of OPEN Items

**What was observed:**
When the AI was asked to produce an updated artifact (updated project plan, revised risk log) after receiving new information, it had a tendency to resolve OPEN items that the new information did not actually address.

**Example:**
After receiving notification that the Epic integration had slipped three weeks, the AI produced a revised project plan that:
- Correctly reflected the integration timeline slip (confirmed change — correct behavior)
- Also resolved the go-live date, setting it to a specific new date (not confirmed — incorrect behavior)
- Also moved the training schedule forward without noting it as OPEN (not confirmed — incorrect behavior)

The AI received one confirmed change and resolved three OPEN items that were downstream consequences of the change — but the downstream decisions had not been made.

**Why this matters:**
This is a particularly dangerous failure mode because the revised plan looks complete and internally consistent. A PM who receives this plan and doesn't cross-reference it against the original OPEN items log would not notice that three decisions were made by the AI that belong to the PM and client.

**Governance response:**
Added explicit instruction for change event tasks: "Reflect confirmed changes only. Mark any item that requires a decision as AT RISK / OPEN. Do not resolve downstream items unless I confirm them explicitly." Added to Gate 2 review: compare revised plan OPEN items against prior OPEN items log — every closure requires a corresponding decision record.

---

## Observation Category 6: Reliable Behaviors (Positive Pattern)

Not all observations were failures. These behaviors were consistent and valuable when guardrails were in place:

**Structured analysis from sparse input.** Given only a project charter, the AI reliably produced a multi-layer risk analysis that separated explicit charter risks from inferred risks. The analysis was usable as a day-one working document with minor review and correction.

**Option presentation without recommendation.** When given explicit instruction not to recommend a decision but to present options, the AI consistently complied. Escalation documents in the simulation listed options without advocating for one. This is the correct behavior for AI in a PM governance context.

**Consistent OPEN tagging (when instructed).** When the guardrail was explicitly stated, the AI maintained OPEN/INFERRED discipline reliably across long outputs. The discipline did not hold in the absence of explicit instruction — but when stated, it held.

**Rapid artifact production.** Template-quality status updates, UAT plans, go-live checklists, and hypercare reports were produced very quickly — substantially faster than drafting each from scratch. The AI-produced versions required editing but not rebuilding.

---

## Summary of Failure Patterns and Mitigations

| Failure pattern | Description | Mitigation |
|---|---|---|
| Gap-filling without disclosure | AI completes fields in output using inferred content presented as confirmed | Explicit no-fabrication guardrail; Gate review for OPEN integrity |
| Soft confirmation language | AI uses hedged-but-authoritative phrasing that implies agreement not in the record | INFERRED labeling guardrail; review templates for assumed agreement |
| Context degradation | Project-specific constraints drop from output in longer sessions | Session restart between phases; restate project context in every instruction |
| Stakeholder fabrication | AI completes name/role fields with plausible or cross-contaminated content | OPEN-for-unknown guardrail; session isolation; RACI name verification |
| Auto-resolution of OPEN items | AI resolves downstream OPEN items when receiving confirmation of a single change | Explicit "confirmed changes only" instruction; revised plan vs. prior OPEN items reconciliation |

---

## Implications for Framework Design

Every structural choice in the framework — the OPEN/INFERRED discipline, the two-gate review process, the session management protocol, the explicit guardrails in every prompt — exists because one of these failure patterns was observed and needed to be countered.

The framework is not AI-skeptical. It is AI-realistic. The AI in this framework is valuable precisely because its failure modes are consistent and predictable. A PM who knows that gap-filling, soft confirmation language, context drift, and OPEN item auto-resolution are the expected failure patterns can design review processes that catch them. That is a manageable governance problem. The unmanageable version is an AI whose failures are random and unpredictable.

These observations suggest that the primary PM competency for AI-assisted delivery work is not technical — it is the same competency that makes a PM effective at scope management: the ability to distinguish between what is confirmed and what is assumed, and to maintain that distinction under time pressure.
