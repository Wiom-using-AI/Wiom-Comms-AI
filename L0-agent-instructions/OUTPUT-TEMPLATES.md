# OUTPUT TEMPLATES — Wiom Comms AI

## FILE PURPOSE
Standard output formats for every agent task type.
Using these templates exactly ensures downstream agents (logger,
measurement, learning) can parse outputs reliably.
Deviating from the template structure breaks the pipeline.

## WHEN TO USE THIS FILE
Before writing any output. Load this file, find the correct template
for your task type, and use it exactly — including all field labels,
section headings, and result lines.

## HOW TO USE THIS FILE
1. Identify your task type (design / log / measure / learn)
2. Find the corresponding template below
3. Copy the template structure exactly
4. Fill in every field — no blanks, no omissions
5. If a field is genuinely not applicable: write N/A and state why
6. Run QUALITY-CHECKLIST.md after filling in the template
7. Run SECURITY-RULES.md self-check last
8. Write the completed output to the correct location

## LAST UPDATED
2026-04-02 — v1.0
  + Template 1: Comms Design Brief added
Maintained by: human only

---

## TEMPLATE 1 — COMMS DESIGN BRIEF

Use when: task_type = design or iterate
Output location: review-queue/[project-id]/[YYYY-MM-DD]-[message-slug].md
  or for one-off tasks: review-queue/adhoc/[YYYY-MM-DD]-[objective-slug].md

---

```
# COMMS DESIGN BRIEF
Status: PENDING HUMAN APPROVAL

---

## HEADER

Date              : [YYYY-MM-DD]
Project ID        : [project_id from MANIFEST.md — or "adhoc"]
Message Ref       : [M1 / M2b / M3 / etc from comms plan — or "adhoc"]
Task type         : [design / iterate]
Designed by       : [Claude — agent session]
Block ID          : [BLOCK-[OS]-[STATE]-[VERSION] — or "new block required"]
PCA version       : [1.0]

---

## SECTION 1 — BEHAVIOURAL OBJECTIVE

What action or belief change this message drives:
[One sentence. Starts with a verb. Example: "Get partner to confirm
technician visit slot within 24 hours of receiving this message."]

What this message is NOT trying to do:
[One sentence. Prevents scope creep in the copy. Example: "Not trying
to explain the bonus structure — that is M8."]

---

## SECTION 2 — AUDIENCE

Segment             : [SEG-XX label from user-segments.md]
Size                : [number of recipients]
Current state       : [structural state — e.g. QUAL_STATE_AT_RISK,
                       or "active CSP, telemetry status = pending"]
Language            : [Hindi-primary / Hinglish / English / bilingual]
Geography           : [Delhi NCR / Bharat tier-2 / Mumbai / All]
Behavioural note    : [one line on what this audience cares about right
                       now — what their primary motivation is]

Product dependency  : [screen or feature this message assumes is live]
Dependency status   : [CONFIRMED LIVE / PENDING — do not send until confirmed]

---

## SECTION 3 — CHANNEL AND RATIONALE

Channel             : [WhatsApp Utility / SMS / Push Notification /
                       Dashboard / Call Script / Field Script]
Why this channel    : [one sentence — why this channel for this state
                       and this audience, not just what the channel is]
Message classification : [Promotional / Transactional / Service]
                         (for TRAI compliance — must be stated)
Send window         : [09:00–21:00 IST / immediate / scheduled —
                       with specific time if known]
Cooling period      : [how long before another message goes to this
                       audience — per comms-principles.md §3.2]
Fallback channel    : [what happens if primary channel is not delivered —
                       e.g. SMS cascade at 24hrs / dashboard only]

---

## SECTION 4 — MESSAGE COPY

### English

[Full message copy here. Exactly as it will be sent.
No placeholders — all variables shown as [variable_name].
For WhatsApp: include header, body, footer, button labels separately.]

Header  : [text — max 60 chars — or N/A]
Body    : [text — max 1024 chars for WhatsApp, 160 for SMS]
Footer  : [text — max 60 chars — or N/A]
Button  : [label — max 25 chars — or N/A]

Character count (body) : [X / 1024 chars used]

---

### Hindi

[Full Hindi message copy here. Same structure as English above.
Must comply with PCA §3.3 Hindi Vocabulary Lock and §4.1 Hindi Tone
Discipline. If audience is English-only: write "N/A — English-only
audience" and state the reason.]

Header  : [हिंदी text — max 60 chars — or N/A]
Body    : [हिंदी text — for WhatsApp Unicode: 70 chars per segment,
           aim for under 300 chars total for single-message delivery]
Footer  : [हिंदी text — max 60 chars — or N/A]
Button  : [label — max 25 chars — or N/A]

Character count (body) : [X chars — note if multi-segment]

Hindi vocabulary check :
  □ No forbidden Hindi terms (ग्राहक, लीड, पेनल्टी, टारगेट, निकाला)
  □ Canonical Hindi terms used where applicable
  □ Tone: neutral-professional — no warmth drift, no cold indifference

---

## SECTION 5 — TIMING AND SEQUENCING

Trigger condition   : [what must be true before this message sends —
                       system event, date, or CSP state]
Send timing         : [immediately on trigger / scheduled — specify]
Sequence position   : [what came before this message in the sequence]
What comes next     : [what message follows this one and when]
Stopping rule       : [what stops this message from sending —
                       e.g. "do not send if M4 quiz not completed"]
Dependencies        : [other messages or product states this relies on]

---

## SECTION 6 — MEASUREMENT PLAN

Primary metric      : [what to measure — e.g. technician visit
                       confirmation rate, quiz completion rate,
                       app download rate]
Target              : [quantified target — e.g. >40% within 48 hours]
Measurement window  : [how long after send before measuring —
                       e.g. 48 hours / 7 days]
Data source         : [Metabase query name / app analytics /
                       manual count — specify exactly]
Review date         : [YYYY-MM-DD — when human reviews results]
Secondary metric    : [optional — e.g. PTL call volume spike check]

---

## PATTERNS APPLIED

[List which proven patterns from the L2 playbook were applied.
If no playbook exists yet for this OS: state "Playbook pending —
designed from L1 globals only." This is honest and logged.]

  Pattern 1: [name / description]
  Pattern 2: [name / description]
  Pattern 3: [name / description — or N/A]

## MISTAKES AVOIDED

[List which mistakes-to-avoid from the L2 playbook were checked.
Same note if playbook is pending.]

  Checked: [name / description]
  Checked: [name / description]

---

## QUALITY CHECK

[Run QUALITY-CHECKLIST.md in full before writing this line.
Replace with the correct result line — do not copy the example.]

QUALITY CHECK: PASS
All checklist items verified. Output is ready for human review.

  — or —

QUALITY CHECK: FLAG
[item number] — [what the issue is] — [what the human needs to do]

---

## SECURITY CHECK

[Run SECURITY-RULES.md self-check in full before writing this line.]

SECURITY CHECK: PASS — all six rule areas checked, no violations.

  — or —

SECURITY CHECK: FLAG — [rule number] — [issue] — [action required]

---

Status: PENDING HUMAN APPROVAL
Next step: human reviews copy, approves or requests changes,
then deploys via Gupshup / channel tool.
After deployment: run logger-agent.md to append to comms-log.md.
```

