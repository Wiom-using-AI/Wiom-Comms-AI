---
FILE PURPOSE: Push-to-Pull Rules — When Wiom Pushes Information vs When CSPs Must Pull It
HOW TO USE: Read this file when deciding whether a communication should be actively sent to a CSP (push) or whether the CSP should be directed to retrieve it themselves (pull). This file defines the transition logic, litmus tests, and circuit breakers. It works alongside comms-principles.md (which sets frequency caps) and channel-specs.md (which defines per-channel mechanics). If a state is pull-only and a task brief asks for a push notification, this file is authoritative: do not design the push.
SCOPE: All CSP-facing communication decisions — channel selection, notification design, dashboard-first logic
LAST UPDATED: March 2026
TAGS: push-to-pull, notification-threshold, pull-channel, dashboard, frequency-caps, opt-in, circuit-breaker, communication-philosophy
---

# PUSH-TO-PULL RULES
## When Wiom Pushes Information to CSPs vs When CSPs Must Pull It

---

## Core Principle

The dashboard is always on. It always reflects structural truth. Push communications — notifications, WhatsApp, SMS — are expensive in credibility, cost, and attention. They are justified only when a CSP cannot reasonably be expected to notice a state change on their own, and when that state change requires their awareness or action.

The default is pull. Push requires justification.

> *If the information is on the dashboard and no action is required — the CSP can pull it. Do not push.*

---

## §1. The Push-Pull Spectrum

Every piece of information Wiom might communicate sits on a spectrum from always-pull to always-push. The position on the spectrum is determined by two questions:

**Q1: Does the CSP need to know immediately?**
If a state change has operational consequences for the CSP right now — their routing has changed, a connection request needs action, an FPV has been triggered — they need to know immediately. Push is justified.

If the state change is visible on the dashboard and the CSP will see it when they next log in with no operational consequence to the delay — they do not need to know immediately. Pull is sufficient.

**Q2: Does the state require CSP action?**
If the CSP must do something — access enablement, confirm a scheduling request, take a process step — push is justified to ensure they receive the prompt.

If the state requires no CSP action — push is not justified. Dashboard is sufficient.

| Q1: Immediate? | Q2: Action Required? | Communication Mode |
|---|---|---|
| Yes | Yes | Push — once, with clear next action |
| Yes | No | Push — once, factual state update only |
| No | Yes | Push or WhatsApp — once, with clear next action |
| No | No | Pull only — dashboard. No push. |

---

## §2. Push-Eligible States

These state changes are eligible for a push notification or WhatsApp message. Eligibility means push is permitted — not that push is mandatory. Always confirm against comms-principles.md §2.1 (Communication Threshold Matrix) and frequency caps.

| State / Event | Push Eligibility | Reason |
|---|---|---|
| SLA: Compliant → At Risk | Yes — once | State change with available action (enablement) |
| SLA: At Risk → Non-Compliant | Yes — once | State change with mandatory action (enablement) + routing consequence |
| SLA: Non-Compliant → Recovery | Yes — once | State change — CSP should be informed |
| Connection request assigned | Yes — action required | Time-sensitive. CSP action required. |
| FPV detected | Yes — immediate | Integrity-level. Immediate notification required. |
| Rate card update | Yes — advance notice | 30-day advance notice required per PCA §12 |
| Bonus tier change | Yes — once | Material economic change. CSP informed. |
| First carry fee accrual | Yes — once | New economic event CSP may not have noticed |
| Suspension | Yes — once | Integrity-level. Immediate. |
| System update (SLA threshold change) | Yes — advance notice | 14-day advance notice required |

---

## §3. Pull-Only States

These states are dashboard-only. Push notifications, WhatsApp, or SMS for these states are a PCA violation (Principle 1: no message without structural justification; Principle 2: no persuasion or unnecessary engagement).

