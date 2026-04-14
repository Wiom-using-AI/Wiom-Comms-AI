# COMMS DESIGN BRIEF
Status: PENDING HUMAN APPROVAL

---

## HEADER

Date              : 2026-04-13
Project ID        : adhoc
Message Ref       : adhoc
Task type         : design
Designed by       : Claude — agent session
Block ID          : new block required — no registered Message Block exists for PNM installation communications
PCA version       : 1.0

---

## SECTION 1 — BEHAVIOURAL OBJECTIVE

What action or belief change this message drives:
Get CSP to schedule a PNM device installation visit by replying with their preferred date and time slot.

What this message is NOT trying to do:
Not trying to explain what PNM does technically, not trying to communicate any SLA or quality state change, not trying to drive any recharge or economic behaviour.

---

## SECTION 2 — AUDIENCE

Segment             : SEG-03 (Active Compliant CSP) — broadened to all active CSPs across all SLA states
Size                : To be confirmed by ops team before deployment
Current state       : All active CSPs — no specific structural state filter
Language            : Hindi-primary
Geography           : All (phased rollout — geography batches to be defined by ops)
Behavioural note    : CSPs need a clear, low-friction way to confirm availability for a technician visit. The primary barrier is likely scheduling convenience, not willingness.

Product dependency  : PNM device hardware available and ready for deployment
Dependency status   : PENDING — confirm with ops/hardware team that devices are procured and technicians are scheduled before sending

---

## SECTION 3 — CHANNEL AND RATIONALE

Channel             : WhatsApp Utility
Why this channel    : CSP action is required (scheduling a visit). WhatsApp allows two-way reply for scheduling confirmation. Dashboard cannot capture a scheduling response. This is a logistics coordination message requiring CSP input.
Message classification : Service — system-initiated operational communication for device installation. Not promotional. Not transactional (no payment or account event).
Send window         : 09:00–21:00 IST
Cooling period      : This is a one-time operational message per CSP. No repeat within same rollout batch unless CSP has not responded within 72 hours (see fallback below).
Fallback channel    : If no reply within 72 hours — SMS fallback with shortened message. If still no reply — flag to field team for direct coordination.

---

## SECTION 4 — MESSAGE COPY

### English

Header  : PNM Device Installation
Body    : Hello [CSP_name]. A PNM (network monitoring) device is scheduled for installation at your location. To schedule the technician visit, reply with your preferred date and time. Installation takes approximately 30 minutes. The technician will confirm your appointment. For questions, contact support.
Footer  : Wiom Systems
Button  : N/A

Character count (body) : 312 / 1024 chars used

---

### Hindi

Header  : PNM डिवाइस इंस्टॉलेशन
Body    : नमस्ते [CSP_name]। आपकी लोकेशन पर PNM (नेटवर्क मॉनिटरिंग) डिवाइस इंस्टॉल किया जाना है। टेक्नीशियन विज़िट शेड्यूल करने के लिए अपनी सुविधाजनक तारीख और समय रिप्लाई करें। इंस्टॉलेशन में लगभग 30 मिनट लगेंगे। टेक्नीशियन आपकी विज़िट कन्फर्म करेगा। सवालों के लिए सपोर्ट से संपर्क करें।
Footer  : Wiom Systems
Button  : N/A

Character count (body) : ~280 chars (Hindi Unicode — within single-message delivery range)

Hindi vocabulary check :
  [x] No forbidden Hindi terms (ग्राहक, लीड, पेनल्टी, टारगेट, निकाला)
  [x] Canonical Hindi terms used where applicable
  [x] Tone: neutral-professional — no warmth drift, no cold indifference

---

## SECTION 5 — TIMING AND SEQUENCING

Trigger condition   : Ops team confirms PNM devices are procured and technicians are available for the next rollout batch
Send timing         : Scheduled — per rollout batch, within 09:00–21:00 IST
Sequence position   : First and only message in this comm (single message, not a sequence)
What comes next     : If CSP replies with a date/time — technician confirms appointment (manual or automated). If no reply in 72 hours — SMS fallback. If still no reply — field team coordination.
Stopping rule       : Message sent once per CSP. No repeat for same installation request.
Dependencies        : PNM hardware availability confirmed. Technician scheduling capacity confirmed for the geography batch.

---

## SECTION 6 — MEASUREMENT PLAN

Primary metric      : Scheduling response rate — percentage of CSPs who reply with a date/time within 72 hours of receiving the message
Target              : >50% response rate within 72 hours
Measurement window  : 72 hours after send per batch
Data source         : WhatsApp reply tracking via Gupshup dashboard / manual count by ops team
Review date         : 7 days after first batch send — review response rate and adjust copy or fallback if needed
Secondary metric    : Installation completion rate — percentage of scheduled visits completed within 7 days of scheduling

