# GAPS.md — Wiom Comms AI
## Auto-log of missing context, fallbacks, and unmatched domains

Maintained by: agents (append only) + human (review and resolve)
Rule: Every time an agent cannot find a file, falls back to a
higher layer, or encounters an unmatched OS trigger — log it here.
Human reviews periodically and resolves by creating the missing file
or updating the MANIFEST.

---

## ACTIVE GAPS

DATE          : 2026-04-02
TASK          : Design the Day 1 welcome message for migrating CSPs
MISSING       : L1-global/regulatory-compliance.md
USED_INSTEAD  : SECURITY-RULES.md Rule 2 (TRAI hard stops only)
RECOMMENDATION: Create regulatory-compliance.md with full TRAI/DND
                detail, consent management, opt-out handling, record-keeping

DATE          : 2026-04-02
TASK          : Design the Day 1 welcome message for migrating CSPs
MISSING       : L2-domain-playbooks/onboarding-playbook.md
USED_INSTEAD  : L1 globals only (PCA + comms-principles + channel-specs)
RECOMMENDATION: Create onboarding-playbook.md with proven patterns and
                mistakes to avoid from prior onboarding comms

DATE          : 2026-04-02
TASK          : Design the Day 1 welcome message for migrating CSPs
MISSING       : L3-projects/project-csp-migration-apr26/comms-log.md
USED_INSTEAD  : none — no prior messages exist (project at plan stage)
RECOMMENDATION: Logger agent creates this file after first message is
                approved and deployed

---

## RESOLVED GAPS

(none yet)
