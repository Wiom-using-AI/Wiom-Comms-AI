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
2026-04-30 — Iteration 4 added: M8 PNM device + bonus eligibility
             evolved from planned WA text comm (Karishni's v2,
             2026-04-27) into a deployed WhatsApp video
             (Wiom_PNM_Bonus.mp4, 1:02). Captures: framework arrival
             (Unified Attention Framework v1.3 + CSP App Adoption
             System v1.2 filed 2026-04-28); in-app event-driven
             approach deferred to new app launch; bonus-led framing
             confirmed by partner mental-model insight; full
             content principle log captured in
             L2-domain-playbooks/content-improvement-log.md.
2026-04-15 — Iteration 3 added: Recap + Quiz deployed 15/04. Captures
             plan-to-reality delta (5Q→8Q, 4/5→all correct, restart-on-
             wrong added, 15-sec video gate added). Also logs full quiz
             copy for reference.
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

## Iteration 3 — Recap + Quiz Deployed, Evolved from Plan (2026-04-15)

  WHAT CHANGED:
  1. Recap + Quiz deployed on 15/04 (was planned for 08/04 in brief,
     then held TBD as of Iteration 2). Deployed 7 days behind original
     plan.
  2. Quiz length: 5 questions → 8 questions (+3 questions).
  3. Pass threshold: 4 out of 5 correct → ALL 8 must be correct.
  4. Wrong-answer behaviour: (not specified in plan) → any wrong answer
     restarts quiz from Q1. No partial pass. No skip.
  5. Video gate before quiz CTA: (not specified in plan) → partner must
     watch the embedded video for at least 15 seconds before the
     "प्रश्नों का जवाब दें" CTA appears.
  6. Delivery structure: Plain quiz → blocker popup containing video +
     3-point recap bullets (Bonus ₹120 / NetBox ₹50 / carry fee rule)
     above the quiz CTA. Header: "ज़रूरी अपडेट".
  7. Trigger context: Popup shown on "New Tasks" screen — blocks the
     partner's task-taking workflow until quiz is passed.

  WHY IT CHANGED:
  1. Date shifts — app launch and campaign timeline moved repeatedly
     (see Iteration 2). Quiz held back to align with operational
     readiness and to incorporate observations from earlier
     deployments.
  2. Learnings from previous quiz deployments — design evolved toward
     stricter retention testing. Reference to specific prior quizzes
     TBD; to be confirmed with campaign team and linked into this
     iteration when identified.
  [Reasons captured from Shiva on 2026-04-15 — to be enriched by
   campaign team with data references.]

  HYPOTHESIS:
  Forcing retention (not just exposure) via strict all-correct quiz
  with restart will produce better actual understanding of the PayG
  economic model than a lenient 4/5 gate, even at the cost of higher
  friction and longer time-to-pass. The 15-second video gate ensures
  minimum forced exposure before any quiz attempt.

  RESULT:
  Pending. First day of deployment 15/04. Measure in 3-5 days.
  Key metrics to watch:
    - Quiz attempt rate (of eligible partners, ~1,400 base)
    - Median attempts to pass
    - Time-to-pass distribution
    - Partners stuck (e.g. >5 attempts without passing)
    - Drop-off at video gate vs drop-off during quiz
    - Which specific questions cause the most wrong answers (topic
      weakness signal)

  FULL QUIZ COPY (captured for measurement + learning reference):

    Q1: हर connection के recharge पर आपको कितना commission मिलेगा?
        A) ₹300 fixed, installation पर भी  ✅
        B) Wiom हर महीने decide करेगा कितना देना है
        C) Commission नहीं, सिर्फ़ bonus मिलेगा

    Q2: ज़्यादा Bonus पाने के लिए क्या करना होगा?
        A) अपनी internet quality अच्छी रखनी होगी  ✅
        B) Wiom office जाकर request करना होगा
        C) ज़्यादा से ज़्यादा phone calls करने होंगे

    Q3: Internet quality का मतलब क्या है?
        A) सारे connections बिना रुके चलें (uptime) और सही ISP speed आए  ✅
        B) Customer को ज़्यादा से ज़्यादा data मिले
        C) WiFi का range बढ़ाना

    Q4: Internet quality measure करने के लिए क्या होगा?
        A) आपके office में PNM device लगेगा, जो हमेशा ON रखना है  ✅
        B) हर हफ़्ते Wiom की team आकर check करेगी
        C) Customer खुद app पर rating देगा

    Q5: Customer से NetBox collect करने पर क्या मिलेगा?
        A) ₹50, हर collected NetBox पर  ✅
        B) कुछ नहीं, यह अलग से paid नहीं है
        C) NetBox का पैसा साल के end में मिलेगा

    Q6: NetBox collect करने के बाद carry fee कब से लगेगी?
        A) 15 दिन बाद से — ₹2 प्रति दिन  ✅
        B) पहले दिन से ही लगेगी
        C) Carry fee जैसा कुछ नहीं है

    Q7: नए system में customer का internet कैसे चलेगा?
        A) Customer जितने दिन चाहे उतने दिन का recharge करेगा  ✅
        B) Wiom khud se customer का plan renew करेगा
        C) Wiom automatically सबको internet देगा, recharge की ज़रूरत नहीं

    Q8: नए app पर क्या-क्या होगा?
        A) NetBox rules, updated rate card — सब एक जगह  ✅
        B) सिर्फ़ Wiom का phone number
        C) सिर्फ़ पुराने bills की list