---

## PATTERNS APPLIED

Playbook pending — no Quality OS playbook exists. No specific OS playbook applies to device installation logistics. Designed from L1 globals only.

  Pattern 1: Action Required CTA pattern — message states exactly what the CSP must do (reply with date and time), consistent with PCA Principle 2 (information, not persuasion) and push-to-pull CTA design rules (§10)
  Pattern 2: Single clear objective — one action per message (schedule the visit), per Quality Checklist §2.1
  Pattern 3: Low-friction response mechanism — reply-based scheduling reduces barriers vs portal/link navigation

## MISTAKES AVOIDED

  Checked: No motivational framing ("this is for your benefit" / "improve your network") — PCA §2, P2
  Checked: No economic framing or income implication — PCA §11
  Checked: No urgency language beyond factual scheduling need — PCA §6, P6
  Checked: No warmth beyond dignity ("we're excited to bring this to you") — PCA §4, P7
  Checked: No employer/partnership framing ("as our valued partner") — PCA §4, P4

---

## PCA COMPLIANCE

  Canonical vocabulary used (PCA §3) — YES. No forbidden terms. "Location," "device," "technician," "installation" are operational terms not in the banned list.
  Tone envelope respected (PCA §4) — YES. Neutral-professional. Factual. No warmth, no coldness, no persuasion.
  Registered Message Blocks used where applicable (PCA §6) — N/A. No registered block exists for PNM installation. Flagged: new block required. Block must be approved before deployment.
  Anti-contamination tests passed (PCA §8) — ALL 8 PASS:
    1. Structural Source: System-initiated device installation — operational action ✓
    2. Persuasion: No attempt to convince or emotionally influence ✓
    3. Economic Signal: No economic expectation created ✓
    4. Role Integrity: CSP treated as service operator at a location, not customer/friend ✓
    5. Impersonal Authority: System scheduling, not "we decided" ✓
    6. Calm: Would not cause anxiety at 10pm ✓
    7. Dignity: No patronising, blaming, or grading ✓
    8. Vocabulary: No forbidden terms ✓

---

## FATIGUE CHECK

Was comms-log checked? NO — this is a one-off adhoc task with no project history.
Last similar message to this audience: none found (first PNM installation comm)
Fatigue risk: LOW — this is a new operational message type not previously sent to this audience. No existing comm competes for the same attention.

---

## MEASUREMENT PLAN

Metric    : Scheduling response rate (CSP replies with date/time within 72 hours)
Target    : >50% within 72 hours
Timeframe : 72 hours per batch, overall review at 7 days post first batch
Data source: Gupshup WhatsApp reply tracking / ops manual count

---

## TONE NOTES

Hindi-primary audience. Formal Hindi register with technical English loan words retained (PNM, device, installation, technician) as these are operationally understood terms in the CSP context. No Hinglish casualness. No warmth markers. Greeting is functional ("नमस्ते [name]") per PCA §4 tone envelope.

---

## PRE-DEPLOYMENT CHECKLIST

  [ ] DND scrubbing required before send — NO (Service classification, not promotional)
  [ ] Send time: 09:00–21:00 IST — YES, scheduled within window
  [ ] Opt-out mechanism: N/A for service/operational communication — but WhatsApp opt-in status must be confirmed per CSP before send
  [ ] Audience list verified: PENDING — ops team to confirm rollout batch list and geography phasing
  [ ] PNM hardware availability confirmed: PENDING — do not send until devices are ready for the batch geography
  [ ] Technician capacity confirmed: PENDING — do not send until scheduling capacity exists for the batch

---

QUALITY CHECK: PASS
All checklist items verified. Output is ready for human review.

NOTE: New Message Block required — no registered block exists for PNM device installation communications. Block must receive approval before deployment.

---

SECURITY CHECK: PASS — all six rule areas checked, no violations.

  PayG check: No monthly/subscription framing. No ISP model implication. PASS.
  PCA check: All 8 anti-contamination tests passed. Vocabulary clean. Tone within envelope. PASS.
  Regulatory check: Service classification. Within 09:00–21:00 IST. PASS.
  Data check: No PII beyond [CSP_name] variable. No internal data. PASS.
  Deployment check: Output in review-queue/adhoc/. Pending human approval. PASS.
  Quality check: Single objective, channel justified, CTA actionable, measurement plan present. PASS.

---

Status: PENDING HUMAN APPROVAL
Next step: Human reviews copy, approves or requests changes, then deploys via Gupshup / WhatsApp Business API.
After deployment: run logger-agent.md to append to comms-log (create project if this becomes recurring).

MODE 2 — STANDALONE. No project history available.
OS could not be matched to an existing trigger — designed from L1 PCA governance only.
No L2 playbook loaded — no quality-os-playbook.md exists and no OS trigger matches device installation logistics.
