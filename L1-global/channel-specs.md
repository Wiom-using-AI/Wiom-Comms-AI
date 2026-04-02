---
FILE PURPOSE: Channel Specifications — Technical Constraints and Eligibility for Every Deployment Channel
HOW TO USE: Read this file when selecting a channel for a communication. Every design task must confirm the chosen channel can carry the message technically and is eligible for the state type being communicated. This file covers the mechanics of each channel. It does not govern which state types trigger which channels — that is in comms-principles.md Section 2.1. It does not govern message content or vocabulary — that is in pca-content-governance.md. Use all three together.
SCOPE: All channels used for CSP-facing communication at Wiom
LAST UPDATED: March 2026
TAGS: channel-specs, whatsapp, sms, push-notification, dashboard, call-script, field-script, character-limits, media, opt-in, delivery, timing
---

# CHANNEL SPECIFICATIONS
## Technical Constraints, Media Support, Delivery, and PCA Eligibility Per Channel

---

## Channel Index

| Channel | Sub-type | Primary Use | PCA Eligibility |
|---|---|---|---|
| WhatsApp | Utility | State changes requiring CSP action or awareness | Informational, Attention, Action Required |
| WhatsApp | Marketing | Promotional / engagement messaging | **NOT ELIGIBLE** — PCA prohibits promotional framing |
| WhatsApp | Authentication | OTP / account verification | Process-only — not for state communications |
| SMS | Standard | Fallback or action-required alerts | Informational, Attention, Action Required |
| In-App Push Notification | — | Immediate state change alerts | Attention, Action Required, Integrity |
| Dashboard | State display | Always-on structural truth | All severity levels |
| Call Script | — | Reactive support, enforcement actions | Attention through Termination |
| Field Script | — | Onboarding, reactive in-person support | Informational, Attention |

---

## 1. WhatsApp

WhatsApp messages to CSPs must always use pre-approved templates registered through the WhatsApp Business API. No free-text messages are permitted for state communications, economics, or enforcement. Templates must reference a registered Message Block ID. See pca-enforcement-governance.md §13 for field improvisation controls.

WhatsApp conversation windows: template-initiated conversations are open for 24 hours. Free-entry point conversations are open for 72 hours.

---

### 1.1 WhatsApp — Utility Template

**What it is:** Pre-approved templates for transactional or operational messages tied to a specific system state or event. Confirms, suspends, or modifies a state. Functional — not promotional.

**PCA classification for Wiom:** This is the primary WhatsApp template type for all CSP state communications. SLA state changes, enforcement notices, asset recovery logistics, and process-step communications all use Utility templates.

**Character limits:**
- Header text: 60 characters
- Body text: 1,024 characters
- Footer text: 60 characters
- Button text (if used): 25 characters per button, maximum 3 buttons

**Media support:**
- Header: image (JPEG / PNG, max 5 MB), video (MP4, max 16 MB), document (PDF, max 100 MB), or text
- Body: text only (with variables for personalisation)
- No emoji in enforcement or state communications per PCA tone rules

**Variables / personalisation:** Dynamic variables supported in body and header using `{{1}}` syntax. Can be used for CSP name, state label, domain name, Block ID reference.

**Opt-in requirement:** CSP must have opted in to receive WhatsApp messages from Wiom. Do not send to CSPs who have not opted in. Check opt-in status before scheduling.

**Delivery reliability:** High — WhatsApp delivers to device when online, queues when offline. Delivery receipts available. Read receipts available if CSP has not disabled them.

**Cost:** Per-message cost applies (utility category pricing from WhatsApp Business API). Lower than marketing template cost. Confirm current rate with ops team.

**Timing restrictions:**
- TRAI DND rules apply for promotional classification — utility messages have more flexibility but confirm classification with legal before sending at odd hours
- Recommended window: 09:00–21:00 IST for all CSP WhatsApp messages
- No overnight sends except FPV / Integrity-level events

**Best use cases for Wiom:**
- SLA state change notifications (At Risk, Non-Compliant, Recovery)
- Enforcement process steps (suspension notice, asset return scheduling)
- Connection request assignment (action required)
- Rate card / bonus tier update (advance notice)
- NetBox return logistics coordination

