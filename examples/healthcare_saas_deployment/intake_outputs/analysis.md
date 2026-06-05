PROJECT INTAKE ANALYSIS
Input document: sample_sow.md
Analysis date: 2026-02-22
Framework version: 1.0

---

LAYER 1 — SCOPE DEFINITION
What is being delivered (explicit):
- Professional services support for Fictional Health Medical Center related to Fictional Health AI Fictional Ambient.
- Support for up to six (6) Authorized Users during an "Evaluation Period."
- Support of Fictional Ambient technology for all Authorized Users following the Evaluation Period.
- Support of Fictional Ambient Live Chat Clinical Support and Live Chat Help.
- General Fictional Health AI-provided services (delivered remotely) including:
  - Scope management with Customer PM.
  - Regular project status calls.
  - Issue list management.
  - Project schedule development/maintenance.
  - Best practices consulting.
  - Training scheduling consulting.
  - Testing planning consulting (including UAT scripts).
  - Testing support.
- Fictional Ambient enablement services:
  - Training (web-based foundational + Q&A up to 11 clinicians; group ILT; optional 1:1; trainer-led sessions up to four attendees/class; attendance minimums for onsite; remote delivery if minimums not met).
  - Technical services (Technical Assessment; AMS/Admin training; SSO integration; Help Desk training).

What is explicitly excluded from scope:
- No explicit "Out of Scope" section is provided in the document.

Embedded assumptions affecting scope:
- EHR in use: Cerner.
- Total Authorized Users: 11.
- Specialty supported list (multiple specialties provided).
- Within five (5) days of General Availability (GA), a mutually agreed project schedule will be established (scope relies on future schedule definition).
- Customer provides environment setup support and owns technical tasks; customer assigns technical resources at initiation.

Fixed vs flexible elements (as stated / implied):
- Fixed: Cerner EHR; 11 total authorized users; evaluation period support capped at 6 users; professional services include listed general activities; technical services include SSO integration and help desk training.
- Flexible / TBD: Definition and duration of "Evaluation Period"; definition/date of "General Availability (GA)"; the project schedule, dependencies, resource requirements, and milestones are to be mutually agreed after GA; whether any services are onsite vs remote is conditional (remote delivery is default and/or fallback).

OPEN ITEMS — SCOPE:
- OPEN: Define the Evaluation Period (start/end dates, success criteria, what constitutes completion).
- OPEN: Define "General Availability (GA)" date for Fictional Ambient in this context.
- OPEN: Define the project's deliverables beyond activity lists (e.g., configured environments, acceptance criteria, go-live criteria).
- OPEN: Confirm whether deployment is limited to the listed specialties or if additional specialties are excluded.
- OPEN: Clarify whether AMS (Admin) training, SSO integration, and Help Desk training are included as standard deliverables for this engagement or optional/additional.

---

LAYER 2 — DEPENDENCY MAPPING
Technical dependencies (explicit):
- EHR: Cerner.
- Fictional Ambient technology.
- SSO integration (implies identity provider and SSO configuration dependencies, not specified).
- AMS (Admin) tooling/training (tool not defined in document).

Resource dependencies (explicit):
- Customer PM and Fictional Health AI PM scope management and regular status calls.
- Customer technical resources assigned at project initiation.
- Customer ownership of technical tasks and timely responses to technical assessments.
- Customer identification of training attendees and driving attendance.
- Engagement of Physician Champions and leadership (customer responsibility).

Approval gates / sign-offs:
- Not explicitly defined.
- Implied gate: establishing mutually agreed project schedule within 5 days of GA.

External vendor / third-party reliance:
- Fictional Health AI is the service provider.
- Potential reliance on customer's SSO/identity provider and Cerner stakeholders (not explicitly named).

OPEN ITEMS — DEPENDENCIES:
- OPEN: Identify customer technical owners for Cerner environment setup, SSO, and any required access provisioning.
- OPEN: Define SSO prerequisites (identity provider, required attributes, security review, test/prod environments).
- OPEN: Define what "Technical Assessment" entails and what inputs/approvals are required.
- OPEN: Define UAT approach and who approves UAT scripts/results.
- OPEN: Identify physician champions (names/roles) and how they will participate.

