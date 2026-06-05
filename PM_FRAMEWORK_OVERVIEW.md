# AI-Assisted Project Delivery Framework
## Architecture, Process, and Human-in-the-Loop Design

---

## What This Framework Is

This workspace contains a structured, human-supervised AI framework built to explore where generative AI can genuinely support project management workflows — and where human judgment is irreplaceable.

It is not a fully automated system. It is a supervised workflow. The AI produces structured analysis and planning artifacts. The PM reviews, validates, corrects, and decides. The AI accelerates documentation throughput. The PM owns every decision.

The framework was built, tested, and refined iteratively across real-world project scenarios using a locally hosted AI agent (OpenClaw) inside a Docker sandbox environment.

---

## The Three Modules

### MODULE 1 — PM Intake (`/PM_Intake`)

**What it does:** Converts any project input document into a structured five-layer analysis within minutes.

**Inputs accepted:**
- Statement of Work (SOW)
- Project brief or charter
- Email summary
- Completed intake form (for informal or verbal inputs)
- Partial or incomplete documents — the engine flags gaps rather than refusing to run

**The Five-Layer Analysis Framework:**
1. **Scope Definition** — What is being delivered, what is excluded, what is assumed, what is fixed vs. flexible
2. **Dependency Mapping** — Technical, resource, approval gates, and third-party reliance
3. **Constraint Identification** — Timeline, budget, resource bandwidth, regulatory/compliance timing
4. **Stakeholder Alignment** — Decision authority, sign-off responsibility, risk absorption
5. **Risk Concentration** — Ambiguity analysis, scope drift potential, tradeoff surfaces, highest-concentration risk

**Outputs (3 files per run):**
- `[projectname]_analysis.md` — Full five-layer analysis with OPEN items flagged per layer and 5 priority questions
- `[projectname]_open_items.md` — Consolidated OPEN items tracking log with status/owner columns
- `[projectname]_stakeholder_map.md` — Stakeholder map with alignment risks (produced only when input has sufficient detail)

**Design guardrails built into the prompt:**
- The engine never invents resolved decisions or confirmed facts
- Anything unclear, ambiguous, or unaddressed is flagged OPEN — not filled with a plausible answer
- Inferred risks are explicitly labeled INFERRED — never presented as confirmed
- Output is calibrated for a PM audience — not an executive summary, not a developer spec

**Worked examples (included):**
- `examples/clinical_quality_reporting_intake/` — clinical quality reporting and analytics SOW (complex, multi-phase, regulatory deadline)
- `examples/healthcare_saas_deployment/` — ambient clinical documentation professional-services SOW (evaluation-period constraints, activity-based scope)

---

### MODULE 2 — PM Delivery (`/PM_Delivery`)

**What it does:** Takes the intake analysis outputs and the original project document, then builds a delivery-ready planning package that a PM can use on day one.

**Inputs required:**
- Original project document (SOW, brief, or charter)
- All three intake outputs from Module 1

**The AI reads all input files together** to understand what is confirmed, what is OPEN, and what risks were flagged — then builds artifacts shaped by that specific project's reality, not a generic template.

**Outputs (4 files per run):**

1. **`[projectname]_kickoff_agenda.md`**
   - Meeting agenda shaped by the actual gaps and open items from intake analysis
   - Each priority open question is a named agenda item with a designated answer owner
   - Not a generic kickoff template — built from what this project needs to resolve

2. **`[projectname]_project_plan.csv`**
   - Importable to Microsoft Project or Excel
   - Tasks derived from SOW activities and five-layer analysis
   - OPEN items carried forward in task Notes column — not resolved
   - Milestone owners, predecessors, phases, and statuses included

3. **`[projectname]_RAID_log.md`**
   - Pre-populated Risks, Assumptions, Issues, Dependencies log
   - Risks from intake analysis populated with severity, probability, impact, and mitigation
   - Inferred risks labeled INFERRED — never presented as confirmed
   - Working tool for delivery, not a filed document

4. **`[projectname]_stakeholder_matrix.md`**
   - Deeper than the intake stakeholder map — assigns RACI responsibilities to specific deliverables and decisions
   - Surfaces accountability gaps explicitly
   - Ready for delivery kickoff review

**Worked example (included):**
- `examples/healthcare_saas_deployment/delivery_outputs/` — full four-file delivery package (kickoff agenda, project plan CSV, RAID log, RACI matrix) for the ambient clinical documentation engagement

---

