# Comms Brief — adhoc — 2026-04-13

MODE        : Mode 2 — Standalone. No project history available.
REQUESTED_BY: not provided
OS_TRIGGER  : Compensation (no L2 playbook available — L1 PCA principles only)
TASK_TYPE   : design
TASK_SUBTYPE: single

---

## Message

**Header (WhatsApp):**
Payout Update — TDS

**Body:**

{{1}},

सरकारी टैक्स नियमों के अनुसार, 1 मई 2026 से सभी CSP payouts पर 5% TDS (Tax Deducted at Source) काटा जाएगा।

इसका मतलब:
- आपके हर payout से 5% TDS सिस्टम द्वारा अपने-आप काटा जाएगा
- बेस payout रेट कार्ड के अनुसार वही रहेगा — रेट कार्ड में कोई बदलाव नहीं है
- TDS कटौती की details आपके wallet/payout statement में दिखेगी

आपको कोई action लेने की ज़रूरत नहीं है। PAN details पहले से सिस्टम में हैं।

यह कटौती टैक्स नियमों के तहत सभी CSPs पर लागू है।

**Footer:**
Details: wallet/payout statement

---

Message classification : Service (tax compliance — regulatory requirement, not promotional)
Character count        : ~430 characters (body) — within WhatsApp Utility 1,024 limit

---

## Channel

WhatsApp Utility template. This is a system update about a regulatory/tax change affecting payouts. WhatsApp is appropriate because:
- CSP awareness is required before the change takes effect
- The change affects every payout, making it action-relevant even though no CSP action is required
- Per §12 System Update Communication Protocol, compensation-affecting updates warrant Dashboard + Push + Notice

Note: Dashboard display of TDS as a line item in wallet/payout statement should also be active from 1 May. This WhatsApp message serves as advance notice.

---

## Audience

All active CSPs across all geographies. Hindi-primary language register.
No segment filtering — TDS applies universally per tax regulations.

---

## Recipient analysis

Message type: Type B — Operational (regulatory/financial process change, not an OS state machine event)

**Questions that block action:**
1. What is TDS? → Answered in body: "TDS (Tax Deducted at Source)" with full form
2. How much will be deducted? → Answered in body: "5%"
3. When does it start? → Answered in body: "1 मई 2026 से"
4. Will my rate card change? → Answered in body: "बेस payout रेट कार्ड के अनुसार वही रहेगा — रेट कार्ड में कोई बदलाव नहीं है"
5. Where will I see the deduction? → Answered in body: "wallet/payout statement में दिखेगी"
6. Do I need to do anything? → Answered in body: "आपको कोई action लेने की ज़रूरत नहीं है"

**Hesitations that block action:**
1. Income reduction concern ("My payout is being cut") → Addressed by clarifying this is a tax regulation, not a rate card change. The base payout per rate card is explicitly stated as unchanged.
2. Targeting concern ("Why me?") → Addressed by normalisation line: "सभी CSPs पर लागू है"
3. Confusion about who is taking money ("Is Wiom taking more?") → Addressed by framing: "सरकारी टैक्स नियमों के अनुसार" — government tax regulation as the authority, not Wiom's decision.

**Operational details for action:**
- TDS rate: 5% — source: human-confirmed
- Applied to: all payouts — source: human-confirmed
- Effective date: 1 May 2026 — source: human-confirmed
- Visibility: wallet/payout statement — source: human-confirmed
- CSP action required: none — source: human-confirmed
- PAN status: already on file — source: human-confirmed

---

## Information architecture

Flow: Context → Relevance → How → Normalisation
(No "What to do" action steps because no CSP action is required — replaced with explicit "no action needed" confirmation)

Mapping:
- Context = line 1 ("सरकारी टैक्स नियमों के अनुसार, 1 मई 2026 से...")
- Relevance/How = bullet list (what gets deducted, rate card unchanged, where visible)
- No-action confirmation = "आपको कोई action लेने की ज़रूरत नहीं है"
- Normalisation = closing line ("सभी CSPs पर लागू है")

