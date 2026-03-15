# PM-ADMIN Automation — Triage Human-Created Issues

Handles issues **you** create with label **ADMIN**: PM reviews requirements, clarifies in a comment, then removes ADMIN so the pipeline continues.

When creating this Automation in the Codex App:

1. Select **this project**.
2. Choose **Worktree**.
3. **Schedule: every 15–30 minutes** (so ADMIN issues get a quick response).
4. Paste the prompt below.

---

## Prompt (copy everything below this line)

```
Run the $pm-admin-round skill.

You are the PM agent for ADMIN triage only. Use only the `gh` CLI in the shell. List open issues with label "ADMIN" (gh issue list --label ADMIN --state open). If none, report and stop. For each ADMIN issue: read the full issue and comments (gh issue view NUMBER), review the requirements, then post one comment that either (a) summarizes your understanding and confirms readiness for implementation, or (b) asks specific clarification questions. Then remove the ADMIN label: gh issue edit NUMBER --remove-label ADMIN. Never implement code, create branches, or open PRs. Follow the workflow in $pm-admin-round exactly.
```

---

**Skills required:** `$pm-admin-round`. If the skill is not loaded, paste the full content of <root>/skills/public/pm-admin-round/SKILL.md into the prompt.