### MODULE 3 — PM Simulation (`/PM_Simulation`)

**What it does:** Exercises the framework under controlled conditions, tests the AI's behavior across a simulated full project lifecycle, and generates a documented supervision report.

**The simulation scenario:**
- **Product:** VoiceRx Cloud — AI-assisted clinical documentation SaaS
- **Client:** Northgate Regional Health System (3 campuses, 85 physicians, Epic EMR)
- **Starting condition:** Contract signed, nothing formally scoped, kickoff in two weeks

**Four simulation phases:**

| Phase | What the AI does | What the PM monitors |
|-------|-----------------|----------------------|
| Phase 1 — Intake | Reads charter, summarizes scope, identifies risks and unknowns, drafts agendas | Does it stay within the charter? Does it flag risks proactively or only when prompted? |
| Phase 2 — Planning | Generates milestone outline, stakeholder map, communication cadence, dependency assumptions | Does it maintain context from Phase 1? Does it carry OPEN items forward? |
| Phase 3 — Execution Support | Drafts status updates, escalation summaries, UAT plans, go-live checklists, hypercare templates | Does it adapt to new inputs or repeat stale assumptions? |
| Phase 4 — Controlled Change Event | Responds to deliberate disruption (e.g., Epic integration slips 3 weeks, key physician champion unavailable) | Does it adapt its plan? Does it hallucinate decisions or outcomes? Does it lose project context? |

**Human role throughout:**
- Define what the agent should produce (instruction architecture)
- Review all outputs for accuracy, completeness, and drift
- Inject change events to test adaptability
- Correct the agent when it hallucinates or misses context
- Document observations throughout

**Primary output:** AI Agent Supervision Report — a structured 2-3 page document covering objective, agent setup, tasks assigned, failure patterns observed, drift examples, corrections applied, lessons learned, and PM application insights.

**Included outputs** (`examples/ai_project_coordinator_simulation/`):
- `outputs/scope_summary.md` — agent-produced scope summary from charter
- `outputs/risk_log.md` — risk log (explicit + inferred)
- `outputs/stakeholder_map.md` — named stakeholder table with engagement levels
- `outputs/project_plan.md` — milestone-level delivery plan
- `outputs/change_event_summary.md`, `outputs/updated_risk_log.md`, `outputs/escalation_draft.md`, `outputs/revised_project_plan.md` — controlled change-event response and re-plan
- `outputs/ai_agent_supervision_report.md` — the supervision report
- `templates/status_update_template.md`, `templates/uat_plan_template.md`, `templates/go_live_checklist.md`, `templates/hypercare_report_template.md`

---

## How the Three Modules Connect

```
PROJECT INPUT DOCUMENT
        │
        ▼
┌─────────────────────┐
│   MODULE 1          │
│   PM INTAKE         │  ← Structured five-layer analysis
│   Analysis Engine   │  ← OPEN items flagged, not filled
└────────┬────────────┘
         │  3 analysis files
         ▼
    ◆ HUMAN REVIEW ◆
    PM validates analysis
    Resolves priority questions
    Confirms accuracy
    Authorizes next phase
         │
         ▼
┌─────────────────────┐
│   MODULE 2          │
│   PM DELIVERY       │  ← Delivery artifacts shaped by intake
│   Planning Engine   │  ← OPEN items carried forward, not assumed
└────────┬────────────┘
         │  4 delivery files
         ▼
    ◆ HUMAN REVIEW ◆
    PM validates all artifacts
    Confirms plan is actionable
    Owns all delivery decisions
         │
         ▼
  DELIVERY-READY PACKAGE
  (Kickoff Agenda · Project Plan · RAID Log · RACI Matrix)

MODULE 3 — PM SIMULATION
Runs in parallel as an evaluation and learning layer.
The PM supervises the AI across all four phases,
documents its behavior, and produces a supervision report.
```

---

## Human-in-the-Loop Decision Points

This framework was designed around a deliberate principle: **AI accelerates, PM decides.**

Every human review checkpoint is a real gate — not a formality.

| Gate | Location | What the PM decides |
|------|----------|---------------------|
| Input quality gate | Before Module 1 runs | Is this input sufficient to analyze? Use intake form if not. |
| Analysis validation | After Module 1 output | Is the five-layer analysis accurate and complete? Are OPEN items correctly identified? Should any inferred risks be confirmed or dismissed? |
| Priority question resolution | Before Module 2 runs | Which priority questions must be answered before delivery planning begins? |
| Delivery artifact review | After Module 2 output | Is the project plan realistic? Is the RAID log pre-populated correctly? Does the kickoff agenda address the right gaps? |
| Scope and risk acceptance | Throughout delivery | Which risks are accepted? Which require mitigation? Where does accountability land? |
| Simulation oversight | Throughout Phase 1–4 | Is the agent staying within scope? Where is it drifting? What corrections are needed? |

