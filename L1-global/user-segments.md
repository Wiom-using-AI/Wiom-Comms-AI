---
FILE PURPOSE: CSP Segment Definitions — Who the Agent Is Talking To
HOW TO USE: Read this file before designing any communication. Every design task requires an audience. This file tells the agent what each audience label means structurally, what signals place a CSP in that segment, which OS triggers are most relevant, and how comms approach should be calibrated. This file does not govern vocabulary or message content — defer to pca-content-governance.md for that. It does not govern channel eligibility — defer to channel-specs.md and comms-principles.md.
SCOPE: All CSP-facing communications across all OS triggers
LAST UPDATED: March 2026
TAGS: segments, audience, csp-state, onboarding, quality, enforcement, exit, compensation, who-to-talk-to
---

# USER SEGMENTS
## CSP Segment Definitions, Signals, and Comms Approach

---

## How to Use This File

Every comm design task will specify an audience. That audience maps to one or more segments below. Before drafting:

1. Identify the segment from the brief or handoff block
2. Read the structural signals — confirm the audience matches
3. Check the relevant OS triggers — ensure you have the right playbook loaded
4. Apply the comms approach notes alongside PCA vocabulary and tone rules

If a CSP fits more than one segment simultaneously (e.g. Non-Compliant AND Enforcement-Flagged), see Section 11 (Compound States).

---

## Segment Index

| ID | Segment Name | One-Line Definition |
|---|---|---|
| SEG-01 | New CSP | Onboarded but not yet activated — no connection assigned or first recharge not completed |
| SEG-02 | Activating CSP | First connection assigned; activation sequence in progress; no completed recharge cycle yet |
| SEG-03 | Active Compliant CSP | Operationally stable; SLA state Compliant; regular recharge activity present |
| SEG-04 | At-Risk CSP | SLA state At Risk; one or more domains below threshold; routing unchanged |
| SEG-05 | Non-Compliant CSP | SLA state Non-Compliant; routing taper active; mandatory enablement triggered |
| SEG-06 | Recovering CSP | SLA state returned to Compliant or At Risk after Non-Compliant; in post-recovery window |
| SEG-07 | Inactive CSP | No recharge activity in current evaluation window; SLA not yet triggered; not yet exiting |
| SEG-08 | Enforcement-Flagged CSP | FPV detected or pattern watch active; enforcement action initiated or pending |
| SEG-09 | Suspended CSP | System participation temporarily suspended; review in progress |
| SEG-10 | Exiting CSP | Voluntary or system-initiated exit in progress; settlement and asset recovery active |

---

## SEG-01 — New CSP

**Definition:** CSP has completed registration and onboarding intake but has not yet been assigned a connection or completed a first recharge cycle. Day 0 to approximately Day 3.

**Structural signals:**
- Onboarding OS state: registered / intake complete
- No active connections in system
- No recharge events recorded
- NetBox may or may not have been issued

**Relevant OS triggers:** Onboarding OS

**Comms approach:**
- This is the highest-volume segment for onboarding communications
- Primary job: set accurate expectations about how the system works — recharge model, connection assignment logic, SLA framework
- Do not frame as "welcome to the team" or any employer / partnership warmth
- Factual orientation: what the CSP can expect, what they must do, what the system will do
- Hindi-primary communications highly likely for this segment
- See onboarding-playbook.md for Day 0 / Day 1 / Day 3 proven patterns

---

## SEG-02 — Activating CSP

**Definition:** First connection has been assigned. CSP is in the activation window — NetBox deployed, first recharge not yet completed. Approximately Day 3 to Day 14.

**Structural signals:**
- Onboarding OS state: connection assigned / activation pending
- At least one active connection in system
- No completed recharge cycle yet
- SLA evaluation window not yet open

**Relevant OS triggers:** Onboarding OS, Quality OS (monitoring only — SLA evaluation not yet active)

**Comms approach:**
- Critical window: most activation drop-offs happen here
- Communications focus on specific next action — completing first recharge, confirming NetBox setup
- Do not motivate with income framing ("start earning now") — frame as system activation steps
- If no action after Day 7: flag for field review per comms-principles.md Section 5, not more messaging
- See onboarding-playbook.md for Day 7 patterns and field escalation triggers

---

## SEG-03 — Active Compliant CSP

**Definition:** CSP is operationally stable. SLA state is Compliant across all domains. Regular recharge activity is present within the evaluation window.

**Structural signals:**
- SLA state: QUAL_STATE_COMPLIANT
- All SLA domains within threshold
- Recharge activity present in current evaluation window
- No enforcement flags active
- Routing exposure: Full

**Relevant OS triggers:** Quality OS (state maintenance), Compensation OS (payout and bonus), Demand & Allocation OS (routing)

**Comms approach:**
- Lowest communication need of any active segment
- Most state updates visible on dashboard — push only for material changes (rate card, bonus tier change)
- Do not send motivational or congratulatory messages for Compliant state — this is expected, not exceptional
- Compensation communications (payout, bonus) are factual and rate card-referenced only
- No proactive economic nudges
- See comms-principles.md Section 2.3 for what never gets a message

