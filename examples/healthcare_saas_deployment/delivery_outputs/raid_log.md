RAID LOG
Project: Fictional Health Medical Center — Fictional Ambient Professional Services
Input document: sample_sow.md
Date opened: 2026-02-22
Framework version: 1.0

---

INSTRUCTIONS FOR USE
Update this log throughout delivery. Add new items as they emerge.
Severity options: HIGH | MEDIUM | LOW
Status options: OPEN | IN PROGRESS | RESOLVED | CLOSED

---

RISKS
| # | Risk Description | Severity | Probability | Impact | Mitigation | Status | Owner |
|---|-----------------|----------|-------------|--------|------------|--------|-------|
| 1 | INFERRED: Definition risk — schedule, milestones, acceptance criteria, and out-of-scope boundaries are not defined and are deferred to a future mutually agreed schedule. | HIGH | HIGH | Misaligned expectations; rework; schedule delays | Use kickoff to lock GA date, evaluation period, acceptance criteria, sign-offs, and change control in writing. | OPEN | Joint |
| 2 | INFERRED: Scope creep risk — expansion beyond 11 authorized users or beyond 6 users during evaluation. | HIGH | MEDIUM | Delivery overload; commercial conflict | Define user enforcement rules and change control; track requests. | OPEN | Joint |
| 3 | INFERRED: Onsite vs remote delivery risk — onsite minimum attendance requirements are undefined; may cause conflict and rescheduling. | MEDIUM | MEDIUM | Training delays; dissatisfaction | Define minimum attendance thresholds and remote fallback rules; publish training plan. | OPEN | Joint |
| 4 | INFERRED: Technical dependency risk — SSO prerequisites and Cerner environment readiness may delay integration and testing support. | HIGH | MEDIUM | Pushes schedule; blocks UAT support | Confirm IdP, security review, access provisioning owners; run technical assessment early. | OPEN | Customer |
| 5 | INFERRED: Adoption/engagement risk — physician champions not identified; attendance may be low. | MEDIUM | MEDIUM | Reduced adoption; increased support needs | Identify physician champions; require attendance commitments; use leadership messaging. | OPEN | Customer |

---

ASSUMPTIONS
| # | Assumption | Consequence if Wrong | Status | Owner |
|---|------------|---------------------|--------|-------|
| 1 | EHR in use is Cerner. | Wrong EHR/workflows could invalidate technical planning and training approach. | OPEN | Customer |
| 2 | Total Authorized Users is 11; Evaluation Period support is limited to 6 users. | User scope disputes and unplanned effort; commercial friction. | OPEN | Joint |
| 3 | Project schedule will be established within 5 days of GA. | Schedule creation may slip; downstream work starts without alignment. | OPEN | Joint |
| 4 | Customer will provide technical support/expertise for environment setup and own technical tasks. | Delays to technical readiness; vendor blocked from delivering services. | OPEN | Customer |
| 5 | Customer will identify attendees and drive full attendance for training sessions. | Training readiness gaps and adoption risk; rework/rescheduling. | OPEN | Customer |

---

ISSUES
No active issues at intake.

---

DEPENDENCIES
| # | Dependency | Type | Required By | Owner | Status | Notes |
|---|------------|------|-------------|-------|--------|-------|
| 1 | GA date confirmation (and whether GA already achieved) | Approval | Project schedule definition | Fictional Health AI | OPEN | SOW: schedule must be established within 5 days of GA. |
| 2 | Evaluation Period definition (dates/success criteria) | Approval | User scope sequencing and schedule | Joint | OPEN | Determines 6-user evaluation vs 11-user support timeline. |
| 3 | Customer technical owners for Cerner environment setup/access | Resource | Technical assessment; SSO work | Customer | OPEN | Names/roles not provided. |
| 4 | SSO prerequisites (IdP, attributes, security approvals, envs) | Technical | SSO integration | Customer | OPEN | Must be confirmed before integration. |
| 5 | Technical Assessment inputs/responses and approvals | Resource | SSO and testing plan | Joint | OPEN | Assessment scope and output approval not defined. |
| 6 | UAT approach and approval process for scripts/results | Approval | Testing planning and support | Joint | OPEN | Needed to finalize UAT scripts and exit criteria. |
| 7 | Physician champions and leadership engagement | Resource | Training scheduling; adoption | Customer | OPEN | Required per Customer Provided Services. |

---

END OF RAID LOG
