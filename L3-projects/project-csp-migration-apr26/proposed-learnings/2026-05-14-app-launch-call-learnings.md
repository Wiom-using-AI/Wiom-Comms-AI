# Proposed Learnings — CSP App Launch Call Analysis
## project-csp-migration-apr26

STATUS        : PROPOSED — awaiting human approval before any playbook edit
DATE          : 2026-05-14
SOURCE        : Inbound CSP support calls, approximately 07–12 May 2026
VOLUME        : ~60+ cases across Navigation Support, Bug, Migration, Blocker,
                Improvement, and Good-to-Have categories
PROPOSED BY   : Learning agent (auto-extracted from call log, confirmed by human)

---

## L1. Login failures are the hardest blocker to adoption

OTP not received, app not opening after install, and post-OTP login loops
are preventing a meaningful subset of CSPs from accessing the app at all.
These are pre-navigation failures — no comm about navigation helps someone
who cannot log in.

IMPLICATION FOR COMMS: This cohort cannot be reached via in-app comms.
Outreach must happen via WhatsApp or direct PTL call. A dedicated support
pathway comm for login-blocked CSPs should be considered — separate from
general navigation guidance.

IMPLICATION FOR PRODUCT: OTP delivery and post-OTP session stability need
investigation. Volume across multiple CSPs suggests a systemic issue, not
isolated edge cases.

---

## L2. Navigation confusion is the dominant post-login issue, not feature gaps

The most common complaint is not that features are absent — it is that CSPs
cannot find features that exist. Wallet, payout, recharge history, pickup
tickets, and customer details are present in the new app but are not locatable
using prior mental models from the old app.

IMPLICATION FOR COMMS: Copy that says "the new app has X" is insufficient.
What CSPs need is step-level navigation guidance: "Go to [section] → tap
[option] → you will see [feature]." General orientation messages are not
translating to task-level confidence.

---

## L3. Passive video is not producing working navigation knowledge

At least one case explicitly states the CSP watched the training tutorial
but still cannot navigate the app. This is consistent with the earlier
Measurement Cycle 1 finding (18.9% full video completion; 66% drop-off
by 20 seconds). Even among CSPs who engaged with video, task-level
navigation confidence is not transferring.

IMPLICATION FOR COMMS: Contextual guidance at the moment of use is more
effective than pre-emptive walkthroughs. In-app prompts, tooltips, or
task-specific WhatsApp messages triggered by specific navigation events
should be explored over additional general training videos.

IMPLICATION FOR STRATEGY: This challenges the current education-first model.
Navigation support needs to be available at the moment of confusion, not
scheduled in advance.

---

## L4. Payout visibility is the most-cited specific navigation gap

"Where is payout?" appears more than any other single question across
the call batches. Payout is also the area of highest financial anxiety —
when payout is not visible, CSPs assume it is missing rather than relocated,
which escalates call urgency and distrust.

IMPLICATION FOR COMMS: A targeted WhatsApp message with step-level payout
navigation instructions (section name, tap path, what to expect on screen)
should be prioritised above other navigation content. This single comm
could reduce a significant share of inbound call volume.

---

## L5. Historical data inaccessibility is creating distrust of migration

CSPs who have migrated report that old payout history and previous balance
records are not visible — only current balance shows. Whether this is a
product display issue or expected migration behaviour, the CSP perception
is that the migration caused data loss. This perception is eroding trust
in the migration itself.

IMPLICATION FOR COMMS: CSPs need a clear, factual message about historical
data: what is accessible, where to find it, and what is not yet available
(and when it will be). Silence on this point will continue to generate
anxiety and inbound calls.

IMPLICATION FOR PRODUCT: If historical data is present but not surfaced
in the UI, this is a priority display fix. If it is genuinely not migrated,
this needs to be communicated proactively, not reactively.

---

## L6. Comms did not set expectations about new app capabilities at launch

The "Improvement" call category reveals that CSPs are asking for features
they expected to find: pre-expiry recharge alerts, expiry tracking,
detailed active connection breakdowns, bonus measurement clarity. These
are either features from the old app or assumed defaults. The launch
comms did not define what the new app does and does not do at launch.

IMPLICATION FOR COMMS: A "what's available now" message — framed as
factual capability mapping, not promotional — should accompany or follow
app launch. This sets a clear baseline and prevents expectation gaps
from generating inbound.

---

## L7. Call volume and breadth signal a structural comms gap at app launch

The range and volume of questions — covering login, navigation, migration,
data access, and feature expectations — across a short window (approximately
5 days) indicates that CSPs received the new app without sufficient context
for what changed and how to use it. The call pattern is consistent with
an onboarding gap rather than isolated technical issues.

IMPLICATION FOR STRATEGY: Future app launches (or major version changes)
should be preceded by a structured comms sequence that covers: what is
changing, what stays the same, where key features have moved, and how to
get help. The current campaign's education model (video → quiz) was
appropriate for the migration concept but did not extend to task-level
app navigation.

---

## PROPOSED ACTIONS (for human decision)

1. Priority comm: WhatsApp message with step-level payout navigation guide.
   Audience: all active OWNERs on the new app. Immediate.

2. Login-blocked cohort: Identify CSPs who have not logged into the new app
   post-migration. Outreach via WhatsApp with PTL support pathway. Not
   addressable via in-app channel.

3. Historical data message: Factual status update on what data is accessible
   in the new app and what is not yet available. Reduces distrust.

4. Feature expectation baseline: Single-message "what's in the new app now"
   comms to close the expectation gap identified in the Improvement calls.

5. Product flag: OTP delivery failures and post-login session loops should
   be investigated as systemic issues. Volume suggests infrastructure
   problem, not isolated cases.

---

SECURITY CHECK: PASS — all six rule areas checked, no violations.
This is a proposed learning document. No comm copy is included.
No deployment action is triggered. Human approval required before
any playbook edit or comm design proceeds from this document.