---

## SEG-04 — At-Risk CSP

**Definition:** SLA state has moved to At Risk. One or more domains are below threshold but above the Non-Compliant boundary. Routing exposure unchanged. Enablement available.

**Structural signals:**
- SLA state: QUAL_STATE_AT_RISK
- One or more domains below threshold
- Routing: Full (not yet tapered)
- Bonus eligibility: paused
- Enablement resources: available and surfaced

**Relevant OS triggers:** Quality OS (primary), Compensation OS (bonus pause communication)

**Comms approach:**
- One push notification on state transition — not repeated within same evaluation window
- Message communicates: domain below threshold, enablement available, bonus eligibility paused
- No urgency language — this is an Attention-level severity, not Action Required
- Do not imply income loss — frame bonus pause as a state-dependent eligibility change, not a penalty
- Do not add reassurance ("don't worry, you can recover") — factual only
- If CSP does not engage with enablement after 3 comms: flag to Capability Development OS, not more messaging
- See quality-os-playbook.md for At Risk proven patterns and timing rules

---

## SEG-05 — Non-Compliant CSP

**Definition:** SLA state is Non-Compliant. One or more domains have crossed the severe threshold. Routing taper is active. Mandatory enablement is triggered.

**Structural signals:**
- SLA state: QUAL_STATE_NON_COMPLIANT
- One or more domains at or beyond severe threshold
- Routing: Tapered (ALLOC_STATE_TAPERED)
- Bonus eligibility: paused
- Mandatory enablement: triggered
- Enforcement OS: monitoring for sustained pattern

**Relevant OS triggers:** Quality OS (primary), Demand & Allocation OS (routing consequence), Enforcement OS (pattern watch), Compensation OS (bonus pause)

**Comms approach:**
- Action Required severity — communication is direct and consequence-specific
- Message communicates: domain crossed threshold, routing taper active, mandatory enablement required
- Do not soften enforcement language — routing taper is a system consequence, not a temporary inconvenience
- Do not frame as income loss — frame as routing exposure reflecting SLA state
- If enablement scheduling requires coordination: WhatsApp / call permitted for scheduling only, not for state communication
- Three-message threshold applies — if no action after 3 comms, route to Enforcement OS escalation
- See quality-os-playbook.md and enforcement-os-playbook.md for Non-Compliant patterns

---

## SEG-06 — Recovering CSP

**Definition:** CSP's SLA state has returned to Compliant or At Risk following a Non-Compliant period. Currently within the post-recovery evaluation window.

**Structural signals:**
- SLA state: QUAL_STATE_COMPLIANT or QUAL_STATE_AT_RISK (transitioned from QUAL_STATE_NON_COMPLIANT)
- Routing: returning to Full or partially restored (depending on Demand & Allocation OS logic)
- Bonus eligibility: may have resumed if returned to Compliant
- Post-recovery window: active (consecutive compliant evaluation windows being tracked)

**Relevant OS triggers:** Quality OS (primary), Compensation OS (bonus resumption), Demand & Allocation OS (routing restoration)

**Comms approach:**
- One notification on recovery state transition — factual, not celebratory
- Do not use language like "congratulations" or "you've improved" — state recovery is a structural event, not an achievement
- Correct framing: "SLA state returned to [state] after [N] consecutive compliant windows"
- If bonus eligibility has resumed: communicate per Compensation OS rules — factual, rate card-referenced
- Routing restoration communicated only if a material change has occurred
- See quality-os-playbook.md for recovery communication patterns

---

## SEG-07 — Inactive CSP

**Definition:** CSP has active connections in the system but no recharge activity has been recorded in the current evaluation window. SLA evaluation may not yet have triggered. CSP has not initiated exit.

**Structural signals:**
- Active connections present in system
- No recharge events in current evaluation window
- SLA state: may be approaching At Risk depending on domain thresholds
- Routing exposure: Full or unchanged
- Not in exit flow

**Relevant OS triggers:** Quality OS (monitoring), Onboarding OS (if still within activation window), Capability Development OS (if inactivity is linked to capability gap)

**Comms approach:**
- Low communication justification — inactivity alone is not a trigger for push messaging unless a state change has occurred
- Do not send "we miss you" or "come back" retention messaging — this is a PayG violation
- If SLA state has changed as a result of inactivity: communicate the state change per SEG-04 or SEG-05 rules
- If inactivity is pre-SLA-trigger: flag for field review or capability development review, not messaging
- Do not assume the reason for inactivity — do not improvise explanations or offers

---

## SEG-08 — Enforcement-Flagged CSP

**Definition:** A Fundamental Principle Violation (FPV) has been detected, or a sustained non-compliance pattern has placed the CSP on pattern watch. Enforcement action is initiated or pending.

**Structural signals:**
- Enforcement OS state: ENFORCE_STATE_PATTERN_WATCH or ENFORCE_STATE_FPV_DETECTED
- FPV type recorded (if applicable)
- System action: in progress or pending review
- Routing: may be frozen (ALLOC_STATE_FROZEN)

