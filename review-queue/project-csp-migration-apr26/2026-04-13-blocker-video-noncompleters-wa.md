# Comms Brief — project-csp-migration-apr26 — 2026-04-13

MODE        : Mode 2 — Standalone
REQUESTED_BY: not provided
OS_TRIGGER  : Education/onboarding campaign — CSP migration (project-csp-migration-apr26)
TASK_TYPE   : design
TASK_SUBTYPE: single

---

## Message

नमस्ते {{1}},

Wiom का नया app लॉन्च हो गया है। नए app में access के लिए system को एक ज़रूरी वीडियो का पूरा होना आवश्यक है।

आपके record में यह वीडियो अभी pending है। इसके बिना नए app का access available नहीं है।

आपको क्या करना है:
1. पुराना Wiom app खोलें
2. वीडियो अपने आप शुरू हो जाएगी
3. पूरी वीडियो देखें — 2 मिनट 10 सेकंड
4. वीडियो पूरी होने पर नए app का access मिल जाएगा

यह step उन सभी CSPs के लिए है जिन्होंने अभी तक वीडियो पूरी नहीं की है।

किसी सवाल के लिए Trust Line पर संपर्क करें: [Trust Line number]

Message classification : Service — system access state communication, not promotional
Character count        : ~450 characters — within WhatsApp Utility body limit (1,024)

---

## Channel

WhatsApp Utility template. This is a process-step notification tied to a specific system state (app launched, video completion pending). Operational content, not promotional. Utility template prevents Marketing auto-reclassification risk. Audience has opted in to WA communications per campaign setup.

---

## Audience

S0/S1 CSPs on project-csp-migration-apr26. Partners who have not completed the blocker video (2:10) deployed 07/04. Estimated ~855+ partners. Hindi-primary. The new app launched ~12/04 and these partners are currently locked out. This is the second WA nudge to this segment (first sent 09/04). OWNERs and ADMINs only — Technicians excluded per campaign design.

---

## Recipient analysis

Message type        : Type B — Operational/Logistics

Questions that block action:
  "Why can't I access the new app?"
    → Answered in context paragraph: system requires video completion before new app access.
  "How do I watch the video?"
    → Answered in steps 1–2: open old app, video plays automatically.

Hesitations that block action:
  Singling-out concern — "Why am I being contacted specifically?"
    → Addressed by normalisation line (paragraph 4): "यह step उन सभी CSPs के लिए है..."
  Time concern — "How long will this take?"
    → Addressed in step 3: 2 मिनट 10 सेकंड, explicit.

Operational details for action:
  Access path : Open old Wiom app — blocker video appears automatically. Source: human-confirmed.
  Duration    : 2 minutes 10 seconds. Source: context-from-teams.md video script structure.
  After       : New app access becomes available upon completion. Source: campaign architecture.
  Cost        : None to CSP. Source: campaign design (no cost mechanic for education steps).

---

## Information architecture

Flow: Context → Relevance → Action → Normalisation

Mapping:
  Context       = Paragraph 1 ("Wiom का नया app लॉन्च हो गया है...")
  Relevance     = Paragraph 2 ("आपके record में यह वीडियो अभी pending है...")
  Action        = Numbered list ("आपको क्या करना है:", steps 1–4)
  Normalisation = Paragraph 4 ("यह step उन सभी CSPs के लिए है...")

Note: HOW IT WORKS is embedded within the action steps (steps 1–2 describe mechanism; steps 3–4 describe what CSP does). For a 4-step numbered list in WA format, a separate HOW header would reduce scannability without adding clarity.

---

## Objective

CSP opens old app and completes the 2:10 blocker video, moving from S0/S1 to S2 state, which unlocks new app access.

---

## How this connects to the project

The campaign's primary measurable target is 100% blocker video completion. As of 10/04, full completion was 18.9% (199 of ~1,054 starters). This message targets the ~855+ remaining non-completers now that the app has launched and the consequence (access lock) is live. Moving these partners to S2 is a prerequisite for them to proceed to quiz and new app transition.

---

## Patterns applied

L1 PCA principles only for content and tone (no domain OS playbook for education campaign comms). Information architecture follows Operational Message Architecture from design-agent.md v1.1: context before ask, embedded friction reduction, normalisation line. Campaign communication tone from context-from-teams.md: "Calm, neutral. Zaroori update — not alarming."

