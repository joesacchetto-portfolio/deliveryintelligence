PROJECT INTAKE ANALYSIS
Input document: sample_sow.md
Analysis date: 2026-02-22
Framework version: 1.0

---

LAYER 1 — SCOPE DEFINITION
What is being delivered (explicit):
- Enterprise implementation of the Fictional CQR Platform (cloud-hosted SaaS) across the Network's eleven acute care facilities.
- Platform configuration:
  - Enterprise tenant configuration.
  - Facility-level configuration for all 11 sites.
  - Role-based access control aligned to Network org structure.
  - CMS quality measure set configuration (eCQM library; version TBD at kickoff).
- System integration:
  - Epic EHR integration (build 2024.1).
  - Enterprise data warehouse (EDW) integration for historical baseline reporting.
  - State HIE integrations for Illinois, Indiana, Ohio for external reporting submissions.
- Data migration:
  - Migration of 3 years of historical quality measure data from legacy tool (Legacy Quality Reporting Platform; EOL Dec 2026).
  - Data validation and reconciliation against source system records.
- Regulatory compliance validation:
  - CMS eCQM submission readiness testing.
  - Validation against current HEDIS specifications.
  - Joint Commission ORYX reporting configuration.
  - ONC certification alignment review (scope/depth TBD).
- Training:
  - Administrator training for Network IT and Quality teams.
  - End-user training for clinical staff across all 11 facilities.
  - Training materials + recorded sessions as artifacts.
- Go-live support:
  - 60-day hypercare post go-live.
  - Dedicated support resource during first CMS submission cycle.

What is explicitly excluded from scope:
- Modifications to Epic or any Network source system.
- Ongoing managed services/platform administration post-hypercare.
- Compliance advisory or legal interpretation of CMS regulations.
- Any integration not explicitly listed.
- Facilities/subsidiaries acquired after contract execution.

Embedded assumptions affecting scope:
- Access to Epic sandbox and production within 3 weeks of contract execution.
- EDW is production-stable and accessible via standard API or SFTP extract.
- Legacy Quality Reporting Platform data exportable in a structured format compatible with Fictional Technology Partners tooling.
- State HIE onboarding for IL/IN/OH can be completed within project timeline.
- Facility quality managers (x11) designated within 2 weeks of contract execution.
- CMS eCQM specs will not change materially after kickoff.
- Network legal/compliance provides interpretation guidance; Fictional Technology Partners configures to requirements as confirmed.
- Sufficient Network IT and clinical staff availability for testing/training throughout.

Fixed vs flexible elements (as stated / implied):
- Fixed: Go-live no later than Aug 1, 2026; all 11 facilities in scope; named integrations (Epic, EDW, 3 state HIEs); 3 years historical migration; 60-day hypercare; first CMS submission cycle dedicated support.
- Flexible / TBD: Phased delivery details (milestone dates, entry/exit criteria, phase sign-offs) to be defined in Project Charter; eCQM library/version for reporting year TBD at kickoff; ONC certification alignment review scope/depth TBD; steering committee cadence/tooling TBD.

OPEN ITEMS — SCOPE:
- OPEN: Define eCQM library/version and applicable reporting year at kickoff (needed for configuration and test submission planning).
- OPEN: Define scope/depth of ONC certification alignment review (what deliverable is expected and what "alignment review" means).
- OPEN: Clarify what "dedicated support resource during first CMS submission cycle" means (hours, duration, responsibilities).
- OPEN: Confirm whether end-user training is expected to be delivered live at all facilities vs train-the-trainer / hybrid (SOW says "delivered," format not specified).
- OPEN: Define exact migration content boundaries (which measures, which data elements, inclusion/exclusion rules) beyond "three years of historical quality measure data."

---

LAYER 2 — DEPENDENCY MAPPING
Technical dependencies (explicit):
- Fictional CQR Platform (cloud-hosted SaaS).
- Epic EHR (build 2024.1).
- Network EDW (access via API or SFTP extract).
- Legacy reporting tool: Legacy Quality Reporting Platform (data export for 3-year history).
- State HIEs in Illinois, Indiana, Ohio (external submissions).
- Regulatory frameworks: CMS eCQM, HEDIS (NCQA), Joint Commission ORYX, ONC certification requirements, HIPAA, state-specific HIE participation agreements.

