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
2026-05-13 — Entry 11 appended: Five belief break moments released in new
             partner app. Three fully locked (A1, A3, A4) with inform +
             quiz. Two inform-only for now (A2, A5 — quizzes pending).
             Triggered at consequence moments, not assignment moments.
2026-05-13 — Entry 10 appended: Old app blocker + new app launch deployed to
             61 CSPs and their field agents (rohits) on 2026-05-12. Two-screen
             in-app blocker with embedded video (wiom-csp-v19.mp4) and download
             CTA. Entry 5 closed with pointer to Entry 10.
2026-04-27 — Entries 8 and 9 appended: PNM activity WA messages sent
             to two cohorts — partners with PNM installed (Entry 8)
             and partners without PNM installed (Entry 9). Both
             include Wiom_PNM_Bonus.mp4 (1:02 min). New video asset
             first appearance in log. Entry 9 introduces first
             WhatsApp CTA button (Form bharein) in this project.
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
                   → See Entry 10 for actual deployment on 2026-05-12.

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

---

### Entry 8

  DATE           : 2026-04-27
  TYPE           : deploy
  CHANNEL        : WhatsApp
  MESSAGE_REF    : PNM Activity — Cohort 1 (PNM installed)
  OS_TRIGGER     : quality + compensation
  AUDIENCE       : Partners with PNM device already installed
                   (PNM Status = "Activation Done")
  AUDIENCE_SIZE  : 756
  SOURCE_LIST    : pnm-partner-contacts-2026-04-29.csv
                   (held locally — not reproduced in repo)
  SUMMARY        : Hinglish WhatsApp message with embedded video
                   (Wiom_PNM_Bonus.mp4, 1:02 min). Informs partners
                   that their PNM device records internet quality and
                   that bonus eligibility is based on this. CTA to
                   keep device ON and watch video for details.
  HEADER         : "Wiom System Update"
  COPY_HI        : "Aapke office mein laga PNM device aapki internet
                   quality record karta hai. Bonus eligibility isi ke
                   anusar hoti hai."
  COPY_BOLD_CTA  : "PNM device hamesha ON rakhein - video mein details
                   dekhein."
  VIDEO          : Wiom_PNM_Bonus.mp4 — 1:02 min, HD
                   Thumbnail text: "New System — Bonus /
                   अब Network Quality पर Bonus मिलेगा"
                   (First appearance of this video asset in the log.
                   File held by campaign team.)
  BUTTON         : None
  CLASSIFICATION : Service (same flag as Entries 3 and 7 — to be
                   human-confirmed against TRAI consent records)
  METRICS        : Pending — see results.md for updates
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : First direct WA communication on PNM device and
                   bonus link for the cohort that has PNM installed.
                   Pairs with Entry 9 (same day, different cohort).
                   Audience size TBD — request from campaign team.

---

### Entry 9

  DATE           : 2026-04-27
  TYPE           : deploy
  CHANNEL        : WhatsApp
  MESSAGE_REF    : PNM Activity — Cohort 2 (PNM not installed)
  OS_TRIGGER     : quality + compensation
  AUDIENCE       : Partners without PNM device installed
                   Status breakdown from source list:
                     Denied        : 235
                     Not Assigned  : 155
                     Rescheduled   :  37
                     Not Available :  15
                     Assigned      :   3
                     Total         : 445
  AUDIENCE_SIZE  : 445
  SOURCE_LIST    : pnm-partner-contacts-2026-04-29.csv
                   (held locally — not reproduced in repo)
  SUMMARY        : Hinglish WhatsApp message with embedded video
                   (Wiom_PNM_Bonus.mp4, 1:02 min). Informs partners
                   their PNM device has not been installed, explains
                   its role in recording internet quality and
                   determining bonus eligibility. CTA to fill a form
                   to get device installed.
  HEADER         : "Wiom System Update"
  COPY_HI        : "Aapke location par PNM device abhi install nahi
                   hua hai. Yeh device internet quality record karta
                   hai — bonus eligibility isi ke anusar hoti hai."
  COPY_BOLD_CTA  : "Device install karaane ke liye neeche diya gaya
                   form bharein."
  COPY_SECONDARY : "Video mein detail dekhein."
  VIDEO          : Wiom_PNM_Bonus.mp4 — 1:02 min, HD (same as Entry 8)
  BUTTON         : "Form bharein" (external link)
                   Form URL : https://forms.gle/MGWVsUQozUCobh916
  CLASSIFICATION : Service (same flag as Entries 3 and 7 — to be
                   human-confirmed against TRAI consent records)
  METRICS        : Pending — see results.md for updates
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : First WA message targeting partners without PNM.
                   First use of a WhatsApp CTA button in this project.
                   Form URL not captured — must be logged once confirmed.
                   Pairs with Entry 8 (same day, different cohort).
                   Audience size TBD — request from campaign team.

