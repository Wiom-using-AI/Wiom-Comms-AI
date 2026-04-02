---
FILE PURPOSE: Comms Principles — When, How Much, and How to Communicate with CSPs
HOW TO USE: Read this file before deciding whether to design a communication. It governs the DECISION to communicate, not the content of communications. When your task involves frequency, fatigue, escalation, or PayG framing — this file is authoritative. When your task involves what words to use or which vocabulary is allowed — defer to pca-content-governance.md and pca-enforcement-governance.md. This file and the PCA files are complementary: PCA says WHAT you may say; this file says WHETHER and HOW OFTEN you should say anything at all.
SCOPE: All CSP-facing communications across all OS triggers and all channels
LAST UPDATED: March 2026
TAGS: communication-philosophy, when-to-communicate, silence-policy, fatigue-rules, frequency-caps, escalation-protocol, payg-positioning, push-to-pull, over-messaging
---

# COMMS PRINCIPLES
## Communication Philosophy, Frequency, Fatigue, Escalation, and PayG Positioning

---

## 1. Core Philosophy

These four principles govern every communication decision. Apply them before designing any comm.

### P1: Silence Is a Valid System Signal

If no state has changed and no CSP action is required, the correct communication is no communication. Silence communicates system stability. Every unnecessary message trains CSPs to expect attention, creates noise that dilutes high-signal messages, and erodes the authority of genuine system alerts. The default is silence. Communication requires justification.

> **Test:** If you cannot name the structural state change that makes this message necessary, the message should not exist.

### P2: Structure Escalates. Messaging Does Not.

When a CSP situation becomes more serious, the response is to escalate system consequences — routing taper, bonus pause, enforcement action — not to increase message volume, urgency, or emotional intensity. More messages never solve what structural escalation exists to address. Messaging reports structure. It does not substitute for it.

> **Test:** Is this additional message attempting to motivate a CSP to act? If yes, it is the wrong response. Structural escalation is the right response.

### P3: Push Sparingly. Let the Dashboard Pull.

The dashboard is always on. It always reflects current structural truth. Push communications — notifications, WhatsApp, SMS — are for state changes that require immediate CSP awareness or action and that a CSP cannot reasonably be expected to check on their own. Any information already visible on the dashboard does not need a push unless the state change demands CSP action. When in doubt, do not push.

> **Test:** Is this state change visible on the dashboard? Is there a specific action the CSP must take in response? If both answers are yes — push once. If the second answer is no — do not push.

### P4: Every Message Carries a Credibility Cost

CSPs calibrate their attention based on past communications. Low-signal messages — motivational nudges, check-ins, repeat reminders for unchanged states — deplete the credibility budget. When a genuinely critical message arrives, it receives less attention because the CSP has learned that most messages are noise. Protect the credibility of the system by only sending messages that earn their place.

> **Test:** If every comm sent over the past 30 days were laid out in sequence, would this message make the set stronger or weaker?

---

## 2. When to Communicate vs Stay Silent

### 2.1 Communication Threshold Matrix

This matrix is binding. It defines which state changes trigger which channels.

| State / Event | Dashboard | Push (Once) | WhatsApp / SMS | Call / Field |
|---|---|---|---|---|
| Daily volume fluctuation | Yes (auto) | No | No | No |
| SLA remains Compliant | Yes (auto) | No | No | No |
| SLA: Compliant → At Risk | Yes (auto) | Yes, once | No | No |
| SLA: At Risk → Non-Compliant | Yes (auto) | Yes, once | No | Only if enablement requires scheduling |
| SLA: Non-Compliant → Recovery | Yes (auto) | Yes, once | No | No |
| Routing taper (gradual) | Yes (auto) | No | No | No |
| Routing: significant change | Yes (auto) | Yes, once | No | No |
| Bonus tier change | Yes (auto) | Yes, once | No | No |
| Rate card update | Yes (auto) | Yes, advance notice | No | No |
| Normal payout cycle | Yes (wallet) | No | No | No |
| Carry fee: first accrual | Yes (wallet) | Yes, once | No | No |
| Carry fee: ongoing | Yes (wallet) | No | No | No |
| FPV detected | Yes (auto) | Yes, immediate | Process steps only | Required for suspension / termination |
| Connection request assigned | Yes (auto) | Yes, action required | No | No |
| System update (economic) | Yes, persistent 14 days | Yes, once | Only if CSP action required | No |
| System update (SLA / routing threshold) | Yes, persistent | Yes, advance | No | No |
| System update (new feature) | Yes (auto) | Yes, once | No | No |