**What the AI never decides:**
- Whether scope is acceptable
- Which risks to accept vs. mitigate
- Stakeholder accountability assignment
- Whether a project is ready to proceed
- How to handle scope change requests
- Go/no-go for any milestone or go-live

---

## File Structure

```
deliveryintelligence/
│
├── README.md                                  ← Portfolio summary
├── PM_FRAMEWORK_OVERVIEW.md                    ← This document
├── AI-assisted_project_delivery_framework.svg  ← Three-module process flow
├── AI-assisted_project_delivery_architecture.svg ← Technical architecture diagram
│
├── prompts/
│   ├── pm_intake_prompt.md          ← Module 1 intake prompt (Five-Layer Framework)
│   ├── pm_delivery_prompt.md        ← Module 2 delivery engine prompt
│   └── pm_simulation_prompt.md      ← Module 3 simulation framework
│
├── docs/
│   ├── technical_implementation_notes.md
│   ├── human_in_the_loop_design.md
│   ├── ai_governance_observations.md
│   └── lessons_learned.md
│
└── examples/
    ├── healthcare_saas_deployment/             ← Intake → delivery (ambient documentation SOW)
    │   ├── example_summary.md
    │   ├── input/sample_sow.md
    │   ├── intake_outputs/                      (analysis.md, open_items.md)
    │   └── delivery_outputs/                    (kickoff_agenda.md, project_plan.csv,
    │                                             raid_log.md, stakeholder_matrix.md)
    │
    ├── clinical_quality_reporting_intake/       ← Intake only (regulatory, multi-phase SOW)
    │   ├── example_summary.md
    │   ├── input/sample_sow.md
    │   └── intake_outputs/                      (analysis.md, open_items.md, stakeholder_map.md)
    │
    └── ai_project_coordinator_simulation/       ← Full lifecycle simulation (Module 3)
        ├── example_summary.md
        ├── input/project_charter.md
        ├── outputs/                             (scope_summary.md, risk_log.md, stakeholder_map.md,
        │                                         project_plan.md, change_event_summary.md,
        │                                         updated_risk_log.md, escalation_draft.md,
        │                                         revised_project_plan.md, ai_agent_supervision_report.md)
        └── templates/                           (status_update_template.md, uat_plan_template.md,
                                                  go_live_checklist.md, hypercare_report_template.md)
```

---

## Operating Environment

The framework was executed locally using a Claude-backed AI agent running in an isolated Docker environment on Windows. All inputs and outputs are plain Markdown (`.md`) or CSV files — no database, no external API, no persistent memory between sessions. Prompt guardrails are defined in structured files within each module's `prompts/` directory and issued to the agent at runtime by the PM.

The PM controls the instruction. The agent executes within it. The PM reviews the output.

For full execution details, see `docs/technical_implementation_notes.md`.

---

## Design Principles

These principles were defined before any outputs were produced and held constant throughout.

| Principle | What it means in practice |
|-----------|--------------------------|
| **No fabrication** | The AI never invents resolved decisions, confirmed agreements, or assumed facts. If it is not in the input, it is OPEN. |
| **OPEN discipline** | Every gap, ambiguity, or unanswered question is flagged as OPEN and tracked. The PM resolves OPEN items — not the AI. |
| **Graceful ambiguity** | The engine works with partial, messy, or informal inputs. It does not require perfect documents. It flags what is missing. |
| **Inferred ≠ confirmed** | Risk analysis requires inference. All inferred items are explicitly labeled INFERRED — never surfaced as fact. |
| **Audience-calibrated output** | Output is written for a PM, not a developer or an executive. Practical, structured, actionable. |
| **Concise over comprehensive** | A short analysis that drives a conversation is more valuable than a long document that gets skimmed. |
| **Human authority maintained** | Scope decisions, risk acceptance, stakeholder accountability, and delivery decisions belong to the PM. The AI drafts — the PM decides. |

---

*Document produced for portfolio and professional reference purposes.*
*Framework version: 1.0 | Built: 2026 | Environment: Windows, Docker, OpenClaw (Claude-backed agent)*
