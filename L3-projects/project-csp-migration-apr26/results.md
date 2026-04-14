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

## Measurement Cycle 2 — (next checkpoint)

  DATE           : TBD
  PERIOD         : TBD
  STAGE          : TBD — will cover quiz deployment, app transition,
                   and launch day metrics when available

---

*results.md — L3-projects/project-csp-migration-apr26/*
*Append-only. Next measurement cycle appended after next data checkpoint.*
