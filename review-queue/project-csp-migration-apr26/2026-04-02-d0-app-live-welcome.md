# COMMS DESIGN BRIEF
Status: PENDING HUMAN APPROVAL

---

## HEADER

Date              : 2026-04-02
Project ID        : project-csp-migration-apr26
Message Ref       : M6 (D0: App is Live, Your State is Ready)
Task type         : design
Designed by       : Claude — agent session
Block ID          : new block required — M6 is a journey communication,
                    not a structural state translation. No registered
                    Message Block exists for this message type.
                    MGO approval required before deployment.
PCA version       : 1.0

---

## SECTION 1 — BEHAVIOURAL OBJECTIVE

What action this message drives:
Get partner to download/update and open the new Wiom app for the first
time and see their dashboard (pending tickets, rate card, device state).

What this message is NOT trying to do:
Not trying to explain the full earning structure, bonus mechanics, or
quality score. Those are M7-M9. This message has one job: get the app
on the phone and the dashboard on the screen.

---

## SECTION 2 — AUDIENCE

Segment             : SEG-01 / SEG-03 (New to new system + Active Compliant
                      CSPs transitioning to new operating model)
Size                : ~1,200 partners
Current state       : Active CSPs on legacy system, transitioning to
                      new system-governed model on launch day
Language            : Hindi-primary. Hinglish acceptable for app UI terms.
Geography           : Delhi NCR, Bharat tier-2, Mumbai
Behavioural note    : Primary motivation is work (tickets and installation
                      requests). App download instruction must be crystal
                      clear. Partner will act if it connects to getting work.

Product dependency  : Dashboard with pending tickets, rate card display,
                      Trust Line number visible on dashboard
Dependency status   : PENDING — do not send until product confirms dashboard
                      is live with tickets, rate card, and Trust Line number

---

## SECTION 3 — CHANNEL AND RATIONALE

Channel             : WhatsApp Utility
Why this channel    : Launch day action required (download/open app).
                      WhatsApp reaches this audience immediately. Utility
                      classification because this is a system migration
                      notification requiring CSP action, not a promotional
                      message. Old app will show redirect screen from this
                      point — WhatsApp provides the bridge.
Message classification : Service (system migration notification requiring
                         action — new app replaces old app)
Send window         : Morning of launch day, within 09:00-12:00 IST
                      (catch partners before they open old app)
Cooling period      : No prior WhatsApp sent in this project (first message
                      via this channel in the migration sequence). Next
                      WhatsApp (M7 in-app cards) is in-app, not push.
Fallback channel    : SMS cascade at 24hrs if WhatsApp unread.
                      Old app redirect screen as passive fallback.

---

## SECTION 4 — MESSAGE COPY

### English

Header  : Wiom App: Your Dashboard is Ready
Body    :

Hello [CSP_Name],

The new Wiom app is now live. Your old app will no longer work from today.

What to do now:
1. Download the new Wiom app: [app_download_link]
2. Open the app and check your dashboard

Your dashboard shows:
- Your pending connection requests
- Your rate card (Rs 300 per connection)
- Your NetBox status

For any issue, call the Trust Line: [trust_line_number]

All information about how the new system works is available anytime:
Settings > Wiom Paathshala

Footer  : Wiom — System Update
Button  : Download App

Character count (body) : ~448 / 1024 chars used

---

### Hindi

Header  : Wiom App: आपका डैशबोर्ड तैयार है
Body    :

नमस्ते [CSP_Name],

नया Wiom app अब लाइव है। पुराना app आज से काम नहीं करेगा।

अभी क्या करें:
1. नया Wiom app डाउनलोड करें: [app_download_link]
2. App खोलें और अपना डैशबोर्ड देखें

आपके डैशबोर्ड पर दिखेगा:
- आपकी पेंडिंग कनेक्शन रिक्वेस्ट
- आपका रेट कार्ड (Rs 300 प्रति कनेक्शन)
- आपका NetBox स्टेटस

किसी भी समस्या के लिए Trust Line पर कॉल करें: [trust_line_number]

नई सिस्टम कैसे काम करती है, यह जानकारी कभी भी देखें:
Settings > Wiom Paathshala

Footer  : Wiom — सिस्टम अपडेट
Button  : App डाउनलोड करें

Character count (body) : ~412 chars (Unicode — within single-message
                         delivery threshold of ~450 chars for reliable
                         WhatsApp delivery)

Hindi vocabulary check :
  [x] No forbidden Hindi terms (ग्राहक, लीड, पेनल्टी, टारगेट, निकाला)
  [x] Canonical Hindi terms used: कनेक्शन रिक्वेस्ट, रेट कार्ड, NetBox
  [x] Tone: neutral-professional — factual, directive, no warmth drift

---

## SECTION 5 — TIMING AND SEQUENCING

Trigger condition   : App goes live (product confirms dashboard is ready
                      with tickets, rate card, Trust Line). Do not send
                      before product confirmation.
Send timing         : Morning of launch day, 09:00-12:00 IST.
                      Batch send to all ~1,200 CSPs.
Sequence position   : M4 (video + quiz) and M5 (download instructions)
                      should have been sent before this. This is the
                      "app is live, go now" message.
What comes next     : M7 — in-app progressive dashboard cards (triggered
                      by first app open, not by WhatsApp). M8 — telemetry
                      nudge at Day 3-5 post-launch.
Stopping rule       : Send once. No repeat. If partner does not open app
                      within 48hrs, SMS cascade triggers (separate flow).
