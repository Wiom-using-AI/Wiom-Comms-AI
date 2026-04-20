# Comms Log — project-csp-migration-apr26

## FILE PURPOSE
Chronological log of every comm sent in this project. The design agent
reads this to avoid audience fatigue and repeat messages. The logger
agent appends to it after every deployment.

## RULES
- Append-only. Never edit or delete existing entries.
- Rolling 20-entry window. When entries exceed 20, summarise older
  entries into the Historical Summary section below.
- Every entry must use the standard format.
- STATUS must be one of: pending / approved / deployed / measured
- PLANNED vs DEPLOYED: Every entry must clearly indicate whether it is
  planned (STATUS: pending / approved) or actually deployed
  (STATUS: deployed). Logger agent always asks before writing.
- Plan becomes reality: When a planned entry is actually deployed,
  do NOT edit the original. Write a NEW entry for the deployment
  with a LINKED_PLAN field referencing the plan entry number.
  Append a single closing line to the plan entry:
  "→ See Entry N for actual deployment on [date]". Add a row to
  iterations.md documenting the plan-to-reality delta.

## LAST UPDATED
2026-04-20 — Entry 7 appended: WA nudge to 651 quiz non-attempters on
             2026-04-20. Copy byte-identical to Entry 3.
2026-04-15 (pm) — Entry 6 appended: Recap + Quiz deployment on 15/04
             (evolved from planned Entry 4). Entry 4 annotated with
             closing line pointing to Entry 6. RULES section extended
             with planned-vs-deployed clause and plan-to-reality
             transition rule. iterations.md Iteration 3 added in same
             commit.
2026-04-15 — Previous Entry 1 (M6 pending design) removed per human
             instruction (was a design draft, never deployed; tracked in
             review-queue). Remaining entries renumbered. Entries 1, 2, 3
             (contextual popup, blocker video, WA nudge) enriched in place
             with actual deployed content. Append-only rule waived per
             explicit human instruction on 2026-04-15.
2026-04-13 — initial version populated from CSP Comms Dashboard.
Maintained by: logger agent writes, human spot-checks.

---

## Historical Summary

No historical entries yet. All entries are within the rolling window.

---

## Log Entries

### Entry 1

  DATE           : 2026-04-05
  TYPE           : deploy
  CHANNEL        : In-App (contextual popup)
  MESSAGE_REF    : Pre-launch — Contextual Popups (2 variants)
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400
  SUMMARY        : Two one-time mandatory contextual popups on Wallet
                   and Service Ticket screens. Partners who see these
                   move from S0 to S1. Dismiss only on "Theek hai" click.

  POPUP_A        : Wallet / Earnings screen
    TRIGGER      : Shown on first landing on Wallet / Earnings section
    INTENT       : Educate on "up to ₹120 per connection based on
                   internet quality" going live 5th April
    COPY_HEADER  : "Bonus – ₹120 तक Internet quality के हिसाब से"
    CTA          : "Theek hai" (mandatory click to dismiss)

  POPUP_B        : Service Ticket full view
    TRIGGER      : Shown on first full view of a service ticket when
                   partner is about to assign it
    INTENT       : Educate on "keep your internet quality good" going
                   live 5th April
    COPY_HEADER  : "Keep your Internet quality well"
    CTA          : "Theek hai" (mandatory click to dismiss)

  METRICS        : Popup reach: 86.3% (1,046 of 1,212 partners as of
                   10/04). Combined metric for both variants under
                   CleverTap event contextual_popup_seen. See
                   results.md for full metrics.
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : First education touchpoint. Designed outside the
                   Comms AI pipeline. Copy enriched 2026-04-15 from
                   campaign team brief + deployed screenshots.

---

