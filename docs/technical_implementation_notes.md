# Technical Implementation Notes

**AI-Assisted Project Delivery Framework**

---

## What This Document Is

This document is the technical companion to the portfolio README and framework overview. Those documents focus on business value, governance philosophy, PM workflow design, and AI-enabled delivery capability. This document goes deeper: it describes how the framework was architected, how information flows through it, what design decisions were made and why, how it was evaluated, and what failure modes were observed and corrected.

The intended reader is someone who wants to understand the technical and methodological substance behind the portfolio — an AI implementation leader, solutions consultant, technical implementation manager, or AI adoption specialist evaluating whether the framework reflects genuine design thinking or surface-level experimentation.

This portfolio demonstrates AI-assisted project delivery workflows — not AI engineering, model development, or software architecture. The technical depth described below is the depth of workflow design, governance control design, and evaluation methodology — not software engineering. The work product is the governance architecture, the five-layer analysis framework, the human review process, and the documented observations about AI behavior under PM supervision.

---

## Workflow Architecture

### Three-Module Design

The framework is organized as three sequentially connected modules: PM Intake (analysis), PM Delivery (artifact generation), and PM Simulation (lifecycle evaluation). Each module was designed as a discrete unit with defined inputs, defined outputs, and a PM review gate before the next module begins.

This separation was a deliberate architectural decision, not an organizational convenience. A single monolithic prompt that accepted a project document and produced a complete delivery package would be faster to build but harder to govern. Separating the workflow into modules creates natural inspection points: the PM can review the intake analysis before any delivery planning begins, catch fabricated assumptions at the source, and decide which priority questions must be answered before the next stage runs. A monolithic workflow skips those gates.

The three-module structure also reflects a real delivery workflow. Analysis and planning are different activities. Treating them as one continuous operation — with no PM review between them — reproduces the error that causes delivery problems in practice: plans built on unvalidated analysis.

### Module Boundaries

**Module 1 — Intake** accepts a project input document (any format: SOW, charter, brief, partial or informal) and applies the five-layer analysis framework. Its job is interrogation, not generation. It identifies what is present, what is absent, and where ambiguity is concentrated. It does not begin delivery planning.

**Module 2 — Delivery** accepts the three intake output files plus the original project document as structured inputs and generates four delivery planning artifacts. It cannot run without Module 1 outputs. This dependency is structural, not just instructional — the prompt explicitly requires all intake files to be present and read before any output is produced.

**Module 3 — Simulation** runs as a parallel evaluation layer. It does not receive outputs from Module 1 or 2. Instead, it accepts a project charter directly and runs an independent four-phase lifecycle simulation, with the PM issuing instructions at each phase and documenting observations in a running log. Its purpose is evaluation and learning, not artifact production.

### Why Artifact-Based Handoffs

Information passes between modules as files, not as conversational context. Module 1 writes three files to an output directory. Those same files are placed in Module 2's input directory. The agent running Module 2 reads all files before producing any output.

The alternative — a single long conversational session in which intake analysis and delivery planning are produced sequentially — was rejected for three reasons:

**Traceability.** When information moves through a file, the PM can inspect exactly what the agent had access to at each stage. There is no ambiguity about whether the delivery artifacts reflect the actual intake analysis or a degraded version of it carried through session memory.

**Repeatability.** File-based handoffs allow any module to be re-run with the same inputs and produce consistent output. If the intake analysis is revised, Module 2 can be re-run against the updated files without re-running the entire workflow.

**Auditability.** The file-based evidence trail means the PM can reconstruct, after the fact, what the agent knew at each stage, what it produced, and what corrections were applied. This is a governance requirement in a real project context — the ability to explain why a risk was flagged, why a decision was deferred, and what information was available when an artifact was produced.

---

## Artifact-Based Context Management

### The Core Problem

AI language model agents do not have persistent memory between sessions. Each session begins with no knowledge of prior work unless that knowledge is explicitly provided as context. For project work — which spans days, weeks, and phases — this means every new instruction must carry the relevant project context, or the agent operates without it and produces generic output.

In practice, there are two responses to this constraint. The first is to use very long sessions and hope context survives across many turns. The second is to accept the constraint, formalize it, and manage context explicitly through structured files. This framework chose the second approach.

### How It Works

