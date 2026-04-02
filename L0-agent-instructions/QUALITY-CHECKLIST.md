# QUALITY CHECKLIST — Wiom Comms AI

## FILE PURPOSE
Pre-output quality standard for every agent in every session.
Run this checklist before writing any output to review-queue/
or any project file. Every item must be checked — not skimmed.

## WHEN TO USE THIS FILE
After producing a draft output and before finalising it.
This runs after the task is complete and before the output is written.
It is the last step before SECURITY-RULES.md self-check.

## HOW TO USE THIS FILE
Work through each section relevant to your output type.
For each item: check it, fix it if needed, then move on.
Do not mark an item as checked if you have not verified it.
At the end: write the QUALITY RESULT line in your output.

## LAST UPDATED
2026-03-27 — initial version
Maintained by: human only

---

## SECTION 1 — FOR ALL OUTPUTS

Run this section regardless of task type.

### 1.1 Format
  □ Does the output follow the correct template from OUTPUT-TEMPLATES.md?
  □ Are all required sections present and in the correct order?
  □ Are headings, labels, and field names exactly as specified?
  → If any box is unchecked: fix the format before proceeding

### 1.2 Destination
  □ Is the output being written to the correct location?
      Design output    → review-queue/[project-id]/ or review-queue/adhoc/
      Log entry        → [project-folder]/comms-log.md (append only)
      Learning proposal → L2-domain-playbooks/proposed-learnings/
      Measurement report → review-queue/[project-id]/
  □ Is the filename following the correct naming convention?
      [YYYY-MM-DD]-[objective-slug].md
  → If any box is unchecked: correct the destination before writing

### 1.3 Completeness
  □ Are all fields in the output filled in — no blanks, no placeholders?
  □ If a field genuinely cannot be filled (e.g. results not yet available):
    is it explicitly marked as "pending" with a reason?
  → If any box is unchecked: complete or mark pending before finalising

### 1.4 Clarity
  □ Can someone unfamiliar with this task read the output and understand
    what was done, for whom, and why?
  □ Are there any acronyms or internal terms that need explaining
    for the reviewer?
  → If any box is unchecked: add context before finalising

---

## SECTION 2 — FOR DESIGN OUTPUTS

Run this section when task_type = design or iterate.

### 2.1 Behavioural objective
  □ Does the message have one clear behavioural objective?
    (one action the recipient should take — not two, not three)
  □ Is that objective stated explicitly in the output brief?
  □ Does the message copy itself drive towards that objective?
    (read the copy — does it lead the recipient to the action?)
  → If any box is unchecked: rewrite the copy or the objective

### 2.2 Channel fit
  □ Is the channel justified in the output?
    (not just named — explained: why this channel for this audience?)
  □ Is the copy within the character limit for the channel?
      WhatsApp          : 1024 characters (text), check channel-specs.md
      SMS               : 160 characters per segment, check channel-specs.md
      App notification  : check channel-specs.md for current limits
      Agent script      : no hard limit but check readability at pace
  □ Does the copy use formatting appropriate for the channel?
    (WhatsApp supports bold, italics, line breaks — SMS does not)
  → If any box is unchecked: revise copy or channel choice

### 2.3 Audience fit
  □ Is the language register appropriate for the audience?
    (formal/informal, Hindi/English/Hinglish — check brand-guidelines.md)
  □ Is the message free of jargon the audience will not understand?
    (technical terms, internal Wiom terminology, industry language, heavy English/Hindi)
  □ Does the message assume the right level of product knowledge
    for this audience segment? (new user vs active vs churned)
  → If any box is unchecked: rewrite for the audience

### 2.4 Playbook compliance
  □ Have you checked the Proven Patterns section of the relevant
    L2 playbook before finalising?
  □ Have you checked the Mistakes to Avoid section?
  □ If the copy contradicts a documented mistake: is there a clear
    reason stated in the output for why the exception applies?
  → If any box is unchecked: check the playbook now

### 2.5 PayG positioning
  □ Does the copy reflect Wiom's PayG model?
  □ Is the word "recharge" used instead of "renew" or "subscribe"?
  □ Is flexibility emphasised over commitment?
  □ If pricing is mentioned: is it framed as a recharge amount,
    not a monthly fee?
  → If any box is unchecked: rewrite before proceeding
    (this overlaps with SECURITY-RULES.md Rule 1 — both must pass)

### 2.6 CTA (Call to Action)
  □ Is there one specific CTA in the message if needed?
  □ Is the CTA actionable — does it tell the recipient exactly
    what to do? ("Recharge now" not "Learn more")
  □ Is the CTA consistent with the behavioural objective?
  □ For WhatsApp: is there a reply keyword or button label if needed?
  → If any box is unchecked: revise the CTA