**Not permitted for:**
- Economic framing or income commentary (PayG violation)
- Motivational or check-in messages (PCA violation)
- Any message without a registered Message Block ID
- Free-text field team messages (improvisation violation)
- Marketing or promotional content (use Marketing template — but see 1.2)

**Auto-classification risk — critical:**
WhatsApp / Meta will automatically reclassify a template as Marketing if it contains any promotional or mixed-intent elements. The rule: if a template contains both utility and marketing elements, it is classified as marketing. Any template that does not clearly fit Utility or Authentication is defaulted to Marketing. Marketing classification means higher per-message cost and stricter frequency rules.

This means PCA compliance and correct template classification are the same job. Copy that is factual, state-based, and non-promotional stays Utility. Copy that drifts toward motivational language, income framing, or any promotional element gets auto-bumped to Marketing — with cost and delivery consequences.

> **Agent rule:** If a draft template contains any language that could be read as promotional, encouraging, or income-related, it is both a PCA violation AND a risk of Marketing misclassification. Flag and rewrite before submitting to review-queue.

---

### 1.2 WhatsApp — Marketing Template

**What it is:** Pre-approved templates for promotional content — offers, announcements, product launches, loyalty programs, engagement nudges.

**PCA classification for Wiom:** **NOT ELIGIBLE for CSP-facing communications.** Marketing templates by definition carry promotional and persuasion intent, which PCA prohibits entirely for partner communications. The PCA principle of No Persuasion (P2) and the PayG positioning principle both exclude this template type from all CSP-facing use.

**When it might be used:** Customer-facing (U2) communications only — governed by Marketing / Growth team, not by this agent. See partner-customer boundary rules in pca-enforcement-governance.md (MDG §8).

> **Agent rule:** If a task brief specifies WhatsApp as a channel and the state being communicated is promotional, motivational, or income-related — do not proceed with a Marketing template. The task itself is a PCA violation. Flag to GAPS.md and halt.

---

### 1.3 WhatsApp — Authentication Template

**What it is:** Strictly regulated templates for account verification, OTP delivery, and secure login flows.

**PCA classification for Wiom:** Not a comms design task. Authentication templates are system-generated for login / verification events — not designed through the comms pipeline.

**Technical constraints (for reference):**
- Fixed preset text: `<VERIFICATION_CODE> is your verification code.`
- Optional security disclaimer: `For your security, do not share this code.`
- Optional expiration warning: `This code expires in <NUM_MINUTES> minutes.`
- No URLs, media, or emojis permitted
- Parameters: maximum 15 characters each
- Button options: one-tap autofill, copy code button, or zero-tap (no button)

> **Agent rule:** Authentication templates are outside this agent's scope. If a task involves authentication flows, route to the engineering / product team.

---

## 2. SMS

**What it is:** Text-only messages delivered to the CSP's registered mobile number via standard SMS infrastructure. Used as a fallback when WhatsApp is unavailable or as a secondary channel for action-required states.

**PCA eligibility:** Informational, Attention, Action Required. Not for Integrity or Termination severity — call script is required for those.

**Character limits:**
- Single SMS: 160 characters (GSM-7 encoding, standard Latin characters)
- Unicode SMS (Hindi / Devanagari script): 70 characters per segment
- Multi-part SMS: automatic — networks concatenate up to 6 parts (960 chars GSM-7 / 420 chars Unicode), but delivery reliability drops with length
- **Practical rule:** Keep CSP SMS under 160 characters (English) or 70 characters (Hindi) to ensure single-message delivery and maximum reliability

**Media support:** None. Text only. No images, no links with media previews, no buttons.

**Links:** URLs are supported as plain text but do not generate previews. Shortened URLs reduce character count. Do not use URL shorteners that obscure the domain — TRAI compliance risk.

**Variables / personalisation:** Supported via SMS gateway (DLT-registered templates with variable fields). CSP name, state label, and portal reference can be personalised.

