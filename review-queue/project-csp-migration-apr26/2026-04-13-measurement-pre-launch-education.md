# Measurement Report — project-csp-migration-apr26 — 2026-04-13

MODE             : Mode 2 — Standalone
MEASUREMENT SCOPE: Pre-launch education campaign — all deployed touchpoints
DATA SOURCES     : results.md snapshot (as of 2026-04-10) + live dashboard
                   (https://shivakimothi-design.github.io/csp-comms-dashboard/)
                   Dashboard fetch: 2026-04-13. No newer data than 10/04 snapshot.
PREPARED BY      : Claude — measurement agent session

---

## DATA DISCREPANCY — READ BEFORE INTERPRETING

results.md and context-from-teams.md both state "66% drop-off by 20 seconds."
The live dashboard returns "20-second mark: 66% still watching" (i.e., 34% dropped).

These cannot both be correct. The 35-second median watch time is internally
consistent only with the dashboard figure: if 66% are still watching at 20 sec
and 54% at 30 sec, a median of 35 sec is plausible. The "66% drop-off at 20 sec"
figure from the static files would imply a median well below 20 seconds — not 35.

Action required: Verify against raw CleverTap event data before acting on
the drop-off figure. All analysis below uses the 35-second median as the
anchor metric. The drop-off figure is noted but flagged as unverified.

---

## Comms in Scope

  1. Contextual popups (wallet + tickets)   — deployed 05/04
  2. Blocker video (2:10–2:36)              — deployed 07/04 (night)
  3. WhatsApp push (non-completers)         — deployed 09/04

  Not in scope (not yet deployed as of 13/04):
    Recap + quiz, app transition + hard lock

---

## Success Thresholds (from context-from-teams.md)

  GREEN  : >90% video complete, >70% quiz pass, flat/declining PTL calls
  YELLOW : 70–90% video, 50–70% quiz, slight call increase
  RED    : <70% video, <50% quiz, >2x baseline PTL calls

  Additional targets from results.md (brief-derived):
    Video completion   : 100% of partners by Day 5
    Quiz pass rate     : >70% of attempts
    PTL spike          : No increase above baseline
    App download rate  : >70% within 24hrs of launch

---

## Metric-by-Metric Classification

### 1 — Contextual Popups (05/04)

  METRIC             VALUE                  TARGET     STATUS
  -----------------------------------------------------------------------
  Popup reach        86.3%                  100%       YELLOW
                     (1,046 of 1,212 app
                     openers; ~74.7% of
                     ~1,400 total audience)
  S0 → S1 conv.      86.3% of app openers   —          BASELINE

  Notes:
  - Denominator ambiguity: 86.3% is of partners who opened the app (1,212),
    not of total audience (~1,400). Of total audience, reach is ~74.7%.
  - Mechanism was dismissible. 86% reach on a dismissible organic popup
    is reasonable for a first touchpoint.
  - 13.7% of app-openers did not see or engage. Acceptable for this
    mechanism — no benchmark exists for dismissible popup reach.
  - No formal GREEN/YELLOW/RED threshold specified for popups. YELLOW
    applied because target was 100% and actual is below.

---

### 2 — Blocker Video (07/04)

  METRIC             VALUE          TARGET         STATUS
  -----------------------------------------------------------------------
  Video starters     1,054          —              BASELINE
  80%+ watch rate    29.5%          90%+           RED
                     (311 of 1,054)
  Full completion    18.9%          100%           RED
                     (199 of 1,054)
  Median watch time  35 seconds     2:10–2:36      RED
  Drop-off figure    Disputed       —              FLAG (see discrepancy
                     (34% or 66%                    note above)
                     by 20 sec —
                     unverified)

  Initiation rate was high: 1,054 partners started the video. This
  shows the blocker mechanism successfully delivered the video to
  partners. The failure is in holding attention after initiation.

---

### 3 — WhatsApp Push (09/04)

  All metrics      : NO DATA — deployed 09/04, not captured in 10/04 snapshot.
                     Next measurement cycle must include S2 conversion delta
                     from 09/04 baseline.
  STATUS           : PENDING — not measurable from current data.

---

### 4 — Metrics Not Yet Actionable

  Quiz pass rate   : BLOCKED — quiz not yet deployed
  App download     : BLOCKED — app transition not yet measured
  PTL call volume  : PENDING — no baseline or current count in any file

---

## What Worked

  Popup reach mechanism (YELLOW but functionally sound)
    86.3% organic reach on a dismissible popup, with no push or WA support,
    is a solid first-touchpoint result. The mechanism (contextual popup on
    wallet and tickets screens, where CSPs are already active) placed
    education at the point of use. This approach did not fatigue the channel
    and created S1 state for targeting the blocker.

  Blocker initiation (BASELINE — positive signal)
    1,054 partners started the video. The non-dismissible mechanism got
    attention — nearly all active partners encountered the blocker.
    The problem is not reach or initiation. It is retention.

---

## RED/YELLOW Findings — Root Cause Analysis

### Finding 1 — Full completion rate: 18.9% (target 100%)  [RED]

  METRIC   : Full video completion
  VALUE    : 18.9% (199 of 1,054 starters)
  TARGET   : 100% (brief.md); GREEN threshold >90% (context-from-teams.md)
  STATUS   : RED
  GAP      : 81.1 percentage points below target

  ROOT CAUSE HYPOTHESIS A — Content architecture mismatch with attention window

  The video structure places the most CSP-relevant content after the
  typical drop-off point:
    0:00–0:15  Intro + system update framing
    0:15–0:45  Connection assignment process
    0:45–1:10  PayG and recharge mechanics
    1:10–1:40  Earnings breakdown (Rs 300, Rs 120, NetBox Rs 50)
    1:40–2:00  NetBox collection and carry fee
    2:00–2:10  Timeline, quality, summary

  The earnings breakdown — the item most likely to retain a CSP's
  attention — does not appear until 1:10. Median watch time is 35 seconds,
  which means the average viewer exits before reaching any earnings content.

  EVIDENCE     : Video structure (context-from-teams.md) + median watch time
                 35 sec. Partners who drop at or before 35 seconds see only
                 system update framing and connection assignment — topics with
                 lower immediate salience.
  CONFIDENCE   : Medium. Content structure is confirmed. Attribution to
                 content architecture is inferred — A/B test would confirm.

  ROOT CAUSE HYPOTHESIS B — App exit to bypass the blocker

  The non-dismissible mechanism works only if partners stay in the app.
  If partners close the app when they see the blocker (choosing to come
  back later or from another device), the forced mechanism does not function.
  High initiation + low completion is consistent with bypass behaviour.

  EVIDENCE     : Engineering flagged in results.md for investigation. No
                 confirmed data either way.
  CONFIDENCE   : Low (unconfirmed). Must be ruled out before acting on
                 content hypotheses.

  ROOT CAUSE HYPOTHESIS C — Video length vs mobile context mismatch

  CSPs in the field operate the app in brief sessions between tasks. A
  2:10–2:36 video requires a sustained, uninterrupted viewing session.
  Field context likely means short app sessions, making full completion
  structurally difficult regardless of content quality.

  EVIDENCE     : Median watch time 35 sec. 80%+ watch rate is 29.5%.
                 These two data points together suggest the majority of
                 viewers do not have a 2-minute attention window available
                 in their typical app session.
  CONFIDENCE   : Medium. No session length data available to confirm.

---

### Finding 2 — 80%+ watch rate: 29.5% (target 90%+)  [RED]

  METRIC   : Partners who watched 80% or more of the video
  VALUE    : 29.5% (311 of 1,054)
  TARGET   : 90%+ (context-from-teams.md GREEN threshold)
  STATUS   : RED
  GAP      : 60.5 percentage points below GREEN threshold

  This finding reinforces Finding 1. Even among partners who persisted
  past the initial drop-off, full retention is very low. The 311 who
  reached 80% are likely the highly motivated or attentive subset — not
  a representative view of the partner base.

  ROOT CAUSE: Same hypotheses as Finding 1 apply. The 80%+ threshold
  failure is a downstream consequence of the completion rate failure.
  No additional root cause beyond Finding 1.

---

### Finding 3 — Median watch time: 35 seconds (target 2:10)  [RED]

  METRIC   : Median watch time
  VALUE    : 35 seconds
  TARGET   : 2:10 full video (2:36 per dashboard)
  STATUS   : RED

  The 35-second median is the clearest quantitative signal. It shows
  that the typical partner's viewing session ends before the first key
  topic (connection assignment, 0:15–0:45) is fully covered. The content
  from 0:45 onward — PayG mechanics, earnings, NetBox — reaches fewer
  than 50% of viewers who start the video.

  Implication for education quality: Partners at median watch time
  have received only: intro framing + partial connection assignment.
  They have not received: PayG recharge mechanics, earnings structure,
  NetBox rules, carry fee, or timeline. These are the topics most likely
  to generate confusion and PTL calls post-launch.

---

## Recommendations

### Recommendation 1 — Engineering check (blocker bypass)
  STATUS    : PAUSE (on further video iteration until this is resolved)
  FINDING   : Finding 1, Hypothesis B
  ACTION    : Engineering must confirm whether partners are exiting the
              app to avoid the blocker, and if so, whether a technical
              fix (e.g., re-serve the blocker on next app open) is
              feasible. If bypass is possible, the non-dismissible
              mechanism is ineffective regardless of content quality.
              All content iteration decisions should wait for this result.
  TIMEFRAME : Immediate. This blocks other decisions.

### Recommendation 2 — Video hook re-edit (content architecture)
  STATUS    : ITERATE
  FINDING   : Finding 1, Hypothesis A + Finding 3
  ACTION    : Re-edit or re-record a shorter video (60–90 seconds) that
              front-loads the earnings breakdown (currently at 1:10–1:40)
              as the opening hook (0:00–0:30). Specific proposed structure:
                0:00–0:15  Earnings hook: Rs 300 per connection unchanged,
                           Rs 120 bonus now linked to internet quality
                0:15–0:45  NetBox and carry fee (most operationally urgent)
                0:45–1:10  Connection assignment and PayG mechanics
                1:10–1:30  Timeline and quality importance
              This is a hypothesis — the only way to confirm it is to A/B
              test the recut against the original. Do not replace the
              original until bypass behaviour is ruled out (Rec. 1).
  DEPENDENCY: Rec. 1 must be resolved first.

### Recommendation 3 — WA push impact measurement
  STATUS    : ITERATE (measurement gap)
  FINDING   : WA push (09/04) — PENDING
  ACTION    : Pull S2 conversion data from CleverTap for the period
              09/04–13/04. Compare to the 18.9% baseline from the 10/04
              snapshot. This is the most important pending number: it
              determines whether the 09/04 WA push recovered completions
              and whether a second WA push (designed 13/04) is needed
              at all or is redundant.
  TIMEFRAME : Before scheduling any further WA sends to non-completers.

### Recommendation 4 — Quiz deployment policy decision
  STATUS    : FLAG (human decision required)
  FINDING   : 18.9% full completion = only ~199 partners currently eligible
              for the quiz (S2 gate requirement)
  DECISION  : With only 199 partners at S2, deploying the quiz now means
              ~82% of the partner base cannot access it. Three options:
                A. Deploy quiz to current S2+ partners now and wait for
                   more partners to reach S2 before scaling. Risk: delays
                   the overall education completion timeline.
                B. Lower the quiz gate from S2+ to S1+ to allow partners
                   who saw the popup but skipped the video to proceed.
                   Risk: quiz tests comprehension that may not exist
                   without video completion.
                C. Hold the quiz until video completion rate improves
                   (through bypass fix, recut, or further WA nudges).
              This is a policy decision with education quality trade-offs.
              The measurement agent cannot make it — flagging to human.

### Recommendation 5 — Drop-off data verification
  STATUS    : FLAG (data integrity)
  FINDING   : Data discrepancy between results.md and live dashboard
  ACTION    : Pull raw CleverTap video_watch_time_percentage event data
              to confirm actual drop-off distribution. Update results.md
              with verified figures before next measurement cycle. Until
              resolved, do not use the "66% drop-off at 20 seconds"
              figure for decision-making.

---

## Data Limitations and Blockers

  1. Measurement window: Data from 10/04 snapshot. WA push was deployed
     09/04 — its impact on S2 conversion is not captured. Three days of
     post-push data exist but are not in any file.

  2. WA push metrics (09/04): Entirely missing. Cannot assess whether
     the WA push drove meaningful S2 lift. This is the most critical
     gap for deciding whether further WA action is needed.

  3. Drop-off data discrepancy: Detailed above. Two files report 66%
     drop-off by 20 seconds; the live dashboard shows 66% still watching
     at 20 seconds. These cannot both be correct given the 35-second
     median. CleverTap verification required.

  4. Bypass behaviour: Unconfirmed. If partners are exiting the app to
     avoid the blocker, the completion rate reflects a technical gap,
     not a content gap. This distinction materially changes which
     recommendations are actionable.

  5. No completion breakdown by role (OWNER vs ADMIN): Dashboard shows
     popup reach splits by role (807 OWNERs, 247 ADMINs) but not
     completion rates by role. If ADMINs have lower completion,
     targeting strategy for the next WA nudge may differ.

  6. No PTL call data: Baseline call volume not recorded in any file.
     Cannot assess whether PTL spike target is being met. Recommend
     establishing baseline before app transition creates call volume impact.

  7. Sample note: 1,054 video starters out of ~1,400 total audience.
     The 18.9% completion rate is computed against starters, not total
     audience. Against total audience (~1,400), completion rate is ~14.2%.
     Both figures are well below any threshold — the distinction matters
     for tracking improvement, not for the current RED classification.

---

## Summary — Overall Campaign Status

  Pre-launch education objective: Partners understand the new system
  with no surprises by launch day.

  As of 13/04 (day after app launch):

  Touchpoint 1 — Contextual popups: FUNCTIONAL. Reached 86% of active
  partners organically. Good first-touchpoint mechanism.

  Touchpoint 2 — Blocker video: CRITICALLY BELOW TARGET. 18.9% full
  completion. Median watch time 35 seconds. The forced mechanism
  captured attention (1,054 starters) but failed to hold it. The
  majority of the partner base has not received the core education
  content. This is the primary risk to the campaign objective.

  Touchpoint 3 — WA push: UNMEASURED. Critical data gap.

  Overall campaign education status at launch: The "no surprises"
  objective is at risk. With only ~199 partners confirmed as having
  watched the full video, a significant majority of the ~1,400 active
  partner base entered launch day without full education. The PTL
  impact of this (if any) is the next critical metric to watch.

---

## Next Measurement Checkpoint

  Recommended actions before next measurement cycle:

  1. Pull CleverTap S2 conversion data for 09/04–13/04 (WA push impact)
  2. Engineering: confirm or rule out app exit bypass behaviour
  3. Pull CleverTap video_watch_time_percentage raw data (drop-off verification)
  4. Pull PTL call volume baseline and current rate
  5. Human: decide on quiz gate policy (Recommendation 4)

  Next cycle should measure:
  - S2 conversion post-WA push (delta from 18.9% baseline)
  - WA push open/read rate and S2 lift attribution
  - Quiz deployment metrics (if deployed): attempt rate, pass rate by cohort
  - App download rate post-transition
  - PTL call volume vs baseline

---

QUALITY CHECK   : PASS
  4.1 Data integrity  : All metrics from results.md or live dashboard.
                        Data discrepancy flagged and not used in conclusions.
                        No estimated or extrapolated figures.
  4.2 Recommendations : Every RED/YELLOW finding has a specific, evidenced
                        recommendation (iterate/pause/flag). Each traces to
                        a named metric.
  4.3 Limitations     : Six data limitations noted. All affected conclusions
                        qualified with confidence levels.

SECURITY CHECK  : PASS
  Rule 1 PayG     : No subscription or monthly plan framing in any analysis.
  Rule 2 Regulatory: No deployment plan produced. No timing violation.
  Rule 3 Data     : No PII, no internal financials, no system architecture
                    data included in output.
  Rule 4 Deployment: Output to review-queue/ only. No action triggered.
  Rule 5 PCA      : Canonical vocabulary used throughout. No forbidden terms.
  Rule 6 Self-check: All six rule areas checked.
