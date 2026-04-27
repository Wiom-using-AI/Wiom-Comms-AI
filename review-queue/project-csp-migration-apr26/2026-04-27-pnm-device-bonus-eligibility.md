# COMMS DESIGN BRIEF
Status: PENDING HUMAN APPROVAL

---

## HEADER

Date              : 2026-04-27
Project ID        : project-csp-migration-apr26
Message Ref       : M8 (Telemetry Nudge — Bonus Consequence Stated)
Task type         : design
Designed by       : Claude — agent session (v2 — rewritten with confirmed
                    support process and recall-aware framing)
Block ID          : New block required — no registered Block ID exists
                    for PNM device + bonus eligibility state in current
                    block library. Requires MGO approval before this
                    wording becomes a reusable canonical block.
PCA version       : 1.0

---

## SECTION 1 — BEHAVIOURAL OBJECTIVE

What action or belief change this message drives:
Get every active CSP to understand that their PNM device (already
installed in their office) must stay ON for bonus eligibility to
remain active — and to know exactly what to do if the device has
an issue.

What this message is NOT trying to do:
Not trying to re-explain the full bonus structure. Not asking for
any confirmation or technician visit. Not a first-time education
moment — it is a recall-aware reminder for partners who have seen
the blocker video but may not have retained the PNM-bonus link.

---

## SECTION 2 — AUDIENCE

Segment             : Active CSPs — OWNERs and ADMINs
Size                : ~1,400
Current state       : Post-launch. 90% have seen the blocker video
                      (Entry 2) which covers PNM device. Retention of
                      the PNM-bonus link is uncertain — message is
                      designed for a partner who saw the video but has
                      not retained this specific detail. Do not assume
                      recall.
Language            : Hindi-primary
Geography           : All (Delhi NCR, Bharat tier-2, Mumbai)
Behavioural note    : Primary motivation is work (tickets), not
                      earnings education. Message must be brief, factual,
                      and self-contained. One-line context re-anchor
                      before the condition and action.

Product dependency  : PNM device physically installed at partner
                      premises (pre-existing operational dependency)
Dependency status   : CONFIRMED — pre-launch infrastructure.

---

## SECTION 3 — CHANNEL AND RATIONALE

Channel             : WhatsApp Utility
Why this channel    : Primary post-launch nudge channel for this
                      project. Partner has received prior comms here.
                      Appropriate for a brief operational condition
                      statement that must reach all active CSPs.
Message classification : Service — communicates an operational
                         condition of the quality measurement system.
                         (Human to confirm against TRAI consent records
                         before deployment — same recurring flag as
                         Entries 3 and 7.)
Send window         : 09:00–21:00 IST
Cooling period      : Entry 7 sent 2026-04-20 (7 days ago). Clear.
                      Watch for cumulative WA fatigue — this will be
                      the 3rd WA message in ~18 days for some partners.
Fallback channel    : SMS cascade at 24hrs for unread WhatsApp

---

## SECTION 4 — MESSAGE COPY

### English

Header  : PNM Device — Bonus Eligibility

Body    : There is a PNM device installed at your office. This device
          measures internet quality — and that measurement is what
          determines your bonus eligibility each month.

          Device ON: quality data captured. Bonus eligibility active
          per rate card.
          Device OFF: quality data not captured. Bonus eligibility
          paused.

          Keep your PNM device ON at all times.

          Device not working? Call PTL: 7836811111

Footer  : N/A
Button  : N/A

Character count (body) : ~370 chars / 1024 chars used

---

### Hindi

Header  : PNM Device — Bonus Eligibility

Body    : आपके office में PNM device लगा है। यह device internet
          quality का data measure करता है — यही data आपकी bonus
          eligibility decide करता है।

          Device ON → Quality data capture active → Bonus eligibility
          rate card के अनुसार
          Device बंद → Quality data capture बंद → Bonus eligibility
          paused

          PNM device हमेशा ON रखें।

          Device काम नहीं कर रहा? PTL पर call करें: 7836811111

Footer  : N/A
Button  : N/A

Character count (body) : ~310 chars (Unicode) — single-message delivery
                          expected. Verify on device before sending.

Hindi vocabulary check :
  ☑ No forbidden Hindi terms (ग्राहक, लीड, पेनल्टी, टारगेट, निकाला)
  ☑ Canonical Hindi terms used where applicable
  ☑ Tone: neutral-professional — no warmth drift, no cold indifference

Recall design note: The opening line "आपके office में PNM device लगा है"
re-anchors the partner without assuming they remember the video or the
device's purpose. The relevance ("यही data आपकी bonus eligibility decide
करता है") is stated in the same breath — one line, not a full re-education.
This follows the contextual/journey-based principle: assume the partner
saw the prior content but may not have retained this specific link.

Note on "internet quality": Consistent with prior deployed comms in this
project (Entry 1 popup, quiz Q3/Q4). PCA canonical is "Service Stability"
— flag if canonical enforcement is introduced uniformly.

---

## SECTION 5 — TIMING AND SEQUENCING

