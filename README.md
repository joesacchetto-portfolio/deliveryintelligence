Delivery Intelligence is an independently developed AI-governed project delivery framework designed to accelerate project management activities while preserving human oversight, accountability, and governance controls.

The framework uses AI-assisted analysis, delivery planning, and lifecycle simulation to generate structured project artifacts such as project plans, RAID logs, stakeholder matrices, and kickoff agendas. Human review gates are incorporated throughout the workflow to validate assumptions, assess risks, and approve outputs before they progress to subsequent stages.

Key findings from the project suggest that workflow design and governance structures are more important than prompt engineering alone, that human review remains essential for judgment-based decisions, and that AI is most effective as a delivery accelerator rather than a replacement for accountability and decision-making.

# AI-Assisted Project Delivery Framework

Purpose:
Explore how generative AI can support project intake, planning, governance, and change management activities while preserving human decision authority.

Outputs Generated:
• Scope Analysis
• Open Item Logs
• Stakeholder Maps
• RAID Logs
• Project Plans
• Kickoff Agendas
• RACI Matrices
• AI Supervision Reports

Role:
Project Delivery Professional | Workflow Architect | AI Supervisor

> Designed and supervised an AI-assisted project delivery framework used to explore and assess how generative AI could support PM workflows across intake, planning, governance, and change management activities.

---

## What problem were you exploring?

Project managers frequently spend significant effort converting incomplete project documentation into actionable delivery artifacts while maintaining governance, traceability, and risk visibility. A Statement of Work arrives. It is vague in places, silent on others, and completely unsigned on the things that will cause problems six weeks in. Before meaningful delivery planning can begin, a PM has to read it carefully, identify what is missing, map the stakeholders, surface the risks, document the open questions, and build a working plan — often under time pressure, before the kickoff meeting is even scheduled.

The question worth exploring: **could a governed, human-supervised AI workflow meaningfully accelerate that process without removing PM judgment from the decisions that matter?**

A secondary question ran alongside it: what does it look like to actually supervise an AI agent across a simulated project lifecycle — not just generate a document, but watch it operate across phases, introduce deliberate disruption, observe where it drifts, and document what that tells you about AI in delivery environments?

---

## What was the objective?

Explore how generative AI could assist project delivery activities — intake analysis, delivery planning, and governance documentation — while maintaining human oversight and decision authority at every meaningful checkpoint.

The framework was not designed to automate project management. It was designed to understand where AI genuinely adds value, where it requires supervision, and where human judgment cannot be delegated.

---

## What did you build?

A structured, three-module human-supervised AI workflow that converts project inputs into a complete set of intake analysis and delivery planning artifacts, exercised through a controlled simulation.

### Module 1 — PM Intake Analysis Engine

Accepts any project input document (SOW, brief, charter, intake form, even partial or informal inputs) and applies a five-layer structured analysis framework:

1. **Scope Definition** — what is being delivered, what is excluded, what is assumed, what is fixed vs. flexible
2. **Dependency Mapping** — technical, resource, approval gates, third-party reliance
3. **Constraint Identification** — timeline, budget, resource bandwidth, regulatory timing
4. **Stakeholder Alignment** — decision authority, sign-off responsibility, risk absorption
5. **Risk Concentration** — ambiguity analysis, drift potential, highest-concentration risk

Produces three output files per run: a full analysis report, a consolidated open items log, and a stakeholder map.

**OPEN / INFERRED protocol:** Every gap, ambiguity, or unconfirmed item is flagged **OPEN** — meaning required information has not yet been established and must be resolved by the PM before it can drive a project decision. Every risk or assumption the framework identifies by reasoning from context — rather than from explicit language in the input — is labeled **INFERRED**, meaning it requires human validation before it enters the project record as a confirmed risk. This protocol exists to prevent AI-generated artifacts from presenting assumptions as confirmed facts. The PM resolves OPEN items; the AI does not.

Exercised against multiple realistic but fictional scenarios — an ambient clinical documentation professional-services engagement (intake through delivery), a clinical quality reporting and analytics implementation with multi-phase scope and regulatory deadlines (intake), and a full-lifecycle SaaS implementation simulation with a controlled change event. Curated examples are in `examples/`.

### Module 2 — PM Delivery Planning Engine

Takes the intake analysis outputs and the original project document as inputs, then builds four delivery-ready artifacts shaped by the specific project's risks and open items:

- **Kickoff agenda** — structured around the actual gaps from intake, not a generic template
- **Project plan (CSV)** — importable to Microsoft Project or Excel, with OPEN items carried forward in task notes
- **RAID log** — pre-populated with risks, assumptions, and dependencies from the analysis; inferred risks labeled
- **Stakeholder matrix (RACI)** — assigns responsibility to specific deliverables and surfaces accountability gaps

OPEN items from intake are carried forward, not resolved. The AI does not fill gaps with plausible assumptions — it preserves the uncertainty so the PM can resolve it deliberately.

### Module 3 — PM Simulation

A controlled sandbox simulation of a full project lifecycle — VoiceRx Cloud implementation for a mid-size hospital network (3 campuses, 85 physicians, Epic EMR integration).

The simulation ran four phases: intake, planning, execution support, and a controlled change event. Phase 4 deliberately introduced three simultaneous disruptions — a confirmed integration timeline slip, an unconfirmed stakeholder change, and a pending scope expansion request — to test whether the governed workflow preserved decision integrity under pressure. Specifically: would the AI correctly separate confirmed decisions from unconfirmed requests? Would it hold unresolved items as OPEN rather than auto-resolving them? Would it maintain project-specific context rather than drifting to generic output? The PM role throughout was supervisor, governance owner, and drift detector. All outputs were reviewed before advancing phases; failure modes and corrections were documented throughout.

