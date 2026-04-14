# COMMS DESIGN BRIEF
Status: PENDING HUMAN APPROVAL
MODE 2 — STANDALONE. No project history available.

---

## HEADER

Date              : 2026-04-13
Project ID        : adhoc
Message Ref       : adhoc
Task type         : design
Designed by       : Claude — agent session
Block ID          : new block required — no registered Message Block exists for PNM installation
PCA version       : 1.0

---

## Message

### Hindi (primary)

Header  : Wiom System Update
Body    :

कस्टमर्स की इंटरनेट दिक्कतों को जल्दी पहचानने और जल्दी ठीक करने के लिए Wiom सिस्टम द्वारा आपकी लोकेशन पर एक नेटवर्क मॉनिटरिंग डिवाइस लगाया जाएगा।

इससे नेटवर्क में आने वाली समस्याओं को जल्दी समझना और उन्हें ठीक करना आसान होगा, ताकि कनेक्शन्स को बेहतर इंटरनेट सर्विस मिलती रहे।

कैसे होगा?
Wiom सिस्टम द्वारा एक तकनीशियन आपके यहाँ आकर यह डिवाइस लगाएगा। इसमें सिर्फ 15–20 मिनट लगेंगे। इस डिवाइस को चलाने के लिए इंटरनेट की ज़रूरत होगी, जिसका खर्चा Wiom उठाएगा।

आपको क्या करना है?
Wiom सिस्टम द्वारा आपको कॉल आएगी — उस पर अपने हिसाब से विज़िट का समय कन्फर्म कर दें। विज़िट के समय OLT के पास जगह और power socket उपलब्ध रखें। डिवाइस लगने के बाद कृपया उसे हमेशा चालू रखें।

Wiom सिस्टम के साथ काम करने के लिए यह सेटअप सभी CSP लोकेशन्स पर किया जा रहा है।

Footer  : Wiom
Button  : N/A

Character count (body) : ~520 chars (Hindi Unicode — within WhatsApp 1024 char body limit)

Message classification : Service — system-initiated operational communication for infrastructure deployment. Not promotional. Not transactional.

---

### English (reference translation — not for deployment)

Header  : Wiom System Update
Body    :

To detect and resolve internet issues for connections faster, the Wiom system will install a network monitoring device at your location.

This will make it easier to identify and fix network problems quickly, so connections continue to receive stable internet service.

How will this work?
A technician from the Wiom system will visit your location to install the device. It will take only 15–20 minutes. The device requires internet to operate, and Wiom will bear this cost.

What you need to do:
You will receive a call from the Wiom system — confirm a visit time that works for you. At the time of the visit, ensure space near the OLT and a power socket are available. After installation, please keep the device switched on at all times.

This setup is being done at all CSP locations as part of the Wiom system process.

Footer  : Wiom

---

## Channel

Channel             : WhatsApp Utility
Why this channel    : CSP awareness is required for an operational change at their physical location. The message is informational with a follow-up action (confirm visit time via call). WhatsApp ensures delivery and read confirmation. The scheduling action itself happens via phone call (not WhatsApp reply), so WhatsApp serves as advance notice and preparation instruction.
Send window         : 09:00–21:00 IST
Fallback channel    : SMS with shortened version if WhatsApp undelivered after 24 hours.

---

## Audience

Segment             : All active CSPs (SEG-03 through SEG-06 — all SLA states)
Size                : To be confirmed by ops team before deployment
Current state       : All active, no structural state filter
Language            : Hindi-primary
Geography           : All (phased rollout — geography batches defined by ops)

---

## Recipient analysis

Message type        : Type B — Operational / Logistics Communication

Questions that block action:
  1. Why is a device being installed? → Answered in CONTEXT paragraph: "to detect and resolve internet issues faster"
  2. How will it happen and how long? → Answered in HOW section: technician visits, 15-20 minutes
  3. Will it cost me anything? → Answered in HOW section: "Wiom will bear this cost"
  4. What do I need to do? → Answered in ACTION section: confirm call, prepare space + power, keep device on

Hesitations that block action:
  Cost concern → "जिसका खर्चा Wiom उठाएगा" embedded in HOW paragraph. CSP knows upfront there is no expense.
  Time/disruption concern → "सिर्फ 15–20 मिनट" embedded in HOW paragraph. Minimal disruption signalled.
  Singling-out concern → "यह सेटअप सभी CSP लोकेशन्स पर किया जा रहा है" in NORMALISATION closing. Standard, not targeted.
  Ongoing obligation concern → "हमेशा चालू रखें" in ACTION section. Clear, one-line ongoing obligation stated upfront.

Operational details for action:
  Duration: 15-20 minutes (human-confirmed)
  Placement: near OLT, needs power socket (human-confirmed)
  Internet cost: Wiom bears it (human-confirmed)
  Scheduling: Wiom system calls CSP, CSP confirms time (human-confirmed)
  Ongoing: keep device always on (human-confirmed as implied)

---

## Information architecture

Flow: Context → Relevance → How → Action → Normalisation (Operational Message Architecture, Type B)

Mapping:
  CONTEXT       = Paragraph 1 ("कस्टमर्स की इंटरनेट दिक्कतों को जल्दी पहचानने...")
  RELEVANCE     = Paragraph 2 ("इससे नेटवर्क में आने वाली समस्याओं को...")
  HOW           = Paragraph 3 under "कैसे होगा?" label — includes duration, cost, who does what
  ACTION        = Paragraph 4 under "आपको क्या करना है?" label — confirm call, prepare site, keep on
  NORMALISATION = Closing line ("यह सेटअप सभी CSP लोकेशन्स पर किया जा रहा है")