| State / Information | Why Pull-Only |
|---|---|
| SLA remains Compliant (no change) | No state change. No action required. Dashboard always shows this. |
| Daily connection volume fluctuations | Normal system behaviour. No action required. No threshold crossed. |
| Routine payout credited | Visible in wallet. No action required. No state change. |
| Ongoing carry fee accrual (after first notification) | Already notified on first accrual. Ongoing balance visible in wallet. |
| Routing exposure (gradual taper — no threshold event) | Gradual change. Visible on dashboard. No single threshold event triggered. |
| Bonus eligibility (unchanged) | No change to eligibility state. Visible on dashboard. |
| Historical comms log | Archive. Pull on demand. Never pushed. |
| Rate card (current version, no change) | Published and accessible. No update event. |
| General enablement resources | Available on dashboard. Not pushed unless SLA state change triggers mandatory enablement. |

---

## §4. Push Threshold Rules

### §4.1 The One-Push Rule

For any single state change event, Wiom sends at most one push notification per channel. If the CSP does not act on the push:

- The push is not resent for the same unchanged state
- The state remains visible on the dashboard (pull)
- If the state worsens and a new threshold is crossed — a new push is eligible for the new state
- If 3 messages have been sent with no response — see comms-principles.md §5 (Escalation Protocol)

> *A push that is ignored is not a reason to send another push. It is a signal that structure — not messaging — must respond.*

### §4.2 Evaluation Window Cooling

No push is sent for the same state category within the same evaluation window, even if the underlying metric fluctuates.

| State Category | Cooling Period After Push |
|---|---|
| SLA state (same level) | Full evaluation window — no repeat until state level changes |
| Enforcement (same trigger) | 7 days minimum |
| Economic (same event type) | No repeat unless structural state changes again |
| Connection request | Per-request — each new request is a new event |
| FPV / Integrity | Once per event — no repeat for same event |

---

## §5. Pull Channel Architecture

When a CSP needs information but a push is not justified, the pull channels are:

| Pull Channel | What It Carries | Access Method |
|---|---|---|
| Dashboard — State panel | All SLA states, routing state, enforcement state | CSP logs into partner app |
| Dashboard — Wallet | All compensation data: payouts, bonus, carry fee, deposit ledger | CSP views wallet section |
| Dashboard — Rate card | Current published rate card | CSP views rate card section |
| Dashboard — Enablement | Enablement resources, training modules | CSP navigates to enablement section |
| Dashboard — Comms history | Log of past notifications | CSP views notification history |
| Portal / Help docs | System rules, process documentation, FAQs | CSP navigates to help section |

Pull channels are always current. They reflect live structural truth. They do not require any communication design work from this agent — they are system-automated.

> *If the information the CSP needs is available in a pull channel — direct them there rather than duplicating it in a push. The CTA in a push notification should point to the relevant pull channel, not restate the content.*

---

## §6. Notification Threshold Matrix

This matrix summarises the push/pull decision for every major event type. It is the operational implementation of the principles above.

| Event Type | Threshold for Push | Pull Fallback |
|---|---|---|
| SLA state level changes | Every threshold crossing (Compliant↔At Risk↔Non-Compliant) | Dashboard — state panel |
| SLA fluctuation within same state level | Never | Dashboard — state panel |
| Routing change (material / threshold event) | Significant change only — not gradual taper | Dashboard — state panel |
| Payout credited | Never | Dashboard — wallet |
| Bonus eligibility changes | On change only | Dashboard — wallet |
| Carry fee starts accruing | First accrual only | Dashboard — wallet |
| Rate card changes | 30 days advance notice — once | Dashboard — rate card section |
| Connection request assigned | Every request (action required) | Dashboard — requests panel |
| FPV triggered | Immediately — once | Dashboard — enforcement panel |
| Suspension | Immediately — once | Dashboard — enforcement panel |
| New enablement resources (SLA-triggered) | On SLA state change that triggers mandatory enablement | Dashboard — enablement section |
| System update / policy change | Per advance notice requirements (30 or 14 days) | Dashboard — notice banner |

