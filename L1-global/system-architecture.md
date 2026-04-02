---
FILE PURPOSE: System Architecture — What Wiom Is, How It Works, and What Data Is Available for Communication Design
HOW TO USE: Read this file to understand what the system can do, what events can trigger a communication, what data is available for personalisation, and what the CSP and customer journeys look like. This is context for the design agent — not a technical spec. When designing a comm, use this file to confirm: does this event actually happen in the system? Is the data I want to reference actually available? Does the channel I'm choosing fit the technical reality?
SCOPE: Wiom product, partner (CSP) journey, customer journey, OS event triggers, API capabilities, personalisation data
LAST UPDATED: March 2026
TAGS: system-architecture, product, csp-journey, customer-journey, event-triggers, personalisation, api, os-overview, recharge-model
---

# SYSTEM ARCHITECTURE
## What Wiom Is, How It Works, and What the Comms Agent Needs to Know

---

## §1. What Wiom Is

Wiom is an affordable home internet brand for lower- and middle-income households in India. The core product differentiator is the **recharge model**: customers pay for days of internet access, not months. There is no fixed monthly commitment, no traditional broadband contract, no modem ownership by the customer.

**One-line structural truth:**
Wiom turns home internet from a fixed monthly commitment into a rechargeable household utility.

**What this means for communication design:**
- Customers are not subscribers — they are recharge-based users
- CSPs are not account managers or salespeople — they execute service delivery for connections assigned by the system
- Payout to CSPs is triggered by valid recharge events — not by connection tenure, customer count, or monthly service
- All economic language must reflect this recharge logic — see pca-content-governance.md §3 and §11

---

## §2. The Wiom Product

### §2.1 How It Works — Customer Side

1. A household gets a Wiom NetBox installed at their premises
2. The NetBox is a Wiom-owned device — it remains Wiom's asset; the household does not own it
3. The household recharges for a chosen number of days (e.g. 7 days, 14 days, 30 days)
4. Internet access is active for the duration of the recharge
5. When the recharge expires, internet access pauses
6. The household recharges again when they need internet — no automatic renewal, no forced commitment

### §2.2 How It Works — CSP Side

1. A CSP (Connection Service Provider) is an individual who takes on responsibility for deploying and maintaining Wiom NetBoxes in their area
2. The CSP does not own customers — they service connections assigned by the system
3. When a household in the CSP's area gets a connection, the connection is assigned to the CSP by the system (Demand & Allocation OS)
4. The CSP earns a base payout per valid recharge event on their assigned connections, per the published rate card
5. Bonus eligibility is determined by SLA state (Quality OS) — active when Compliant, paused when At Risk or Non-Compliant
6. The NetBox remains Wiom's asset — CSP is responsible for its physical care; carry fee accrues if NetBox is held beyond expiry without return

### §2.3 The Recharge Model — Communication Implications

Because the model is recharge-based and not subscription-based:

| Traditional ISP Mental Model | Wiom Recharge Model |
|---|---|
| Customers are retained month-to-month | Customers recharge when they need internet |
| CSP earns monthly per active subscriber | CSP earns per valid recharge per assigned connection |
| Churn is a loss metric | Non-recharge is a demand signal, not a CSP failure |
| Volume targets drive income | Rate card and SLA state determine earnings |

Do not design communications that activate the traditional ISP mental model. See pca-content-governance.md §3 and comms-principles.md §6.

---

## §3. The CSP Journey

Understanding where a CSP is in their journey determines which OS triggers are active and what communications are appropriate.

### §3.1 CSP Journey Stages

**Stage 1: Registration and Onboarding**
- CSP completes registration
- Onboarding OS activates: welcome sequence, expectation-setting, Day 1 / Day 3 / Day 7 communications
- NetBox issued (if applicable)
- First connection not yet assigned

**Stage 2: Activation**
- First connection assigned by Demand & Allocation OS
- CSP's first recharge event expected
- SLA evaluation window not yet open (insufficient data)
- Onboarding OS active: activation nudges, setup guidance

**Stage 3: Active Operation**
- Regular recharge activity present
- SLA evaluation window open — Quality OS scoring active
- Compensation OS: payouts, bonus eligibility live
- Demand & Allocation OS: routing exposure responding to SLA state
- Communications: state-based, triggered by OS events

