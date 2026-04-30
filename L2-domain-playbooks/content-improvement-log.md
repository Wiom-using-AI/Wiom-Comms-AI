# Content Improvement Log

## FILE PURPOSE
Captures fundamental content principles that emerge from real comms
work — not just specific edits, but the *underlying rules* that
should be applied to every future comm.

The design agent (when authored) must read this file before any
copy-writing task. Karishni (or any human author) reads it before
reviewing/approving comms in review-queue/.

## RULES
- Append-only. Never edit prior entries — they are the audit trail
  of how the comms system learned.
- Each entry must include: the principle (general rule), the trigger
  (what session/feedback surfaced it), and an example pair (before/after
  or do/don't).
- Entries that turn out to be wrong over time are *retired* by adding
  a new entry that supersedes them, not by deleting.

## LAST UPDATED
2026-04-30 — initial version. 11 principles captured from the
2026-04-28 / 2026-04-29 sessions on the M8 PNM device + bonus
eligibility comm (CSP migration project). All principles surfaced
during real iterative feedback from Shiva (and Satyam Darmora via
Shiva) on the video script and accompanying calling pitch.

Maintained by: design agent proposes (once authored), human approves
and edits.

---

## Principles

### P1 — Lead with the partner's own word, not the team's word
**Source**: 2026-04-28 M8 video iteration (Shiva: "Partners call it bonus.")

Partners think in their language, not the system's language. Copy
must enter the partner's mental model first, then explain the
mechanism. If the team says "rating construct" but the partner says
"bonus," the headline is bonus.

| Don't | Do |
|---|---|
| "Bonus Eligibility — based on Internet Quality" | "आपका Bonus और PNM Device" |
| "Rating governs payouts" | "Bonus आपकी quality पर मिलता है" |

### P2 — No excited tone for operational state-change comms
**Source**: 2026-04-28 M8 video v1 → v2 rewrite (Shiva: "We cannot sound excited. Keep it very simple.")

System-change comms are not marketing. No rhetorical hooks ("क्या आप
जानते हैं..."), no slogans, no "तो याद रखें" recap pedagogy. Factual
statements, factual instructions. The partner's attention is borrowed,
not earned with energy.

| Don't | Do |
|---|---|
| "क्या आप जानते हैं कि आपका bonus कौन decide करता है?" | "हर recharge पर bonus आपकी internet quality पर निर्भर है।" |

### P3 — Cause-effect chain reads cleaner than conditional warning
**Source**: 2026-04-28 M8 video v3 (Shiva: "Sounds confusing — say if device is not on, no data, hence impacts bonus.")

State the chain of consequence rather than a conditional warning. The
chain feels factual; the warning feels punitive.

| Don't | Do |
|---|---|
| "Device बंद होगा तो eligibility paused हो जाएगी" | "PNM ON हो तभी data capture होता है। बंद रहेगा तो data नहीं — bonus पर असर पड़ेगा।" |

### P4 — Specify the install agent / origin
**Source**: 2026-04-28 M8 video v4 (Shiva: "We have to incorporate that this device is installed by Wiom.")

When referencing a device or system in the partner's environment,
name who put it there. Closes the partner's "but who is doing this?"
gap. (Caveat: if the agent is the brand monitoring the partner, see P11.)

| Don't | Do |
|---|---|
| "PNM device आपके office में लगा है" | "Wiom आपके office में PNM device install करता है" |

### P5 — Use temporal qualifiers in conditionals to ground them in the partner's reality
**Source**: 2026-04-28 M8 video v4 (Shiva: "agar aapke office mein PNM device install ho chuki hai...")

Bare conditionals ("अगर PNM installed है") read as abstract. Adding a
temporal qualifier ("पहले से installed है", "अब तक installed नहीं है")
makes the condition feel like the partner's actual situation.

| Don't | Do |
|---|---|
| "अगर PNM device installed है" | "अगर आपके office में PNM device install हो चुकी है" |

### P6 — Headings must not crowd their visual
**Source**: 2026-04-28 M8 video v5 (Shiva: "Heading of the second screenshot is looking a bit odd.")

A short heading sets up the message; a heavy heading competes with
the visual elements below it. Drop optional words ("Device", "आपका",
articles) when the visual already conveys them.

| Don't | Do |
|---|---|
| "PNM Device और आपका Bonus" | "PNM और Bonus" |

### P7 — Long digit strings (5+ digits) stay on screen, never in VO
**Source**: 2026-04-28 M8 video v5 (Shiva: "Don't say the number — it is on the slide.")

Phone numbers, OTPs, account numbers, codes, etc., should be readable
from the slide in large type (≥34px) and referenced in VO generically
("PTL number पर call करें"). Reading 10+ digits aloud wastes 5–10 sec
and partners cannot dictate from voice — they need to read to dial.

Also documented in the video-creation-guidelines skill as section 2.1a.

| Don't | Do |
|---|---|
| "PTL को call करें — सात-आठ-तीन-छह-आठ, एक-एक-एक-एक-एक" | "PTL number पर call करें" (number visible on slide) |

### P8 — Sequence: mechanism → consequence → action
**Source**: 2026-04-29 M8 video v9 (Shiva: "Add one more point post slide 3 which is that if PNM device is not working it will directly impact the bonus.")

When introducing a system change, place the consequence-of-breakage
between the explanation of how the system works and the actions the
partner must take. Mechanism alone is forgettable; mechanism +
consequence + action lands as a coherent unit.

Order: How does it work? → What happens if it breaks? → What do you do?

### P9 — Communicate transition / grace periods explicitly when introducing new system rules
**Source**: 2026-04-29 M8 video v8 (Satyam Darmora via Shiva: "One month support to be aligned.")

"Bonus is changing" without a window reads as immediate pressure. With
a stated grace period, the partner gets cognitive room. State the
grace duration and what happens at the end.

| Don't | Do |
|---|---|
| "अब Network Quality पर Bonus मिलेगा" (no window) | "अब Network Quality पर Bonus मिलेगा। 1 महीना समझने का समय. फिर apply होगा।" |

### P10 — Once a campaign establishes a vocabulary set, don't deviate within the same campaign
**Source**: 2026-04-29 M8 video v8 (Shiva: "Keep as previous which is uptime and speed as in the earlier video.")

Continuity reduces partner cognitive load. If the earlier deployed
comm used "uptime + ISP speed", the next comm in the same campaign
must use the same terms — don't simplify to just "speed" or rename to
"latency."

| Don't | Do |
|---|---|
| Rotate "quality" → "speed" → "latency" mid-campaign | Lock the term used in the first deployed comm and reuse |

### P11 — Avoid framing the system/brand as the active monitor of the partner
**Source**: 2026-04-29 M8 video v11 (Shiva: "We don't have to show that Wiom is sort of monitoring the CSP.")

Even when the system *is* measuring or recording, active framing
("Wiom measures you", "We track your...") creates a surveillance feel.
Use passive voice or device-centric framing — the device measures, the
system records, *not* the brand watching.

This sits *opposite* to P4 (specify the install agent): you can name
who installs the device, but the act of measurement itself should be
passive.

| Don't | Do |
|---|---|
| "व्योम इसे measure करेगा एक PNM device से" | "यह PNM device से measure होती है" |

### P12 — Tell partners directly when a system has hard-cutoff implications
**Source**: 2026-04-29 Pilot 20 calling pitch (Shiva → my pushback → Shiva final call: "Tell them clearly.")

When the new system makes the old one stop working, tell partners
directly. Hiding the cutoff to avoid panic creates worse outcomes
when reality hits — partners stranded mid-task with no warning lose
trust faster than partners who knew the cutoff was coming.

| Don't | Do |
|---|---|
| "अब से नए app पर काम करें" (no cutoff mention) | "पुराना app आज से बंद हो रहा है — अब से सारा काम नए app पर ही करना है" |

### P13 — Lever language should state the actual business objective, not aspirational identity
**Source**: 2026-04-29 Pilot 20 calling pitch (Shiva: "system ko stable karne ke liye aapka feedback important hai — we should tell them the objective.")

When asking partners to do something extra (provide feedback, test a
pilot, take time to learn), state *why* in plain business terms — not
as identity inflation. "You shape the future" sounds like marketing
fluff; "we're stabilizing the system, your feedback matters" reads as
honest and motivates pragmatically.

| Don't | Do |
|---|---|
| "आपकी input से तय होगा कि बाकी partners को कैसा app मिले" | "हमारा मकसद है — नए system को stable करना। उसके लिए आपकी feedback ज़रूरी है।" |

### P14 — Partners chosen for pilots should be addressed as early-access stakeholders, not subjects
**Source**: 2026-04-29 Pilot 20 calling pitch design.

The word "test" or "pilot" signals "not the real thing" to partners,
who may then discount the experience. Reframe as recognition + influence:
"You're getting it first" is true and motivating; "We're testing it on
you" is true and demotivating.

| Don't | Do |
|---|---|
| "आप 20 partners हैं जिन पर हम नया app test कर रहे हैं" | "आप पहले 20 partners में से एक हैं जिन्हें यह app अभी मिलेगा" |

### P15 — Permission to break: explicitly tell pilot/early-access partners that issues are expected
**Source**: 2026-04-29 Pilot 20 calling pitch design.

Partners who feel they're being evaluated will hide problems to look
competent. Pilot/early-access partners are not being evaluated — but
they don't know that unless we say so. Explicit "issues are normal,
that's why you're here" framing unlocks honest issue reporting.

| Don't | Do |
|---|---|
| "If anything goes wrong, let us know" (implies wrong = bad) | "नया app है, तो कुछ चीज़ें शुरू में अलग लगेंगी। कोई भी issue हो — PTL को call करें" (issues = expected data) |

---

*content-improvement-log.md — L2-domain-playbooks/*
*Append-only. Next principle appended when surfaced from real session feedback.*