### 2.2 The Silence Rule

> If a state is visible on the dashboard and no CSP action is required, the message should not exist.

This is not a guideline. It is the governing principle for every push, WhatsApp, and SMS decision. Channel eligibility in the matrix above already applies this rule. Do not seek exceptions.

### 2.3 What Never Gets a Message

Regardless of any other context, the following states or conditions never generate a CSP-facing push, WhatsApp, or SMS:

- States that have not changed since the last communication
- Normal payout cycles (payout is visible in wallet)
- Motivational or check-in communications ("just reminding you," "keep it up," "how are you doing")
- Volume fluctuations within normal system range
- Routine dashboard updates with no CSP action required
- Any state that is purely informational and already dashboard-visible

---

## 3. Frequency Caps and Fatigue Rules

### 3.1 Hard Caps — System-Level (Non-Negotiable)

These caps override all other decisions. If a comm would breach any cap, it is suppressed.

| Cap | Limit | Override? |
|---|---|---|
| Push notifications per CSP per week | Maximum 2 proactive (connection request notifications excluded) | Never |
| WhatsApp messages per CSP per week | Maximum 1, process-related or action-required states only | Never |
| Economic messaging (proactive) | Zero, unless structural state change triggers it | Never |
| Repeat notification for same state | Not until new state change or evaluation window resets | Never |
| Motivational / check-in messages | Zero. Permanently. | Never |

### 3.2 Channel-Specific Cooling Periods

After any communication, these cooling periods apply before re-notifying the same CSP in the same category:

| Category | Cooling Period |
|---|---|
| Informational change (no CSP action required) | 30 days |
| Economic change | No follow-up unless structural state changes again |
| SLA state change | No repeat push within same evaluation window |
| Enforcement (routing taper / bonus pause / suspension) | 7 days minimum |
| Integrity event (FPV) | No repeat for same event — one notification per channel, once |

### 3.3 Fatigue Indicators

If any of these signals are present, evaluate whether recent communication volume is too high before designing a new comm:

- CSP has received 2 or more pushes in the current week
- The same state has generated multiple messages in the same evaluation window
- The last 3 entries in comms-log.md are for the same OS trigger on the same audience
- A message is being designed because a previous message was "ignored"

> **If a CSP ignores a message, the response is NOT more messaging.** See Section 5.

---

## 4. Escalation Tone Protocol

As severity increases, word count decreases and tone becomes more formal and impersonal. Higher severity means fewer words, not more emotion.

| Severity Level | Tone | Character | Volume Direction |
|---|---|---|---|
| Informational | Neutral, factual | State description only. No action required. | Full block — complete context |
| Attention | Neutral, directive | State change. Optional CSP action available. | Medium — state + action |
| Action Required | Factual, clear | Consequence active. CSP must act. | Short — state + consequence + next action |
| Integrity | Formal, impersonal | FPV. System action. Binary fact. | Very short — state + system action only |
| Termination | Formal, minimal | Ended. Process reference only. | Minimal — outcome + process reference |

> **Escalation Invariant:** As severity increases, word count decreases, precision increases, and emotion stays at zero. A longer or more urgent message is never the right response to higher severity.

