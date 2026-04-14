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

## TEMPLATE 2 — MEASUREMENT REPORT

Use when: task_type = measure
Output location: review-queue/[project-id]/[YYYY-MM-DD]-measurement-[cycle-or-slug].md
  or for one-off: review-queue/adhoc/[YYYY-MM-DD]-measurement.md

---

```
# MEASUREMENT REPORT
Status: PENDING HUMAN REVIEW

---

## HEADER

Date              : [YYYY-MM-DD]
Project ID        : [project_id from MANIFEST.md — or "adhoc"]
Measurement cycle : [cycle identifier — e.g. "Cycle 1: 05/04–10/04"]
Measured comms    : [which messages — e.g. "Contextual popups + Blocker video"]
Measured by       : [Claude — agent session]
Data sources      : [results.md snapshot date + live dashboard fetch timestamp
                     — or "results.md only"]

---

## SECTION 1 — MEASUREMENT SCOPE

Period             : [start date — end date]
Stage              : [pre-launch / launch day / post-launch / ongoing]
Comms measured     : [list each comm with its message ref and channel]
Audience           : [segment and size]
Benchmarks used    : [brief.md targets / context-from-teams.md thresholds /
                      playbook benchmarks — list which]

---

## SECTION 2 — PERFORMANCE SUMMARY

[Table format. One row per metric. All four columns mandatory.]

  METRIC                    VALUE          TARGET         STATUS
  -------------------------------------------------------------------------
  [metric name]             [actual]       [benchmark]    [GREEN/YELLOW/RED/BASELINE]
  [metric name]             [actual]       [benchmark]    [GREEN/YELLOW/RED/BASELINE]

---

## SECTION 3 — WHAT WORKED

[For each GREEN metric: one paragraph explaining what contributed
to the success. Be specific — was it the mechanism, timing, targeting,
copy, or channel? This feeds the learning agent.]

---

## SECTION 4 — WHAT DIDN'T WORK

[For each RED or YELLOW metric:]

  Finding          : [specific metric that missed target]
  Value vs Target  : [X% actual vs Y% target — STATUS]
  Root cause       : [hypothesis for why — must be specific and
                      evidence-backed, not generic]
  Evidence         : [what data supports this hypothesis]
  Confidence       : [high / medium / low]

---

## SECTION 5 — RECOMMENDATIONS

[For each finding in Section 4:]

  Finding ref      : [which finding from Section 4]
  Action           : [ITERATE / SCALE / PAUSE / FLAG]
  Specifics        : [exactly what to do — concrete enough for the
                      design agent or human to act on directly]
  Expected impact  : [what improvement this should produce — be honest
                      about uncertainty]

---

## SECTION 6 — COMPARISON

[How these results compare to:]
  Brief.md targets           : [summary — on track / behind / ahead]
  Context-from-teams thresholds : [GREEN / YELLOW / RED overall]
  L2 playbook benchmarks     : [if available — or "no playbook benchmarks
                                exist for this OS yet"]
  Prior measurement cycles   : [if this is Cycle 2+, compare to Cycle 1]

---

## SECTION 7 — DATA LIMITATIONS

[Mandatory. Even if data is clean, note:]
  Sample size      : [adequate / limited — and why]
  Time window      : [sufficient / early — and why]
  Missing metrics  : [which metrics could not be measured and why]
  Confounds        : [anything else happening that could explain results]
  Blocked metrics  : [metrics that cannot be measured due to product
                      dependencies not being live]

---

## QUALITY CHECK

[Run QUALITY-CHECKLIST.md §4 before writing this line.]

QUALITY CHECK: PASS — all §4 items verified.

  — or —

QUALITY CHECK: FLAG
[item number] — [what the issue is] — [what the human needs to do]

---

## SECURITY CHECK

[Run SECURITY-RULES.md self-check in full.]

SECURITY CHECK: PASS — all six rule areas checked, no violations.

  — or —

SECURITY CHECK: FLAG — [rule number] — [issue] — [action required]

---

Status: PENDING HUMAN REVIEW
Next step: human reviews findings and recommendations, then decides
whether to iterate (hand back to design agent), scale, pause, or
investigate blockers.
If iterating: create a new design task referencing this report.
If findings are significant: learning agent should review for
cross-project pattern extraction.
```

---

## FIELD NOTES FOR THE MEASUREMENT AGENT

### On data sources
Always state which data you used and when it was collected. If you
WebFetched a live dashboard, note the fetch timestamp separately
from the results.md snapshot date. If numbers differ between the
two sources, use the newer numbers but note the delta.

### On root causes
"Low completion rate" is a finding, not a root cause. A root cause
hypothesis must explain WHY the rate is low. "66% of viewers drop off
within the first 20 seconds, suggesting the video opening does not
establish relevance fast enough" is a root cause hypothesis.