Every significant output is written as a file. The file becomes the context carrier for the next stage. When Module 2 begins, the agent does not rely on remembering Module 1's analysis — it reads it. When a change event is introduced in the simulation, the agent does not rely on remembering the project plan — it is provided as a file.

This approach has a secondary benefit: it makes gaps visible. A project context that exists only in session memory can degrade silently — the agent forgets a constraint, drops a stakeholder, or loses a nuance without the PM noticing. A project context that exists in files can be reviewed. The PM can open the stakeholder map before issuing the next instruction and confirm that it still reflects the correct project state.

### OPEN Items as Managed State

The OPEN items log is the most direct expression of artifact-based context management. Every unresolved item identified in Module 1 is written to a structured tracking file. That file is passed to Module 2. Module 2 is explicitly instructed to carry OPEN items forward into delivery artifacts — not to resolve them, not to assume answers, but to preserve the uncertainty in the project record until the PM resolves it.

This is the PM equivalent of a risk register: a structured, persistent record of what is known, what is unknown, and what must be decided. The agent maintains the record. The PM works the record.

---

## Prompt Chaining Strategy

### Structured Inputs, Not Freeform Conversation

The prompts in this framework do not ask the agent to "help with a project." They specify inputs, processing instructions, guardrails, and output format requirements in precise terms. Each prompt defines what files to read, what analytical framework to apply, what to flag as OPEN vs. INFERRED, and what files to produce.

This specificity serves a governance function. An underspecified prompt produces underspecified output — output that fills gaps with plausible content, assumes decisions that haven't been made, and defaults to generic structure rather than project-specific analysis. A precisely specified prompt constrains the output to what the input actually supports.

### How Information Flows

The chaining pattern works as follows:

1. Project input document → Module 1 intake prompt → three analysis files (analysis, open items log, stakeholder map)
2. Analysis files + project input document → Module 2 delivery prompt → four delivery artifacts (kickoff agenda, project plan, RAID log, RACI matrix)
3. Project charter → Simulation prompt (one instruction per phase) → phase outputs + PM observation log → AI Agent Supervision Report

At each step, the downstream prompt is designed to consume the upstream outputs as structured inputs. Module 2 is explicitly instructed to: list all files in the input directory, read every file before producing any output, identify which file is the original project document and which are intake outputs, and proceed only after reading all inputs.

### Preserving Ambiguity Deliberately

A standard information pipeline tries to resolve ambiguity as information moves through it — normalizing, inferring, filling gaps. This framework inverts that design. Ambiguity is preserved, not resolved.

OPEN items identified in Module 1 appear in the open items log. They are passed to Module 2. Module 2 references them in the kickoff agenda (as items requiring resolution), carries them into the project plan (as task-level notes), and reflects them in the RAID log (as active risks or assumptions). They are not closed until the PM explicitly resolves them.

This design choice reflects a real project governance principle: an unresolved question that is visible in the project record is manageable. An unresolved question that has been silently assumed away — by an agent, a template, or a junior team member — is a delivery risk that surfaces six weeks later.

---

## Governance Controls

### OPEN Discipline

The OPEN flag is the primary governance mechanism of the framework. Any information not explicitly confirmed in the source document is flagged OPEN rather than filled in. This applies to stakeholder names, scope boundaries, approval requirements, timeline commitments, budget constraints, and every other project parameter that matters.

The practical effect: an intake analysis produced against a vague or incomplete SOW will contain many OPEN items. That is the correct output. An analysis that produces few OPEN items against a vague SOW has fabricated answers — and those fabricated answers will appear in every downstream artifact unless caught at Gate 1.

### INFERRED Labeling

Risk analysis requires inference. A PM reading a SOW cannot identify only the risks explicitly listed — they must also reason about what is absent, what is ambiguous, and what could go wrong given what the document does and does not say. The framework performs this inference and outputs it as risk analysis. All inferred items are explicitly labeled INFERRED to distinguish them from risks stated in the source document.

This label is a chain-of-custody marker. When a RAID log entry says "INFERRED: integration complexity may exceed stated timeline assumptions given the absence of a confirmed Epic sandbox environment," the reader knows this was an analytical inference, not a confirmed risk. The PM can accept it, reject it, or escalate it for confirmation — but they know its status. Without the label, the inference hardens into fact as it moves through the project record.

### Fabrication Prevention