**Opt-in / DLT requirement:**
- All commercial SMS in India must comply with TRAI DLT (Distributed Ledger Technology) regulations
- Templates must be pre-registered on the DLT platform
- Sender ID (header) must be registered — typically a 6-character alphabetic ID (e.g. WIOMCO)
- Transactional SMS: higher delivery priority, can be sent 24 hours
- Promotional SMS: restricted to 09:00–21:00 IST, subject to DND registry scrubbing
- **Classify CSP state communications as Transactional or Service** — not Promotional — to ensure delivery and compliance
- See regulatory-compliance.md for full TRAI DND rules

**Delivery reliability:** Medium-high for transactional. Variable for promotional. Network-dependent. No delivery receipts by default (depends on gateway). No read receipts.

**Cost:** Low. Per-message cost. Bulk rates available. Confirm with ops team.

**Timing restrictions:**
- Transactional / Service messages: 24-hour delivery permitted
- Promotional messages: 09:00–21:00 IST only
- Classify correctly — misclassification is a regulatory violation

**Best use cases for Wiom:**
- Fallback when CSP does not have WhatsApp or has not opted in
- Short action-required alerts (connection request, SLA state change)
- Rate card update advance notice (brief reference + portal link)

**Not permitted for:**
- Long-form state explanations (use dashboard + push instead)
- Economic framing or income commentary
- Enforcement actions (call script required)
- Any message not registered on DLT platform

---

## 3. In-App Push Notification

**What it is:** System-generated notification delivered to the CSP's mobile device via the Wiom partner app. Appears as a push alert when the app is installed and notifications are enabled.

**PCA eligibility:** Attention, Action Required, Integrity. Can carry Informational for high-significance state changes (rate card update, bonus tier change). Not for routine informational states.

**Character limits:**
- Title: 50 characters (truncated on most devices beyond this)
- Body: 100–240 characters depending on device and OS (Android typically shows up to 240 chars in expanded view; iOS shows approximately 100 chars in banner)
- **Practical rule:** Write body copy for 100 characters — ensure the core state information fits before truncation on any device

**Media support:**
- Rich push (if app supports it): single image (JPEG / PNG, recommended 1440 × 720 px, max 1 MB), icon image
- Standard push: text only
- No video, no documents, no buttons beyond deep-link tap action
- **PCA rule:** No emoji in enforcement or state communications

**Deep-linking:** Push notifications should deep-link directly to the relevant dashboard state or enablement resource — not to the app home screen. Reduces friction for action-required states.

**Opt-in requirement:** CSP must have app notifications enabled on their device. Opt-in is device-level — cannot be managed by Wiom directly. Delivery is not guaranteed if CSP has disabled notifications.

**Delivery reliability:** High when notifications are enabled. Delivery drops to zero if disabled. No guaranteed delivery — do not rely on push as the only notification for critical states. Dashboard is the reliable fallback.

**Cost:** Effectively free (app infrastructure cost). No per-message charge.

**Timing restrictions:**
- TRAI DND time restrictions apply to notifications classified as promotional
- Transactional / service push: 24-hour delivery technically possible — but apply 09:00–21:00 IST window for all non-urgent comms
- FPV / Integrity-level events: immediate delivery permitted regardless of time

**Best use cases for Wiom:**
- SLA state change alerts (At Risk, Non-Compliant, Recovery)
- Connection request assignment (action required — high time sensitivity)
- Rate card / bonus tier changes (advance notice)
- FPV detected (immediate, Integrity-level)
- First carry fee accrual alert

**Not permitted for:**
- Motivational or check-in messages
- Repeat notifications for unchanged states within same evaluation window
- More than 2 proactive pushes per CSP per week (hard cap — see comms-principles.md §3.1)
- Economic framing or income commentary

---

## 4. Dashboard

**What it is:** The always-on state display within the Wiom partner app. Automatically reflects current system state for all OS outputs. No design required for standard state displays — these are system-automated. Design is required for banners, notices, and non-automated text elements.

**PCA eligibility:** All severity levels. Dashboard is the universal channel — it carries everything. Push and WhatsApp are selective; dashboard is always.

**Character limits:**
- State labels: defined by system UI — not a copywriting task
- Banner / notice text: 200–300 characters recommended for readability
- Full state description panels: up to 500 characters practical limit before scrolling reduces engagement
- No hard technical limit — but longer text reduces CSP engagement

