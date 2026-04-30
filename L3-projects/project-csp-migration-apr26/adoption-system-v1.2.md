# L1 CANDIDATE — CSP App Adoption System v1.2 (FINAL LOCK)

**Status**: Pending human promotion to `L1-global/adoption-system.md`.
Agents cannot write to L1 directly. This file is staged here for human review.

**Source**: Shared by Shiva 2026-04-28. Original docx:
`CSP_App_Adoption_System_v1_2 (3).docx`. Covers Adoption Canvas v1.2,
UX Layer v1.1, Event Triggers v1.0, Lifecycle Canvas v1.0.

**Why L1**: Cross-project. Hard locks the philosophy ("system change is
a behaviour problem, not a knowledge gap"), the three-phase model
(Belief Reset → Immediate Proof → Event-Driven Reinforcement), and
the six locked event types. Any comm produced by this system must respect
these constraints. Belongs alongside `pca-content-governance.md`,
`comms-principles.md`, `push-to-pull-rules.md`.

**Implication for comms design**:
- Bonus loss / carry fee / routing drop / etc. → in-app full-screen
  interrupts at the moment of state change, **not pre-emptive WhatsApp**
  warnings.
- Past tense only. No reversibility implied. No "you can avoid this"
  framing. No countdown timers. No urgency language.
- Cold by design. Warmth signals old relationship model still applies.
  It does not.
- WhatsApp/SMS for state-change events should be *delivery bridges*
  back to the in-app surface, not standalone narratives.

---

## Founder note

> This system is cold on purpose. Warmth would signal the old
> relationship model still applies — it does not. If any part of this
> requires explanation, repetition, or human clarification, the system
> design has failed. That is the bar. Any team member can raise a violation.

## In 60 seconds

- **System change is a behaviour problem, not a knowledge gap.** CSPs
  interpret new systems through old mental models — leading to wrong
  decisions, hesitation, distrust.
- **Objective is action correctness, not comprehension.** Eliminate the
  need for interpretation. State + next action must be self-evident at
  every step.
- **Three-phase adoption**: Belief Reset → Immediate Proof →
  Event-Driven Reinforcement. Each phase has locked purpose, form, and
  rules. No training, no tutorials, no comfort-building.
- **Six reinforcement events**: Install Failure, Complaint Delay, Bonus
  Loss, Carry Fee, Routing Drop, Cap Contraction. Fire only on real
  system triggers. First-occurrence logic is critical; anti-spam
  cooldowns are mandatory.
- **UX architecture** = Home action feed + Task detail. One CTA per
  surface. No dead ends. Consequence timing must be visible before
  action. Server decides priority, not the CSP.
- **Cold by design.** Warmth would signal the old relationship model
  still applies. It does not. Any need for explanation = system failure.

## Objective (LOCKED)

**Eliminate the need for CSP interpretation by making system state and
next action self-evident at every step.**

Operational translation:
- Correct action > understanding
- State clarity > memory
- System guidance > human judgment
- Behaviour inevitability > education

Non-objectives (FORBIDDEN):
- Teaching app navigation
- Explaining policies in isolation
- Increasing CSP comfort or satisfaction
- Training or tutorials

## Critical actions CSP must not get wrong

- Accept / ignore connection request
- Complete install within TAT
- Respond to complaint within SLA
- Manage NetBox custody correctly
- Handle recharge state correctly

## Belief layer

Old beliefs to break:
- "Main decide karta hoon kaunsa kaam lena hai"
- "Reject karne se farq nahi padta"
- "Rule negotiate ho sakta hai"
- "Bonus = mehnat"
- "Manager solve karega"

## Three-phase adoption system

### Phase 1 — Belief Reset (first session only)

**Purpose**: Create a crack in the old mental model (not conversion).

**Form**: Single screen. No scroll. No walkthrough. No tutorial.

**Content (LOCKED)**:
> "Wiom system mein kaam ek hi cheez se chalta hai —
> aapke service outcomes.
> Routing, bonus, aur growth — sab system state se decide hota hai.
> Har cheez app mein dikhegi."

Rules: No emotional framing. No loss framing. No persuasion. Must end
with visibility assurance.

Output: CSP is disoriented from old model. Not yet convinced.

### Phase 2 — Immediate Proof

**Purpose**: Show the new contract is real, using *actual live system state*.

Strict constraints: No simulation. No demo data. No illustrative
explanation. No teaching UI. Show only if exists: actual routing state,
SLA / quality state, bonus / payout state, NetBox / carry state.

If no live state exists: Phase 2 remains dormant. Only Phase 1 runs.
Proof is deferred to first real event.

### Phase 3 — Event-Driven Reinforcement

**Core principle**: Events do not warn. Events record. Actions only move forward.

**Event structure (NON-NEGOTIABLE)**:
- Impact must be **past tense**
- No reversibility implied
- No "you can avoid this" framing

## The six events (FINAL COPY LOCK)

### Event 1 — Install Failure (Task-bound)
> Install Not Completed
> Time window ended.
> This install is counted as delayed in your SLA record.
> [Complete Install Now]

### Event 2 — Complaint Delay (Task-bound)
> Complaint Not Responded
> Response time exceeded threshold.
> This complaint is counted as delayed in your SLA record.
> [Respond Now]

### Event 3 — Bonus Loss (Full-screen interrupt)
> Bonus Paused
> Current SLA state: At Risk.
> Bonus eligibility is already paused.
> [See What To Fix]

### Event 4 — Carry Fee (Full-screen interrupt)
> NetBox Idle
> Device inactive for 16 days.
> ₹2 per day — deducting while idle.
> [Return Device]

### Event 5 — Routing Drop (Full-screen interrupt)
> Routing Reduced
> Current SLA state: At Risk.
> Routing has already adjusted based on this state.
> [See What To Fix]

### Event 6 — Cap Contraction (Inline, feed only)
> Exposure Reduced
> Recent performance below threshold.
> Exposure has already been reduced.
> [Improve Quality]

## Action forcing mechanisms

1. **Single CTA dominance** — one dominant CTA per surface
2. **CTA proximity** — action immediately follows problem
3. **No dead ends** — every screen leads to action or fix
4. **Consequence timing visibility** — show deadline, not countdown
   ("Window closes at 6 PM" not "2h 14m left"). No countdown timers.
   No urgency language. No emotional pressure.

## System principles (LOCKED)

1. **No memory dependency** — nothing must be remembered
2. **No interpretation layer**
3. **Action clarity < 2 seconds** — immediate decision
4. **Consequence visibility** — every outcome must feel inevitable
5. **No human override for non-discretionary decisions** — no escalation
   for routing, bonus, carry fee, cap. Human paths only for infra
   issues, system defects, explicit review states.

## Copy discipline (LOCKED)

All copy must be:
- factual
- impersonal
- system-led

Economic copy must describe **mechanism, not status**.

## What this system is NOT

- Onboarding
- Training
- Help system
- Education flow

## Final anchor (LOCKED)

> Old behaviour must become impossible. Correct behaviour must feel inevitable.

## Lifecycle Canvas — duration locks

| Component | Duration | Reset logic |
|---|---|---|
| Phase 1 — Belief Reset screen | Once per CSP | Only shown again if explicit reset condition is met |
| Phase 2 — Immediate Proof | First session only, if live state exists | If no live state exists, remains dormant until first real state |
| Full-screen Event: Install Failure | Once per CSP for belief-breaking interrupt | Later failures appear only task-bound |
| Full-screen Event: Complaint Delay | Once per CSP for belief-breaking interrupt | Later delays appear only task-bound |
| Full-screen Event: Bonus Loss | Once per CSP | Later changes shown inline / drilldown |
| Full-screen Event: Carry Fee | Once per CSP | Later fee state shown inline / wallet / asset surfaces |
| Full-screen Event: Routing Drop | Once per CSP | Later routing changes shown inline / drilldown |
| Cap Contraction Event | Ongoing, inline only | No full-screen repeat |
| Task-bound correction UX | Per occurrence | Repeats as long as the task type recurs |
| Action Feed | Forever | Permanent |
| State Drilldown | Forever | Permanent |
| Deadline Visibility | Forever | Permanent |
| Event Trigger System | Forever | Permanent |

## Reset conditions (when belief-break can re-fire)

Allowed reset triggers:
- Long inactivity (CSP returns after long absence — system memory likely degraded)
- Major model change (foundational contract change, not small UI/rule update)
- Role migration / identity migration (legacy LCO → CSP, etc.)
- New app generation with changed control logic (not visual refresh)
- Account recreation after formal exit and re-entry

Not allowed: app reinstall, device change, cache clear, normal updates,
one missed month, small policy edits, cosmetic redesigns.

## Failure conditions (UX)

UX fails if:
- CSP asks "kya karna hai?"
- CSP ignores tasks due to confusion
- CSP calls support for routing/bonus
- CSP delays action due to interpretation

## Final UX anchor (LOCKED)

> Every screen = one decision.
> Every decision = one action.
> Every action = visible consequence.

## Final system lock

> If an event sounds like a warning, it is wrong.
> If it sounds like a record, it is correct.

---

*Source: CSP App Adoption System Canvas v1.2 + UX Layer v1.1 + Event
Triggers v1.0 + Lifecycle Canvas v1.0. Filed in review-queue/adhoc
2026-04-28. To be promoted to L1-global/adoption-system.md by human.*
