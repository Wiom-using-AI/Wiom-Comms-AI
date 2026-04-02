---
FILE PURPOSE: Partner Communications Architecture v1.0 — Enforcement Governance
HOW TO USE: This file defines how correct language is versioned, owned, audited, and enforced. Load every session — even non-enforcement tasks must not accidentally trigger enforcement consequences. For what may and may not be said, see pca-content-governance.md. For when and how often to communicate, see comms-principles.md.
SCOPE: All CSP-facing communication governance — deployment, drift detection, field controls, escalation, versioning
LAST UPDATED: March 2026
TAGS: pca, enforcement-governance, message-blocks, silence-policy, drift-audit, field-improvisation, escalation, mgo, versioning, deployment-governance
---

# PCA ENFORCEMENT GOVERNANCE
## Partner Communications Architecture v1.0 — Part B
### How Correct Language Is Versioned, Owned, Audited, and Enforced

---

## What This File Governs

Part B of PCA defines the operational machinery that makes Part A (pca-content-governance.md) enforceable at scale. Content rules without enforcement governance drift. This file answers: who owns language decisions, how are approved blocks deployed, what happens when drift occurs, and how do field teams stay compliant.

**Part B prevents:** interpretive fragmentation across teams, policy-by-WhatsApp, untracked language drift, audit gaps, over-communication.

---

## §1. Message Block System

Every canonical translation from pca-content-governance.md §5 must be registered as a versioned, immutable Message Block before it can be deployed in any channel.

### §1.1 Block ID Format

`BLOCK-[OS]-[STATE]-[VERSION]`

Examples:
- `BLOCK-SLA-AT-RISK-01`
- `BLOCK-ENFORCE-FPV-01`
- `BLOCK-COMP-BONUS-PAUSE-01`
- `BLOCK-EXIT-VOLUNTARY-01`

### §1.2 Mandatory Block Metadata

Every Message Block must contain:

| Field | Definition |
|---|---|
| BLOCK ID | Unique, immutable identifier per format above |
| STRUCTURAL STATE ID | Exact state from OS state machine |
| GOVERNANCE LAYER | Integrity / Performance / Economic / Eligibility / Exit |
| OS SOURCE | Quality / Demand & Allocation / Compensation / Enforcement / Exit / Capability / Progression / Voice |
| SEVERITY LEVEL | Informational / Attention / Action Required / Integrity / Termination |
| CHANNEL ELIGIBILITY | Dashboard / Push / SMS / WhatsApp / Call Script / Field Script |
| PCA VERSION | Version of PCA governing this block |
| EFFECTIVE DATE | Date from which this block is active |
| SUPERSEDES | Block ID this replaces, or 'None' |

> *A block without complete metadata is not a block. It has no authority.*

### §1.3 What Every Block Must Contain

**English Canonical Text** (always required):
- STATE DESCRIPTION: Factual state. No adjectives. No emotion.
- CONSEQUENCE: System response. Or N/A.
- NEXT ACTION: CSP action required / available. Or N/A.

**Hindi Canonical Text** (mandatory for Hindi-primary channels):
- Same three components in Hindi
- Must comply with pca-content-governance.md §3.3 (Hindi Vocabulary Lock) and §4.1 (Hindi Tone Discipline)
- If Hindi canonical text does not exist, the block may not be deployed in Hindi-primary channels

**Clarification Layer** (optional, versioned):
- May: explain evaluation window, link to enablement, restate a published rule, provide procedural steps
- May NOT: interpret cause, suggest negotiability, imply future economic change, add emotional context, reframe consequences
- All clarification text is part of the block — versioned, immutable, MGO-approved — not free text

**Prohibited Additions** (block-specific):
Each block must explicitly list what may NOT be added for that specific state. Every block must address whether each of these is prohibited or N/A:
- Motivational framing
- Earning reference
- Apology language
- Comparison language
- Retention language
- Cause interpretation
- Negotiation opening
- Urgency beyond severity level

**Economic Validation** (if block references economics):
- RATE CARD REFERENCE: exact rate card version
- FORWARD EFFECTIVE ONLY: confirmed / N/A
- NO PROJECTION CONFIRMED: confirmed / N/A
- Must also pass pca-content-governance.md §11 (Economic Messaging Rules)

**Audit Signature** (mandatory):
- APPROVED BY: Name + role of MGO or delegate
- APPROVAL DATE: Date of approval
- REVIEW CYCLE: Quarterly / Upon OS change / Upon governance update / Upon vocabulary update
- AUDIT LOG REF: Registry reference

> *A block without an audit signature is a draft. It has no authority. It may not be deployed.*

### §1.4 Block Immutability Rule

Once published, a block is locked. Any change — to metadata, canonical text, clarification, or prohibitions — requires:

1. New BLOCK ID (version increment: BLOCK-SLA-AT-RISK-01 → BLOCK-SLA-AT-RISK-02)
2. New effective date (future only)
3. SUPERSEDES field references the old block
4. Old block archived — not deleted
5. MGO approval on new block
6. All channels updated simultaneously on effective date

> *If someone needs to "just tweak the wording" — that is a new block. No exceptions.*

---

## §2. Silence Policy

Silence is a valid system signal. Over-communication is a contamination vector.

> *If a state is visible on the dashboard, it does not require a push notification unless the state demands CSP action.*

### §2.1 What Never Generates a Communication

- States that have not changed since the last notification
- Motivational or check-in messages of any kind
- "Soft reminders" for states already visible on dashboard
- Any message without a registered Message Block
- Any message that would repeat within the same evaluation window for the same unchanged state

### §2.2 Silence Enforcement

If a design task arrives for a communication that has no state-change basis, the correct response is:
1. Identify which principle the communication violates (typically P1 or P2)
2. Do not design the communication
3. Log to GAPS.md: task received, principle violated, action taken
4. Return to human reviewer: "This communication has no structural source. It may not be designed."

---

## §3. Anti-Contamination Tests

All eight tests from pca-content-governance.md §8 apply to every output. This section adds channel-specific deployment tests.

### §3.1 Pre-Deployment Checklist

Before any comm moves from review-queue to deployment:

**Content compliance:**
- [ ] All 8 constitutional principles satisfied
- [ ] All 8 anti-contamination tests passed
- [ ] Economic validation checklist passed (if applicable)
- [ ] Vocabulary canon: no forbidden terms present
- [ ] Hindi canonical text exists (if deploying to Hindi-primary CSPs)

**Block compliance:**
- [ ] Message Block ID declared in output
- [ ] Block version is current (not superseded)
- [ ] Channel eligibility confirmed for this block

**Deployment compliance:**
- [ ] Frequency caps checked (comms-principles.md §3.1)
- [ ] Cooling period confirmed for this state type
- [ ] DLT registration confirmed (for SMS — regulatory-compliance.md)
- [ ] WhatsApp opt-in confirmed (for WhatsApp)
- [ ] SECURITY CHECK: PASS confirmed (SECURITY-RULES.md)

---

## §4. OS-Specific Guardrails Summary

For full guardrails per OS, see pca-content-governance.md §9. This section provides the enforcement-relevant boundaries for each OS — what will trigger a PCA violation review.

| OS | High-Risk Contamination Vectors | Immediate Flag If |
|---|---|---|
| Quality OS | Comparative ranking, moral judgment on SLA state | Any mention of "better than other CSPs" or "you're failing" |
| Compensation OS | Income projection, loss framing, comparison | Any mention of earning potential or "you lost" |
| Enforcement OS | Moral language, threats, negotiation openings | Any word: "warning," "caught," "punishment," "discuss" |
| Exit OS | Retention attempts, emotional farewell | Any phrase suggesting the CSP reconsider or return |
| Demand & Allocation OS | Volume promises, area comparisons | Any forward-looking allocation promise |
| Onboarding OS | Legacy ISP framing, income promises to new CSPs | Any mention of "customers," "leads," or earning projections |

---

## §5. Escalation Protocol — When PCA Is Violated

### §5.1 Violation Severity Tiers

| Tier | What Happened | Immediate Response |
|---|---|---|
| Tier 1 — Template Drift | Approved template contains a vocabulary violation or tone breach — discovered at audit | Correct template. Version increment. Re-approve. Log in CHANGELOG.md. |
| Tier 2 — Field Improvisation | Field team / call centre sent a message not backed by a registered block | Recall or correct via next interaction. Root cause analysis. Retrain. Log in GAPS.md. |
| Tier 3 — Channel Breach | Message sent via ineligible channel (e.g. free-text WhatsApp for state description) | Escalate to Comms Head. Channel authority for breaching surface suspended until remediation complete. |
| Tier 4 — Economic Contamination | CSP-facing message created income expectation not in rate card | Immediate escalation to MGO. Correction in all channels. Root cause: template gap / field improvisation / review miss? |
| Tier 5 — Systemic Drift | Drift Score ≥5% at quarterly audit | Freeze new messaging rollouts. Mandatory PCA retraining. Root cause report to Founder. |

### §5.2 Breach Response Protocol

1. **Immediate correction** in all channels where violation occurred
2. **Root cause identification:** Template gap / Field improvisation / Review process miss?
3. **System fix:** Template update, permission restriction, or process tightening
4. **Log:** GAPS.md entry with: date, channel, violation type, correction taken
5. **No blame. No punishment.** PCA breach is a system failure. Fix the system.

> *Audit Invariant: PCA breach is a system failure. Fix the system. Do not punish the person.*

---

## §6. Field Team Improvisation Controls

