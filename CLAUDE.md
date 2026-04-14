# Wiom Comms AI

You are operating inside the Wiom Comms AI repository — a structured
knowledge base that Claude agents use to design, deploy, measure, and
iterate on Wiom communications across all channels and OS domains.

Read this file fully before doing anything else.

---

## WHAT THIS SYSTEM IS

Wiom is a Pay-As-You-Go (PayG) home internet provider in India.
This repo is the knowledge and instruction layer for an AI-assisted
communications design system. It is not a software product — it is
a file organisation and instruction system that tells agents where
to find what they need, how to use it, and what to do when something
is missing.

CRITICAL CONTEXT — read before any task:
  Wiom is NOT a monthly subscription ISP.
  Every comm this system produces must reflect PayG flexibility.
  Never imply fixed plans, monthly validity, or subscription framing.
  This rule applies in every session, for every task, without exception.

---

## HOW TO START ANY TASK

Step 1 — Read SECURITY-RULES.md first, always:
  L0-agent-instructions/SECURITY-RULES.md

  This file contains hard constraints that override everything else.
  No task begins until you have read it.

Step 2 — Identify the task type and load the correct agent file:

  | Task type                          | Load this file                                      |
  |------------------------------------|-----------------------------------------------------|
  | New task — needs routing           | L0-agent-instructions/orchestrator-agent.md         |
  | Design or iterate a comm           | L0-agent-instructions/design-agent.md               |
  | Log a deployed comm                | L0-agent-instructions/logger-agent.md               |
  | Analyse performance data           | L0-agent-instructions/measurement-agent.md          |
  | Extract learnings from results     | L0-agent-instructions/learning-agent.md             |

  DEFAULT: if you are unsure which agent to load, always load the
  orchestrator. It will determine the correct route.

Step 3 — Follow the loaded agent file exactly.
  The agent file is your instruction set for the task.
  Do not improvise beyond what it specifies.

---

## REPO STRUCTURE — where everything lives

  CLAUDE.md                          ← you are here
  README.md                         ← human documentation (never loaded by agents)

  L0-agent-instructions/             ← HOW each agent behaves
    orchestrator-agent.md            ← routes tasks, assembles context
    design-agent.md                  ← designs comms copy and briefs
    logger-agent.md                  ← logs comms to project comms-log
    measurement-agent.md             ← analyses performance data
    learning-agent.md                ← extracts patterns to playbooks
    QUALITY-CHECKLIST.md             ← pre-output checklist (all agents)
    SECURITY-RULES.md                ← hard constraints (all agents)
    OUTPUT-TEMPLATES.md              ← standard output formats

  L1-global/                         ← WHAT applies to all tasks
    pca-content-governance.md        ← PCA Part A: 8 principles, vocabulary
                                       canon, Hindi lock, tone envelope,
                                       state-to-language translations
    pca-enforcement-governance.md    ← PCA Part B: message blocks, silence
                                       policy, anti-contamination tests,
                                       OS guardrails, escalation, economic
                                       rules, deployment governance, drift audit
    system-architecture.md           ← OS state machines, event triggers
    channel-specs.md                 ← per channel: limits, media, cost, timing
    comms-principles.md              ← when to communicate, fatigue rules
    user-segments.md                 ← segment definitions, behavioural signals
    regulatory-compliance.md         ← TRAI DND, consent, opt-out, legal
    push-to-pull-rules.md            ← transition rules, litmus tests,
                                       circuit breakers — permanent constraint

  L2-domain-playbooks/               ← WHAT works per OS domain
    quality-os-playbook.md           ← At Risk, Non-Compliant, recovery comms
    compensation-os-playbook.md      ← payout, bonus, carry fee, holds comms
    enforcement-os-playbook.md       ← restriction, FPV, suspension comms
    exit-os-playbook.md              ← voluntary/system exit, settlement comms
    onboarding-playbook.md           ← journey exception: Day 1/3/7 sequences
    continuity-support-playbook.md   ← customer comms during partner exits
    proposed-learnings/              ← agent proposes, human approves

  L3-projects/                       ← WHAT is specific to one project
    partner-412/
      brief.md
      comms-log.md
      iterations.md
      results.md
      context-from-teams.md
    project-template/                ← copy this for every new project

  review-queue/                      ← all agent output lands here first
    [project-id]/
    adhoc/                           ← one-off task outputs

  system/
    MANIFEST.md                      ← master routing table
    GAPS.md                          ← missing context log
    CHANGELOG.md                     ← knowledge base change record
    CROSS-PROJECT-REFS.md            ← curated cross-project index

  templates/                         ← starter templates for new files
  triggers/                          ← code that fires agents externally
    wiom_design_engine_trigger.gs    ← Google Form → Apps Script → Claude API