For exact vocabulary and tone rules at each severity level, see pca-content-governance.md §4 and §10.

---

## 5. Escalation Protocol — When a CSP Is Unresponsive

### 5.1 What Unresponsiveness Means

If a CSP does not act on one or more communications, the system treats this as a data signal, not a communication failure. It does not mean a better-worded message is needed. It does not mean more messages are needed. Unresponsiveness is the signal that structure — not messaging — must respond.

### 5.2 The Three-Message Threshold

If a CSP has received 3 or more relevant communications for the same OS state and has taken no action:

**Step 1: Messaging stops.** Do not design a fourth message for the same state. Additional messaging past this point is a fatigue and credibility violation.

**Step 2: Flag to human review.** Add an entry to GAPS.md or the project's context-from-teams.md with: CSP segment / audience, OS state, comms sent (dates + Block IDs from comms-log.md), action not taken, evaluation window open.

**Step 3: Identify the structural response.** Choose from:

| Structural Response | When to Use |
|---|---|
| Invoke Capability Development OS | CSP has not engaged with enablement resources despite sustained At Risk / Non-Compliant SLA state |
| Escalate via Enforcement OS | Pattern of non-response meets enforcement criteria per Enforcement OS state machine |
| Flag for field review | Physical or access issue suspected (NetBox, connectivity, onboarding gap) |
| Hold — wait for evaluation window reset | State not yet eligible for enforcement; no structural lever available |

**Step 4: Do not send a "final warning" message.** If enforcement is warranted, the Enforcement OS issues the correct communication through its Message Block. That is the structural consequence — not a warning composed outside the block system.

> **Unresponsiveness Rule:** Three messages sent and not acted on means the communication design work is done. The next job belongs to a different OS. Flag the pattern, route to the structural response. Do not design more messages.

### 5.3 What Escalation Is Not

The following are not valid escalation responses and are PCA violations:

- Resending the same message with different wording
- Increasing urgency or adding loss framing
- Switching to a different channel specifically to reach the CSP
- Adding emotional appeals or retention language
- Asking field teams to follow up via free-text WhatsApp
- Creating a custom one-off message not backed by a registered Message Block

See pca-enforcement-governance.md §13 for field improvisation controls.

---

## 6. PayG Positioning Principle

### 6.1 What This Principle Governs

The PayG (Pay-as-you-Go) positioning principle governs how the Wiom system and the CSP's role within it are framed in all CSP-facing communications. It exists because the recharge-based model is structurally different from traditional ISP models — and the language used with CSPs must reflect that difference accurately and consistently.

PCA governs which words are allowed. This principle governs which mental model must never be activated.

### 6.2 The Core Structural Truth

Wiom's home internet works on recharge logic. Customers pay for days, not months. There is no fixed monthly commitment, no modem ownership, no guaranteed continuous connection independent of recharge activity.

The CSP's payout model mirrors this: payouts are triggered by valid recharge events per the published rate card — not by connection tenure, not by customer count, not by monthly service delivery.

> **The CSP earns per recharge cycle per valid connection. Not per connection held. Not per customer retained. Not per month served.**

This is structural truth. Any communication that implies otherwise is factually incorrect and a PayG contamination violation.

### 6.3 The Forbidden Mental Model

These frames must never be activated through CSP communications:

- **Traditional ISP / employer model:** CSP as account manager, customer retention agent, or salaried employee with recurring income tied to a stable connection base
- **Commission / growth model:** CSP income grows as connection base grows, with projections and targets
- **Ownership model:** CSP "has customers" who belong to them, with churn risk, loyalty incentives, and retention duties

These frames are wrong because they are structurally false. They create expectations the system cannot fulfill and produce contested enforcement, economic misunderstanding, and belief divergence between what CSPs believe they are owed and what the system delivers.

### 6.4 PayG Language Rules

**Never use these frames:**

