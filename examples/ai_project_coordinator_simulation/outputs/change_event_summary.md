# Change Event Summary — VoiceRx Cloud Implementation (Northgate)

**Context:** Three change events occurred simultaneously and materially affect schedule, adoption readiness, and scope. No decisions have been made yet. Items requiring a decision are flagged **OPEN**.

> **Simulation note:** These events were deliberately introduced by the PM-supervisor to test how the AI agent adapted its planning artifacts under real-world delivery disruption. See `ai_agent_supervision_report.md` for observations on agent behavior.

---

## Event 1 — Epic integration timeline slip (3 additional weeks)
**What changed (plain language):** Northgate IT reported their Epic integration approval process will take **~3 additional weeks**.

**Direct impact:**
- The planned **integration sign-off moves from 2026-03-30 to ~2026-04-20**.
- This compresses downstream testing/UAT and go-live readiness activities.

**Why this matters:**
- With go-live currently planned for **2026-05-01**, integration sign-off on ~**2026-04-20** leaves ~11 calendar days to complete remaining validation, readiness gates, and cutover prep. That is high risk and may not be feasible without changes.

**Status:** OPEN (timeline change received; mitigation decision not made)

---

## Event 2 — Physician champion lost (Cardiology)
**What changed (plain language):** Dr. James Okafor (Cardiology department head and primary physician champion) is on unexpected medical leave with no confirmed return date.

**Direct impact:**
- Loss of a key decision-maker/advocate for Cardiology workflow validation and adoption.
- Increased risk of training delays, reduced engagement, and weaker peer influence in Cardiology.

**Status:** OPEN (replacement champion not identified)

---

## Event 3 — Scope expansion request (add 4th campus ED)
**What changed (plain language):** The CMO (Dr. Patricia Howe) verbally requested adding the **Emergency Department at a fourth campus (Northgate South)** to the go-live scope.

**Direct impact:**
- This campus is **not in the original contract** and **not in the project charter scope**.
- Likely adds work across discovery, integration validation, training scheduling, cutover planning, and hypercare load.

**Status:** OPEN (request is verbal; not approved/contracted; scoping and impact assessment needed)

---

## Combined impact (all three events together)
1. **Go-live date at risk (2026-05-01):** The integration slip alone compresses remaining readiness work to a near-minimum window; adding scope and losing a champion further increases the probability of missing readiness criteria.
2. **Higher adoption risk:** Champion loss + first-time AI tool + ED scheduling complexity increases likelihood of low adoption and readiness gaps.
3. **Governance / change control needed immediately:** We need an explicit decision path on:
   - Whether to **move go-live**, **phase scope**, or **proceed with reduced/adjusted scope**.
   - Whether/how to treat **Northgate South ED** (change request vs separate phase).
   - Who will serve as **Cardiology champion** and how adoption ownership will be handled.

## Decisions needed (all OPEN)
- **OPEN:** Confirm acceptable go-live strategy given integration sign-off ~2026-04-20 (move date vs phase vs other).
- **OPEN:** Determine whether Northgate South ED is in scope for 2026-05-01 (and if not, agree on a Phase 2 date).
- **OPEN:** Identify/confirm a replacement Cardiology physician champion (and backup).
