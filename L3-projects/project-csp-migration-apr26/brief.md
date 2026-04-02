# Project Brief — project-csp-migration-apr26

## FILE PURPOSE
Primary context for the design agent for all tasks on this project.
Contains the project objective, audience, constraints, comms plan,
and success metrics. Read this before designing any comm.

## WHEN TO USE
Loaded by the orchestrator for every task on this project.
Read in full before starting any design task.

## HOW TO USE THIS FILE
- Read the Objective and Core Risk before drafting any message
- Read the Comms Plan section to understand what has been planned
  and where each message sits in the sequence
- Cross-reference comms-log.md to see what has actually been sent
- Never design a message that contradicts the design principles below
- Never reference a hard app launch date — use "launch hone wala hai"

## LAST UPDATED
2026-03-27 — initial version. Plan stage. No messages sent yet.
Maintained by: human

---

## Objective

Migrate ~1,200 CSPs (Channel Service Partners) from legacy partner
contract to new system-governed operating model by end of April 2026.

By month-end, every partner must:
- Understand what changed: earning structure, work allocation,
  PayG model, and new app interface
- Know how to earn: rate card, bonus tiers, quality score
- Be on the new app and using it daily for tickets and self-serve
- Trust the system: no surprises, every number explained before it appears

---

## The Core Risk

The risk is NOT partner resistance. The risk is that partners open
the new app without any mental model of what has changed, see things
they don't recognise, and either flood the PTL with calls or
disengage entirely.

Every comm in this project exists to prevent that.

---

## What Is Changing (Three Simultaneous Shifts)

**Earning structure**
Bonus was split across device recovery, SLA, and customer rating.
Now: single monthly performance bonus.
Rate: ₹300 per connection (permanent). Bonus: up to ₹120 per month.
NetBox collection: ₹50 per device. Carry fee: ₹2/day per idle device
(15+ days with no active connection).

**Work allocation**
No fixed area, no guaranteed work. System assigns work based on
performance — better performance = more work.

**Interface + PayG**
Old app replaced by new app. Customers now take PayG plans.
New app is the single source of truth for state, earnings, devices,
tickets, and next actions.

---

## Audience

  Segment        : Active CSPs (Channel Service Partners)
  Size           : ~1,200 partners
  Geography      : Delhi NCR, Bharat tier-2, Mumbai
                   Delhi and Bharat/Mumbai may need separate content
                   where earning or operating context differs
  Language       : Hindi-primary. Hinglish acceptable for nudges.
                   English only for system labels and app UI terms.
  Status         : Active CSPs transitioning to new operating model
  Behavioural    : Primary app motivation is work (tickets and
  signals          installation requests) — not earnings or education.
                   Education must sit alongside the work workflow,
                   not compete with it.

---

## OS Triggers

This project spans multiple OS systems simultaneously:

  onboarding        : new app, Day 1/3/7 activation sequences,
                      first experience with new system
  compensation      : bonus structure, rate card, carry fee,
                      payout breakdown, wallet
  quality           : quality score, SLA, at-risk, performance
                      measurement, bonus eligibility
  enforcement       : protection period close-out, enforcement
                      start (May 1), compliance consequences

When designing any message, check which OS is active for that message
and load the corresponding playbook.

---

## Channels

  Primary     : WhatsApp (nudges, announcements, trigger-based)
  Secondary   : SMS (cascade fallback for unread WhatsApp, 24hrs)
  In-app      : Dashboard cards, banners, push notifications
                (requires product to build the screen first)
  Old app     : Video + quiz hosting pre-launch only (Apr 4–5)
                Old app blocked from launch day (~Apr 7)

Channel selection per message is specified in the Comms Plan below.

---

## Design Principles

These apply to every message in this project. Non-negotiable.

  1. Intent-driven, not calendar-driven
     Post-launch comms fire on triggers. No message goes out
     without a trigger condition. WA is the nudge — app/video/quiz
     carries the education weight.

  2. No hard dates in pre-launch
     App launch date is not locked. Use "launch hone wala hai".
     Reinstate date in M3 and D0 only if date locks officially.

  3. Policy before data
     Declare rules (carry fee, enforcement) before surfacing
     individual partner data. Partner must know the rule before
     seeing their own numbers.

  4. Bonus consequence delayed
     M1 (telemetry ask) deliberately excludes bonus consequence.
     This connects only at Day 3–5 post-launch when partner has
     context from the rate card.

  5. Progressive disclosure
     Do not information-dump. Each message has one job.
     Rate card surfaces as expandable card — not full-screen on open.
     Device alerts only show if partner has idle devices.

  6. Permanent home for all content
     Every temporary card or nudge must reference Wiom Paathshala
     (Settings > Help in new app) as the permanent location.
     "Yeh information kabhi bhi dekhne ke liye: Settings > Wiom Paathshala"

  7. No field support or BDO teams
     All comms must work without human mediation. Every message
     must be self-contained — partner should not need to call
     anyone to understand it.