The guardrail against fabrication — stated in every instruction to the agent — is: "Do not invent resolved decisions, confirmed facts, or agreed details not present in the input." This single constraint addresses the most dangerous failure mode in AI-assisted PM work: the production of confident-sounding, internally consistent output that does not reflect the actual state of the project.

Fabricated output is hard to detect on a quick read because it passes plausibility checks. A stakeholder matrix that assigns all RACI roles looks complete. A project plan with no TBD dates looks ready to use. The fabrication prevention guardrail, combined with OPEN flagging, ensures that apparent completeness is replaced with visible incompleteness — which is more useful in a PM context.

### Human Review Gates

Two formal review gates sit between modules. Gate 1 is the PM review of intake outputs before delivery planning begins. Gate 2 is the PM review of delivery artifacts before they are used externally.

These gates are structural, not advisory. Nothing from Module 1 is used as Module 2 input until the PM has validated it. Nothing from Module 2 is distributed to stakeholders until the PM has reviewed it. The gates are enforced by workflow design — the PM must move the files and issue the instruction — not by policy statements that can be bypassed under time pressure.

### Output Format Constraints

All outputs are produced in defined formats specified in the prompt. Analysis follows the five-layer structure. Open items use a table format with status, owner, and notes columns. Delivery artifacts follow templates defined in the prompt. The RACI matrix has defined columns and role labels.

Structured output formats serve governance. A free-form analysis is difficult to audit. A structured analysis with defined sections, consistent labeling, and explicit OPEN items is reviewable and comparable across different projects or runs. The PM knows exactly where to look for risks, exactly where to find the priority questions, and exactly what format to expect in the RAID log.

---

## Evaluation Methodology

### Three-Stage Approach

The framework was evaluated at three levels of increasing complexity: individual module testing, pipeline testing (intake → delivery), and full lifecycle simulation.

Individual module testing validated that each module produced correct output for a given input — that OPEN items were flagged accurately, that inferred risks were labeled, that delivery artifacts reflected the intake analysis rather than generic templates. Pipeline testing validated that information moved correctly between modules — that OPEN items in Module 1 appeared in Module 2 outputs, that inferred risks carried forward into the RAID log, and that the kickoff agenda reflected the actual priority questions rather than a generic kickoff structure.

The full lifecycle simulation, described below, exercised the framework under conditions much closer to real delivery.

### Multiple Scenario Testing

The intake engine was exercised against multiple scenario types to assess whether the five-layer framework held across different input characteristics. Two are included in this public repository:

- A healthcare clinical quality reporting SOW: complex regulatory timeline dependencies, multi-phase scope, incomplete stakeholder section, external submission dependencies
- A healthcare ambient clinical documentation SOW: evaluation period constraints, integration dependencies, physician adoption risk embedded in contractual language

An additional retail Customer Data Platform SOW (well-structured scope, lower regulatory complexity, shorter timeline) was exercised during development but is not included in this public repository.

These scenarios were selected to stress-test specific layers of the framework. The clinical quality reporting scenario specifically targeted Layer 3 (constraint identification) and Layer 5 (risk concentration) — testing whether the engine could surface regulatory deadline risk and dependency conflicts distributed across different sections of the document.

### Controlled Simulation

The VoiceRx/Northgate simulation provided a full lifecycle test environment: a mid-size hospital network, 85 physicians, Epic EMR integration, 10-week compressed timeline, contract signed with nothing formally scoped. The PM inherited the project post-signature. Every project artifact had to be built from a charter.

The simulation ran four phases: intake and alignment, planning, execution support, and controlled disruption. Each phase was a separate agent session with explicit context re-establishment at the start. Outputs from each phase were reviewed before the next phase began. Observations were recorded in a running log throughout.

The four-phase structure mirrored a real implementation lifecycle deliberately. The goal was not to produce the fastest outputs — it was to observe how the agent behaved across a realistic sequence of tasks, with increasing context complexity and increasing dependency on prior outputs.

### Change Event Injection

Phase 4 introduced three simultaneous change events:
- A confirmed change: Epic integration timeline slipped three weeks (structural impact, requires plan revision)
- An unconfirmed change: Primary physician champion went on unexpected medical leave (stakeholder risk, status unknown)
- A scope request: CMO verbally requested adding a fourth campus and ED department (unapproved, not a confirmed change)

