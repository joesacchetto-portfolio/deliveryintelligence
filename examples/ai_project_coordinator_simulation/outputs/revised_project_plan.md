# Revised Project Plan (Milestone-Based) — VoiceRx Cloud Implementation (Northgate)

**Revision reason:** Epic integration approval timeline slip (+3 weeks). Integration sign-off moves from **2026-03-30** to approximately **2026-04-20**.

**Contract signed:** 2026-02-15
**Original target go-live:** 2026-05-01 (**NOW AT RISK**)

**Important:** This plan revision only reflects the confirmed integration slip. Other change events (champion loss, scope expansion request) are tracked as **OPEN** risks/decisions and are not assumed as resolved.

---

## Key schedule callouts
- **Integration sign-off ~2026-04-20 leaves ~11 calendar days to go-live (2026-05-01).**
- With UAT, training readiness gates, and cutover planning still required, **go-live is at risk unless scope/timeline decisions are made**.
- **Decision needed (OPEN):** confirm go-live strategy (move date vs phase scope vs other) given new integration timing.

---

## Phase 0 — Mobilize (Post-signature / pre-kickoff)
| Milestone | Target date | Owner (placeholder) | Status |
|---|---:|---|---|
| Confirm internal resourcing (SE, Training Lead, EMR Integration Specialist) | 2026-02-20 | Vendor PM / Delivery Leadership | **OPEN** |
| Internal alignment call (roles, timeline reality check, risks) | 2026-02-21 | Vendor PM | **OPEN** |
| Draft client kickoff deck + project plan v0.1 | 2026-02-24 | Vendor PM + SE (TBD) | **OPEN** |
| Prepare discovery question set + intake checklist (Epic/FHIR, stakeholders, training) | 2026-02-24 | Vendor PM + Integration Spec (TBD) + Training Lead (TBD) | **OPEN** |

## Phase 1 — Discovery & Scope Baseline
| Milestone | Target date | Owner (placeholder) | Status |
|---|---:|---|---|
| Customer discovery call (CMO + IT lead) | 2026-02-27 | Vendor PM | **OPEN** |
| Formal kickoff meeting | 2026-03-02 | Vendor PM + Northgate IT Lead | **OPEN** |
| Confirm stakeholder map (campus leads, ED leadership, Epic approvers) | 2026-03-04 | Vendor PM + Northgate IT Lead | **OPEN** |
| Confirm scope baseline + assumptions + out-of-scope reminders | 2026-03-06 | Vendor PM | **OPEN** |
| Confirm go-live approach (phased vs single date) | 2026-03-06 | Northgate CMO + IT Lead + Vendor PM | **OPEN** |

## Phase 2 — Solution Design / Configuration Planning (can proceed in parallel)
| Milestone | Target date | Owner (placeholder) | Status |
|---|---:|---|---|
| Workflow discovery by specialty (Primary Care / Cardiology / ED) | 2026-03-10 | Vendor SE (TBD) + Northgate champions (OPEN) | **OPEN** |
| Configuration requirements documented (inputs/decisions needed) | 2026-03-12 | Vendor SE (TBD) | **OPEN** |
| Training approach draft (audiences, format, completion criteria) | 2026-03-13 | Vendor Training Lead (TBD) | **OPEN** |

## Phase 3 — Epic Integration (HL7 FHIR API) — UPDATED DATES
| Milestone | Target date | Owner (placeholder) | Status |
|---|---:|---|---|
| Define Epic integration approval steps, owners, and lead times | 2026-03-06 | Northgate IT Lead + Epic IT Approver (OPEN) + Vendor Integration Spec (TBD) | **OPEN** |
| Submit integration approval request package (if required) | 2026-03-09 | Northgate IT Lead (primary) + Vendor Integration Spec (TBD) | **OPEN** |
| Confirm environments/access (test/prod), change windows | 2026-03-11 | Northgate IT Lead + Vendor Integration Spec (TBD) | **OPEN** |
| Integration build/config complete (vendor side) | 2026-03-20 | Vendor Integration Spec (TBD) | **OPEN** |
| Integration testing window (end-to-end) | 2026-04-13 to 2026-04-17 | Vendor Integration Spec (TBD) + Northgate IT | **OPEN** |
| **Integration sign-off (shifted)** | **~2026-04-20** | Northgate IT Lead + Vendor PM | **OPEN** |

## Phase 4 — Training Prep & Delivery (some work can proceed; final validation depends on integration)
| Milestone | Target date | Owner (placeholder) | Status |
|---|---:|---|---|
| Confirm training roster (85 physicians + admin + IT) and scheduling constraints | 2026-03-13 | Northgate IT Lead + Department leadership (OPEN) | **OPEN** |
| Finalize training materials/runbooks (role-based) | 2026-03-20 | Vendor Training Lead (TBD) | **OPEN** |
| Begin training delivery (IT/admin first) | 2026-03-23 | Vendor Training Lead (TBD) + Northgate IT | **OPEN** |
| Begin physician training delivery (multiple sessions; ED requires special scheduling) | 2026-03-30 | Vendor Training Lead (TBD) + Northgate physician champions (OPEN) | **OPEN** |
| Training completion checkpoint #1 (readiness review) | 2026-04-10 | Vendor PM + Training Lead (TBD) + Northgate sponsors | **OPEN** |
| Training completion checkpoint #2 (final readiness review) | 2026-04-24 | Vendor PM + Training Lead (TBD) + Northgate sponsors | **OPEN** |

## Phase 5 — UAT / Go-Live Readiness — AT RISK / RE-PLAN REQUIRED
| Milestone | Target date | Owner (placeholder) | Status | Notes |
|---|---:|---|---|---|
| Define go-live readiness criteria (go/no-go checklist) | 2026-03-13 | Vendor PM + Northgate IT Lead + Training Lead (TBD) | **OPEN** | Criteria must reflect new integration timing |
| **UAT / validation window (needs adjustment)** | **OPEN** | Northgate champions (OPEN) + Vendor SE (TBD) | **OPEN** | Original window 2026-04-06 to 2026-04-17 conflicts with new integration testing/sign-off |
| Go-live cutover plan + support model finalized | 2026-04-27 | Vendor PM + Northgate IT Lead | **OPEN** | Shifted later; depends on decisions |
| Final go/no-go meeting | 2026-04-29 | Northgate CMO + IT Lead + Vendor PM | **OPEN** | Feasible only if readiness criteria can be met |

## Phase 6 — Go-Live + Hypercare
| Milestone | Target date | Owner (placeholder) | Status | Notes |
|---|---:|---|---|---|
| **Go-live** | **2026-05-01 (AT RISK)** | Vendor PM + Northgate IT Lead | **OPEN** | Decision needed (OPEN) to confirm feasibility |
| Hypercare period (30 days) | 2026-05-01 to 2026-05-31 | Vendor PM + Support/Training (TBD) + Northgate IT | **OPEN** | Scope and staffing may change based on decisions |
| Legacy Olympus decommission date confirmed (separate decision) | **OPEN** | Northgate sponsor/IT (OPEN) | **OPEN** | Still unresolved |

---

## Decisions needed to resolve schedule risk (all OPEN)
1. **OPEN:** Confirm go-live strategy given integration sign-off ~2026-04-20:
   - Move go-live date, OR
   - Phase rollout scope, OR
   - Other agreed approach.
2. **OPEN:** Confirm updated UAT plan and dates that meet entry/exit criteria.
3. **OPEN:** Confirm whether any part of UAT/training can proceed safely before final integration sign-off (requires IT confirmation).
