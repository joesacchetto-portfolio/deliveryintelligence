# Risk & Unknowns Log — VoiceRx Cloud Implementation (Northgate)

> Source: project charter (post-contract signature). Includes explicit risks and reasonable inferences requiring validation.

## A) Explicit risks from the charter

1. **Physician adoption risk (top risk):** Historically low adoption for new documentation tools.
   - Impact: Low utilization, workflow resistance, executive dissatisfaction.
   - Early mitigations: Adoption plan (champions), staged enablement, targeted comms, office hours during hypercare.

2. **Epic integration approval process risk:** Northgate Epic IT requires a separate approval process.
   - Impact: Integration start delayed; overall timeline/go-live at risk.
   - Early mitigations: Identify approvers, submission requirements, and lead times immediately; set integration decision gates.

3. **ED training coordination risk:** ED physicians have variable schedules.
   - Impact: Training completion slips; uneven readiness; go-live support load increases.
   - Early mitigations: Multiple session formats/times; short modules; coordinate with ED leadership for protected time.

4. **Legacy decommission unknown:** Olympus decommission date not confirmed.
   - Impact: Dual-running costs/complexity; confusion and adoption drag.
   - Early mitigations: Define owner and decommission decision date; establish cutover/rollback expectations.

## B) Inferred risks (reasonable from charter context)

5. **Aggressive timeline risk (contract 2026-02-15 → go-live 2026-05-01):** ~10–11 weeks for a 3-campus, 85-physician first-time AI tool rollout.
   - Impact: Compressed discovery, training, and integration; quality issues.
   - Early mitigations: Confirm critical path; lock dates; scope discipline; prioritize must-haves.

6. **Scope ambiguity risk:** No formal scope documentation has been completed yet.
   - Impact: Misaligned expectations; change requests; rework.
   - Early mitigations: Rapid discovery; written scope + assumptions; sign-off on acceptance criteria.

7. **Internal resourcing risk:** SE/Training Lead/Integration Specialist are TBD.
   - Impact: Delays to discovery, integration planning, and training design.
   - Early mitigations: Confirm assignments and availability within 48–72 hours; create RACI.

8. **First-time AI-assisted documentation change-management risk:** Northgate's first AI-assisted tool.
   - Impact: Higher anxiety, workflow concerns, heightened scrutiny.
   - Early mitigations: Set expectations; provide demos and workflow mapping; identify champions.

9. **Executive visibility / escalation risk:** CMO expects high visibility.
   - Impact: Increased reporting burden; faster escalation; reputational risk.
   - Early mitigations: Agree on reporting cadence, dashboard content, and escalation paths early.

10. **Multi-campus deployment complexity:** 3 campuses; likely differing workflows/local champions.
    - Impact: Inconsistent adoption and training; coordination overhead.
    - Early mitigations: Site leads per campus; campus-by-campus readiness checks.

11. **Specialty workflow fit risk:** Primary Care vs Cardiology vs ED documentation workflows differ.
    - Impact: Tool perceived as "not for my specialty."
    - Early mitigations: Validate specialty-specific workflows and templates during discovery; pilot with representative users.

12. **Integration dependency risk (FHIR/HL7 + Epic constraints):** Integration scope may be more constrained than assumed.
    - Impact: Reduced functionality; re-planning.
    - Early mitigations: Confirm exact integration endpoints, data flows, environments, and testing plan early.

13. **Testing/UAT time risk:** Charter doesn't specify testing/UAT owners, environments, or timeline.
    - Impact: Late defects; go-live instability.
    - Early mitigations: Define test plan, roles, entry/exit criteria, and schedule.

14. **Training content/scheduling risk across roles:** Role-based training is in scope (physician/admin/IT) but volume and completion criteria are not defined.
    - Impact: Readiness disagreements; adoption issues.
    - Early mitigations: Define training curriculum, completion requirements, and tracking.

15. **Hypercare capacity risk:** 30-day hypercare is in scope; if adoption or training readiness is low, support demand may exceed planned capacity.
    - Impact: SLA misses; dissatisfied stakeholders.
    - Early mitigations: Forecast call volume; define triage process; ensure staffing plan.

## C) Open unknowns to resolve during discovery/internal alignment

- **Internal assignments and availability:** Named resources (SE, Training Lead, EMR Integration Specialist) and their capacity/backup.
- **Epic integration specifics:** Approval steps, required documentation, lead times, technical constraints, environments (test/prod), and who submits what.
- **Success criteria:** What "successful adoption" means for the CMO (usage expectations, qualitative outcomes).
- **Go-live definition:** Big-bang vs phased by campus/specialty; cutover/rollback expectations.
- **Training plan details:** Format (virtual/on-site), duration, number of sessions, tracking method, and required attendance.
- **Physician champion list:** Who are the early adopters by specialty/campus.
- **Legacy Olympus plan:** Decommission owner/date, data retention needs, and communications to clinicians.
- **Stakeholder map:** Operational owners per campus and ED leadership contact.
- **Change control:** How scope changes will be approved (especially if integration approval delays occur).