This combination was designed to test three specific governance behaviors simultaneously:
1. **Confirmed vs. unconfirmed separation** — Would the agent correctly distinguish a confirmed change from an unconfirmed event and a pending request, and handle each differently in its output?
2. **OPEN discipline under pressure** — When receiving a confirmed change that had downstream implications (integration slip → go-live risk), would the agent auto-resolve the downstream decisions, or hold them as OPEN pending PM direction?
3. **Scope change handling** — Would the agent incorporate the verbal scope request as if it were approved, or hold it as a request pending a formal change order?

First-run outputs failed on item 2: the agent resolved the go-live date as a confirmed new date rather than marking it AT RISK / OPEN. This failure was caught in review, corrected with an explicit instruction, and produced the expected behavior on the revised run. The correction and outcome were documented.

### Observation and Correction Cycles

Each simulation phase followed a structured observation pattern: issue instruction, review output against expected behavior, document what was correct and what deviated, apply correction if needed, document the correction and outcome. This pattern was applied consistently across all four phases.

The observation log was the primary evidence trail for the AI Agent Supervision Report. It captured not only what the agent produced, but whether it was correct, what was wrong when it was not, and what instruction change produced the correct behavior. This produced a documented correction record rather than a general impression of AI capability.

---

## Failure Modes Observed

Six specific failure patterns were identified through testing and simulation. Each is described with its mechanism and the correction applied.

### Assumption Insertion

The agent would fill gaps in the input document with plausible-sounding details, presented as confirmed. In one instance, a RAID log assigned a go-live sign-off owner to a named executive whose role appeared in the input but whose sign-off responsibility did not. The assignment was inferred from role, not stated in the document, and was presented without an OPEN flag.

Correction: Explicit no-fabrication guardrail added to every instruction. Verified at Gate 1 review that all OPEN fields in output were genuinely unresolved.

### Soft Confirmation Language

Even with the no-fabrication guardrail in place, the agent produced output using hedged-but-authoritative language: "the CMO will likely want weekly executive updates," "standard Epic integrations typically require 4–6 weeks." This language sounds reasonable in isolation but introduces inference into the project record without labeling it.

This is a subtler failure mode than outright fabrication because it passes a quick read. A status update template referencing "the agreed weekly CMO briefing cadence" — when that cadence was never agreed — could survive several review cycles before the assumption hardened into project fact.

Correction: INFERRED labeling guardrail added. Communication and status templates specifically reviewed for assumed-agreement language at Gate 2.

### Context Degradation

In sessions exceeding three or four sequential tasks, the agent's output began to reference generic implementation content rather than project-specific content. Northgate-specific constraints — three-campus coordination complexity, CMO visibility expectations, ED scheduling challenges — were dropped in favor of standard healthcare SaaS implementation language.

The mechanism: as the session grew longer, project-specific context became a smaller proportion of the active context window relative to the accumulating output. Generic training patterns filled the space vacated by project specifics.

Correction: Session management protocol established. Each phase runs as a separate session. Project-specific context (client, product, key constraints, known risks) is re-stated at the top of every instruction regardless of session history.

### Stakeholder Fabrication

When asked to produce a stakeholder map or RACI matrix, the agent had a consistent tendency to complete rows rather than leave them blank. In the most specific documented instance, a UAT plan produced during simulation included a named sign-off owner — Kerry Shaw — whose name appeared in a different example project processed in the same session. The agent cross-contaminated context from a different project.

Correction: "Use OPEN for any name or role not confirmed in the input document" added as an explicit guardrail. Session isolation protocol established: no two projects run in the same session.

### Auto-Resolution of OPEN Items

When asked to revise an artifact in response to new information, the agent had a tendency to resolve OPEN items that the new information did not address. After receiving confirmation that the Epic integration had slipped three weeks, the agent produced a revised project plan that also moved the go-live date to a specific new date and rescheduled training — downstream implications of the confirmed slip that had not been approved.

The revised plan was internally consistent and looked complete. The problem was that three decisions had been made by the agent that belonged to the PM and client.

Correction: Explicit instruction for change event tasks: "Reflect confirmed changes only. Mark any item that requires a decision as AT RISK / OPEN. Do not resolve downstream items unless I confirm them explicitly."

### Drift to Generic Output

Across longer simulations, the agent's output drifted toward generic implementation content even when project-specific context had been re-stated. Risk logs began to list standard healthcare SaaS risks rather than Northgate-specific risks. Communication templates lost the specific constraints that made them relevant to the project.