---

## Objective

Get CSP to confirm a technician visit time when called, prepare the site (space near OLT + power socket), and keep the device on after installation.

---

## How this connects to the project

One-off operational deployment. Enables network monitoring infrastructure across all CSP locations, which supports the Quality OS by providing diagnostic data for faster issue detection and resolution.

---

## Patterns applied

Playbook pending — no OS playbook loaded. Designed from L1 PCA governance only.

  Pattern 1: Operational Message Architecture (Context → Relevance → How → Action → Normalisation) — new design agent pattern for Type B communications
  Pattern 2: Friction reduction embedded in operational detail — cost and time concerns addressed within the "how" section, not as separate reassurance
  Pattern 3: Normalisation closing — standard system process framing to prevent singling-out perception

---

## Mistakes avoided

  Checked: No motivational framing ("this will help you serve better") — PCA §2, P2
  Checked: No economic framing or income implication — PCA §11
  Checked: No warmth beyond dignity ("we're excited to bring this") — PCA §4, P7
  Checked: No jumping to action without context — design agent guardrail
  Checked: No unanswered action-blocking questions — recipient analysis complete
  Checked: No generic "inform + CTA" — operational details included

---

## PCA compliance

  Canonical vocabulary used (PCA §3) — YES. "कनेक्शन्स" used instead of "ग्राहक" for end-users in service context. "CSP" used instead of "पार्टनर" as identity. No forbidden terms.
  Tone envelope respected (PCA §4) — YES. Neutral-professional. Factual. No warmth drift, no motivational language.
  Registered Message Blocks used (PCA §6) — N/A. No block exists for PNM installation. FLAG: new block required before deployment.
  Anti-contamination tests passed (PCA §8) — ALL 8 PASS:
    1. Structural Source: System-initiated infrastructure deployment ✓
    2. Persuasion: No attempt to convince or emotionally influence ✓
    3. Economic Signal: No economic expectation created ✓
    4. Role Integrity: CSP treated as location operator, not customer ✓
    5. Impersonal Authority: "Wiom सिस्टम द्वारा" — system as subject throughout ✓
    6. Calm: Would not cause anxiety at 10pm ✓
    7. Dignity: No patronising, grading, or blaming ✓
    8. Vocabulary: No forbidden terms ✓

---

## Fatigue check

Was comms-log checked? NO — one-off adhoc task, no project history.
Last similar message to this audience: none found (first PNM installation comm)
Fatigue risk: LOW — new operational message type, no competing comms.

---

## Measurement plan

Metric    : Visit confirmation rate — percentage of CSPs who confirm a time slot when called
Target    : >60% confirmation on first call attempt
Timeframe : 7 days per rollout batch
Data source: Ops team call log / CRM tracking (manual or system)

---

## Tone notes

Hindi-primary. Formal Hindi register with English technical terms retained where operationally understood (OLT, power socket, CSP). "Wiom सिस्टम द्वारा" used consistently as subject to maintain impersonal authority per PCA §5. Functional greeting omitted — message opens with context (system update format). Labels ("कैसे होगा?", "आपको क्या करना है?") break the message into scannable sections for WhatsApp readability.

---

## Pre-deployment checklist

  [ ] DND scrubbing required — NO (Service classification)
  [ ] Send time: within 09:00–21:00 IST — YES
  [ ] Opt-out mechanism: N/A for service communication
  [ ] Audience list verified: PENDING — ops team to confirm rollout batch
  [ ] PNM hardware available for batch geography: PENDING
  [ ] Technician call capacity confirmed for batch: PENDING
  [ ] New Message Block approved: PENDING — required before deployment

---

## Friction audit result

  Cost: ADDRESSED — "जिसका खर्चा Wiom उठाएगा" in HOW section
  Time: ADDRESSED — "सिर्फ 15–20 मिनट" in HOW section
  Targeting: ADDRESSED — normalisation closing line
  Control: ADDRESSED — clear description of what happens (technician installs, CSP keeps on)
  Obligations: ADDRESSED — "हमेशा चालू रखें" in ACTION section

  Normalisation: PRESENT — closing line confirms all CSP locations

---

QUALITY CHECK: PASS
All checklist items verified. Output is ready for human review.

NOTE: New Message Block required — no registered block exists for PNM installation. Must be approved before deployment.

---

SECURITY CHECK: PASS — all six rule areas checked, no violations.

  PayG check: No monthly/subscription framing. PASS.
  PCA check: All 8 tests passed. Vocabulary clean. Tone within envelope. PASS.
  Regulatory check: Service classification. Within send window. PASS.
  Data check: No PII beyond [CSP_name] variable placeholder (not used in this message). PASS.
  Deployment check: Output in review-queue/adhoc/. Pending human approval. PASS.
  Quality check: Objective clear, channel justified, architecture followed, measurement present. PASS.

---

Status: PENDING HUMAN APPROVAL
Next step: Human reviews copy, approves or requests changes, then deploys via Gupshup / WhatsApp Business API.
After deployment: run logger-agent to log. Consider creating a project if this becomes a recurring comm type.