---

## Mistakes avoided

From campaign context (context-from-teams.md):
  Do not explain SLA mechanics — confirmed: not mentioned.
  Do not give Mbps numbers — confirmed: not mentioned.
  Do not promise area stability — confirmed: not mentioned.
  Do not mention enforcement dates yet — confirmed: not mentioned.

From PCA §11 (economic prohibitions):
  No income framing — confirmed: no economic content.

From SECURITY-RULES.md Rule 1:
  No subscription/monthly ISP framing — confirmed: not present.

---

## PCA compliance

Canonical vocabulary used (PCA §3)     : YES — no forbidden terms. "CSPs" used correctly.
Tone envelope respected (PCA §4)        : YES — Neutral-Professional throughout. No warmth, no cold, no urgency.
Registered Message Blocks (PCA §6)      : N/A — this is an education/onboarding campaign message, not an OS state machine transition. No registered block required.
Anti-contamination tests (PCA §8)       : ALL 8 PASS

  1. Structural source : App launch + mandatory video completion requirement. PASS.
  2. Persuasion        : No emotional appeal. No motivation language. No "please". PASS.
  3. Economic signal   : No income, earnings, or rate card mention. PASS.
  4. Role integrity    : CSP as system participant. Not customer, not friend, not employee. PASS.
  5. Impersonal auth.  : "system को आवश्यक है", "access available नहीं है" — system as subject. PASS.
  6. Calm              : No urgency, no deadline framing, no countdown. PASS.
  7. Dignity           : Factual, direct. No patronising, no apology, no blame. PASS.
  8. Vocabulary        : No forbidden terms. Hindi lock: no ग्राहक, no पेनल्टी, no जुर्माना. PASS.

---

## Fatigue check

Was comms-log checked?    : YES
Last similar message      : Entry 4 — WA Push (non-completers) — 2026-04-09 — 4 days ago
Fatigue risk              : MEDIUM — same channel, same audience, 4 days apart (under 7-day window). However, the situation has materially changed: the app has now launched and access lock is live. The consequence described on 09/04 was future; this message describes present state. This is a new state communication, not a repeat nudge. Fatigue risk is accepted given changed context. Deploying team should confirm.

---

## Measurement plan

Metric     : S2 conversion rate — partners who complete blocker video after this message send
Target     : Meaningful increase from 18.9% baseline; campaign target is 100%
Timeframe  : Measure 48 hours post-send (CleverTap event lag considered)
Data source: CleverTap — blocker_video_completed event; cross-reference with campaign dashboard https://shivakimothi-design.github.io/csp-comms-dashboard/

---

## Tone notes

Hindi-primary per audience geography and campaign convention. No Hinglish mixing beyond established technical terms ("app", "record", "pending", "step", "Trust Line") which appear across existing campaign communications. Register: plain, functional. No formal honorifics beyond standard "आपको" / "आपके". No closing warmth. Consistent with campaign tone from context-from-teams.md: "Zaroori update, not alarming."

---

## Pre-deployment checklist

  [ ] DND scrubbing required before send — Classified as Service; confirm with legal whether DND scrub required. Recommend applying as precaution.
  [ ] Send time: proposed 10:00–18:00 IST — within 09:00–21:00 IST window
  [ ] Opt-out mechanism: N/A for Service classification — confirm classification with legal before deploying
  [ ] Audience list verified: confirm S0/S1 segment pull from CleverTap before deploying. Exclude S2+ partners.
  [ ] Trust Line number: insert actual number before submitting template for WA API approval
  [ ] WA Utility template: submit for Meta approval before send. Template must be registered before first use.
  [ ] {{1}} variable: confirm CSP name field mapping in Gupshup / WA API before send

---

QUALITY CHECK   : PASS — all sections complete, single objective, PCA vocabulary enforced, measurement plan with data source, fatigue check with reasoning, channel-compliant format
SECURITY CHECK  : PASS — all six rule areas checked: PayG (no subscription framing), PCA (all 8 anti-contamination pass), regulatory (Service classification, 09:00–21:00 window), data (no PII beyond name variable), deployment (output to review-queue, pending human approval)
