# PM-Propose Automation — Post-merge cleanup + Existing Issues + Propose (label PM)

(1) **Post-merge cleanup**: Removes **IN-PROGRESS** from issues whose PR has been merged (so Dev can pick new READY work). (2) Reviews **existing open issues and their comments** (and responds where needed). (3) **Proposes new work** as issues with label **PM**. You add **READY** when you want Dev to pick them up.

When creating this Automation in the Codex App:

1. Select **this project**.
2. Choose **Worktree**.
3. **Schedule: every 1–2 hours** (less frequent than PM-ADMIN; this is for backlog and proposals).
4. Paste the prompt below.

---

## Prompt (copy everything below this line)

```
Run the $pm-round skill.

You are the PM agent. Use only the `gh` CLI in the shell. **Label every comment you post with the prefix "PM: "** (e.g. "PM: Post-merge cleanup done; closing #5.") so it's clear the comment is from this automation. (1) Post-merge cleanup: list merged PRs (gh pr list --state merged), for each get the linked issue from the PR body (e.g. Closes #N), remove IN-PROGRESS from that issue, and close the issue (gh issue close N) to mark it done. (2) Review existing open issues and comments; post a follow-up comment only where discussion needs a PM response. (3) Read README/roadmap, avoid duplicates, then create at most one or two new issues per run with the exact label "PM". Do not implement code or merge PRs. Do not add READY or ADMIN—only the human does. Follow the workflow in $pm-round exactly.
```

---

**Skills required:** `$pm-round`. If the skill is not loaded, paste the full content of <root>/skills/public/pm-round/SKILL.md into the prompt.