---

## FIELD NOTES FOR THE DESIGN AGENT

### On Message Ref
Always match the message reference to the Comms Plan in brief.md.
If this is an ad hoc message with no comms plan reference: write
"adhoc" and explain why in the Behavioural Objective section.

### On Block ID
If a registered Message Block exists for this structural state:
use it. Reference the Block ID. Do not paraphrase the block wording.
If no block exists yet: write "new block required" and note it.
A new block requires MGO approval before the message can deploy.
For this project (csp-migration-apr26): most messages are journey
communications, not structural state translations — Block IDs may
not exist yet. State this explicitly rather than inventing a Block ID.

### On Hindi copy
Hindi copy is mandatory. If the audience is English-only, state
"N/A — English-only audience" with a reason. Do not leave the
Hindi section blank. A blank Hindi section fails the quality check.
For this project: audience is Hindi-primary. Hindi copy is required
for every message. Do not skip it.

### On character counts
WhatsApp body: 1024 chars max (Latin). Hindi Unicode segments at
70 chars each — aim under 300 chars total for reliable single-message
delivery on most devices. Flag if the Hindi copy is approaching
multi-segment length — it affects delivery and cost.

### On product dependencies
If a message assumes a screen or feature that is not yet confirmed
live: mark dependency status as PENDING and add a flag to the
Quality Check section. The human must confirm the dependency before
deploying. See brief.md for the full product dependency list for
this project.

### On PayG positioning
This project (csp-migration-apr26) is a CSP-facing migration brief —
not a customer-facing marketing brief. PayG framing applies in the
context of explaining the new system to CSPs: recharge model,
no fixed area, system-assigned work. Do not use subscription or
monthly plan language. SECURITY-RULES.md Rule 1 applies in full.

---

*OUTPUT-TEMPLATES.md — L0 Agent Instructions — v1.0*
*Maintained by: human only*
*Do not modify without updating CHANGELOG.md*
