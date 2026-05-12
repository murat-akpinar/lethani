---
description: List all lethani slash commands with one-line descriptions
---

Print a compact reference of every lethani slash command grouped by phase.
Use this when the operator types `/lethani-help`, `help`, or asks "what
commands do I have?".

Output format (use exactly this layout):

```
LETHANI COMMANDS — quick reference
─────────────────────────────────────────────────────────────────
ENGAGEMENT LIFECYCLE
  /new-target <t>      scaffold engagements/<slug>/ + scope.md
  /recon <t>           Phase 1 — 6 parallel recon sub-agents
  /scan <t>            Phase 2 — cve-match + nuclei + ffuf (parallel)
  /manual-test <t>     Phase 3 — bucketed manual vuln testing
  /chain <t>           Phase 4 — vulnerability chaining (single thread)
  /report <t>          Phase 5 — duplicate check + severity + report
  /status [t]          engagement status across all / one target

LEARNING MODE
  /learn [cat]         fetch + filter + propose + apply (interactive)
  /learn-fetch [cat]   fetch + filter + stage to _pending_patches.md
  /learn-pending       review/apply staged patches with operator approval

HEALTH / UPDATE
  /lethani-check       version + freshness + pending count
  /lethani-help        this reference
─────────────────────────────────────────────────────────────────
SHORTCUTS
  `<t>` = engagement slug (e.g. `acme` for `acme.example`)
  `[cat]` = optional vuln class filter (e.g. `ssrf`, `oauth`)
```

Then add a one-line tail suggesting the most relevant next step based on
local state:

- If no engagements exist yet: `Tip: try /new-target <domain> to start.`
- If at least one engagement exists but no `recon/_summary.md`: `Tip: run /recon <slug> on a target.`
- If pending patches exist: `You have N patches in /learn-pending.`
- If a newer release is available: `Update available — see /lethani-check.`
- Otherwise: `Run /lethani-check for status, or /new-target to begin.`

Do not load any playbooks or modify any files. This is purely informational.