The difference between a generic risk log and a project-specific one is often invisible to a reader who hasn't read the charter. This is what makes context drift dangerous — the output passes a plausibility check while losing the specificity that makes it useful.

Correction: Key project constraints added to every instruction as a reference block. Instructions structured as: [project context re-statement] + [guardrails] + [task].

---

## Human-in-the-Loop Architecture

### Division of Labor

The framework's core architectural principle is a clean division between what the AI produces and what the PM decides. This division is enforced by structure, not just by policy.

**The AI produces:**
- Structured analysis of project inputs
- Draft delivery artifacts based on that analysis
- Risk and assumption logs derived from document review
- Template documents for delivery activities
- Change event summaries and option analyses

**The PM decides:**
- Whether intake analysis is accurate
- Which OPEN items are blockers and which are watch items
- Which inferred risks to accept, reject, or escalate for confirmation
- Whether delivery artifacts are ready to use
- All scope decisions, at intake and throughout delivery
- All risk acceptance and mitigation strategy decisions
- All stakeholder accountability assignments
- Whether the project is ready to proceed at any milestone
- All responses to change events

No output from the AI is used without PM review. No decision is delegated to the AI.

### PM as Supervisor

In the simulation module specifically, the PM role is defined as supervisor. This means: issuing instructions (not just approving AI-generated instructions), reviewing every output before it advances, detecting drift and fabrication, applying corrections, and documenting what was corrected and why.

Supervision in this framework looks like managing any capable but imperfect resource: define the scope clearly, review the output carefully, correct what is wrong, document what you corrected. The primary difference from managing a human resource is that the AI requires more explicit instruction — it does not carry project context implicitly, and it does not apply governance discipline unless told to.

### PM as Validator

The two formal review gates are the PM's primary mechanism for maintaining authority over the project record. Gate 1 is not a rubber stamp — it requires the PM to verify that OPEN items are correctly identified, that no fabricated assumptions have been presented as confirmed facts, and that the priority questions are correctly prioritized. Gate 2 requires the PM to confirm that all four delivery artifacts are accurate, that OPEN items from intake have been carried forward, and that the plan reflects the actual project rather than a plausible generic one.

Both gates take time. The time savings from AI-accelerated documentation drafting are only realized if the review is fast — and the review is fast only if the PM knows exactly what failure modes to look for. The six failure modes described above are the Gate 1 and Gate 2 review checklist.

### PM as Escalation Point

All decisions that carry delivery risk belong to the PM. The AI is explicitly instructed not to recommend a course of action on escalation items — to present options, not advocate for one. This instruction held consistently once the guardrail was established. The escalation document produced in Phase 4 of the simulation listed three options with their respective risk implications and left the decision explicitly OPEN.

This is the correct behavior. The PM who escalates to their stakeholders with a structured options analysis has done their job. The PM who escalates with the AI's recommendation has delegated a judgment that belongs to them.

---

## Operating Environment

The framework ran locally on Windows 10 using OpenClaw, a Claude-backed AI agent containerized in Docker Desktop. All instructions were issued via PowerShell command line. All inputs and outputs are plain Markdown (`.md`) or CSV files stored in a local directory structure.

The local, file-based environment was a deliberate choice. It produced a visible, inspectable evidence trail: every input file, every output file, every prompt, and every correction is present in the file system and attributable to a specific workflow stage. There is no conversation history to reconstruct and no API log to interpret — the project record is the file record.

The agent had no persistent memory between sessions. This constraint, rather than being worked around, was incorporated into the workflow design: each session began with an explicit context re-establishment, and all context required for a session was provided in files. This made the context boundary a design requirement rather than a limitation.

No external APIs, databases, vector stores, embedding pipelines, or automation tools were used. The framework is intentionally minimal — the complexity is in the governance design, not the infrastructure.

---

## What This Document Is Not

This document is not a setup guide, a deployment guide, or a developer reference. It describes architectural and design decisions for readers who want to understand the framework's methodology.

The framework is not:
- A model training or fine-tuning project
- A machine learning engineering project
- A production software system
- An autonomous project management system
- A software development project

It is a governed, human-supervised AI workflow designed and evaluated by a project manager to understand where AI genuinely accelerates project delivery work — and where human judgment cannot be delegated.

---

*Framework version: 1.0 | Built: 2026 | Environment: Windows, Docker, OpenClaw (Claude-backed agent)*
