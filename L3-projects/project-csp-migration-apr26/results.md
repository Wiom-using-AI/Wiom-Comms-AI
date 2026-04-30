# Results — project-csp-migration-apr26

## FILE PURPOSE
Performance data per measurement cycle. The measurement agent and
learning agent both read this. Standard format is critical.

## RULES
- Append-only. Latest cycle loaded by default.
- Only use numbers actually present in this file. Never estimate.
- Each entry must include benchmark comparison where available.

## LIVE DATA SOURCE
For the most current metrics, WebFetch the live dashboard:
  URL: https://shivakimothi-design.github.io/csp-comms-dashboard/
The dashboard updates in real time. This file captures snapshots
at measurement checkpoints.

## LAST UPDATED
2026-04-28 — Cycle 2 added: post-launch quiz attempt rate and PNM device
             activation status (~Day 23 of campaign). 1,131 of 1,200 PNM
             partners completed quiz (94.3%). 393 partners (32.8%) did
             quiz but PNM activation NOT done — of these, 50.6% (199)
             actively DENIED PNM activation. ~16% of total partner base
             knowingly denied. This is the data triggering the M8 PNM
             device + bonus eligibility comm (see review-queue/
             project-csp-migration-apr26/2026-04-27-pnm-device-bonus-eligibility.md).
2026-04-13 — initial version populated from dashboard (data as of 10/04).
Maintained by: human or automated Metabase script.

---

## Benchmarks

No historical benchmarks available for this project type (first CSP
migration campaign). Targets from brief.md and campaign dashboard
used as reference.

  Video completion target    : 100% of partners by Day 5
  Quiz pass rate target      : >70% of attempts
  PTL call spike target      : No spike above baseline
  App download rate target   : >70% within 24hrs of launch

---

## Measurement Cycle 1 — Pre-Launch Education (as of 10/04)

  DATE           : 2026-04-10
  PERIOD         : 05/04 to 10/04 (first 5 days of campaign)
  STAGE          : Pre-launch education

### Contextual Popups (deployed 05/04)

  COMM_REF       : Contextual Popups (Wallet + Tickets)
  CHANNEL        : In-App popup
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : 1,212 (partners who opened app)

  METRIC                    VALUE          TARGET         STATUS
  -------------------------------------------------------------------------
  Popup reach               86.3%          100%           Below target
                            (1,046 of 1,212)
  S0 → S1 conversion       86.3%          —              Baseline

  NOTES: Dismissible popup. 13.7% of partners who opened the app
  did not see or engage with the popup. Acceptable for an organic,
  dismissible mechanism.

### Blocker Video (deployed 07/04 night)

  COMM_REF       : Blocker Video (2:10)
  CHANNEL        : In-App blocker (full-screen, non-dismissible)
  AUDIENCE       : Active OWNERs + ADMINs
  AUDIENCE_SIZE  : ~1,400

  METRIC                    VALUE          TARGET         STATUS
  -------------------------------------------------------------------------
  Video starters            1,054          —              Baseline
  80%+ watch rate           29.5%          90%+           RED
                            (311 partners)
  Full completion rate      18.9%          100%           RED
                            (199 partners)
  Median watch time         35 seconds     2:10 (full)    RED
  Drop-off at 20 sec       66%            —              Key concern

  HYPOTHESIS_TESTED: Forced (non-dismissible) video will drive education
  completion across the full partner base.

  RESULT: Hypothesis partially invalidated. While 1,054 partners started
  the video (high initiation), completion is critically low. The 66%
  drop-off by 20 seconds suggests the opening hook is not compelling
  enough, or partners are finding ways to bypass without watching.

  NEXT_ACTION:
  - Investigate whether partners are closing the app to bypass the
    blocker (technical check with engineering)
  - Review video opening 0:00-0:20 for hook strength
  - Consider whether WA push (deployed 09/04) recovers completion
    for non-completers
  - Survey plan (50-60 PTL calls) should test whether popup-only
    partners (S1) retained any information vs video completers (S2)

### WhatsApp Push (deployed 09/04)

  COMM_REF       : WA Push (non-completers)
  CHANNEL        : WhatsApp
  AUDIENCE       : S0/S1 partners (non-completers)
  AUDIENCE_SIZE  : TBD

  METRIC                    VALUE          TARGET         STATUS
  -------------------------------------------------------------------------
  (Metrics not yet available as of 10/04 snapshot)

  NOTES: Deployed 09/04. Impact on S2 conversion to be measured
  in next cycle.

