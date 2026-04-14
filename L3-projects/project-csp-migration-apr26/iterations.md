# Iterations — project-csp-migration-apr26

## FILE PURPOSE
Record of every significant change to the comms plan and why.
The learning agent needs this to understand whether results came
from the message itself or from a change made partway through.

## RULES
- Append-only. Each iteration must document what changed, why,
  and the hypothesis behind the change.
- Include A/B test results where available.

## LAST UPDATED
2026-04-13 — initial version documenting plan-to-execution evolution.
Maintained by: design agent proposes, human confirms.

---

## Iteration 0 — Original Plan (brief.md, 2026-03-27)

  WHAT WAS PLANNED:
  13-message sequence (M1-M13) over pre-launch, launch day, and
  post-launch phases. Started Mar 31. App launch ~Apr 7.
  Primary channel: WhatsApp with SMS cascade.
  Education model: individual messages building progressive context.
  No audience state tracking beyond segment definitions.

  KEY ASSUMPTIONS:
  - WhatsApp is the primary education delivery channel
  - Sequential messages build understanding over time
  - App launch ~Apr 7 is the hard transition point
  - Each message has a single behavioural objective
  - 13 messages covers the full migration journey

---

## Iteration 1 — Execution Shift (2026-04-05)

  WHAT CHANGED:
  1. Campaign window shifted from Mar 31 start to 05/04 start
  2. App launch moved from ~Apr 7 to ~Apr 12
  3. Education model changed from WhatsApp-first sequential messages
     to in-app education (popups + blocker video + quiz) with WA as
     cascade for non-completers
  4. New audience state model introduced (S0-S4) based on education
     completion, not just segment membership
  5. Blocker video (2:10) replaced individual pre-launch messages
     (M1-M4 in the brief). Single video covers all key topics.
  6. Quiz became gated: only available to S2+ (video completers)
  7. Hard lock mechanism added: S0/S1 partners locked out of old app
     on transition day

  WHY IT CHANGED:
  - In-app mechanisms reach partners at the moment of use (higher
    attention than push channels)
  - Forced blocker video ensures education cannot be skipped
  - State-based targeting (S0-S4) allows precision: non-completers
    get nudged, completers get advanced content
  - WA push as cascade (not primary) reduces channel fatigue

  HYPOTHESIS:
  Forcing education through a non-dismissible in-app blocker will
  achieve higher comprehension than sequential WhatsApp messages,
  because partners cannot skip it when they want to use the app.

  RESULT:
  Partially invalidated. Initiation was high (1,054 starters) but
  completion was critically low (18.9%). The forced mechanism got
  attention but did not hold it. 66% dropped off by 20 seconds.
  See results.md Measurement Cycle 1 for full data.

---

## Iteration 2 — Timeline Adjustment (2026-04-07 to 2026-04-09)

  WHAT CHANGED:
  1. Blocker video deployed on 07/04 (night), not 06/04 as originally
     planned in the dashboard timeline
  2. WA push deployed on 09/04, not 07/04
  3. Recap + quiz not yet deployed as of 13/04 (was planned for 08/04)
  4. App transition + hard lock not yet deployed as of 13/04

  WHY IT CHANGED:
  Deployment timing adjusted based on operational readiness.
  Recap + quiz held back, possibly pending video completion data
  or quiz content finalisation.

  HYPOTHESIS:
  Delaying quiz deployment allows more time for WA push (09/04) to
  recover video completion rates before gating the next education step.

  RESULT:
  Pending. WA push impact and quiz deployment still to be measured.

---

## Open Questions for Next Iteration

  1. Is the 66% drop-off at 20 seconds a hook problem or a length
     problem? Would a shorter video (60-90 sec) with the same
     content perform better?

  2. Are partners closing the app entirely to bypass the blocker?
     Technical check needed with engineering.

  3. Should the quiz gate be lowered from S2+ to S1+ given low
     video completion? Or does that undermine education quality?

  4. What does the survey (50-60 PTL calls) reveal about recall
     across the three cohorts (quiz pass / video only / popup only)?

---

*iterations.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next iteration appended when plan changes.*