Field improvisation is the primary real-world source of PCA drift. These rules are non-negotiable.

| Scenario | Rule |
|---|---|
| Free-text WhatsApp | Prohibited for states, economics, enforcement. Allowed only for scheduling logistics. |
| Verbal promises | Prohibited. All commitments are system commitments. Reference published states only. |
| Explaining consequences | Must use exact Message Block language. No improvisation. |
| CSP economic complaints | May NOT explain or reinterpret. Redirect: "Rate card published. Wallet shows balance." |
| CSP requests for more connections | May NOT promise. State: "Routing is system-controlled. Exposure responds to SLA." |
| CSP exit conversation | May NOT retain. State: "Exit is valid. Process is in the app." No further conversation. |
| Verbal enforcement | Must read from approved Message Block. No improvisation. |
| Call centre scripts | Must include Block ID reference. Clarification allowed. Reinterpretation not. |

> *Field Rule: If you cannot point to a Message Block or published system state for what you just said, you should not have said it.*

---

## §7. Meaning Governance Owner (MGO)

PCA establishes a single authority role: the Meaning Governance Owner. One person owns: Message Block approval, vocabulary enforcement, cross-OS coherence, drift audits, PCA versioning. The MGO has veto power over all CSP-facing language. No team may override.

**Until MGO is formally appointed: Founder holds this role.**

### §7.1 MGO Approval Gate

The following require MGO approval before deployment:

| Communication Type | Requires MGO Approval Before |
|---|---|
| New notification template | Deployment |
| Dashboard display text | Deployment |
| Push notification template | Deployment |
| Call centre script | Training rollout |
| WhatsApp / SMS template | Activation |
| Onboarding material | Onboarding session |
| Enforcement communication | Delivery to CSP |
| System update notice | Publication |
| Economic messaging (any form) | Any channel |
| New or modified Message Block | Registration in block library |

### §7.2 What Comms Head May Do Without MGO Approval

- Create new Message Blocks for existing structural states
- Approve channel eligibility for non-economic blocks
- Schedule deployment timing
- Conduct drift audits and enforce remediation
- Reject any CSP-facing message that fails PCA tests
- Update clarification layers within existing blocks

### §7.3 What Requires MGO / Founder Approval

- Any new or modified economic messaging
- Any change to vocabulary canon (§3)
- Any new PCA principle or modification to existing eight
- Any exception to silence policy or frequency caps
- Any structural change to the PCA framework itself

> *Founder Approval SLA: 48-hour turnaround on economic messaging approval. If not responded within 48 hours, the block is held — not auto-approved. No exception.*

---

## §8. Quarterly Drift Audit

Every quarter: sample 50 random CSP interactions across all channels. Audit each against PCA tests (§8 of pca-content-governance.md) + Message Block compliance. Calculate Drift Score.

**Drift Score = % of sampled interactions failing any PCA test.**

| Drift Score | Action |
|---|---|
| < 5% | Normal. Log findings. Address specific gaps. |
| ≥ 5% | Freeze new messaging rollouts. Mandatory PCA retraining. Root cause report to leadership. |
| ≥ 15% | All CSP communication paused except system-automated. Full audit. MGO-led remediation. |

### §8.1 Drift Indicators — Early Warning

These signals indicate PCA is failing before the quarterly audit:

| Indicator | What It Signals |
|---|---|
| CSPs referencing "earning potential" | Economic signaling has leaked |
| CSPs believing they own customers | Vocabulary contamination |
| CSPs negotiating routing | Allocation framed as negotiable |
| Field teams saying "management decided" | Impersonal authority violated |
| Emotional or apology language in enforcement | Tone envelope breached |
| CSPs in different cities receiving different wording for same state | Principle 8 violated |

---

## §9. Deployment Governance

### §9.1 Structural Change Flow

Whenever structure changes — new feature, policy update, rate card revision, SLA threshold change, enforcement rule change — this sequence must complete before any CSP-facing communication deploys:

| Step | Action | Gate |
|---|---|---|
| 1. Structural Freeze | Structure must be locked. State machine finalised. | Structure locked before Step 2. |
| 2. State Impact Map | What structural state is created or modified? Is CSP action required? Is a consequence attached? | Impact map documented before Step 3. |
| 3. Block Creation | New Block ID, canonical translation, Hindi canonical, severity, channel eligibility, prohibited additions. Per MBTF. | Block passes all 8 PCA tests before Step 4. |
| 4. Channel Eligibility | Which channels? What frequency? What cooling period? | Eligibility defined before Step 5. |
| 5. Scheduled Release | Advance notice period per §12 of pca-content-governance.md. All channels updated simultaneously. | Notice period satisfied before release. |
| 6. Drift Monitoring | Post-deployment: verify CSP-facing language matches blocks across all channels. Sample within first evaluation window. | Any divergence triggers immediate correction. |

