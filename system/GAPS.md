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

DATE_RESOLVED : 2026-04-30
ORIGINAL_DATE : 2026-04-28
TASK          : File product/UX design frameworks shared by Shiva
RESOLUTION    : Split decision (per Shiva 2026-04-29):
                - Unified Attention Framework v1.3 → promoted to
                  L1-global/attention-framework.md (cross-project,
                  governs all CSP-app attention surfaces). Override
                  banner added to file header.
                - CSP App Adoption System v1.2 → filed at L3 project
                  level (L3-projects/project-csp-migration-apr26/
                  adoption-system-v1.2.md) since it is migration-
                  specific per Shiva's reading.
                - L1 promotion done under EXPLICIT HUMAN OVERRIDE of
                  CLAUDE.md rule "L0/L1 → human only, never agent."
                  Override flagged in file banner + commit message.
                  Karishni notified via prominent banner; she may
                  review/move/edit freely.
NEXT_ACTIONS  : (1) Karishni review of the L1 file when convenient.
                (2) When design-agent.md is authored, it should
                require reading attention-framework.md before any
                in-app or in-app-bridged comms task.
                (3) MANIFEST.md should be updated to include the new
                L1 entry and the new L3 file (human update per the
                MANIFEST rule).

DATE_RESOLVED : 2026-04-30
ORIGINAL_DATE : 2026-04-28
TASK          : Design M8 PNM device + bonus eligibility comm
RESOLUTION    : Resolved via WhatsApp video instead of WA text:
                - Wiom_PNM_Bonus.mp4 (1:02 min) produced in
                  C:\Users\shiva\wiom-ptl-analysis\output\ (binary,
                  not committed to repo)
                - Deployed by Karishni 2026-04-29 to two cohorts
                  (Entries 8 + 9 in comms-log.md)
                - Bonus-led framing chosen over Karishni's v2 WA
                  text framing — partners think in "bonus" not
                  "quality" (Shiva's mental-model insight)
                - In-app event-driven approach per the new Adoption
                  System framework deferred to new app launch (old
                  app is what's deployable now)
                - 15 content principles consolidated into
                  L2-domain-playbooks/content-improvement-log.md
NEXT_ACTIONS  : Measure PNM activation movement 5-7 days post-deploy.
                Active denial rate is the key metric (was 16.6%, may
                grow before it shrinks).

---

## NOTES FOR KARISHNI (when next accessing repo)

This commit (2026-04-30) introduces three significant changes that
warrant your attention:

  1. NEW L1 file under explicit human override:
     L1-global/attention-framework.md
     (See override banner at top of file.)

  2. NEW L3 project file:
     L3-projects/project-csp-migration-apr26/adoption-system-v1.2.md
     (Migration-specific framework, filed at project level.)

  3. NEW L2 domain playbook:
     L2-domain-playbooks/content-improvement-log.md
     (15 content principles surfaced from M8 video iteration.
     Append-only. Will be referenced by design-agent.md when authored.)

If you'd like to discuss placement, scope, or content of any of these,
ping Shiva — he authorized each decision in this session.
