# MANIFEST.md — Wiom Comms AI
## Master Routing Table

Maintained by: human only
Last updated: 2026-04-02
Rule: Every time a project is added, a playbook is created, or a global
file changes — update this file and log the change in CHANGELOG.md.
The orchestrator reads nothing else before this file. One bad edit
cascades. Edit carefully.

---

## SECTION A — GLOBAL FILES (always loaded)

These 9 files are loaded in every session regardless of OS trigger.
If any file is missing, log to GAPS.md and halt.

  File                              Path
  --------------------------------  ------------------------------------------
  SECURITY-RULES.md                 L0-agent-instructions/SECURITY-RULES.md
  QUALITY-CHECKLIST.md              L0-agent-instructions/QUALITY-CHECKLIST.md
  OUTPUT-TEMPLATES.md               L0-agent-instructions/OUTPUT-TEMPLATES.md
  pca-content-governance.md         L1-global/pca-content-governance.md
  pca-enforcement-governance.md     L1-global/pca-enforcement-governance.md
  push-to-pull-rules.md             L1-global/push-to-pull-rules.md
  system-architecture.md            L1-global/system-architecture.md
  channel-specs.md                  L1-global/channel-specs.md
  comms-principles.md               L1-global/comms-principles.md
  user-segments.md                  L1-global/user-segments.md
  regulatory-compliance.md          L1-global/regulatory-compliance.md
  data-sources.md                   L1-global/data-sources.md

Note: regulatory-compliance.md is referenced by SECURITY-RULES.md Rule 2.
If this file is missing, flag to human before proceeding with any task.

Note: data-sources.md is used by measurement-agent.md Job B (construct).
If this file is missing, measurement agent can still run Job A (analyse)
but cannot construct SQL queries.

---

## SECTION B — DOMAIN PLAYBOOKS

Indexed by os_trigger. Load all playbooks matching the project's
os_trigger field. A project can have multiple os_triggers — load all.

Orchestrator uses OS SIGNAL WORDS for fuzzy matching when os_trigger
is not explicitly stated in the task input.

  os_trigger           File                                  Status
  -------------------  ------------------------------------  ----------
  onboarding           L2-domain-playbooks/onboarding-playbook.md          PENDING — not yet created
  quality              L2-domain-playbooks/quality-os-playbook.md          PENDING — not yet created
  compensation         L2-domain-playbooks/compensation-os-playbook.md     PENDING — not yet created
  enforcement          L2-domain-playbooks/enforcement-os-playbook.md      PENDING — not yet created
  exit                 L2-domain-playbooks/exit-os-playbook.md             PENDING — not yet created
  continuity-support   L2-domain-playbooks/continuity-support-playbook.md  PENDING — not yet created

OS SIGNAL WORDS by playbook (for fuzzy matching):

  onboarding       : onboarding, welcome, Day 1, Day 3, Day 7, new CSP,
                     activation, first recharge, app download, launch,
                     system reboot, migration
  quality          : quality, SLA, at risk, non-compliant, service stability,
                     uptime, resolution, quality score, telemetry, bonus eligibility
  compensation     : payout, bonus, carry fee, rate card, wallet, settlement,
                     financial hold, earning, ₹300, device collection
  enforcement      : restriction, FPV, suspension, fraud, integrity,
                     pattern watch, terminated, enforcement, May 1, compliance
  exit             : exit, voluntary, offboarding, asset return,
                     transition, settlement, system exit
  continuity-support : continuity, U2, customer during exit,
                       service continuity, transition support

Fallback rule: if no os_trigger matches and signal word scan yields
< 3 matches — use L1 global files only. Log to GAPS.md.

---

## SECTION C — PROJECT REGISTRY

One row per project. os_trigger can be a comma-separated list.
Orchestrator uses project_id to locate the correct L3 folder.