---

## §7. Opt-In Boundaries

Push is only appropriate for CSPs who have opted in to the relevant channel. Opt-in is not a blanket permission — it is channel-specific.

| Channel | Opt-In Type | What Happens Without Opt-In |
|---|---|---|
| In-app push notifications | Device-level (CSP enables notifications in phone settings) | Notification is not delivered. Dashboard is the fallback. Do not attempt alternative channel as substitute. |
| WhatsApp | Explicit opt-in to receive business messages from Wiom | WhatsApp message is not sent. SMS or dashboard is the fallback if state warrants notification. |
| SMS (promotional category) | DND registry check required | Message is blocked by TRAI DND. Not delivered. |
| SMS (transactional / service category) | No opt-in required — but DLT registration required | Delivered subject to TRAI compliance. |
| Dashboard | No opt-in — always available to logged-in users | N/A — dashboard is always on. |

> *If a CSP has not opted in to push notifications, the dashboard carries the information. Do not design workaround communications to fill the gap. The dashboard is sufficient for pull-only states.*

---

## §8. Push-to-Pull Transition Logic

Some states start as push-eligible but transition to pull-only as the situation persists. This prevents message escalation when structure escalation is what is needed.

### §8.1 SLA State Persistence

| Scenario | Communication Logic |
|---|---|
| CSP enters At Risk (first time) | Push once — state change notification |
| CSP remains At Risk (subsequent evaluation windows) | Pull only — state visible on dashboard. No repeat push for unchanged state. |
| CSP moves from At Risk to Non-Compliant | New push — new state crossing |
| CSP remains Non-Compliant (subsequent windows) | Pull only — state visible on dashboard. Structure escalates (routing taper deepens). Messaging does not. |
| CSP recovers to Compliant | Push once — recovery notification |

### §8.2 The Escalation Trap

The escalation trap is when a team perceives CSP inaction as a communication failure and responds by increasing push volume or urgency. This is always wrong.

**The trap:** CSP is Non-Compliant. Push sent. No action. Team sends second push with stronger language. No action. Team sends WhatsApp. No action. Team asks field to call. Etc.

**What is actually happening:** Structure is doing its job (routing tapered, bonus paused). The CSP is either unable or choosing not to engage. More communication does not change structural reality — it only depletes credibility and violates PCA.

**The correct response:** Three messages sent and no response → route to comms-principles.md §5 (Escalation Protocol). The next job is structural, not communicative.

> *Circuit Breaker: If more than 3 communications have been sent for the same state with no CSP action — messaging stops. Structure responds. No exceptions.*

---

## §9. Push Frequency Cap Reference

These caps are defined in comms-principles.md §3.1 and restated here for quick reference:

| Cap | Limit |
|---|---|
| Push notifications per CSP per week (proactive) | Maximum 2 (connection requests excluded) |
| WhatsApp per CSP per week | Maximum 1 (process-related or action-required only) |
| Economic messaging (proactive) | Zero unless structural state change triggers it |
| Same-state repeat | Not until new state change or evaluation window reset |
| Motivational / check-in | Zero. Permanently. |

---

## §10. Pull CTA Design Rule

When a push notification or WhatsApp message is designed, the call to action must direct the CSP to the relevant pull channel — not re-explain the content in the notification.

**Correct CTA pattern:**
- "View your SLA state: [Dashboard link]"
- "Access enablement: [Enablement section link]"
- "See rate card details: [Wallet link]"
- "Review process steps: [Portal link]"

**Incorrect CTA pattern:**
- "Keep working hard to improve your score" (motivational — PCA violation)
- "Contact us to discuss" (negotiation opening — PCA violation)
- "Click here to learn more" (vague — not directing to structural truth)
- No CTA at all for action-required states (incomplete)

---

*push-to-pull-rules.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Comms / Ops*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