### 2.7 Measurement plan
  □ Is there a measurement plan in the output?
  □ Does it specify: metric, target, timeframe, and data source?
  □ Is the metric measurable with tools available (Metabase/Snowflake)?
  □ Is the target realistic relative to benchmarks in results.md
    (if available) or L2 playbook benchmarks?
  → If any box is unchecked: complete the measurement plan

### 2.8 Fatigue check
  □ Have you checked comms-log.md for this project?
    (if available — not applicable for one-off tasks)
  □ Has a similar message been sent to this audience in the last 7 days?
  □ If yes: is the new message sufficiently differentiated, or should
    it be held back? Flag for human review if uncertain.
  → If fatigue risk exists: note it in the output for human review

### 2.9 For sequences only (task_subtype = sequence)
  □ Does each message in the sequence have its own distinct objective?
  □ Does each message build on the previous one — not repeat it?
  □ Is there a logical progression in urgency, tone, or information?
  □ Are the send timings specified for each message in the sequence?
  □ Is there a stopping rule — what stops the sequence?
    (user recharged / user replied / sequence completes)
  → If any box is unchecked: revise the sequence before finalising

---

## SECTION 3 — FOR LOG ENTRIES

Run this section when task_type = log.

### 3.1 Append-only check
  □ Are you appending to the file — not overwriting it?
  □ Is the new entry at the bottom of the file?
  □ Have you confirmed the existing entries above are untouched?
  → If any box is unchecked: stop and correct immediately

### 3.2 Entry completeness
  □ Does the log entry include all required fields?
      DATE, TYPE, CHANNEL, AUDIENCE, AUDIENCE_SIZE,
      SUMMARY, METRICS, DESIGNED_BY, STATUS
  □ If metrics are not yet available: is the field marked "pending"?
  □ Is SUMMARY a one-line description — not the full message copy?
  → If any box is unchecked: complete the entry

### 3.3 Rolling window
  □ After appending: are there more than 20 active entries?
  □ If yes: have you summarised the oldest entries into the
    Historical Summary section at the top?
  □ Is the Historical Summary dated and concise?
  → If any box is unchecked: apply the rolling window rule

---

## SECTION 4 — FOR MEASUREMENT OUTPUTS

Run this section when task_type = measure.

### 4.1 Data integrity
  □ Are all metrics sourced from results.md — not assumed or estimated?
  □ Are comparisons made against the correct benchmark
    (from brief.md success metrics or L2 playbook benchmarks)?
  □ Is the measurement cycle clearly identified
    (which period does this data cover)?
  → If any box is unchecked: correct the data source before outputting

### 4.2 Recommendations
  □ Does every finding lead to a recommendation?
    (not just "open rate was low" but "open rate was low — recommend
    testing a different send time or subject line")
  □ Is each recommendation specific and actionable?
  □ Is there a clear next step indicated:
    iterate / pause / scale / flag for human review?
  → If any box is unchecked: add recommendations

### 4.3 Limitations
  □ Are any limitations of the data noted?
    (small sample size, incomplete data, confounding factors)
  □ Are conclusions appropriately qualified where data is limited?
  → If any box is unchecked: add a limitations note

---

## SECTION 5 — FOR LEARNING PROPOSALS

Run this section when task_type = learn.

### 5.1 Evidence standard
  □ Is the proposed learning supported by data from 2+ projects?
  □ If from only 1 project: is it clearly marked as
    "watch — needs more evidence" not a confirmed pattern?
  □ Are the project IDs and metrics cited explicitly?
  → If any box is unchecked: revise the confidence level

### 5.2 Generalisability
  □ Is this pattern genuinely generalisable beyond the source project?
  □ Or is it specific to a unique context that won't recur?
  □ If context-specific: do not promote to proposed-learnings/
    — note it in the project's iterations.md instead
  → If any box is unchecked: reconsider whether this belongs in L2

### 5.3 Format
  □ Does the proposal include:
      PATTERN, EVIDENCE, RECOMMENDATION, CONFIDENCE?
  □ Is it written for a human reviewer — clear, concise, actionable?
  □ Is it going to proposed-learnings/ — not directly into a playbook?
  → If any box is unchecked: fix before writing the file

---

## QUALITY RESULT

Every output must end with one of these two lines:

  QUALITY CHECK: PASS
  All checklist items verified. Output is ready for human review.

  QUALITY CHECK: FLAG
  [Item number] — [what the issue is] — [what the human needs to do]

  Multiple flags are allowed. List each one on a separate line.
  A flagged output still goes to review-queue — the flags tell the
  human what to look at before approving.

  Example:
  QUALITY CHECK: FLAG
  2.8 — fatigue risk — similar WhatsApp sent 5 days ago to same segment.
        Human to confirm whether to proceed or hold for 2 more days.
  2.7 — measurement plan incomplete — no data source specified.
        Human to confirm whether Metabase query exists for this metric.