**Media support:**
- Text, icons (system-defined), status indicators
- No video
- Images in specific sections only (enablement resources, onboarding materials) — confirm with product team
- No emoji in state description text per PCA tone rules

**Personalisation:** CSP name, state label, domain name, threshold values, evaluation window reference — all available via system variables.

**Opt-in requirement:** None. Dashboard is always visible to logged-in CSPs. No opt-in or opt-out.

**Delivery reliability:** Highest of all channels. State is live and always accurate for logged-in users. Does not depend on notifications, device settings, or network at time of send (only at time of viewing).

**Cost:** None per display.

**Timing restrictions:** None. Dashboard is always on. State updates are system-triggered and immediate.

**Text categories on dashboard:**
- **Automated state text:** System-generated from Message Block. Not a design task — must match registered block exactly.
- **Banner / notice text:** Designed by Comms Head, approved per MDG process, deployed for a defined period (typically 7–14 days, then sunset).
- **Enablement resource links:** Functional labels only. No promotional framing.
- **Wallet / compensation display:** Rate card values only. No narrative.

**Best use cases for Wiom:**
- Primary display for all SLA states, routing states, compensation states
- System update notices (persistent banner for 7–14 days)
- Enablement resource surfacing for At-Risk and Non-Compliant CSPs
- Settlement and wallet balance display
- Rate card reference (always current version)

**Always on — never requires a separate push if:**
- The state change is routine and no CSP action is required
- The information is visible in wallet or state panel with no action needed

---

## 5. Call Script

**What it is:** Pre-approved script read by call centre agents when handling inbound CSP calls or outbound calls required by process (e.g. suspension, termination). All call centre communication must reference a registered Message Block ID. No paraphrasing of state descriptions.

**PCA eligibility:** Attention through Termination. Call is required for suspension and termination communications. Call is reactive only for all other states (CSP initiates).

**Character limits:** None technically — but scripts follow escalation compression rules. Higher severity = fewer words. See comms-principles.md §4.

**Media support:** None. Voice only.

**Script structure:**
- Opening: functional greeting + CSP ID confirmation
- State reference: exact language from Message Block (read verbatim for enforcement states)
- Clarification layer: permitted within approved block boundaries only — no improvisation
- Next action: specific, factual
- Closing: clean — reference portal or dashboard for details

**Opt-in / timing:**
- Outbound calls: only for process-required communications (suspension, termination, enablement scheduling)
- No proactive outbound calls for state changes that are already on dashboard
- Timing: 09:00–21:00 IST
- No cold calls, no motivational calls, no check-in calls

**Delivery reliability:** Dependent on CSP answering. Not guaranteed. If CSP does not answer, do not leave voicemail with state details — leave a neutral callback request only.

**Cost:** Medium-high (call centre agent time + telephony cost). Use only when process requires it.

**Key rules:**
- Agent must reference Block ID at the start of enforcement calls: "I'm calling regarding [Block ID reference]."
- Clarification is permitted within the block's clarification layer — agents may explain what a threshold means or how to access enablement resources
- Reinterpretation is not permitted — agents may not soften enforcement language, add reassurance, or make promises
- Economic conversations: if CSP raises compensation questions, agent must redirect: "Rate card is published in your dashboard wallet section."
- Retention conversations: if exiting CSP raises continuation, agent must state: "Exit is valid. Process is in the app." No further discussion.

**Best use cases for Wiom:**
- Suspension and termination notifications (mandatory call for these states)
- Enablement scheduling when required by Non-Compliant state
- Reactive support for CSP-initiated queries about any state
- Asset recovery coordination (NetBox return scheduling)

**Not permitted for:**
- Proactive outreach for SLA states that are already on dashboard
- Economic advice, income commentary, or rate card interpretation
- Retention conversations with exiting CSPs
- Any communication not backed by a registered Message Block

---

## 6. Field Script

**What it is:** Pre-approved guidance used by field teams (BDOs and field agents) during in-person interactions with CSPs — primarily in onboarding visits and reactive support situations. All field communication must reference registered Message Block language for state descriptions. No improvisation on states.

**PCA eligibility:** Informational, Attention. Field teams do not deliver Integrity or Termination communications — those require call script or formal written channel.

