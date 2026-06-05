# UAT Plan — VoiceRx Cloud Implementation (Template)

**Project:** VoiceRx Cloud Implementation
**Client:** Northgate Regional Health System
**EMR:** Epic
**Integration:** HL7 FHIR API
**UAT window (planned):** [YYYY-MM-DD] to [YYYY-MM-DD] (OPEN)
**UAT owner (vendor):** [Solutions Engineer — TBD]
**UAT owner (client):** [Clinical champion lead — OPEN]

---

## 1) Purpose
- Validate that in-scope workflows function as expected for in-scope physician specialties and campuses.
- Confirm integration behavior meets agreed requirements.
- Identify defects/issues early enough to remediate before go-live.

## 2) UAT Scope
### In scope
- VoiceRx Cloud core clinical documentation workflows (specialty-specific scenarios)
- Epic integration touchpoints via HL7 FHIR API
- Role-based access checks (physician/admin/IT as applicable)

### Out of scope
- Billing integration (out of scope)
- Patient portal (out of scope)
- Mobile app (out of scope)

## 3) Participants (placeholders)
| Participant | Role | Specialty/Campus | Responsibilities | Confirmed (Y/N) |
|---|---|---|---|---|
| [Name] | Clinical champion | [PCP/Cardiology/ED + campus] | Execute scenarios, document results | [ ] |
| [Name] | IT lead/contact | [Epic] | Support access/env, troubleshoot | [ ] |
| [Name] | Vendor SE | [Vendor] | Facilitate, triage issues | [ ] |

## 4) Test Environments & Access (OPEN)
- **Epic environment(s):** [OPEN]
- **VoiceRx environment(s):** [OPEN]
- **Test accounts:** [OPEN]
- **Access prerequisites:** [OPEN]

## 5) Test Scenarios (outline)
> Add detailed steps in an attached spreadsheet or table if needed.

### A) Primary Care (placeholder)
- Scenario 1: [OPEN]
- Scenario 2: [OPEN]

### B) Cardiology (placeholder)
- Scenario 1: [OPEN]
- Scenario 2: [OPEN]

### C) Emergency Medicine (placeholder)
- Scenario 1: [OPEN]
- Scenario 2: [OPEN]

### D) Integration / interoperability (Epic)
- Scenario 1: [OPEN]
- Scenario 2: [OPEN]

## 6) Defect / Issue Management
- **Logging method:** [Jira/Service desk/Shared log — OPEN]
- **Severity definitions:** [OPEN]
- **Triage cadence:** [daily standup / working session — OPEN]
- **Ownership:** Vendor triage lead [OPEN]; client contact [OPEN]

## 7) Entry Criteria (must be true to start UAT)
- [ ] Scope baseline and acceptance criteria available (OPEN)
- [ ] Integration approval obtained or testing access granted (OPEN)
- [ ] Environments available and stable (OPEN)
- [ ] Participants scheduled and trained on how to execute UAT (OPEN)
- [ ] Test scenarios defined and distributed (OPEN)

## 8) Exit Criteria (must be true to complete UAT)
- [ ] All planned scenarios executed or formally deferred with approval
- [ ] No open critical defects; high defects have accepted remediation plan
- [ ] UAT results reviewed with client stakeholders
- [ ] Sign-off recorded

## 9) Sign-Off Tracking
| Sign-off item | Signatory | Date | Status | Notes |
|---|---|---:|---|---|
| UAT completion | [Client signatory — OPEN] | [YYYY-MM-DD] | OPEN / Signed | [notes] |
| Go-live readiness confirmation | [CMO/IT Lead — OPEN] | [YYYY-MM-DD] | OPEN / Signed | [notes] |

## 10) Attachments / Links (placeholders)
- UAT scenario details: [link]
- Defect log: [link]
- Readiness checklist: [link]