**Stage 4: Performance Events**
- SLA state changes (At Risk, Non-Compliant, Recovery)
- Enforcement events (pattern watch, FPV)
- Quality OS, Enforcement OS, Capability Development OS active
- Communications: state change notifications, mandatory enablement triggers

**Stage 5: Exit**
- Voluntary or system-initiated exit
- Exit OS active: settlement, asset recovery, access revocation
- Continuity Support OS active if customers are still being served
- Communications: process steps, settlement notifications, NetBox return coordination

### §3.2 Key CSP Journey Events — Communication Triggers

| Event | OS Source | Communication Triggered |
|---|---|---|
| Registration complete | Onboarding OS | Welcome + expectation-setting (Day 1) |
| First connection assigned | Demand & Allocation OS | Activation prompt (Day 3 / Day 7 if no recharge) |
| First recharge event recorded | Compensation OS | No notification required — wallet updated |
| SLA evaluation window opens | Quality OS | No notification required — state shown on dashboard |
| SLA state: Compliant → At Risk | Quality OS | Push notification + dashboard update |
| SLA state: At Risk → Non-Compliant | Quality OS | Push notification + dashboard update + mandatory enablement trigger |
| Routing taper activated | Demand & Allocation OS | Dashboard update (no push unless significant change) |
| Bonus eligibility paused | Compensation OS | Included in SLA state change notification |
| SLA recovery: Non-Compliant → Compliant | Quality OS | Push notification + dashboard update |
| FPV detected | Enforcement OS | Immediate push + call required |
| Suspension | Enforcement OS | Immediate push + call required |
| Termination | Enforcement OS | Call required + settlement initiated |
| Payout credited | Compensation OS | Wallet update only — no push |
| Carry fee first accrual | Compensation OS | Push notification — once |
| Rate card updated | Compensation OS | Push + dashboard — 30 days advance notice |
| Exit initiated | Exit OS | Process notification + settlement initiation |
| NetBox return required | Asset Recovery OS | WhatsApp / call for logistics coordination |

---

## §4. The Customer Journey

The design agent primarily designs CSP-facing communications. Customer-facing communications are a separate domain. However, understanding the customer journey is necessary to avoid boundary violations and to handle continuity-support scenarios.

### §4.1 Customer Journey Stages

**Signup:** Customer discovers Wiom (via CSP referral, marketing, or app). Submits connection request through the app.

**Serviceability check:** System checks whether the customer's address is within a serviceable zone. If yes — connection request assigned to nearest CSP via Demand & Allocation OS.

**Installation:** CSP visits to install NetBox. Customer is onboarded.

**First use:** Customer recharges for their first period. Internet activates.

**Recharge cycle:** Customer recharges as needed. No automatic renewal. No subscription obligation.

**Churn risk:** Extended periods without recharge trigger a churn-risk signal in the Customer Lifecycle OS. This is a system signal — not a CSP performance failure by itself.

**Churned:** Customer has not recharged for an extended period and is unlikely to return.

### §4.2 Customer Events That Affect CSP Communications

| Customer Event | Effect on CSP | Communication Implication |
|---|---|---|
| Customer recharges | CSP payout triggered | Wallet update — no CSP push required |
| Customer does not recharge (extended) | Churn-risk signal — may affect CSP's connection base over time | No direct CSP communication required for individual customer churn — this is normal system behaviour |
| Customer complaints / support ticket | May surface in Quality OS as Service Stability signal | CSP may receive SLA state update if pattern persists |
| CSP's area goes offline / connectivity issue | May trigger Service Stability domain signal in Quality OS | CSP receives SLA state communication if threshold crossed |

> *Customer behaviour is a system input — not a CSP responsibility to manage. Do not design CSP communications that imply CSPs must "keep customers happy" or "retain customers." This is a PayG and PCA violation.*

---

## §5. Operating System Overview

Wiom runs 20 Operating Systems across 4 clusters. The comms agent interacts primarily with the following OS systems as communication triggers:

### §5.1 OS Systems — Comms-Relevant