| Forbidden Frame | Why | Correct Alternative |
|---|---|---|
| "Earn more as your base grows" | Creates income projection tied to volume | "Payout per valid recharge per active connection. See rate card." |
| "Keep your customers happy" | Activates ownership / retention model | "Service Stability domain status reflects connection performance." |
| "You lost income due to poor quality" | Loss framing against earning potential | "Bonus eligibility paused. SLA state: At Risk. Resumes when Compliant." |
| "Build your business with Wiom" | Employer / franchise framing | Remove entirely — no equivalent framing exists |
| "Monthly income from your connections" | Salary / recurring income framing | "Payout per recharge cycle per valid connection per rate card." |
| "Grow your customer base" | Sales target framing | "Routing exposure responds to SLA state." |
| "Guaranteed earnings with good quality" | Conditional income promise | "Bonus eligibility is active when SLA state is Compliant." |

**Always frame economics as:**
- Deterministic: triggered by valid recharge events, not by performance effort or loyalty
- Rate card-bound: exact amounts from the published rate card only, no projections
- State-dependent: bonus eligibility is a binary function of SLA state, not a reward for effort
- Forward-effective: no retroactive payout changes; rate card changes apply from effective date

### 6.5 PayG Self-Check (Run Before Finalising Any Comm)

Before placing any comm in review-queue, verify:

- [ ] Does this message imply recurring or monthly earnings? → Remove
- [ ] Does this message frame the CSP as owning, retaining, or growing a customer base? → Remove
- [ ] Does this message suggest effort leads to more income? → Remove
- [ ] Does this message contain "earn," "income," "salary," "potential," or "opportunity" in reference to money? → Replace with rate card language
- [ ] Does this message create any expectation not already in the published rate card? → Remove
- [ ] Does this message treat the CSP as a customer to motivate or retain? → Rewrite as factual state communication

If any item is checked, the message has a PayG contamination violation. Do not proceed to review-queue. Rewrite and re-run.

For the full PayG contamination check and violation protocol, see SECURITY-RULES.md Rule 1.

---

## 7. Quick-Reference Decision Checklist

Use this before designing any comm. If any check fails, resolve it before proceeding.

**Is this comm justified?**
- [ ] A structural state change has occurred OR a specific CSP action is required
- [ ] The state is not already dashboard-visible with no action needed
- [ ] A Message Block exists for this state (or will be created and approved before deployment)

**Is frequency within bounds?**
- [ ] CSP / audience has not received 2+ push notifications this week (excluding connection requests)
- [ ] This is not a repeat for an unchanged state within the same evaluation window
- [ ] CSP has NOT had 3+ comms sent for the same state with no response (if yes → Section 5, not more design)

**Is the channel correct?**
- [ ] Channel eligibility confirmed against Communication Threshold Matrix (Section 2.1)
- [ ] Not using WhatsApp or SMS unless the matrix explicitly permits it for this state

**Is the PayG frame clean?**
- [ ] No income framing, no growth framing, no ownership framing
- [ ] All economics traceable to published rate card
- [ ] PayG self-check (Section 6.5) passed

**Is the severity and tone calibrated?**
- [ ] Severity level identified
- [ ] Word count direction confirmed (higher severity = fewer words)
- [ ] No urgency beyond what the severity level permits

---

## 8. What This File Does Not Cover

This file governs the decision to communicate and the principles of volume and frequency. It does not cover:

- **Exact vocabulary, tone rules, or forbidden terms** → pca-content-governance.md
- **Message Block creation, versioning, and enforcement** → pca-enforcement-governance.md
- **Push vs. pull transition rules and litmus tests** → push-to-pull-rules.md
- **Per-channel technical constraints** (character limits, media support, opt-in) → channel-specs.md
- **TRAI DND compliance, consent, time-of-day restrictions** → regulatory-compliance.md
- **OS-specific proven patterns, timing, and accumulated learnings** → relevant OS playbook

---

*comms-principles.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Comms team*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