---

LAYER 3 — CONSTRAINT IDENTIFICATION
Timeline constraints (explicit):
- Within five (5) days of GA, Fictional Health AI and customer will establish a mutually agreed project schedule.

Budget constraints:
- Not addressed.

Resource bandwidth limitations (explicit / implied):
- Evaluation Period support is capped at 6 authorized users.
- Training includes up to 11 clinicians (web-based foundational training) and trainer-led sessions with up to four attendees per class.
- Minimum attendance requirements for onsite sessions; remote delivery if minimums not met.

Regulatory/legal/compliance timing requirements:
- Not addressed.

OPEN ITEMS — CONSTRAINTS:
- OPEN: Project schedule dates and milestones (all TBD pending GA and mutual agreement).
- OPEN: Any go-live deadline or business deadline.
- OPEN: Any budget/not-to-exceed or commercial constraints.
- OPEN: Onsite vs remote delivery rules (what are the onsite minimums and what is considered "not met").

---

LAYER 4 — STAKEHOLDER ALIGNMENT
Decision-making authority (as stated):
- Customer executive sponsors section lists Kerry Shaw (Project Manager / License Recipient). Decision authority is not explicitly defined.
- Fictional Health AI escalation path provides two named account management leaders (Alex Stanton; Jordan McManus) as escalation contacts.

Influence without final authority:
- Customer PM (scope management, schedule collaboration, issue list management).
- Customer technical resources (own technical tasks).
- Physician Champions and leadership (customer responsibility to engage; influence adoption).

Who is responsible for sign-off:
- Not stated.

Who absorbs risk if something goes wrong:
- Not stated. In practice, delivery risks are shared; accountability boundaries are not explicit.

OPEN ITEMS — STAKEHOLDERS:
- OPEN: Confirm who is the Fictional Health AI Project Manager (not named in document) and who is the customer PM.
- OPEN: Confirm who has final decision authority for schedule, scope changes, and go-live readiness.
- OPEN: Identify Cerner stakeholders on the customer side required for environment setup and any integration approvals.
- OPEN: Define sign-off roles for technical assessment, SSO integration, training completion, and UAT.

---

LAYER 5 — RISK CONCENTRATION
Where ambiguity sits:
- The engagement is described largely as activity-based services; acceptance criteria, success measures, and concrete deliverables are not specified.
- "GA" and "Evaluation Period" are undefined but drive scheduling.
- No explicit out-of-scope statements, which increases likelihood of expectation mismatch.

Where scope or requirements drift could occur:
- Expansion beyond 11 authorized users or beyond the initial 6 during evaluation.
- Adding additional EHR workflows, specialties, or technical integrations not specified.
- Onsite training expectations if attendance minimums are contentious.

Where tradeoffs are likely to surface:
- Timeline/schedule creation vs readiness of customer technical resources and environment setup.
- Training quality/coverage vs scheduling constraints and attendance minimums.
- Remote vs onsite delivery expectations.

Single highest-concentration risk in this project:
- INFERRED: Definition risk — key structural elements (schedule, milestones, acceptance criteria, and out-of-scope boundaries) are not defined in the SOW and are deferred to a future "mutually agreed project schedule." This creates a high likelihood of misaligned expectations once execution begins.

---

PRIORITY OPEN QUESTIONS
1. Confirm the Evaluation Period definition (dates, success criteria, what users/specialties are included) and what changes after evaluation.
2. Confirm the GA date that triggers the "within five days" scheduling requirement and whether GA is already achieved.
3. Define the concrete deliverables and acceptance criteria for this engagement (technical assessment outputs, SSO integration completion criteria, training completion criteria, UAT exit criteria).
4. Confirm stakeholder decision rights and sign-off owners (customer sponsor vs PM vs IT vs Cerner stakeholders; Fictional Health AI PM).
5. Define explicit out-of-scope boundaries (e.g., additional integrations, number of users beyond 11, onsite delivery commitments) and change control approach.

---

END OF ANALYSIS
Stakeholder map not produced — insufficient stakeholder detail in input document.