| OS | Cluster | Primary Communication Triggers |
|---|---|---|
| Quality OS | Performance | SLA state changes (Compliant / At Risk / Non-Compliant / Recovery) |
| Compensation OS | Economics | Payout events, bonus eligibility changes, carry fee, rate card updates |
| Enforcement & FPV OS | Governance | Pattern watch, FPV detection, suspension, termination |
| Exit OS | Lifecycle | Exit initiation, settlement, access revocation |
| Partner Onboarding OS | Formation | Welcome, activation sequence, Day 1 / 3 / 7 |
| Demand & Allocation OS | Operations | Connection request assignment, routing state changes |
| Capability Development OS | Performance | Mandatory enablement triggers, training module assignments |
| Partner Progression OS | Governance | Eligibility changes, access state changes |
| Asset Recovery OS | Operations | NetBox return initiation, carry fee management |
| Continuity Support OS | Lifecycle | Customer continuity communications during CSP exit |
| Voice & Change Log OS | Governance | System updates, policy changes, feedback responses |

### §5.2 OS State IDs — Reference Format

OS states follow the naming convention from OSTF (Addendum 3):
`[OS_PREFIX]_STATE_[NAME]`

Key states the comms agent will encounter:

| State ID | Meaning |
|---|---|
| QUAL_STATE_COMPLIANT | SLA state: Compliant — all domains within threshold |
| QUAL_STATE_AT_RISK | SLA state: At Risk — one or more domains below threshold |
| QUAL_STATE_NON_COMPLIANT | SLA state: Non-Compliant — severe threshold crossed, routing taper active |
| ALLOC_STATE_FULL | Routing exposure: Full |
| ALLOC_STATE_TAPERED | Routing exposure: Tapered — reflects Non-Compliant SLA state |
| ALLOC_STATE_FROZEN | Routing exposure: Frozen — enforcement-triggered |
| ENFORCE_STATE_PATTERN_WATCH | Enforcement: Pattern watch active |
| ENFORCE_STATE_FPV_DETECTED | Enforcement: Fundamental Principle Violation detected |
| ENFORCE_STATE_SUSPENDED | Enforcement: System participation temporarily suspended |
| ONBOARD_STATE_REGISTERED | Onboarding: Registration complete, not yet activated |
| ONBOARD_STATE_ACTIVATION_PENDING | Onboarding: Connection assigned, first recharge not completed |
| EXIT_STATE_ACTIVE | Exit: Exit flow in progress |
| COMP_STATE_BONUS_ACTIVE | Compensation: Bonus eligibility active (SLA Compliant) |
| COMP_STATE_BONUS_PAUSED | Compensation: Bonus eligibility paused (SLA not Compliant) |

---

## §6. Event Triggers — What the System Can Detect

The comms agent must only design communications for events the system can actually detect and verify. This section lists the real system events available as triggers.

### §6.1 Confirmed Event Triggers