**Relevant OS triggers:** Enforcement OS (primary), Quality OS (pattern source), Demand & Allocation OS (routing freeze), Compensation OS (hold or settlement)

**Comms approach:**
- Integrity-level severity — shortest possible communication, most formal tone
- Message communicates: pattern or FPV type, system action, next step in process
- No moral language — no "fraud," "dishonesty," "bad behaviour" — use structural terms: "Fundamental Principle Violation: [Principle #]," "Pattern detected in [domain]"
- No negotiation openings — do not frame as a discussion or review request
- No emotional framing in either direction — no accusation, no reassurance
- Call / field script required for suspension communications — must read from approved Message Block only
- Free-text WhatsApp prohibited — process steps only via approved template if CSP action required
- See enforcement-os-playbook.md for all FPV and pattern watch communication patterns

---

## SEG-09 — Suspended CSP

**Definition:** System participation has been temporarily suspended. CSP access is restricted. Review is in progress.

**Structural signals:**
- Enforcement OS state: ENFORCE_STATE_SUSPENDED
- System access: restricted
- Routing: frozen
- Compensation: on hold pending review outcome
- Review process: active

**Relevant OS triggers:** Enforcement OS (primary), Compensation OS (hold), Asset Recovery OS (if NetBox return is in scope)

**Comms approach:**
- Integrity / Termination-level severity — minimal words, maximum precision
- Message communicates: participation suspended, reason (structural — FPV type or enforcement trigger), review in progress
- No framing that implies negotiability — suspension is a system state, not a decision open for discussion
- Call script required — must reference Block ID, no improvisation
- Do not add timeline promises ("this will be resolved in X days") unless the process has a defined SLA
- Asset recovery communications (NetBox return) may require WhatsApp for logistics coordination — process steps only, from approved template
- See enforcement-os-playbook.md for suspension communication patterns

---

## SEG-10 — Exiting CSP

**Definition:** CSP is in an active exit flow — either voluntary (CSP-initiated) or system-initiated. Settlement process is running. Asset recovery may be active.

**Structural signals:**
- Exit OS state: active (S1 through S6 depending on exit stage)
- Settlement: in process
- NetBox return: scheduled or in progress (Asset Recovery OS)
- Routing: frozen or winding down
- If system-initiated: Enforcement OS trigger present

**Relevant OS triggers:** Exit OS (primary), Asset Recovery OS, Compensation OS (final settlement), Enforcement OS (if system-initiated exit)

**Comms approach:**
- Communications are process-only: what steps are required, what the timeline is, what the CSP must do
- Do not attempt retention — no "are you sure," no "we'd like you to stay," no re-entry promises
- Do not add farewell warmth — "we hope you'll come back" is a PCA violation
- Voluntary exit: factual process communication only
- System-initiated exit: enforcement language applies — state reason structurally, no moral framing
- Final settlement communication: amounts from rate card and settlement formula only, no narrative
- WhatsApp / SMS permitted for asset return logistics (NetBox pickup scheduling, return confirmation) — process steps only from approved template
- See exit-os-playbook.md and continuity-support-playbook.md if customer continuity is also active

---

## 11. Compound States

Some CSPs will be in two segments simultaneously. The following combinations are the most common. In compound states, load all relevant OS playbooks and apply the higher-severity communication rules.

| Combination | Primary Segment | Secondary Segment | Comms Rule |
|---|---|---|---|
| Non-Compliant + Enforcement-Flagged | SEG-05 | SEG-08 | Apply Integrity-level severity. Enforcement OS communication takes precedence over Quality OS communication. Do not send both separately. |
| At-Risk + Compensation Hold | SEG-04 | — | Compensation hold communicated in same message block where possible. Do not send two separate push notifications. |
| Suspended + Asset Recovery Active | SEG-09 | — | Asset recovery logistics (NetBox return) may use WhatsApp process template alongside suspension communication. Keep separate by subject. |
| Exiting + Continuity Support Active | SEG-10 | — | Load both exit-os-playbook.md and continuity-support-playbook.md. Customer-facing continuity communications are separate from CSP-facing exit communications. Zero bleed between domains. |
| Inactive + SLA Approaching Threshold | SEG-07 | SEG-04 (imminent) | Do not pre-communicate a state that has not yet triggered. Wait for the state change. Then communicate per SEG-04 rules. |

---

## 12. What This File Does Not Cover

- **Exact message copy or vocabulary** → pca-content-governance.md
- **Channel eligibility per state** → comms-principles.md Section 2.1 and channel-specs.md
- **Frequency caps and fatigue rules** → comms-principles.md Section 3
- **Proven patterns and timing per OS** → relevant OS playbook
- **Customer (U2) segments** — this file covers CSP segments only. Customer-facing segments are a separate domain. See continuity-support-playbook.md for U2 context during exit events.

---

*user-segments.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Product / Data*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