---

## Iteration 4 — M8 PNM Comm: Text → Video; Frameworks Filed (2026-04-28 to 2026-04-30)

  WHAT CHANGED:
  1. M8 deliverable evolved from WhatsApp text message (Karishni's v2
     brief at review-queue/project-csp-migration-apr26/2026-04-27-
     pnm-device-bonus-eligibility.md) to a 1:02-minute WhatsApp video
     (Wiom_PNM_Bonus.mp4). Video sent to two cohorts on 2026-04-29:
     - Entry 8 (comms-log): 756 PNM-installed partners
     - Entry 9 (comms-log): 445 PNM-not-installed partners (with
       form CTA: https://forms.gle/MGWVsUQozUCobh916)
  2. Two product-team frameworks were filed mid-flight:
     - Unified Attention Framework v1.3 (cross-project, in-app
       attention rules) — promoted to L1-global/attention-framework.md
       on 2026-04-30 under explicit human override (CLAUDE.md normally
       forbids agent-authored L1 files)
     - CSP App Adoption System v1.2 (migration-specific, three-phase
       adoption + six locked event types) — filed at L3 project level
       since per Shiva's reading it is migration-specific despite the
       doc claiming permanence
  3. Content principles surfaced from script iteration consolidated
     into L2-domain-playbooks/content-improvement-log.md (15 principles
     covering tone, framing, vocabulary, sequencing, surveillance
     framing, transition disclosure, and pilot-partner positioning).

  WHY IT CHANGED:
  1. Video over text: better for the operational complexity (3 audiences
     in one comm — quiz+PNM-done partners get reinforcement; 393 quiz-
     done-but-PNM-not-done get the action; 16% deniers get the
     consequence). Video carries more density per second.
  2. Framework deferral: the new Adoption System framework demands
     in-app full-screen Event 3 (recorded-impact past-tense framing)
     for bonus-loss state changes — but the new app is not yet
     deployed. WA video is the deployable channel for the current
     partner base. Framework becomes the path for future designs once
     the new app ships.
  3. Bonus-led copy: per Shiva (2026-04-28), partners think in their
     own word ("bonus") not the team's word ("rating" / "quality").
     Copy was reordered to lead with the partner's stake, not the
     mechanism.
  4. 1-month grace period framing added per Satyam Darmora feedback
     (2026-04-28): "Bonus is changing" without a window reads as
     immediate pressure; with grace, partners get cognitive room.

  HYPOTHESIS:
  A short, bonus-led, factually-toned WhatsApp video — with explicit
  consequence-of-breakage framing and a clear two-path action (keep ON
  if installed; book a slot if not) — will move PNM activation among
  the 32.8% quiz-done-but-PNM-not-done cohort more than a text-only
  reminder would. Pre-emptive education is unlikely to move the 16%
  active deniers; for them, the recorded-consequence framing in
  Slide 4 ("PNM काम नहीं कर रहा? Bonus पर सीधा असर") sets up the
  in-app Event 3 framework when it eventually ships.

  RESULT:
  Pending. Video deployed 2026-04-29 to ~1,201 partners across two
  WhatsApp cohorts. Measure in 5-7 days:
    - PNM activation movement among Entry 9 cohort (445 partners)
    - Form submission rate for not-installed cohort
    - Active-denial rate change (was 235 deniers per Karishni's
      Apr 29 logging, up slightly from the 199 in this file's
      Cycle 2 snapshot — denial appears to be growing not shrinking)
    - Any PTL call spike on PNM device issues post-video

  NOTES ON DATA RECONCILIATION:
  This file's Measurement Cycle 2 (results.md) was snapshot on
  2026-04-28 with 199 deniers and 393 PNM-not-done. Karishni's
  Entry 8/9 audience data (Apr 29) shows 235 deniers and 445 PNM-not-
  done — newer data, slightly different totals. Future Cycle 3 should
  use the latest dashboard pull, not these snapshots.

  CONTENT PRINCIPLES SURFACED (consolidated to content-improvement-log.md):
  - Lead with partner's word ("bonus" not "rating")
  - No excited tone for state-change comms
  - Cause-effect chain over conditional warnings
  - Specify install agent (Wiom installs the device)
  - Temporal qualifiers in conditionals ("install हो चुकी है")
  - Headings must not crowd the visual
  - Long digit strings stay on screen, never in VO
  - Sequence: mechanism → consequence → action
  - Communicate transition / grace periods explicitly
  - Vocabulary continuity within a campaign
  - Avoid surveillance framing (passive measurement, not active monitoring)
  - Tell partners directly when there's a hard cutoff
  - Direct objective beats aspirational lever language
  - Pilot partners are early-access stakeholders, not subjects
  - Permission-to-break: tell pilot partners issues are expected

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