---

## INPUT SOURCES

This system accepts tasks from multiple sources.
The orchestrator handles all of them — you do not need to
treat them differently before loading the orchestrator.

  Claude Code (terminal)   → you type the task directly
  Google Form              → team submits a structured request,
                             Apps Script fires the orchestrator via API
  Any future trigger       → Gupshup webhook, Slack bot, cron job,
                             event-driven API call

---

## HUMAN INPUT — USE INTERACTIVE OPTIONS

When you need a decision, clarification, or approval from the human,
always use the AskUserQuestion tool to present options as clickable
choices. Never ask open-ended questions in plain text when structured
options are possible.

Use this for:
  - Missing context: "Which audience segment?" with segment options
  - Ambiguous tasks: "Which OS trigger applies?" with trigger options
  - Design decisions: "Which channel?" with channel options
  - Approval gates: "Approve this output?" with approve/reject/revise
  - Conflict resolution: "Brief says X, dashboard says Y — which?"

Rules:
  - 2-4 options per question. Keep labels short (1-5 words).
  - Add a description to each option explaining the implication.
  - The human can always type a custom answer (built-in "Other" option).
  - If multiple independent decisions are needed, ask up to 4 questions
    in a single prompt rather than asking one at a time.
  - Never guess when you can ask. A 5-second popup is better than
    a wrong design that needs rework.

---

## WHAT AGENTS CAN AND CANNOT DO

  CAN:
    Design comms copy, sequences, and deployment plans
    Log comms to project files
    Analyse performance data and recommend actions
    Propose learnings for human review
    Write to review-queue/, L3 project files, GAPS.md,
    CHANGELOG.md, proposed-learnings/

  CANNOT:
    Send any message via any channel (WhatsApp, SMS, Gupshup)
    Edit MANIFEST.md, any L0 file, or any L1 file
    Edit domain playbooks directly
    Deploy anything without human approval
    Override any rule in SECURITY-RULES.md
    Produce output that violates PCA vocabulary, tone, or
    message block rules (enforced via QUALITY-CHECKLIST.md)

---

## MAINTENANCE RULES

  MANIFEST.md         → human updates only, every time a project is added
  GAPS.md             → agent writes automatically, human reviews weekly
  CHANGELOG.md        → human updates every time any file changes
  Domain playbooks    → learning agent proposes, human approves and edits
  L0 and L1 files     → human only, never agent
  PCA files           → human only (Founder for economic, Comms Head for rest)

---

## LIVE DATA SOURCES

For active campaigns with live dashboards, the agent should WebFetch
the dashboard URL before any design, measurement, or iteration task
to get current metrics. Static context files capture stable facts;
dashboards capture volatile numbers.

  project-csp-migration-apr26:
    Dashboard: https://shivakimothi-design.github.io/csp-comms-dashboard/
    Contains : real-time popup reach, video completion, quiz pass rates,
               deployment statuses, campaign timeline, partner state
               distribution (S0-S4)
    When     : before any task on project-csp-migration-apr26 that
               needs current metrics (design, measurement, iteration)
    Fallback : if dashboard is unreachable, use the snapshot in
               L3-projects/project-csp-migration-apr26/results.md

---

## LAST UPDATED
2026-04-13 — v1.2
  + Live Data Sources section added for CSP migration dashboard
  + L3 project files created for project-csp-migration-apr26:
    context-from-teams.md, comms-log.md, results.md, iterations.md
2026-03-27 — v1.1
  + OS-level domain routing (replaces journey-based)
  + PCA files added to L1 (pca-content-governance, pca-enforcement-governance)
  + push-to-pull-rules.md added to L1
  + README.md added to root
  + PCA compliance added to CANNOT section
Maintained by: human only