Resource dependencies (explicit):
- Network:
  - Epic Applications Manager (integration lead).
  - Compliance and Regulatory Affairs Director (regulatory sign-off authority; confirms requirements/deadlines).
  - Director of Clinical Informatics (primary business owner; day-to-day counterpart).
  - Facility Quality Managers x11 (site contacts).
  - VP of IT (technical executive) and CQO (exec sponsor).
- Fictional Technology Partners:
  - Engagement Director (delivery accountability).
  - Senior Implementation Consultant (day-to-day lead).
  - Integration Architect.
  - Clinical Informatics Specialist.
  - Training Lead.
- Third parties:
  - Epic Systems support (scope/SLA not defined).
  - State HIE contacts (not identified).

Approval gates (explicit / implied):
- Project Charter within 2 weeks of contract execution defines milestone dates, entry/exit criteria, and phase sign-offs.
- Go-live acceptance requires CQO or designated authority signature.
- Compliance and Regulatory Affairs Director confirms applicable regulatory requirements and submission deadlines.

External vendor / third-party reliance:
- Epic Systems vendor support is relied upon, but scope/SLA undefined.
- HIE onboarding and coordination depends on state HIE entities; contacts not identified.
- CMS submission deadlines are non-negotiable; at least one full CMS eCQM test submission required prior to go-live acceptance.

OPEN ITEMS — DEPENDENCIES:
- OPEN: Epic integration approach specifics (interfaces, data elements, environments, auth, build responsibilities) and what "custom configuration" could entail.
- OPEN: Epic vendor support terms (SLA, availability, scope) and how/when Epic is engaged.
- OPEN: State HIE onboarding requirements per state (IL/IN/OH), timelines, technical specs, and named contacts.
- OPEN: EDW integration specifics (API vs SFTP, file formats, cadence, security requirements, ownership).
- OPEN: Define formal phase sign-off gates and who signs each (beyond go-live acceptance).
- OPEN: Tooling for shared issue/risk log and status reporting (to be determined at kickoff).
- OPEN: Contract authority for change orders on Network side (explicitly not identified in SOW).

---

LAYER 3 — CONSTRAINT IDENTIFICATION
Timeline constraints (explicit):
- CAP compliance deadline: Oct 1, 2026.
- Required go-live no later than Aug 1, 2026 to allow validation/UAT and first CMS submission cycle prior to Oct 1.
- Contract execution anticipated early March 2026; ~22 weeks from execution to required go-live.
- High-level phases with week ranges are stated; milestone dates and sign-offs must be defined in Project Charter within 2 weeks of contract execution.

Budget constraints (explicit):
- Fixed fee: $1,875,000.
- Travel billed separately at cost with prior written approval.
- Change orders require written approval from both parties prior to commencing work.

Resource bandwidth limitations (explicit / implied):
- Network access provisioning (Epic sandbox + production) within 3 weeks of contract execution.
- Facility quality managers designated within 2 weeks.
- Network IT and clinical staff availability may be constrained during summer (explicit risk).

Regulatory/legal/compliance timing requirements (explicit):
- CMS eCQM reporting requirements; at least one full CMS eCQM test submission must be successfully completed at go-live.
- HEDIS specs, Joint Commission ORYX configuration.
- HIPAA data handling requirements apply to integrations and migration.
- State-specific HIE participation agreements may impose timing/approval requirements.

OPEN ITEMS — CONSTRAINTS:
- OPEN: Exact contract execution date (needed to anchor week 1–22 and Aug 1 go-live readiness plan).
- OPEN: CMS submission cycle dates relevant to "first CMS submission cycle" support requirement (deadlines not specified).
- OPEN: Whether Aug 1 is a hard go-live gate vs latest acceptable date (SOW states "must achieve go-live no later than Aug 1").
- OPEN: Constraints on production access/change windows for Epic/EDW and facility operations (not specified).
- OPEN: Budget governance for travel approvals (who approves; lead times) and change order approval workflow.

---