---

## Comms Plan — 13 Messages

This is the full sequenced plan. Use this as the reference when
designing individual messages. Cross-reference comms-log.md to
see which messages have been sent and what the initial results were.

### PRE-LAUNCH (Mar 31 – Apr 6)

M1 — PNM Alert: Telemetry Device Installation
  Planned date   : Mar 31
  Channel        : WhatsApp + Call follow-up (SMS cascade at 24hrs)
  OS trigger     : quality (telemetry = prerequisite for bonus eligibility)
  Trigger        : All CSPs with telemetry status = Pending
  Intent         : Get partner to allow technician visit. Operational
                   ask — confirm a slot.
  Design note    : Bonus consequence deliberately excluded.
                   Connected at M8 (Day 3–5 post-launch).
  Status         : PLANNED — not sent

M2b — Carry Fee Declaration (₹2/day)
  Planned date   : Apr 1
  Channel        : WhatsApp only
  OS trigger     : compensation
  Trigger        : All active CSPs
  Intent         : Declare carry fee policy before app goes live.
                   No action needed — partner just knows this exists.
                   Individual device counts surface only in app.
  Wiom Paathshala: Carry fee policy → Device Management section
  Status         : PLANNED — not sent

M3 — Protection Confirmation
  Planned date   : Apr 2
  Channel        : WhatsApp only
  OS trigger     : onboarding
  Trigger        : All active CSPs
  Intent         : Reassure partner they will have time to adjust.
                   No surprises on day one. Psychological safety
                   net before launch.
  Design note    : "Launch hone wala hai" — no hard date.
  Status         : PLANNED — not sent

M4 — System Reboot + PayG: Video + Quiz Module
  Planned date   : Apr 4–5
  Channel        : WhatsApp + SMS + Old App (content host)
  OS trigger     : onboarding + compensation
  Trigger        : All active CSPs
  Intent         : Single most important pre-launch education moment.
                   Partner must understand earning changes and PayG
                   BEFORE opening the new app.
  Format         : 2–3 min explainer video + quiz gate (must complete
                   quiz to confirm comprehension, not just views)
  Hosted         : Old app (pre-launch). Moves to Wiom Paathshala
                   after launch.
  Product dep    : Video must be produced. Quiz must be built.
  Status         : PLANNED — not sent

### LAUNCH DAY (~Apr 7)

M5 — App Download / Update Instructions
  Planned date   : ~Apr 7 (morning)
  Channel        : WhatsApp + SMS + Old App redirect
  OS trigger     : onboarding
  Trigger        : All active CSPs
  Intent         : Get new app on partner's phone.
                   One link, crystal clear instruction.
  Open question  : New download or update? Confirm with product.
                   Content placeholder covers both options.
  Status         : PLANNED — not sent

M6 — D0: App is Live, Your State is Ready
  Planned date   : ~Apr 7
  Channel        : WhatsApp + Old App (now blocked)
  OS trigger     : onboarding
  Trigger        : App goes live
  Intent         : Get partner to open new app and see their state.
                   Old app blocked from this point — redirect screen
                   shows on any partner who opens old app.
  App screen dep : Dashboard with pending tickets, ₹300 rate,
                   Trust Line number
  Status         : PLANNED — not sent

M7 — Launch Day App: Dashboard + Earning + Devices
  Planned date   : ~Apr 7 (in-app, on open)
  Channel        : New App (progressive dashboard cards)
  OS trigger     : onboarding + compensation
  Trigger        : Partner opens new app for first time
  Intent         : Work queue (tickets) is primary view. Earning
                   and device info surfaces as secondary cards.
                   Rate card: expandable, 7-day sticky, not dismissable.
                   Device alert: only if partner has idle devices.
  App screen dep : Dashboard with tickets, earnings summary card,
                   device alert card, rate card (expandable)
  Status         : PLANNED — not sent

### POST-LAUNCH (Day 3 – Month End)

M8 — Telemetry Nudge: Bonus Consequence Stated
  Planned date   : Day 3–5 post-launch
  Channel        : WhatsApp
  OS trigger     : quality + compensation
  Trigger        : Partners with telemetry status = Pending
                   (not blasted to all — only pending partners)
  Intent         : Connect telemetry installation to bonus eligibility.
                   Partner now knows bonus structure — right moment
                   to state the consequence.
  App screen dep : Telemetry status: Pending / Scheduled / Installed
  Status         : PLANNED — not sent

M9 — Bonus Cycle Nudge: Check Quality Score
  Planned date   : Day 7–10 post-launch
  Channel        : WhatsApp + In-App Banner + Push
  OS trigger     : quality + compensation
  Trigger        : First bonus cycle active
  Intent         : Make partner aware they are being measured.
                   Create urgency to check quality score while
                   there is time to improve.
  App screen dep : Quality score screen MUST be live before this
                   goes out. Hard blocker.
  Status         : PLANNED — not sent