| Event | Detection Method | Available for Personalisation |
|---|---|---|
| SLA state change | Quality OS evaluation engine — runs per evaluation window | State name, domain(s) affected, threshold values, evaluation window |
| Recharge event | Payment system — event on successful recharge | Recharge amount, duration, timestamp (do not use in CSP comms) |
| Connection request assignment | Demand & Allocation OS — routing decision | Connection request reference, assignment timestamp |
| FPV detection | Enforcement OS — pattern analysis + manual verification | FPV type (Principle #), detection date |
| Payout credited | Compensation OS — payment cycle | Payout amount, cycle reference (wallet — not pushed) |
| Bonus eligibility change | Quality OS + Compensation OS — state linkage | New eligibility state, effective from |
| Carry fee first accrual | Asset Recovery OS — NetBox tracking | Carry fee amount/day, accrual start date |
| Rate card update | Compensation OS — version management | New rate card version, effective date, what changed |
| Exit initiation | Exit OS — CSP action or system trigger | Exit type (voluntary / system-initiated), effective date |
| NetBox return required | Asset Recovery OS — device tracking | Device ID, return deadline |

### §6.2 Events That Are NOT Available as Triggers

Do not design communications based on these — they are not system-detectable or not available to the comms pipeline:

| Event | Why Not Available |
|---|---|
| Customer satisfaction / NPS | Not a system event — survey-based, not real-time |
| CSP effort or activity level | Not measured — system measures outcomes, not effort |
| Competitor activity | Not a system input |
| CSP financial situation | Not a system input — PayG violation to reference |
| Individual customer recharge | Not surfaced to CSP level — privacy and PayG architecture |
| Predicted future SLA state | Predictive models not yet in comms pipeline — communicate actual states only |

---

## §7. Data Available for Personalisation

The design agent may reference these data fields in communication templates. All references must be from registered Message Block variable slots — not free-text speculation.

### §7.1 Available Personalisation Fields

| Field | Source | Example Use in Communication |
|---|---|---|
| CSP Name | Partner registration data | "Hello [Name]." — functional greeting only |
| CSP ID | System identifier | Block ID reference, audit trail |
| SLA State (current) | Quality OS | "Your SLA state is [state]." |
| Domain(s) below threshold | Quality OS | "[Domain] below threshold." |
| Evaluation window reference | Quality OS | "Current evaluation window: [dates]." |
| Routing state | Demand & Allocation OS | "Routing: [state]." |
| Bonus eligibility state | Compensation OS | "Bonus eligibility: [Active/Paused]." |
| Rate card reference | Compensation OS | "Rate card version [X]. Effective [date]." |
| Carry fee amount per day | Asset Recovery OS | "Carry fee: [amount]/day." |
| NetBox return deadline | Asset Recovery OS | "Return required by: [date]." |
| Exit effective date | Exit OS | "Exit effective: [date]. Settlement per timeline." |
| Connection request reference | Demand & Allocation OS | "Connection request: [reference]." |

### §7.2 Fields That Must NOT Be Referenced in CSP Communications

| Field | Why Prohibited |
|---|---|
| Individual customer names or details | Privacy. Customer data is not CSP data. |
| Customer recharge amounts | Privacy + PayG violation — implies CSP owns customer economics |
| CSP income or earnings history | PayG violation — income framing |
| CSP ranking or percentile vs other CSPs | PCA §9.2 — Quality OS may not publish comparative data |
| Individual connection recharge rates | Privacy + PayG architecture |
| Predicted or projected values of any kind | PCA §11 — no projections |

---

## §8. API Capabilities — What Is Technically Possible

This section tells the design agent what the system can and cannot do technically, so communications are not designed for capabilities that do not exist.

### §8.1 Current Capabilities

| Capability | Status | Notes |
|---|---|---|
| Dashboard state display — all OS states | Live | System-automated. Reflects live state. |
| In-app push notifications | Live | Via partner app. Device notification permission required. |
| WhatsApp Business API (via Gupshup) | Live | Template-based. Utility classification for state comms. |
| SMS (transactional / service) | Live | DLT-registered templates. TRAI compliant. |
| Wallet — payout and compensation display | Live | CSP views own wallet. Not pushed. |
| Enablement resource delivery (in-app) | Live | Available in partner app. |
| Google Apps Script trigger (form-to-Claude) | Phase 2 | Form-driven intake — not yet fully live |
| Metabase reporting (performance data) | Live | Manual data entry into results.md for Phase 0–2 |

### §8.2 Not Yet Available

| Capability | Phase | Implication for Comms Design |
|---|---|---|
| Automated results entry from Metabase | Phase 3 | Results entered manually for now — do not design comms that depend on automated performance feedback loops |
| Full API + backend automation | Phase 3+ | Full pipeline currently runs on Claude Code + human review |
| Predictive SLA alerts (pre-threshold) | Not planned | Design comms for actual state changes only — not predicted ones |
| Real-time channel API calls from agent | Not permitted | Agent writes to review-queue; human deploys. No direct channel sends. |

---

## §9. What the Agent Can and Cannot Do

The design agent produces communications but does not deploy them. This is a hard architectural constraint.

| Agent Can | Agent Cannot |
|---|---|
| Design communication briefs (message copy, channel, timing, measurement plan) | Send messages directly to any channel |
| Write to review-queue/ for human approval | Access or modify CSP personal data |
| Reference Message Block IDs | Create new Message Blocks (proposes; human approves) |
| Load and apply OS playbook patterns | Modify OS state machines |
| Propose learnings to proposed-learnings/ | Modify playbooks directly (proposes; human approves) |
| Log to comms-log.md (via Logger Agent) | Override frequency caps or silence policy |
| Flag gaps to GAPS.md | Auto-deploy any communication |

> *The agent is a communications design engine. The human is the deployment gate. Nothing the agent produces is live until a human approves and deploys it.*

---

*system-architecture.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Engineering / Product (structural sections) | Comms team (communication implications sections)*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