LAYER 4 — STAKEHOLDER ALIGNMENT
Decision-making authority (as stated):
- Network CQO is Executive Sponsor (likely final business authority and go-live acceptance signatory or designator).
- Network VP of IT is Technical Executive (technical executive sponsor).
- Network Compliance and Regulatory Affairs Director is Regulatory Sign-Off Authority (confirms applicable requirements and submission deadlines).
- Network's designated contract authority for change orders is not yet identified.

Influence without final authority (as stated / implied):
- Director of Clinical Informatics is Primary Business Owner and day-to-day counterpart (significant influence on scope/priorities).
- Epic Applications Manager is EHR Integration Lead (influences integration feasibility and timelines).
- Facility Quality Managers x11 influence readiness and local adoption.
- Fictional Technology Partners Engagement Director holds overall delivery accountability.
- Fictional Technology Partners Senior Implementation Consultant leads day-to-day delivery.
- Integration Architect and Clinical Informatics Specialist influence technical and measure configuration decisions.

Who is responsible for sign-off:
- Go-live acceptance requires CQO or designated authority signature.
- Regulatory requirements and deadlines confirmation sits with Compliance and Regulatory Affairs Director.
- Phase sign-offs beyond go-live are not defined (to be defined in Project Charter).

Who absorbs risk if something goes wrong:
- Network absorbs financial penalty risk if CAP compliance not met (Medicare reimbursement penalties estimated at $4.2M annually).
- Fictional Technology Partners absorbs delivery execution risk within fixed fee (rework/overrun risk), but boundaries are not explicitly defined.

OPEN ITEMS — STAKEHOLDERS:
- OPEN: Identify Network change order contract authority (required for scope/budget changes).
- OPEN: Identify state HIE contacts for IL/IN/OH and confirm their roles/authority.
- OPEN: Clarify whether CQO delegates go-live acceptance and which roles sign phase acceptances.
- OPEN: Confirm internal Network owners for EDW integration and for Epic environment provisioning.

---

LAYER 5 — RISK CONCENTRATION
Where ambiguity sits:
- Phased delivery details and phase acceptance criteria are deferred to the Project Charter.
- Epic integration complexity is acknowledged but not scoped (what constitutes "custom configuration," and who owns it).
- HIE onboarding variability across three states; contacts and onboarding timelines are not defined.
- ONC certification alignment review is included but scope/depth is TBD.
- Change order authority on Network side is unknown, creating governance risk for out-of-scope demands.

Where scope or requirements drift could occur:
- ONC alignment review could expand from "review" to extensive gap remediation.
- Measure set/version changes (CMS/Joint Commission updates) could drive rework.
- Facility-level variability could drive "one-off" requests per site (templates, workflows, training expectations).
- Requests to include newly acquired facilities/subsidiaries are explicitly out of scope, but may arise if acquisitions occur.

Where tradeoffs are likely to surface:
- Time (Aug 1 go-live) vs breadth of validation across 11 facilities and 3 external HIE connections.
- Fixed fee vs integration complexity and state variability (who funds additional work if Epic/HIE needs exceed standard).
- Summer resource constraints vs testing/training intensity (weeks 15–19 overlap with summer period).

Single highest-concentration risk in this project:
- INFERRED: External dependency risk concentrated in integrations (Epic + three state HIEs) under a hard regulatory timeline. The project's success depends on timely approvals/access and variable third-party onboarding, while the go-live deadline (Aug 1) is framed as mandatory to avoid Oct 1 CAP penalties.

---

PRIORITY OPEN QUESTIONS
1. Confirm contract execution date and lock a detailed milestone plan backward from the Aug 1, 2026 go-live (including phase entry/exit criteria and sign-offs).
2. Define the Epic integration scope and responsibilities (data elements, environments, auth, custom work expectations) and confirm Epic Systems support terms/SLA.
3. Identify state HIE contacts for Illinois, Indiana, and Ohio and confirm onboarding requirements, timelines, and technical submission specifications for each.
4. Confirm the applicable CMS eCQM reporting year/measure set version and the acceptance criteria for "one full CMS eCQM test submission completed successfully."
5. Identify the Network's change order contract authority and define the change control workflow (to avoid governance stalls under fixed-fee delivery).

---

END OF ANALYSIS
