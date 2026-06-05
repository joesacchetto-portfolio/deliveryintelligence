# Example Summary: Healthcare SaaS Deployment

---

## Scenario

A vendor PM inherits a signed professional-services SOW to deploy an ambient clinical documentation product ("Fictional Ambient") for Fictional Health Medical Center. The EHR in use is Cerner. The engagement supports up to 11 authorized users (with up to 6 supported during an initial "Evaluation Period") across a broad list of specialties, and is delivered largely remotely. The SOW is activity-based: it lists services (technical assessment, SSO integration, training, help desk training, UAT support) but does not define a project schedule, milestones, or acceptance criteria — these are deferred to a "mutually agreed project schedule" to be established within five days of General Availability (GA).

---

## Objective

Test whether the AI intake engine could extract a structured, actionable analysis from an activity-based SOW that defines services but not schedule, milestones, or acceptance criteria — and then use that analysis, with the original SOW, to produce delivery-planning artifacts a PM could work from on day one.

---

## My Role

PM and framework architect. Designed the intake prompt and guardrails, provided the SOW as input, reviewed all AI outputs against the source document, verified OPEN item flags, corrected any assumptions the AI presented as confirmed, and accepted or modified the delivery artifacts before treating them as working documents.

---

## Input

Vendor SOW for an ambient clinical documentation professional-services engagement. Standard healthcare vendor format. Scope defined at activity level; schedule, milestones, and acceptance criteria not stated; stakeholders only partially named (one customer sponsor and two vendor escalation contacts).

---

## Outputs Produced

**Intake (2 files):**
- `intake_outputs/analysis.md` — five-layer analysis covering scope definition, dependency mapping, constraint identification, stakeholder alignment, and risk concentration
- `intake_outputs/open_items.md` — open items log consolidating all unresolved items from the five layers plus the priority open questions

> Note: a stakeholder map was intentionally **not** produced at intake. The SOW contained insufficient stakeholder detail to make one meaningful, and the engine recorded that fact ("Stakeholder map not produced — insufficient stakeholder detail in input document") rather than fabricating one. This is the framework's conditional-output behavior working as designed.

**Delivery (4 files):**
- `delivery_outputs/kickoff_agenda.md` — kickoff agenda tailored to the specific open items from the intake analysis
- `delivery_outputs/project_plan.csv` — project plan, importable to Excel or Microsoft Project
- `delivery_outputs/raid_log.md` — RAID log pre-populated from the intake analysis, with inferred risks labeled INFERRED
- `delivery_outputs/stakeholder_matrix.md` — stakeholder and responsibility matrix (RACI)

Six artifacts total (2 intake + 4 delivery).

---

## Key Observation

The engine flagged "definition risk" — the absence of a defined schedule, milestones, acceptance criteria, and out-of-scope boundaries — as the single highest-concentration risk, and labeled it INFERRED rather than asserting it as fact. In the RACI matrix it left unconfirmed owners as OPEN instead of inventing them, including leaving decision authority OPEN for the only named stakeholder (Kerry Shaw, listed as sponsor / license recipient but with no decision rights stated in the SOW). The most valuable check at Gate review was confirming the engine had not silently assigned sign-off owners (UAT, SSO completion, training completion) that the SOW never specified — the kind of inferred-as-confirmed gap-filling that would otherwise propagate into delivery artifacts as fact.