### On recommendations
Every recommendation must be concrete enough for someone to act on
without reading the full report. "Iterate on the video" is not
actionable. "Shorten the video to under 60 seconds, front-load
earnings information (currently delayed until 1:10)" is actionable.

### On GREEN findings
Do not skip what worked. The learning agent needs GREEN findings
to extract proven patterns. A GREEN finding with a clear attribution
("popup reach was 86.3% because the mechanism was organic and
dismissible, reducing friction") is high-value learning material.

---

## TEMPLATE 3 — MEASUREMENT SETUP (SQL + Instructions)

Use when: task_type = construct-measurement
Output location: review-queue/[project-id]/[YYYY-MM-DD]-measurement-setup-[slug].md
  or for one-off: review-queue/adhoc/[YYYY-MM-DD]-measurement-setup.md

---

```
# MEASUREMENT SETUP
Status: PENDING HUMAN EXECUTION

---

## HEADER

Date              : [YYYY-MM-DD]
Project ID        : [project_id — or "adhoc"]
Source brief       : [which comms design brief this tracks —
                      e.g. "2026-04-02-d0-app-live-welcome.md"]
Constructed by    : [Claude — agent session]

---

## SECTION 1 — MEASUREMENT PLAN (from brief)

[Copy the measurement plan from the source brief Section 6]

  Primary metric      : [what to measure]
  Target              : [success threshold]
  Measurement window  : [when to check]
  Data source         : [where the data lives]
  Secondary metric    : [if any]

---

## SECTION 2 — QUERIES

### Query 1: [metric name]

  Metabase question name : [suggested name]
  Collection             : [suggested collection path]
  Visualisation          : [line / number / table / bar]
  Exposed filters        : [which date filters the human can adjust]

```sql
-- ═══════════════════════════════════════════════
-- METRIC: [metric name]
-- COMM: [message ref]
-- TARGET: [target]
-- WINDOW: [measurement window]
-- ═══════════════════════════════════════════════

[Complete, ready-to-paste SQL query]
;
```

### Query 2: [metric name]

[Same structure as Query 1. Repeat for each metric.]

---

## SECTION 3 — CLEVERTAP EVENTS (if applicable)

[For metrics that live in CleverTap, not Snowflake:]

  Event name          : [e.g. blocker_video_completed]
  Filter              : [e.g. quiz_score >= 4]
  How to check        : [CleverTap dashboard path or export instruction]
  Note                : [whether this event is synced to Snowflake or not]

---

## SECTION 4 — METABASE SETUP INSTRUCTIONS

[Step-by-step for the human:]

  1. Go to [collection path] in Metabase
  2. Click New > SQL Query
  3. Paste Query 1 above
  4. Save as "[suggested name]"
  5. Set visualisation to [type]
  6. [Optional] Set up alert: "[condition — e.g. if daily PTL
     calls exceed 2x baseline, send email"]
  7. Repeat for each query

---

## SECTION 5 — MEASUREMENT CHECKLIST

[Dated checklist the human follows:]

  DATE               CHECK                         QUERY       THRESHOLD
  -----------------------------------------------------------------------
  [deploy + 24hrs]   [first metric read]           [query 1]   [GREEN/YELLOW/RED values]
  [deploy + 48hrs]   [target window reached]        [query 1]   [target value]
  [deploy + 7days]   [full cycle review]            [all]       [overall assessment]

  Action triggers:
    GREEN  : no action needed, log result in results.md
    YELLOW : review with team, consider iteration
    RED    : escalate, trigger measurement agent Job A for full analysis

---

## SECTION 6 — LIMITATIONS

[What this setup cannot measure:]
  - [e.g. "Video watch time not available in Snowflake — requires
    CleverTap export or manual check"]
  - [e.g. "PTL call content not captured — only volume, not topic"]

---

Status: PENDING HUMAN EXECUTION
Next step: human creates the queries in Metabase, runs the first
check at [deploy + 24hrs], and logs results in results.md.
After first measurement cycle: run measurement agent Job A to
analyse the data.
```

---

## FIELD NOTES FOR MEASUREMENT SETUP

### On query parameterisation
Always leave dates as editable comments in the SQL. The human will
adjust the measurement window as the campaign progresses. Never
hardcode dates without a comment explaining what to change.

### On CleverTap gaps
Many comms metrics (especially behavioural events like popup_seen,
video_completed, quiz_passed) live in CleverTap, not Snowflake.
If the event is not synced to Snowflake, do not pretend you can
query it. State clearly what lives where and provide the CleverTap
event spec so the human can check manually or set up an export.

### On PTL measurement
PTL call volume is the primary success metric for CSP migration.
Always include a baseline query (7-day average before the comm
was sent) alongside the post-comm query. The spike is relative
to baseline, not absolute.

---

*OUTPUT-TEMPLATES.md — L0 Agent Instructions — v1.2*
*Maintained by: human only*
*Do not modify without updating CHANGELOG.md*