M10 — Protection Close-out: Enforcement Starts May 1
  Planned date   : Day 14 post-launch
  Channel        : WhatsApp + App Card
  OS trigger     : enforcement
  Trigger        : Day 14 after launch
  Intent         : Close the M3 promise. Partners were told they'd
                   have time — this tells them exactly when protection
                   ends. Clear before/after line at May 1.
  App screen dep : Compliance status card: protection active,
                   enforcement date May 1
  Status         : PLANNED — not sent

M11 — Pre-Bonus Nudge: Cycle Closing
  Planned date   : Day 25–27 post-launch
  Channel        : WhatsApp + Push
  OS trigger     : compensation + quality
  Trigger        : Bonus cycle closing window
  Intent         : Partner must have context BEFORE seeing the
                   bonus amount. Last chance to fix issues.
                   Most important post-launch message.
  App screen dep : Month summary: performance, projected bonus,
                   disqualifying flags. Hard blocker — must be live.
  Status         : PLANNED — not sent

M12 — Bonus Credited: Full Itemised Breakdown
  Planned date   : May 1+
  Channel        : App + Push
  OS trigger     : compensation
  Trigger        : System event — bonus calculation complete
  Intent         : Every rupee accounted for. Full line-item breakdown.
                   If bonus not paid, reason shown explicitly.
                   Prevents "why less" PTL calls.
  App screen dep : Full payout breakdown — every line itemised.
                   Non-negotiable.
  Status         : PLANNED — not sent

M13 — Performance Tips: Contextual Education
  Planned date   : Ongoing — trigger-based
  Channel        : In-App Contextual
  OS trigger     : quality
  Trigger        : Score drops / Post-bonus / Before enforcement /
                   First week active (if quiz completed)
  Intent         : Educate on what helps/hurts score — only when
                   partner needs it. Without a trigger, no impact.
  Wiom Paathshala: Full DOs/DON'Ts and improvement guides
  Status         : PLANNED — not sent

---

## Product Dependencies

These screens must be live before the corresponding message goes out.
The design agent must flag if a message is being designed before
its dependency is confirmed.

  Dashboard with tickets (Launch Day)
    → Required for M6. Without it D0 message has nowhere to land.

  Telemetry status card (Day 3–5)
    → Required for M8. Partners cannot verify installation status.

  Quality score screen (Day 7–10)
    → HARD BLOCKER for M9. Message cannot go out without it.

  Month summary screen (Day 25–27)
    → HARD BLOCKER for M11. Partners see bonus without context
      if this is not live — PTL spike guaranteed.

  Payout breakdown screen (May 1+)
    → Required for M12. Lump sum without breakdown = immediate PTL calls.

  Contextual tips engine
    → Required for M13. Education has no delivery mechanism without it.

  Wiom Paathshala section
    → Required before launch. Partners have no way to revisit
      information after temporary cards expire.

---

## Success Metrics

  Primary metric   : PTL call volume — target: no spike at any
                     transition point (launch, bonus, enforcement)
  Secondary metrics:
    App download / update rate on launch day
    Quiz completion rate (M4) — target: >60%
    Telemetry installation confirmation rate (M1 + M8)
    Quality score screen access rate (M9) — target: >40%
    Enablement access rate within 48hrs of nudge
    Bonus breakdown screen open rate (M12)
  Measurement tool : Metabase + app analytics
  Review cadence   : After each major message send (M4, M6, M9, M11, M12)

---

## Open Items (Must Resolve Before Execution)

  App launch date
    Target ~Apr 7. Once confirmed: reinstate in M3 and M6.

  App download flow
    New download or update? Determines instruction in M5.
    Confirm with product.

  System Reboot video
    2–3 min explainer — system changes + PayG together.
    Hosted on old app pre-launch, moves to Wiom Paathshala after.
    Must be produced before M4 can go out.

  Quiz module
    Same format as earlier PayG quiz. Build content for merged
    system + PayG education. Required for M4.

  Quality score screen
    Must be live before M9. Avoid "rating" — use "quality score".

  Projected bonus screen
    Must be live before M11. Non-negotiable.

  Contextual tips engine
    Can product build state-triggered in-app cards?
    Required for M13.

---

## Related Projects
None at this time.

## Stakeholders
  Owner          : Shiva (Karishni)
  Comms design   : Wiom Comms AI (this system)
  Product dep    : Engineering / Product team (screen dependencies above)

## Notes
This brief was created at the plan stage — no messages have been sent.
The design agent should use this brief to design individual messages
when triggered. For each message: read the Comms Plan entry for that
message, check comms-log.md for what has already gone out, check the
product dependency for that message, then design.
