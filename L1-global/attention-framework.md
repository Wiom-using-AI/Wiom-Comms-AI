# L1 — Unified Attention Framework v1.3

> **⚠️ AGENT-AUTHORED L1 — EXPLICIT HUMAN OVERRIDE**
>
> CLAUDE.md rule: *"L0 and L1 files → human only, never agent."*
>
> This file was authored by an agent (Claude Code session) on
> 2026-04-28, staged in `review-queue/adhoc/`, and promoted directly
> to L1 on 2026-04-30 under explicit instruction from Shiva — who
> waived the rule because the framework is genuinely cross-project
> and was already being treated as authoritative in design decisions.
>
> **Karishni — please review when you next access the repo.**
> If placement, scope, or content needs adjustment, the file can be
> moved/edited freely. The override is documented in:
> - this banner
> - `system/GAPS.md` (RESOLVED entry, 2026-04-30)
> - the commit message that introduced this file

**Source**: Shared by Shiva 2026-04-28. Original docx:
`Unified_Attention_Framework_v1_1.md (1).docx` (note: filename says v1_1
but document body says v1.3 — content is v1.3).

**Why L1**: Cross-project. Governs how every CSP-facing surface (notifications,
banners, badges, feed items, bell entries) requests attention. Not specific
to any single project. Belongs alongside `system-architecture.md`,
`comms-principles.md`, `channel-specs.md`.

**Implication for comms design**: Any in-app comm must select its surface
(Home feed / Bell / Banner / Owning surface) and intensity (Level 1/2/3,
Level 3 gated) per this framework. WhatsApp / SMS / push are *delivery
bridges*, not independent surfaces. Belief-break events use mandatory
inline quiz — once, never again.

---

## Core principle

**One attention system. Multiple surfaces.**

Every attention item — regardless of source — passes through the same
classification, priority, and surface selection rules.

- **Three lifetime classes**: Belief break (once, with verification quiz),
  Task correction (repeatable in task context), Permanent guidance
  (visible while true).
- **Two primary surfaces**: Home feed = doing. Bell = noticing and
  routing. Notifications are delivery bridges, not a third surface.
- **No duplication across surfaces**: each attention item has ONE
  owning surface. All others link to it.
- **No system internals exposed**: attention items show consequence,
  not mechanics.

## Owning surface tie-break (when multiple domains touch)

1. If item requires immediate execution on a task → task surface owns it.
2. Else if item is a governed state → its program/module surface owns it.
3. Bell may route but never own.

Example: CI activation affects quality + earnings + routing. CI is a
governed program state → CI surface owns. Quality links. Earnings links.
Bell does not own (CI has its own banner).

## Source classes

| # | Source | Covers | Example |
|---|---|---|---|
| 1 | TASK_EVENT | Task changed in a way that may affect action | New install, slot accepted, customer rescheduled |
| 2 | SYSTEM_STATE | System state changed and CSP should know | Quality at risk, payout frozen, carry fee started |
| 3 | HUMAN_CONVERSATION | Wiom message that materially changes action/constraint/operating context | Ops msg about specific task, policy clarification |
| 4 | PROGRAM_STATE | Governed system program became active or changed | CI active, CI recovery confirmed |
| 5 | REFERENCE_CHANGE | Policy or account info changed and CSP should see it | Policy update, payout rule change |

## Lifetime classes

### A. Belief Break (once, with verification quiz)
Used to break an old mental model the first time it happens.

Lifecycle:
1. Event fires with `is_first_occurrence = true`
2. **INFORM** — one-time screen explaining what changed, why, consequence
3. CSP taps [ठीक है]
4. **VERIFY** — quiz appears INLINE (same flow, next screen, mandatory)
5. CSP answers. Wrong → correction shown with correct answer. Right → complete.
6. Never shown again for this event type for this CSP.

Rules: one-time per event type per CSP. `is_first_occurrence` must be in
the event payload from backend — client never tracks this. No skip. No
bell fallback. Inform + quiz = one atomic moment. 5 seconds total.

### B. Task Correction (repeatable in context)
Used when an execution error or state issue recurs on a task. May repeat
per task / per occurrence. Must stay in task context. Must not become
a recurring global interrupt after first belief-break.

### C. Permanent Guidance (continuous)
State truths that must remain visible while true. Examples: Quality
state (Assurance Strip), Carry fee ongoing (NetBox), CI active (Home
banner + CI surface), Bonus state (Earnings), Wallet state (Wallet
banner). Visible while true. No one-time logic. No educational framing.
Part of the product, not onboarding. Disappears when state ends — no
"completed" celebration.

