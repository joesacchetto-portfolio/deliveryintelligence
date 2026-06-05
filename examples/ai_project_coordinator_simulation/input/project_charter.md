# PROJECT CHARTER — VoiceRx Cloud Implementation

**Client:** Northgate Regional Health System
**Campuses:** 3 (Main, Eastside, Westview)
**Physicians in scope:** 85 (Primary Care, Cardiology, Emergency Medicine)
**EMR:** Epic
**Legacy system being replaced:** Olympus dictation system
**Contract signed:** 2026-02-15
**Target go-live:** 2026-05-01
**Executive sponsor (client):** Dr. Patricia Howe, CMO
**IT lead (client):** Marcus Webb, Director of Clinical Informatics
**Project Manager (vendor):** [Vendor PM]
**Solutions Engineer (vendor):** TBD internal assignment
**Training Lead (vendor):** TBD internal assignment
**EMR Integration Specialist (vendor):** TBD internal assignment

---

## Known Risks at Contract Signature

- Physician adoption historically low for new documentation tools
- Epic integration requires separate IT approval process at Northgate
- ED physicians have variable schedules — training coordination will be complex
- Legacy system decommission date not yet confirmed by client

---

## Project Scope

**In scope:**
- Deploy VoiceRx Cloud to all 85 physicians across 3 campuses
- Integrate with Epic via HL7 FHIR API
- Deliver role-based training (physician, admin, IT)
- Provide 30 days post go-live hypercare support

**Out of scope:**
- Billing integration
- Patient portal
- Mobile app

---

## Implementation Context

- Contract was signed by sales; PM is inheriting the project post-signature
- Kickoff with client is scheduled in approximately two weeks
- No formal scope documentation has been completed yet
- Internal resource assignments (SE, Training Lead, Integration Specialist) are pending
- This is Northgate's first AI-assisted clinical documentation tool
- The CMO (executive sponsor) has high visibility expectations for this rollout
- Epic IT team at Northgate runs a separate approval process for integrations — timeline risk
- ED physician scheduling complexity makes training coordination a known challenge
- Physician adoption is the top delivery risk based on historical patterns with similar tools