### Active Projects

  project_id                   : project-csp-migration-apr26
  os_trigger                   : onboarding, compensation, quality, enforcement
  folder_path                  : L3-projects/project-csp-migration-apr26/
  status                       : active
  owner                        : Shiva (Karishni)
  description                  : Migration of ~1,200 CSPs from legacy partner
                                 contract to new system-governed operating model
                                 by end of April 2026. 13-message comms plan
                                 spanning pre-launch, launch day, and post-launch.
  tags                         : csp-migration, whatsapp, onboarding, payg,
                                 rate-card, enforcement, bonus, delhi-ncr, bharat,
                                 mumbai, hindi-primary
  related_projects             : none
  product_dependencies         : dashboard-with-tickets, telemetry-status-card,
                                 quality-score-screen, month-summary-screen,
                                 payout-breakdown-screen, wiom-paathshala
  notes                        : App launch date ~Apr 7 — not locked. Use
                                 "launch hone wala hai" in all pre-launch copy.
                                 No hard dates until officially confirmed.
                                 Brief at plan stage — no messages sent yet.

### Completed Projects

  (none yet)

### Archived Projects

  (none yet)

---

## SECTION D — SYSTEM FILE LOCATIONS

Supporting files the orchestrator and agents reference.

  File                  Path                        Purpose
  --------------------  --------------------------  ----------------------------
  MANIFEST.md           system/MANIFEST.md          This file — routing table
  GAPS.md               system/GAPS.md              Auto-log of missing context
  CHANGELOG.md          system/CHANGELOG.md         All knowledge base changes
  CROSS-PROJECT-REFS.md system/CROSS-PROJECT-REFS.md Curated cross-references

---

## SECTION E — FOLDER STRUCTURE REFERENCE

  L0-agent-instructions/          Agent instruction files (human-maintained)
  L1-global/                      Global knowledge files (human-maintained)
  L2-domain-playbooks/            OS playbooks (learning agent proposes, human approves)
    proposed-learnings/           Staging area for unreviewed learning proposals
  L3-projects/                    One subfolder per project
    project-csp-migration-apr26/  Active project
    project-template/             Empty template — copy for new projects
  review-queue/                   All agent output lands here first
    project-csp-migration-apr26/  Project-specific output queue
    adhoc/                        One-off task outputs
  system/                         Maintenance files
  templates/                      Starter templates for new files
  triggers/                       External trigger code

---

## HOW TO ADD A NEW PROJECT

1. Create a new folder under L3-projects/ using the project_id as name
2. Copy all files from L3-projects/project-template/ into the new folder
3. Fill in brief.md with the project objective, audience, OS triggers,
   constraints, and success metrics
4. Add a row to SECTION C of this file with all required fields
5. Create a subfolder in review-queue/ using the same project_id
6. Log the addition in CHANGELOG.md

Do not add a project to the registry until brief.md exists and is filled in.
An empty brief is worse than no project — the orchestrator hard-stops on
missing brief.md, but a blank brief will produce broken output silently.

---

## HOW TO ADD A NEW PLAYBOOK

1. Create the playbook file in L2-domain-playbooks/ using the naming
   convention: [os_trigger]-playbook.md
2. Include the mandatory FILE HEADER: purpose, OS SIGNAL WORDS, TAGS,
   when to use, how to use, last updated
3. Add the os_trigger and file path to SECTION B of this file
4. Log the addition in CHANGELOG.md

---

## MANIFEST INTEGRITY RULES

- This file is updated by humans only — never by any agent
- Every change to this file must be logged in CHANGELOG.md
- The orchestrator hard-stops if this file is missing
- The orchestrator hard-stops if a project's folder_path does not exist
- The orchestrator hard-stops if a project's brief.md is missing
- Playbooks listed as PENDING are expected gaps — orchestrator falls
  back to L1 globals and logs to GAPS.md, does not halt
- If MANIFEST.md appears corrupted: reconstruct from CHANGELOG.md

---

*MANIFEST.md — system/MANIFEST.md — human-maintained*
*Do not edit without logging the change in CHANGELOG.md*