## v1 belief-break events (LOCKED LIST)

Five rules, five questions, all proactive (fire BEFORE the consequence).
Belief break teaches the rule. The first real consequence ("first bonus = 0",
"first routing drop") is a *proof moment*, not a belief break — it is a
highlighted feed entry confirming the rule, no quiz.

| # | Belief | Old model | New model | Quiz | Correct answer | Fires when |
|---|---|---|---|---|---|---|
| 1 | Idle NetBox = daily cost | Idle device has no cost | Unused asset = daily loss until installed | "कैरी शुल्क कब रुकेगा?" | "जब NetBox इंस्टॉल हो जाएगा" | First NetBox assigned |
| 2 | Withdrawals are governed | My money, I take whenever | 2 times/week, governed days | "पैसे कब निकाल सकते हैं?" | "हफ़्ते में 2 बार, तय दिनों पर" | First earnings credited |
| 3 | Recharge earns ₹300 | Unclear payout model | Direct: recharge → ₹300 | "रिचार्ज होने पर कितना मिलेगा?" | "₹300 हर रिचार्ज पर" | First connection activated |
| 4 | NetBox pickup earns ₹50 | Pickup is unpaid chore | Pickup is compensated | "पिकअप करने पर कितना मिलेगा?" | "₹50 हर पिकअप पर" | First pickup task assigned |
| 5 | Quality governs bonus + routing | Bonus is fuzzy, work comes regardless | Quality directly changes money and future work | "Quality का बोनस और काम पर क्या असर है?" | "अच्छी quality = ज़्यादा बोनस + ज़्यादा काम" | Onboarding or first quality evaluation |

## Quiz constraints

| Constraint | Rule |
|---|---|
| When | Only on belief-break events. Never on task corrections or permanent guidance. |
| Frequency | Once per event type per CSP. Forever. No repetition. |
| Length | One question. Not two. Not three. |
| Delivery | Inline — immediately after inform dismiss. Mandatory. No skip. |
| Format | Binary or single-select (2-3 options). Never free text. Never multi-step. |
| Scoring | No scores. No streaks. No gamification. Right = done. Wrong = re-inform once. |

## Attention channels

- **Home Feed** = execution attention. For doing. If CSP can act on it as work right now → Home feed.
- **Bell** = cross-surface attention inbox. For noticing and routing, not duplicating full content. Every bell item must deep-link to its owning surface.
- **Push / Notification** = delivery bridge. Not a third logic layer. Same identity line, same latest attention line, compact form, tap → exact owning surface via deep-link.

## Notification intensity ladder

- **Level 1** — Feed only. No push, no sound, no haptic. Passive updates, ongoing states.
- **Level 2** — Push / silent or light haptic. Normal new task, slot accepted, reschedule, reminder, belief-break inform + quiz delivery.
- **Level 3** — Strong attention (heads-up + sound + vibration). **GATED — not active in v1.** Reserved for dispatch-mode tasks. Activation requires deliberate product decision.

## Bell admission rules (HUMAN_CONVERSATION)

Human messages may enter the bell **only if they materially change action,
consequence, or operating context.**

Test: "Does this message change what the CSP does, what consequence
they face, or what they need to know to operate?" If no → do not create
a bell item.

| Enters bell | Does NOT enter bell |
|---|---|
| "आपका payout KYC issue से रुका है" | "Hi, hope you're doing well" |
| "NB-4821 का customer cancel कर रहा है" | "Monthly update: everything looks good" |
| "नई policy: carry fee rate change" | Generic motivational messages |
| Task-specific instruction that changes action | Status confirmations with no new information |

## What the system must NEVER do

- Never let the client decide event truth
- Never let Firebase or notification transport define policy
- Never make bell a second work queue
- Never duplicate the same explanation across multiple surfaces
- Never use sound/haptic for everything (Level 3 gated)
- Never repeat first-time belief-break interrupts forever
- Never expose internal mechanics CSPs can optimize against
- Never create two separate attention systems for system events and human messages
- Never let quiz become training, gamification, or recurring assessment
- Never make belief-break quiz skippable — one question, mandatory, 5 seconds
- Never admit human messages to bell without the material-change test

## Final lock

**One attention system. One source of truth.** Home feed is for doing.
Bell is for noticing and routing. Notifications are only delivery
bridges. Belief breaks once. Mandatory verification confirms. Behavior
is shaped forever.

---

*Source: Unified Attention Framework v1.3. Filed in review-queue/adhoc
2026-04-28. To be promoted to L1-global/attention-framework.md by human.*