---

### Entry 10

  DATE           : 2026-05-12
  TYPE           : deploy
  CHANNEL        : In-App (blocker + new app redirect)
  MESSAGE_REF    : App Transition — Old App Blocker + New App Launch
  LINKED_PLAN    : Entry 5
  APP_VERSION    : Old partner app (pre-transition)
  AUDIENCE       : CSPs and their field agents (rohits)
  AUDIENCE_SIZE  : 61 CSPs + rohits (exact rohit count not confirmed)
  PREVIEW_URL    : https://shivakimothi-design.github.io/csp-migration-preview/

  SUMMARY        : Old app now shows a 2-screen non-dismissible blocker.
                   Partners cannot proceed past it without downloading the
                   new app. Bilingual (Hindi / English). Introduces the
                   "CSP" identity label for partners across the platform.
                   30-day financial features grace period communicated.

  SCREEN_1       : Blocker / Announcement
    HEADER       : "Wiom System Update"
    BODY_HI      : "नया ऐप नए सिस्टम में लाइव है"
    BODY_EN      : "New App is live under the new system"
    CTA_HI       : "जानें और डाउनलोड करें"
    CTA_EN       : "Learn more & Download"
    DESTINATION  : Screen 2 (transition.html)

  SCREEN_2       : Transition / Detail
    TAGLINE_HI   : "रिचार्ज वाला घर का नेट"
    TAGLINE_EN   : "Pay-as-you-go home internet"
    IDENTITY_NOTE: Partner is now designated "CSP" throughout the platform
    VIDEO        : wiom-csp-v19.mp4 — embedded in screen
                   Topics: bonus structures, payouts, NetBox, customer plans
                   (exact script not captured — file held by campaign team)
    GRACE_PERIOD : 30-day adjustment period communicated as 4 points:
                   1. Full time to learn the new app
                   2. Financial features (bonus, carry fee, etc.) not active
                      for 30 days
                   3. In-app guidance replaces separate training materials
                   4. Support available on 78368-11111
    CTA_HI       : "नया ऐप डाउनलोड करें"
    CTA_EN       : "Download New App"

  CREATIVE_FILE  : wiom-csp-v19.mp4 (file held by campaign team;
                   not archived in repo)
  METRICS        : Pending — not yet captured
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : This is the actual deployment of planned Entry 5
                   (App Transition + hard lock). Audience is CSPs and
                   their field agents (rohits), not the full ~1,400
                   partner base from earlier entries — this is a scoped
                   rollout to 61 CSPs at this stage. Video script not
                   logged — must be captured from campaign team before
                   next iteration. 30-day grace period on financial
                   features is a new commitment not present in planned
                   Entry 5 — note for iterations.md.

---