### Entry 2

  DATE           : 2026-04-07 (night)
  TYPE           : deploy
  CHANNEL        : In-App (blocker video)
  MESSAGE_REF    : Pre-launch — Blocker Video (2:10)
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400
  SUMMARY        : Full-screen, non-dismissible blocker video. 2 min
                   10 sec. Covers connection assignment, PayG, earnings,
                   NetBox, carry fee, timeline. Partners who complete
                   move from S1 to S2.
  CREATIVE_FILE  : Wiom_System_Updates_v2.mp4 (source file held by
                   campaign team; not archived in repo)
  METRICS        : Video starters: 1,054. 80%+ watch: 29.5% (311).
                   Full completion: 18.9% (199). Median watch time:
                   35 seconds. 66% drop-off by 20 seconds.
                   (As of 10/04 — see results.md for updates.)
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : Most critical pre-launch education moment. Forced
                   mechanism (non-dismissible). Low completion rate is
                   a key concern. CleverTap event:
                   blocker_video_completed. Deployed night of 07/04.
                   Creative filename logged 2026-04-15.

---

### Entry 3

  DATE           : 2026-04-09
  TYPE           : deploy
  CHANNEL        : WhatsApp
  MESSAGE_REF    : Pre-launch — WA Push (non-completers)
  AUDIENCE       : Partners at S0 or S1 (did not complete blocker video)
  AUDIENCE_SIZE  : TBD — targeted to non-completers only
  SUMMARY        : Short Hindi WhatsApp nudge redirecting non-completers
                   back to the blocker video via deep link. Targeted,
                   not blasted to all.
  COPY_HI        : "ज़रूरी अपडेट अभी तक नहीं देखा। App खोलें -
                   https://partnerapp.wiom.in/page/home"
  COPY_EN_GLOSS  : "Haven't seen the important update yet.
                   Open the App - [deep link]"
  CLASSIFICATION : Transactional / Service (to be human-confirmed
                   against TRAI consent records before re-use as pattern)
  METRICS        : Pending — see results.md for updates
  DESIGNED_BY    : Campaign team
  STATUS         : deployed
  NOTES          : Only sent to non-completers. S2+ partners excluded.
                   Copy logged 2026-04-15 from campaign team screenshot.

---

### Entry 4

  DATE           : TBD (not yet deployed as of 2026-04-13)
  TYPE           : planned
  CHANNEL        : In-App (recap + quiz)
  MESSAGE_REF    : Pre-launch — Recap + Quiz
  AUDIENCE       : Partners at S2+ (completed blocker video)
  AUDIENCE_SIZE  : TBD — depends on S2 conversion
  SUMMARY        : Recap of key changes followed by 5-question quiz.
                   Pass threshold: 4/5. Partners who pass move to S4.
                   Only available to S2+ states.
  METRICS        : N/A — not yet deployed
  DESIGNED_BY    : Campaign team
  STATUS         : pending
  NOTES          : Quiz is the education verification gate. Target:
                   >70% pass rate of attempts. Not yet deployed as of
                   13/04.
                   → See Entry 6 for actual deployment on 2026-04-15.

---

### Entry 5

  DATE           : TBD (not yet deployed as of 2026-04-13)
  TYPE           : planned
  CHANNEL        : In-App (app transition + hard lock)
  MESSAGE_REF    : Pre-launch — App Transition
  AUDIENCE       : All active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400
  SUMMARY        : S0/S1 partners locked out of old app. S2+ partners
                   offered new app download. Hard transition point.
  METRICS        : N/A — not yet executed
  DESIGNED_BY    : Campaign team + Product
  STATUS         : pending
  NOTES          : This is the hard cutover. Partners below S2 cannot
                   proceed without completing education.

---