Trigger condition   : Human decision — broadcast to all active CSPs.
                      No automated system trigger.
Send timing         : On human approval, within 09:00–21:00 IST
Sequence position   : Post-launch Day ~15. Follows Entry 6 (quiz,
                      2026-04-15) and Entry 7 (nudge to non-attempters,
                      2026-04-20). First direct communication connecting
                      PNM device status to bonus for the full audience.
What comes next     : M9 (Bonus Cycle Nudge) — requires quality score
                      screen confirmed live before sending.
Stopping rule       : No automated stop. Human controls.
Dependencies        : None — no new product screen required.

---

## SECTION 6 — MEASUREMENT PLAN

Primary metric      : PTL call volume — check for spike within 48hrs.
                      A spike on bonus-related calls suggests partners
                      interpreted this as a deduction notice rather than
                      a condition statement.
Target              : No increase vs 7-day baseline
Measurement window  : 48 hours post-send
Data source         : PTL call volume (manual count or Metabase)
Review date         : 2 days after deployment
Secondary metric    : Any inbound PTL calls to 7836811111 referencing
                      PNM device issues within 72hrs — useful signal of
                      how many devices may actually be off or faulty.
                      Track separately from general PTL volume.

---

## RECIPIENT ANALYSIS

Message type        : Type C — Hybrid (state condition + operational action)

Questions that block action:
  Q1: What is the PNM device?
      → Answered: "आपके office में PNM device लगा है" — names it as
        the device already in their office.
  Q2: Why does it matter for bonus?
      → Answered: "यही data आपकी bonus eligibility decide करता है"
  Q3: What do I do if the device is not working?
      → Answered: "PTL पर call करें: 7836811111"

Hesitations that block action:
  Singling-out concern (why is only my device an issue?) → Addressed
  by framing as a system-wide condition, not a targeted complaint.
  Loss concern (am I already losing bonus?) → Avoided by using
  "eligibility paused" not "lost" and framing as an ongoing condition,
  not a deduction that has happened.

Operational details for action:
  Support process    : Call PTL 7836811111 — human-confirmed 2026-04-27
  Ongoing obligation : Keep PNM device ON at all times — confirmed
  Who bears cost     : No cost to CSP (not stated in message — no
                       friction to address here)

---

## INFORMATION ARCHITECTURE

Flow: Context → State condition → Action → Support process
Mapping:
  Context        = Line 1 ("आपके office में PNM device लगा है...")
  State condition= Lines 2-3 (Device ON → active / Device बंद → paused)
  Action         = Line 4 ("PNM device हमेशा ON रखें")
  Support process= Line 5 ("Device काम नहीं कर रहा? PTL: 7836811111")

---

## PATTERNS APPLIED

Playbook pending — compensation-os-playbook.md not yet created.
Designed from L1 globals (PCA + comms-principles) and project context.

  Pattern 1: Recall-aware re-anchoring (design-agent.md v1.3, Step 5d)
             — one opening line re-establishes subject and relevance
             without assuming retention of prior video/quiz content.
  Pattern 2: State condition framing, not loss framing (PCA §11 P4)
             — "bonus eligibility paused" not "you will lose bonus".
  Pattern 3: System as subject (PCA Principle 5)
             — conditions stated as system outcomes, not Wiom decisions.
  Pattern 4: Confirmed support process included (design-agent.md v1.2)
             — PTL number human-confirmed, not invented.

## MISTAKES AVOIDED

  Checked: Loss framing — replaced with canonical eligibility state
  Checked: Invented process — PTL 7836811111 confirmed by human
  Checked: Recall assumption — opening line re-anchors without assuming
           partner remembers the blocker video's PNM content
  Checked: Economic signaling — no income projection or narrative

---

## QUALITY CHECK

QUALITY CHECK: FLAG

FLAG 1 — Audience targeting
Brief M8 specifies: Partners with telemetry status = Pending.
Human instruction: all active CSPs. Design follows human instruction.
Action: Human to confirm broadcast scope before deploying.

FLAG 2 — TRAI classification pending confirmation
Classified as Service. Same recurring flag from Entries 3 and 7.
Recommend resolving once for all Service-classified WA messages
in this project rather than carrying this flag indefinitely.

---

## SECURITY CHECK

SECURITY CHECK: FLAG — Rule 2

Message classification (Service) requires human confirmation against
TRAI consent records. No other violations.

PayG check      : PASS — no subscription or monthly plan language
PCA check       : PASS — vocabulary canon respected, neutral-professional
                  tone, no forbidden terms, economic content passes §11
Regulatory check: FLAG — classification pending (Rule 2, above)
Data check      : PASS — PTL number is a business support line, not PII.
                  No personal data included.
Deployment check: PASS — output in review-queue/, not sent to any channel
Quality check   : PASS — self-contained, clear objective, one action,
                  tone consistent with PCA, recall-aware framing applied

---

Status: PENDING HUMAN APPROVAL
Next step: Human resolves the two flags above, approves, then deploys
via Gupshup. After deployment: run logger-agent.md to append Entry 8.