Produced a full set of delivery artifacts across all phases, including scope summary, risk log, stakeholder map, project plan, communication cadence, escalation templates, UAT plan, go-live checklist, hypercare template, change event response, and revised project plan.

Final deliverable: an AI Agent Supervision Report documenting objective, agent setup, tasks assigned, failure patterns, drift examples, corrections applied, and lessons learned.

### Human Review Gates

Two formal review gates sit between the modules and ensure AI-generated content never advances to the next workflow stage without PM validation.

**Gate 1 — After intake analysis:** The PM reviews the five-layer analysis, confirms that OPEN items are correctly identified and no inferred assumptions are presented as confirmed facts, resolves or escalates the priority open questions, and authorizes Module 2 to begin. Nothing from Module 1 is used as planning input until the PM has accepted it.

**Gate 2 — After delivery artifacts:** The PM reviews all four delivery artifacts before any are used for downstream planning or distributed to stakeholders. OPEN items from intake must be carried forward — not silently resolved. The PM confirms the plan is realistic, accountability structure is correct, and outputs are ready to use.

These gates are not formalities. They are the mechanism by which the PM maintains authority over what enters the project record.

---

## What was your role?

Designed the workflow architecture, governance controls, validation checkpoints, and human review gates. Authored both master prompts (intake and delivery engines) including the five-layer analysis framework, guardrail specifications, OPEN/INFERRED labeling discipline, and output format requirements. Operated all three modules as PM and supervisor — running the agent, reviewing every output, detecting where it drifted or fabricated, injecting change events into the simulation, and iteratively refining prompts based on observed failure modes.

The AI generated the documents. Every decision embedded in those documents belongs to the PM.

---

## What did you learn?

**AI was effective at accelerating documentation throughput.** Five-layer analysis of a complex SOW that would otherwise take substantial careful manual review was produced in a fraction of that time — structured, consistent, and traceable. Delivery artifacts that would normally take hours to draft were available for PM review much sooner. The reduction in drafting time was meaningful, though it was observed informally rather than formally measured.

**Prompt architecture is governance architecture.** The quality, reliability, and trustworthiness of AI output in a PM context is almost entirely a function of how precisely you define the task, constrain the behavior, and specify what the AI is and is not permitted to do. The five-layer framework, the OPEN discipline, and the INFERRED labeling requirement did not emerge from the AI — they were designed in by the PM. Garbage guardrails produce garbage output.

**The AI required active supervision, not passive review.** Left to fill gaps, the AI would insert plausible-sounding assumptions as if they were confirmed. It would suggest soft decisions where none had been made. It would occasionally lose thread across a longer simulation session. The guardrails suppressed most of this, but not all of it. Supervision was not optional.

**Human judgment was irreplaceable at every decision boundary.** Which risks are acceptable? Whose accountability is it? Is this scope interpretation correct or is it an assumption the client never agreed to? What does "go-live ready" actually mean for this stakeholder? None of these questions can be answered by a document analysis engine. They require PM judgment, client relationships, organizational context, and accountability that no AI holds.

**The most valuable thing the AI did was reveal what was missing.** By applying consistent structure to inconsistent inputs, the engine surfaced gaps, ambiguities, and undefined decisions that a tired PM doing a quick read might miss. The OPEN items log was often more valuable than the analysis itself — a pre-populated list of the questions that would create problems later if not resolved before kickoff.

**The simulation exposed failure modes that static testing would not.** Running the AI across four phases, then introducing deliberate disruption, showed how the agent handles context degradation, stale assumptions, and novel inputs. It did not always adapt well. Those failure patterns are the most instructive part of the exercise — they clarify exactly where human judgment cannot be delegated and why.

**This is not about AI capability. It is about PM accountability.** The framework works because it was designed with a clear principle: AI accelerates, PM decides. Every design choice — the OPEN flagging, the INFERRED labeling, the human review gates, the guardrails against fabrication — was made to preserve PM authority over the decisions that carry delivery risk. The moment the PM stops reviewing and starts accepting AI output without challenge, the governance model fails.

---

## Why this matters beyond the framework itself

I spent 15 years delivering projects. I wanted to understand where AI fits into that work without removing human accountability from it. Not "look at what the AI can do" — but "where does AI genuinely help, where does it need supervision, and where should a PM never delegate to a machine?"

This framework is the result of that investigation. It is not a product. It is a documented experiment with a clear answer: AI belongs in the workflow as an accelerant, not an authority. The PM who understands that distinction — and can design, supervise, and correct AI systems accordingly — is more valuable, not less, in a world where every organization is trying to figure out how to use these tools responsibly.

---

## Framework Architecture

See `PM_FRAMEWORK_OVERVIEW.md` for complete architecture documentation including file structure, design principles, and human-in-the-loop decision points.

See `AI-assisted_project_delivery_framework.svg` for a visual overview of the three-module architecture and process flow.

For operating environment and execution details, see `docs/technical_implementation_notes.md`.

---

## Note on Examples

All scenarios, organizations, products, and individuals in this repository are fictional. The SOWs, charters, and stakeholder names (e.g., "Fictional Health Medical Center," "VoiceRx Cloud," "Northgate Regional Health System") were created for demonstration only and do not represent any real client, engagement, or confidential information. References to real platforms such as Epic and Cerner appear only as neutral context.

---

*Built 2026 | OpenClaw (Claude-backed agent) | Docker | Windows | PowerShell*
*Framework version 1.0*
