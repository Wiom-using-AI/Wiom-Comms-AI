# Context from Teams — project-csp-migration-apr26

## FILE PURPOSE
Inputs from product, engineering, CX, and campaign teams that affect
comms strategy for the CSP migration. This file captures the campaign
architecture, audience state model, key messages, PTL guide, and
operational context that the design agent needs beyond what is in brief.md.

## WHEN TO USE
Loaded by the orchestrator for every design task on this project.
Read after brief.md. Where this file conflicts with brief.md,
this file takes precedence (it reflects execution reality).

## HOW TO USE THIS FILE
- Read the Campaign Architecture section to understand the current
  execution plan (this supersedes the 13-message plan in brief.md)
- Read Audience States to know where each partner sits
- Read Key Messages before drafting any copy
- Read PTL Guide before designing any partner-facing content
- Read Post-Launch Triggers to understand what comes after launch

## LIVE METRICS
For current campaign metrics (popup reach, video completion, quiz
pass rates), WebFetch the live dashboard before any measurement or
design task:
  URL: https://shivakimothi-design.github.io/csp-comms-dashboard/
This dashboard is the single source of truth for volatile numbers.

## LAST UPDATED
2026-04-13 — populated from CSP Comms Dashboard (live).
Maintained by: human

---

## Campaign Architecture (supersedes brief.md Comms Plan)

The original brief planned 13 messages starting Mar 31 with ~Apr 7
launch. Execution shifted to a 5-day pre-launch education campaign
(05/04-09/04) with app launch ~12/04. The mechanism changed from
WhatsApp-first to in-app education with WA as cascade.

### Campaign window
05/04/26 to 12/04/26 (pre-launch education)
Post-launch: trigger-based, not calendar-based

### Audience
~1,400 partners (OWNERs + ADMINs). Technicians excluded.
Daily active audience: ~1,200-1,460.

### Campaign objectives
- By 12/04: Partners understand the new system with no surprises
- By 30/04: Full partner trust, no unexplained numbers or confusion calls
- Measurable targets: 100% blockers complete, >70% quiz pass,
  no Trust Line spike

### 5-Day Pre-Launch Timeline

  05/04 — Contextual popups (Wallet + Tickets)
    Mechanism  : Dismissible popups, organic discovery
    Status     : Deployed

  07/04 (night) — Blocker video (2:10 min)
    Mechanism  : Full-screen, non-dismissible, forced completion
    Status     : Deployed

  09/04 — WhatsApp push (non-completers only)
    Mechanism  : WA message redirecting to blocker video
    Status     : Deployed

  TBD — Recap + quiz (5 questions, 4/5 to pass)
    Mechanism  : For S2+ states only (completed blocker video)
    Status     : Not yet deployed (as of 13/04)

  TBD — App transition + hard lock
    Mechanism  : S0/S1 locked out. S2+ offered new app download.
    Status     : Not yet deployed (as of 13/04)

### App launch: ~12/04

---

## Audience States (Partner Segmentation)

Partners progress through states based on education completion.
These states drive targeting for all subsequent comms.

  S0 — No exposure
    Partner has not interacted with any education content.
    CleverTap event: app_opened_post_05apr (absence = S0)

  S1 — Saw contextual popup
    Partner saw wallet or tickets popup on Day 1.
    CleverTap event: contextual_popup_seen

  S2 — Completed blocker video
    Partner watched the full 2:10 blocker video.
    CleverTap event: blocker_video_completed

  S3 — Watched recap
    Partner watched the recap content on Day 4.
    CleverTap event: recap_watched

  S4 — Passed quiz (4/5 or higher)
    Partner completed quiz with passing score.
    CleverTap event: quiz_passed (score >= 4/5)

Design rule: Never send post-launch content to partners below S2.
Partners at S0/S1 need education first, not operational nudges.

---

## Key Messages (Canonical Framing)

These are the approved framings for each topic. All comms must
use these framings. Do not rephrase the core numbers.

### Earnings
Rs 300 per connection. Unchanged.
Rs 120 bonus now tied to internet quality (not amount change this month).
Framing: "amount same, what it is linked to has changed."

### NetBox
Rs 50 per collection.
15-day return window.
Rs 2/day carry fee after 15 days with no active connection.

### Connections
System-assigned. Mandatory app install.
No manual process. No fixed area.

### Timeline
12 April app launch.
No scoring impact until partner adjustment period ends.
Protection period active until explicitly closed.

### PayG
30-day ISP recharge required (not monthly plans).
Framing: recharge-based, never subscription or monthly plan.

---

## Video Script Structure (2:10)

  0:00-0:15  : Intro + system update framing
  0:15-0:45  : Connection assignment process
  0:45-1:10  : PayG and recharge mechanics
  1:10-1:40  : Earnings breakdown (Rs 300, Rs 120, NetBox Rs 50)
  1:40-2:00  : NetBox collection and carry fee rules
  2:00-2:10  : Timeline, quality importance, summary

Design note: 66% of viewers drop off by 20 seconds. The hook
(0:00-0:15) may need strengthening. Median watch time is 35 seconds.

---

## PTL (Partner Talk Line) Response Guide

### 8 core topics
1. Earnings
2. Timeline
3. NetBox
4. Work/System
5. Internet Quality
6. App
7. PayG
8. Other

### Response principle
"Poori jaankari app mein milegi. Is mahine sab purane tarike se."
(Full info in app. Everything old-way this month.)

### Restrictions (do NOT say)
- Do not explain SLA mechanics
- Do not give Mbps numbers
- Do not promise area stability
- Do not mention enforcement dates yet

---

## Post-Launch Triggers (Not Calendar-Based)

Post-launch comms fire on conditions, not dates.

  Days 3-5   : Telemetry pending → partner outreach
  Days 7-10  : First bonus cycle active → quality score check
  Day 14     : Scoring impact begins (protection period ends)
  Days 25-27 : Cycle closing, projected bonus preview
  Month end  : Full itemised bonus breakdown
  Ongoing    : Contextual tips on score changes

---

## Survey Plan (from 10/04)

  Design  : 50-60 PTL calls across 3 cohorts
  Cohorts : Quiz pass / Video only / Popup only
  Method  : 5 open-ended questions testing recall
  Goal    : Identify if education stuck or if quiz is non-negotiable

---

## Success Thresholds

  GREEN  : >90% video complete, >70% quiz pass, flat/declining PTL calls
  YELLOW : 70-90% video, 50-70% quiz, slight call increase
  RED    : <70% video, <50% quiz, >2x baseline PTL calls

---

## Constraints and Boundaries

  Duration    : 5 days pre-launch (05/04-09/04), app launch ~12/04
  Audience    : OWNERs and ADMINs only (~1,400-1,460 daily).
                Technicians excluded.
  Old app     : Static display only. No CSP-specific data post-lock.
  Tone        : Calm, neutral. "Zaroori update" (necessary update),
                not alarming.
  Messaging   : WA/SMS redirect only. Education in app/video.
  Blockers    : Only Day 2 video is forced. Other content dismissible.
  No field    : All comms must work without human mediation.
                No BDO teams, no field support.

---

*context-from-teams.md — L3-projects/project-csp-migration-apr26/*
*Updated: 2026-04-13*