---

## Measurement Cycle 2 — Quiz + PNM Activation Funnel (as of 28/04)

  DATE           : 2026-04-28
  PERIOD         : ~15/04 (quiz launch) to 28/04 (snapshot)
  STAGE          : Post-launch — quiz adoption + PNM device activation
  UNIVERSE       : 1,200 PNM partners
  DEFINITIONS    : "Quiz Done" = either OWNER or ADMIN of the partner
                   account completed quiz
                   "PNM Done" = Activation Done (PNM device installed
                   and operational)

### Quiz × PNM activation cross-tab

  CELL                         COUNT     % OF UNIVERSE
  ---------------------------------------------------------
  Quiz Done × PNM Done          738      61.5%   ← target state
  Quiz Done × PNM Not Done      393      32.8%   ← key concern
  Quiz Not Done × PNM Done       11       0.9%
  Quiz Not Done × PNM Not Done   58       4.8%
  ---------------------------------------------------------
  Quiz Done totals             1,131     94.3%
  PNM Done totals                749     62.4%

### PNM Not Done — sub-status breakdown (n = 393)

  PNM STATUS        COUNT    % OF 393    % OF UNIVERSE
  ---------------------------------------------------------
  Denied               199      50.6%        16.6%   ← critical
  Not Assigned         145      36.9%        12.1%
  Rescheduled           36       9.2%         3.0%
  Not Available         12       3.1%         1.0%
  Assigned               1       0.3%         0.1%

### Headline read

  METRIC                       VALUE       TARGET       STATUS
  ---------------------------------------------------------------
  Quiz attempt rate            94.3%       >70%         GREEN
                               (1,131 / 1,200)
  PNM activation rate          62.4%       100%         RED
                               (749 / 1,200)
  Quiz-to-PNM conversion       65.3%       —            Baseline
                               (738 / 1,131 quiz-done partners)
  Active PNM denial rate       16.6%       <5%          RED
                               (199 of 1,200 — knowingly denied
                               despite quiz exposure)

  HYPOTHESIS_TESTED: The blocker video + 8-question quiz (Entry 6)
  would drive sufficient understanding of PNM device's role in bonus
  eligibility to result in PNM activation across the partner base.

  RESULT: Hypothesis partially invalidated. Quiz attempt rate is high
  (94.3%) — partners did engage with the verification mechanism. But
  PNM activation funnel breaks down post-quiz: only 65.3% of
  quiz-completers also activated PNM. More concerning: 16.6% of the
  full base (199 partners) actively DENIED PNM activation despite
  quiz exposure. This is a behaviour problem, not a knowledge gap —
  these partners likely understand the PNM-bonus link but still
  refused activation.

  Per the L1-candidate Adoption System framework filed 2026-04-28
  (review-queue/adhoc/), this profile fits "system change is a
  behaviour problem, not a knowledge gap" — solution is event-driven
  reinforcement at the moment of consequence (Event 3 — Bonus Loss
  full-screen interrupt when bonus actually pauses), not pre-emptive
  pre-loss WhatsApp education.

  NEXT_ACTION:
  - Investigate WHY 199 partners denied PNM. Possible drivers:
    (a) distrust of measurement device, (b) physical space concern,
    (c) electricity cost concern, (d) belief that bonus loss is
    not real / negotiable, (e) preference for old contract.
  - PTL outbound to a sample of the 199 deniers — qualitative
    diagnosis of the actual block.
  - Resolve M8 PNM comm design — see Karishni's PENDING brief at
    review-queue/project-csp-migration-apr26/2026-04-27-pnm-device-
    bonus-eligibility.md. Two open flags: audience scope, TRAI
    classification.
  - Tension: M8 brief uses pre-emptive WhatsApp framing
    ("eligibility paused" conditional). New L1-candidate frameworks
    (filed 2026-04-28) demand event-driven recorded-impact framing
    via in-app full-screen Event 3 at moment of bonus pause. Human
    decision needed: ship M8 as designed, or redesign per new
    frameworks, or both (WA bridge + in-app interrupt).
  - For "Not Assigned" (145) and "Rescheduled" (36): operational
    follow-through, not comms problem. Different cohort.

---

## Measurement Cycle 3 — (next checkpoint)

  DATE           : TBD
  PERIOD         : TBD
  STAGE          : TBD — will cover post-M8 PNM denial movement and
                   any in-app event implementation

---

*results.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next measurement cycle appended after next data checkpoint.*