Dependencies        : M4 (video + quiz) should be completed by partner.
                      M5 (download instructions) should have been sent.
                      Dashboard must be live with tickets visible.

---

## SECTION 6 — MEASUREMENT PLAN

Primary metric      : App download/update rate within 24 hours of send
Target              : >70% of ~1,200 CSPs have new app installed within
                      24 hours (840+ partners)
Measurement window  : 24 hours post-send, then 48 hours, then 7 days
Data source         : App analytics — new app install/first-open events.
                      Cross-reference with WhatsApp delivery + read receipts
                      via Gupshup delivery reports.
Review date         : Launch day + 1 (immediate), Launch day + 7 (full)
Secondary metric    : PTL call volume on launch day. Target: no spike
                      above baseline. If spike >20% above 7-day average,
                      review message clarity and dashboard readiness.

---

## PATTERNS APPLIED

Playbook pending — onboarding-playbook.md not yet created.
Designed from L1 globals only.

Applied from L1:
  Pattern 1: Single behavioural objective per message (comms-principles P1).
             This message does one thing: get the app open.
  Pattern 2: Push-to-pull architecture (push-to-pull-rules.md).
             WhatsApp pushes to app (pull channel). CTA directs to dashboard.
             Wiom Paathshala referenced as permanent pull destination.
  Pattern 3: Progressive disclosure (brief design principle 5).
             Dashboard shows tickets first (work), rate card second,
             device status third. This message does not explain any of
             these — it just gets the partner to the screen.

## MISTAKES AVOIDED

Playbook pending — no documented mistakes available from L2.

Checked against L1 and project brief:
  Checked: No hard date used. Message says "अब लाइव है" (now live),
           not a specific date. Complies with Design Principle 2.
  Checked: No earning explanation in this message. Rate card is mentioned
           as a dashboard item ("Rs 300 per connection") but not explained.
           Full earning structure is M7-M9 territory.
  Checked: No information dump. Message has 3 dashboard items only.
           Does not mention bonus, quality score, carry fee, or enforcement.
  Checked: Self-contained message. Partner does not need to call anyone
           to understand what to do (Design Principle 7). Trust Line
           provided only as fallback for issues.

---

## QUALITY CHECK

QUALITY-CHECKLIST.md run in full.

Section 1 (all outputs):
  [x] 1.1 Format — follows OUTPUT-TEMPLATES.md Template 1
  [x] 1.2 Destination — review-queue/project-csp-migration-apr26/
  [x] 1.3 Completeness — all fields filled, product dependency marked PENDING
  [x] 1.4 Clarity — readable by reviewer unfamiliar with project

Section 2 (design outputs):
  [x] 2.1 Behavioural objective — one action: download and open app
  [x] 2.2 Channel fit — WhatsApp Utility, within 1024 char limit
  [x] 2.3 Audience fit — Hindi-primary, simple language, no jargon
  [x] 2.4 Playbook compliance — N/A, playbook PENDING
  [x] 2.5 PayG positioning — "Rs 300 per connection" (recharge-based
        rate card reference, no subscription framing)
  [x] 2.6 CTA — "Download App" button, directs to specific action
  [x] 2.7 Measurement plan — app install rate, 24hr window, app analytics
  [x] 2.8 Fatigue check — no prior messages sent in this project

QUALITY CHECK: FLAG
  2.4 — Playbook not available (onboarding-playbook.md PENDING).
        Designed from L1 globals only. Human to note this is expected
        at current repo maturity. No action required unless playbook
        is created before deployment.

---

## SECURITY CHECK

SECURITY-RULES.md self-check run in full.

PayG check:
  [x] No word implies monthly plans or subscription
  [x] "Rs 300 per connection" is rate card language, not monthly fee
  [x] No reader could mistake this for a traditional ISP message

PCA check:
  [x] No PCA banned vocabulary used
  [x] Tone within Neutral-Professional band
  [x] No registered Message Block exists for this journey state (noted)
  [x] Hindi follows vocabulary lock — कनेक्शन रिक्वेस्ट, रेट कार्ड used
  [x] No economic content beyond rate card reference — 5 prohibitions pass

Regulatory check:
  [x] Message classified as Service (system migration notification)
  [x] Send window 09:00-12:00 IST — compliant

Data check:
  [x] No PII beyond CSP first name (personalisation variable)
  [x] No internal financial or system data
  [x] Output written to review-queue/ (authorised location)

Deployment check:
  [x] Output in review-queue/, not sent to any channel
  [x] Status clearly shows PENDING HUMAN APPROVAL

Quality check:
  [x] Read as recipient — clear what to do (download app, open dashboard)
  [x] Objective clear from message alone
  [x] Tone consistent with PCA envelope
  [x] Format matches OUTPUT-TEMPLATES.md

SECURITY CHECK: PASS — all six rule areas checked, no violations.

---

Status: PENDING HUMAN APPROVAL
Next step: Human reviews copy, approves or requests changes,
then deploys via Gupshup / WhatsApp Business API.
After deployment: run logger-agent to append to comms-log.md.

---

GAPS LOGGED THIS SESSION:
  1. regulatory-compliance.md missing from L1 (flagged to human)
  2. onboarding-playbook.md PENDING (expected — no L2 patterns available)
  3. comms-log.md does not exist yet (expected — no messages sent)
  4. Block ID not assigned — M6 is a journey comm, not a structural
     state translation. MGO to assign Block ID before deployment.