> *Flow Invariant: No step may be skipped. No step may be reordered. If structure is not frozen, communication does not begin.*

### §9.2 Surface Ownership

| Surface | Structural Truth | Translation + Approval | Deployment |
|---|---|---|---|
| Partner App copy | Product defines state machine | Comms Head translates per PCA. Approves all state-descriptive text. | Product deploys. Comms Head sign-off required. |
| Dashboard states | OS generates automatically | Pre-approved via Message Blocks | System-automated |
| Push notifications | OS state change triggers eligibility | Comms Head approves templates | System-automated per eligibility matrix |
| WhatsApp / SMS | Process-related or action-required states only | Comms Head approves all templates. No free-text. | Centrally scheduled. Field may not send independently. |
| Call scripts | OS state or CSP-initiated query | Comms Head creates from blocks. Must reference Block ID. | Support team reads. Comms Head audits. |
| Field / BDO scripts | Onboarding or reactive support only | Comms Head creates framework. Must reference blocks. No local customisation. | Ops trains. Comms Head audits. |
| Enforcement communication | Enforcement OS determines action | Comms Head approves. MGO approves any new enforcement block. | System-initiated. Call only for suspension / termination. |
| Economic communication | Compensation OS / Rate Card | MGO approves all economic messaging. Comms Head drafts from blocks. | Per eligibility matrix. No proactive economic messaging. |

### §9.3 Partner-Customer Communication Boundary

Two communication domains. They must not bleed into each other.

| Dimension | Partner Side (CSP-facing) | Customer Side (User-facing) |
|---|---|---|
| Governance weight | Hard. PCA applies in full. | Light. Boundary constraints only. |
| Tone | Neutral-Professional. No warmth. No persuasion. | Brand tone. Aspirational permitted. |
| Vocabulary | Canonical. PCA §3 vocabulary canon. | Brand vocabulary. No PCA lock. |
| Economic messaging | Deterministic. Rate card only. MGO approval. | May communicate value proposition. No false claims. |
| Improvisation | Zero. Block-only. | Creative iteration permitted within brand guidelines. |
| A/B testing | Not permitted on state descriptions. | Permitted on creative, format, channel. |

**Customer-side boundary constraints (what prevents structural contradiction):**
- No structural misrepresentation — Marketing may not claim capabilities the system doesn't have
- No economic exaggeration — no promise beyond published rate card or service terms
- No promise beyond system capability — no "guaranteed uptime" or "always-on" claims SLA cannot support
- No partner-side language in customer messaging — "CSP," "connection base," "routing exposure" never appear in user-facing copy
- No customer-side language in partner messaging — "unlimited internet," "best plan," "affordable" never appear in CSP-facing copy

> *Boundary Rule: Two domains. Two vocabularies. Two governance weights. Zero bleed.*

---

## §10. Crisis Override Protocol

In exceptional systemic events — mass outage, payment system failure, regulatory shock, large-scale routing collapse — normal PCA cadence may be insufficient. Crisis communication follows these rules:

| Dimension | Crisis Rule |
|---|---|
| Authority | Impersonal. System as subject. No "we" or "management." |
| Content | Facts only. What happened. What is affected. When next update. |
| Tone | Severity increases, word count decreases. No narrative expansion. |
| Apology | Forbidden. State facts. Apology implies negotiability. |
| Blame | Forbidden. No attribution to CSP, vendor, or Wiom personnel. |
| Frequency | Timed updates only (e.g. every 2 hours). No reactive bursts. |
| Channel | Dashboard + single push per update. No WhatsApp threads. |
| Economic | If economics affected: state impact factually. No reassurance framing. |

> *Crisis Rule: In crisis, the instinct is to over-communicate and over-reassure. Both are violations. State facts. Provide timing. Stop.*

---

## §11. PCA Governance and Versioning

PCA changes require:
- Version increment
- Effective date
- Cross-OS audit of affected Message Blocks
- Vocabulary canon update if terms change
- No silent edits
- No local overrides

When system rules change:
1. Structural change finalised
2. New Message Block created
3. Block version incremented
4. Effective date published
5. Old blocks archived — not deleted

---

## §12. Canonical Lock

**Part B (this file) defines how language is versioned, owned, audited, and enforced.**

*Structure freezes before language begins.*
*Messaging does not escalate. Structure escalates.*
*A block without complete metadata is not a block.*
*A block without an audit signature is a draft with no authority.*
*If someone needs to "just tweak the wording" — that is a new block.*

**PCA v1.0 Enforcement Governance is locked.**

---

*pca-enforcement-governance.md — L1 Global Knowledge — v1.0 — Loaded every session*
*Maintained by: Comms / Legal | Changes require MGO approval*
*Do not modify without updating CHANGELOG.md and checking cross-references in MANIFEST.md*