---

## Objective

CSP reads the message and understands that from 1 May 2026, 5% TDS will be deducted from their payouts as a tax compliance measure, with no action required from them.

---

## How this connects to the project

One-off regulatory compliance communication. Not tied to a project. Serves the goal of advance notice before a financial process change, per PCA §12 System Update Communication Protocol (advance notice required for compensation-affecting changes).

---

## Patterns applied

L1 PCA principles only (no L2 compensation playbook available):
- §12 System Update Protocol: what changed, effective date, what does NOT change, where to see details
- §9.3 Compensation OS guardrails: rate card amounts stated factually, no framing as good/bad/fair
- §11 Economic Messaging Rules: no income framing, no loss framing, no upside narrative
- Principle 5 (Impersonal Authority): regulation as subject, not Wiom decision
- Principle 8 (No Alternate Interpretations): single canonical framing for all CSPs

---

## Mistakes avoided

- Loss framing (§11 Prohibition 4): checked — message does not say "your payout will reduce" or frame the deduction as a loss. States the factual deduction and confirms rate card is unchanged.
- Income framing (§11 Prohibition 1): checked — no reference to earning, income, or salary.
- Apology language (§3.1 vocabulary ban): checked — no "sorry" or "apologies" for the deduction.
- Warmth beyond dignity (§4 tone): checked — no "we understand this may concern you" or similar softening.
- Economic signaling (Principle 3): checked — no expectation beyond published rate card.
- Human as decision-maker (Principle 5): checked — "सरकारी टैक्स नियमों" (government tax regulations) is the authority, not "Wiom has decided."

---

## PCA compliance

Canonical vocabulary used (PCA §3)        : YES — no forbidden terms
Tone envelope respected (PCA §4)          : YES — Neutral-Professional throughout
Registered Message Blocks used (PCA §6)   : N/A — no registered block exists for TDS; this is a new communication type
Anti-contamination tests passed (PCA §8)  : ALL 8 PASS
  1. Structural source: tax regulatory compliance requirement ✓
  2. Persuasion: none — purely informational ✓
  3. Economic signal: rate card reference only, no expectations created ✓
  4. Role integrity: CSP informed as service provider ✓
  5. Impersonal authority: government regulation as subject ✓
  6. Calm: factual, would not cause anxiety at 10pm ✓
  7. Dignity: no patronising, no blame, no grading ✓
  8. Vocabulary: no forbidden terms ✓

---

## Fatigue check

Was comms-log checked? NO — Mode 2 standalone, no project comms-log available.
Last similar message to this audience: none found (first TDS communication).
Fatigue risk: LOW — first message on this topic, regulatory in nature, not a repeat nudge.

---

## Measurement plan

Metric     : WhatsApp delivery rate + read rate
Target     : >90% delivery, >70% read rate (awareness-only message, no click CTA)
Timeframe  : 7 days post-send
Data source: WhatsApp Business API delivery/read receipts via Gupshup dashboard

---

## Tone notes

Hindi-primary, Neutral-Professional register. TDS is a familiar concept for most Indian business operators, so the message uses the term directly with full form provided once. No over-explanation. No emotional cushioning around the deduction. The "rate card unchanged" line is factual reassurance, not emotional — it answers the most likely operational question without softening.

---

## Pre-deployment checklist

- [ ] DND scrubbing required before send: NO — classified as Service (tax/regulatory compliance)
- [ ] Send time: within 09:00-21:00 IST recommended — no restriction for Service classification
- [ ] Opt-out mechanism: N/A for Service classification
- [ ] Audience list verified: confirm all active CSPs before deploying
- [ ] WhatsApp template registered: template must be submitted to Meta for Utility approval before deployment
- [ ] Dashboard/wallet: confirm TDS line item will be visible in wallet/payout statement from 1 May

---

QUALITY CHECK  : PASS — all items checked, no violations
SECURITY CHECK : PASS — all six rule areas checked, no violations