### Entry 6

  DATE           : 2026-04-15
  TYPE           : deploy
  CHANNEL        : In-App (blocker popup → video + recap → quiz)
  MESSAGE_REF    : Pre-launch — Recap + Quiz (actual deployment)
  LINKED_PLAN    : Entry 4
  APP_VERSION    : Current (old) partner app — pre-transition
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400
  TRIGGER        : Blocker popup appears on "New Tasks" screen.
                   Non-dismissible until quiz passed.
  SUMMARY        : Full-screen blocker. Header:
                   "ज़रूरी अपडेट — आगे बढ़ने से पहले यह जानना ज़रूरी है।"
                   Video embedded at top. Below video: 3-point recap
                   (Bonus ₹120 / NetBox ₹50 / 15-day carry fee rule).
                   CTA "प्रश्नों का जवाब दें" appears only after partner
                   watches video for 15 seconds. Clicking CTA starts an
                   8-question quiz.
  VIDEO_GATE     : 15 seconds of video watch required before quiz CTA
                   appears.
  RECAP_BULLETS  : "Bonus ₹120 तक — internet quality पर निर्भर"
                   "NetBox collect करने पर ₹50"
                   "15 दिन बाद NetBox idle हो तो ₹2/दिन carry fee"
  QUIZ_LENGTH    : 8 questions (Hindi/Hinglish)
  QUIZ_TOPICS    : Q1 commission (₹300 fixed, on recharge + installation);
                   Q2 bonus driver (good internet quality);
                   Q3 internet quality definition (uptime + ISP speed);
                   Q4 measurement mechanism (PNM device in partner office,
                   always ON);
                   Q5 NetBox collection fee (₹50 per collected NetBox);
                   Q6 NetBox carry fee (no charge for 15 days, then
                   ₹2/day);
                   Q7 PayG customer model (customer recharges as needed,
                   not monthly);
                   Q8 new app contents (NetBox rules, rate card, updates —
                   one-stop destination).
  PASS_LOGIC     : Must answer ALL 8 correctly. Wrong answer on any
                   question → quiz restarts from Q1. No partial pass.
                   No skip.
  METRICS        : Pending — first day of deployment. See results.md
                   for updates.
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : Stricter than planned Entry 4: 8Q vs 5Q, all-correct
                   vs 4/5 pass, restart-on-wrong added, 15-sec video
                   gate added. See iterations.md Iteration 3 for full
                   plan→reality delta. Full quiz copy captured in
                   Iteration 3. CleverTap event name: to be confirmed
                   with campaign team (expected: quiz_started /
                   quiz_completed).

---

### Entry 7

  DATE           : 2026-04-20
  TYPE           : deploy
  CHANNEL        : WhatsApp
  MESSAGE_REF    : Post-launch — WA Nudge (quiz non-attempters)
  AUDIENCE       : Partners who had not yet attempted the Recap + Quiz
                   (Entry 6) as of 2026-04-20 morning. Source list:
                   "Not completed reminder.xlsx" — phone numbers only.
  AUDIENCE_SIZE  : 651
  SUMMARY        : Hindi WhatsApp nudge redirecting quiz non-attempters
                   back to the app via deep link. Targeted send to the
                   pending pool only. Copy is byte-identical to Entry 3
                   (the earlier WA nudge for blocker-video non-completers).
  COPY_HI        : "ज़रूरी अपडेट अभी तक नहीं देखा। App खोलें -
                   https://partnerapp.wiom.in/page/home"
  COPY_EN_GLOSS  : "Haven't seen the important update yet.
                   Open the App - [deep link]"
  CLASSIFICATION : Transactional / Service (inherits Entry 3 flag —
                   to be human-confirmed against TRAI consent records
                   before re-use as a pattern)
  METRICS        : Pending — see results.md for updates
  DESIGNED_BY    : Human (ad-hoc, not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : Follows Entry 6 (Recap + Quiz, live since 2026-04-15).
                   Targets the residual pool that hadn't attempted the
                   quiz 5 days after launch. Copy is identical to Entry 3,
                   so any partner who was an S0/S1 non-completer on
                   09/04 AND is still a quiz non-attempter on 20/04 has
                   now received this exact WA twice. Worth watching for
                   WA template fatigue / report-spam signals before the
                   next targeted nudge.

---

*comms-log.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next entry appended after next deployment.*

SECURITY CHECK: PASS — PayG positioning intact (no subscription framing),
no PII in log (phone list referenced generically, not reproduced), copy
within PCA tone envelope. Flag carried forward: Entry 3 + Entry 7
classification (Transactional/Service) to be human-confirmed against
TRAI consent records before re-use as a pattern.