**Character limits:** None — verbal delivery. But scripts follow the same word-count discipline as other channels: higher severity = fewer words.

**Media support:** Physical materials (onboarding guides, rate card printouts) — must reflect current PCA-compliant language. No verbal improvisation on content not in the materials.

**Opt-in / timing:**
- Onboarding visits: scheduled, within business hours
- Reactive support visits: CSP-initiated or ops-assigned — not proactive state-delivery visits
- No cold visits for the purpose of delivering state communications already visible on dashboard

**Delivery reliability:** Highest context richness — in-person. But highly variable in compliance — field improvisation is the primary source of PCA drift. See regulatory-compliance.md and pca-enforcement-governance.md §13.

**Cost:** Highest of all channels (field agent time + travel). Use for onboarding and physical issues only — not as a channel for messaging work.

**Key rules:**
- For state communications: field agent reads from approved Message Block — no paraphrasing
- Clarification is permitted within the block's clarification layer only
- No verbal promises on routing, income, or connection growth
- No interpretation of enforcement consequences
- If CSP asks about something not covered in the approved block: "I'll confirm with the system — you can also see this in your dashboard."
- Field agents do not deliver suspension or termination communications — those are system + call script

**Best use cases for Wiom:**
- New CSP onboarding (Day 1 activation visit, NetBox setup)
- Reactive support for physical issues (NetBox malfunction, connectivity investigation)
- Enablement delivery when digital channel has not been effective and Capability Development OS has flagged for field support

**Not permitted for:**
- Delivering SLA state changes that are already on dashboard
- Economic conversations beyond "rate card is in the app"
- Enforcement communications of any kind
- Any verbal commitment not grounded in a registered Message Block or published system state

---

## 7. Channel Selection Decision Logic

When the design task does not specify a channel, use this logic:

**Step 1: Is the state already on the dashboard?**
→ Yes, and no CSP action required → Dashboard only. No push, no WhatsApp.
→ Yes, but CSP action required → Dashboard + one push notification or WhatsApp Utility.

**Step 2: Does the state require immediate CSP awareness?**
→ Yes (FPV, connection request, SLA threshold crossing) → Push notification (primary) + dashboard.
→ No (rate card update, bonus tier change) → Dashboard + scheduled push with advance notice period.

**Step 3: Does the process require direct verbal or written confirmation?**
→ Yes (suspension, termination) → Call script mandatory. Push + dashboard also active.
→ No → Do not use call script proactively.

**Step 4: Does the CSP need to take a physical action?**
→ Yes (NetBox return, enablement scheduling) → WhatsApp Utility template for logistics coordination. Field script if in-person coordination needed.
→ No → No WhatsApp required unless state change notification is warranted.

**Step 5: Does the CSP not have WhatsApp or push notifications enabled?**
→ SMS as fallback for action-required states only. Keep under 160 characters. Confirm DLT registration.

---

## 8. Quick Reference — Limits and Constraints

| Channel | Body Char Limit | Media | Opt-in Required | Cost Level | Timing Restriction |
|---|---|---|---|---|---|
| WhatsApp Utility | 1,024 (body) | Image, video, doc (header only) | Yes — WhatsApp opt-in | Medium | 09:00–21:00 IST recommended |
| WhatsApp Marketing | N/A | N/A | N/A | N/A | **NOT ELIGIBLE for CSP comms** |
| WhatsApp Authentication | System-generated | None | N/A | Low | Anytime |
| SMS (English) | 160 per segment | None | DLT registration | Low | 09:00–21:00 IST (promotional) / 24hr (transactional) |
| SMS (Hindi / Unicode) | 70 per segment | None | DLT registration | Low | As above |
| Push Notification | ~100 chars visible | Rich image optional | Device notifications on | Free | 09:00–21:00 IST / immediate for FPV |
| Dashboard | ~300 chars practical | Text + icons | None | Free | Always on |
| Call Script | No limit (verbal) | None | None (inbound) / TRAI (outbound) | High | 09:00–21:00 IST |
| Field Script | No limit (verbal) | Physical materials | None | Highest | Business hours |

---

*channel-specs.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Ops / Channel team*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