### Entry 11

  DATE           : 2026-05-13
  TYPE           : deploy
  CHANNEL        : In-App (new partner app — contextual belief breaks)
  MESSAGE_REF    : Belief Break System v1.5 — Five Cases
  APP_VERSION    : New partner app (post-transition)
  AUDIENCE       : CSPs and their field agents (rohits)
  AUDIENCE_SIZE  : 61 CSPs + rohits (same cohort as Entry 10)
  MOCKUP_URL     : https://ashishagrawal-iam.github.io/wiom-belief-break-mockups/

  SUMMARY        : Five contextual belief-correction moments released in
                   the new app. Each triggers at a consequence moment —
                   the instant a financial or behavioural outcome occurs —
                   not at an assignment moment. Three cases fully locked
                   (inform screen + quiz). Two cases inform-only for now
                   (quiz copy pending). All screens follow a shared
                   template: inform screen with "ठीक है" CTA, followed
                   by a 3-option Hindi quiz where wrong answers show the
                   correct answer with explanation.

  CASE_A1        : Carry Fee — Two Paths Stop It
    TRIGGER      : Day 16, first carry fee debit (after 15-day grace)
    BELIEF_BREAK : Partner can install the NetBox OR return it to Wiom —
                   both stop the fee immediately
    STATUS       : Locked v1.5 — inform + quiz live
    QUIZ         : "How do you stop the carry fee charge?"
    CORRECT_ANS  : "NetBox install करें या Wiom को वापस करें"

  CASE_A2        : Withdrawal Timing — Tuesday and Friday Only
    TRIGGER      : First earnings credited to CSP wallet
    BELIEF_BREAK : Withdrawals are restricted to Tuesday and Friday only
    STATUS       : Inform locked v2 — quiz copy still in development
    QUIZ         : Pending

  CASE_A3        : ₹300 Per Activation — Not Per Recharge
    TRIGGER      : First PayG plan connection activates and ₹300 credits
    BELIEF_BREAK : ₹300 auto-credits on each new customer activation;
                   existing customer recharges do not trigger payouts
    STATUS       : Locked v1.5 — inform + quiz live
    QUIZ         : "अगला connection activate करने पर भी ₹300 मिलेंगे?"
    CORRECT_ANS  : Activation events only (one per customer); recharge
                   events do not trigger commission

  CASE_A4        : ₹50 Auto-Credits Every Pickup
    TRIGGER      : First successful pickup completion and ₹50 credits
    BELIEF_BREAK : Every successful pickup auto-credits ₹50 — no
                   claiming required; it recurs on every pickup
    STATUS       : Locked v1.5 — inform + quiz live
    QUIZ         : "अगली pickup पर भी ₹50 मिलेंगे?"
    CORRECT_ANS  : Automatic credit on every successful pickup; no
                   action needed

  CASE_A5        : Quality Score Drives Bonus and Work Volume
    TRIGGER      : Onboarding day or first quality score available
    BELIEF_BREAK : Quality score directly drives both bonus amount AND
                   volume of tasks routed to the CSP
    STATUS       : Inform locked v2 — quality measurement model pending;
                   quiz TBD
    QUIZ         : Pending

  METRICS        : Pending — in-moment quiz pass rates to be tracked
                   per case via CleverTap (event names to be confirmed
                   with product team)
  DESIGNED_BY    : Campaign team + Product (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : Belief break system is the primary conceptual clarity
                   mechanism for the measurement framework agreed
                   2026-05-13. Operational clarity is measured separately
                   via behavioural signals per case. A5 operational
                   measurement is a known dependency on the quality
                   measurement model (open question). Quiz copy for A2
                   and A5 to be logged as a new entry when deployed.
                   Implementation via MockAttentionRepository — no screen
                   code changes as template is frozen.

---

*comms-log.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next entry appended after next deployment.*

SECURITY CHECK: PASS — PayG positioning intact (no subscription framing),
no PII in log (audience lists referenced generically, not reproduced),
copy within PCA tone envelope, Hinglish copy reviewed — no forbidden
terms, neutral-professional tone maintained.
Flags carried forward:
  Entry 3 + 7 + 8 + 9: message classification (Service) to be
  human-confirmed against TRAI consent records before re-use as pattern.
  Entry 9: Form URL confirmed — https://forms.gle/MGWVsUQozUCobh916
