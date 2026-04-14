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

## LAST UPDATED
2026-04-13 — initial version populated from CSP Comms Dashboard.
Maintained by: logger agent writes, human spot-checks.

---

## Historical Summary

No historical entries yet. All entries are within the rolling window.

---

## Log Entries

### Entry 1

  DATE           : 2026-04-02
  TYPE           : design
  CHANNEL        : WhatsApp Utility
  MESSAGE_REF    : M6 (D0: App is Live, Your State is Ready)
  AUDIENCE       : Active CSPs (~1,200)
  AUDIENCE_SIZE  : ~1,200
  SUMMARY        : App download/update instructions. Dashboard is ready.
                   Single CTA: download new app, check dashboard.
                   Hindi-primary. Trust Line fallback.
  METRICS        : N/A — designed but deployment pending product
                   confirmation of dashboard readiness
  DESIGNED_BY    : Claude — agent session
  STATUS         : pending
  NOTES          : Output in review-queue/project-csp-migration-apr26/
                   2026-04-02-d0-app-live-welcome.md.
                   Designed from L1 globals only (onboarding playbook
                   not yet created). QUALITY CHECK: FLAG (2.4 playbook
                   pending). SECURITY CHECK: PASS.

---

### Entry 2

  DATE           : 2026-04-05
  TYPE           : deploy
  CHANNEL        : In-App (contextual popup)
  MESSAGE_REF    : Pre-launch — Contextual Popups
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400
  SUMMARY        : Dismissible contextual popups on Wallet and Tickets
                   screens. Organic discovery mechanism. Partners who
                   see these move from S0 to S1.
  METRICS        : Popup reach: 86.3% (1,046 of 1,212 partners as of
                   10/04). See results.md for full metrics.
  DESIGNED_BY    : Campaign team (not via Comms AI pipeline)
  STATUS         : deployed
  NOTES          : First education touchpoint. Designed outside the
                   Comms AI pipeline. CleverTap event:
                   contextual_popup_seen.

---

### Entry 3

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

---

### Entry 4

  DATE           : 2026-04-09
  TYPE           : deploy
  CHANNEL        : WhatsApp
  MESSAGE_REF    : Pre-launch — WA Push (non-completers)
  AUDIENCE       : Partners at S0 or S1 (did not complete blocker video)
  AUDIENCE_SIZE  : TBD — targeted to non-completers only
  SUMMARY        : WhatsApp message to partners who have not completed
                   the blocker video. Redirects them back to blocker.
                   Targeted, not blasted to all.
  METRICS        : Pending — see results.md for updates
  DESIGNED_BY    : Campaign team
  STATUS         : deployed
  NOTES          : Only sent to non-completers. S2+ partners excluded.

---

### Entry 5

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

---

### Entry 6

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

*comms-log.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next entry appended after next deployment.*
