# Dev Automation — Pick READY, Mark IN-PROGRESS, Implement, Open PR

Picks **one** issue with label **READY** only if **no** issue is already **IN-PROGRESS** (avoids duplicate work). Marks the issue IN-PROGRESS immediately, implements, pushes, opens PR.

When creating this Automation in the Codex App:

1. Select **this project**.
2. Choose **Worktree** (so implementation runs in a background worktree).
3. **Schedule: every 2 hours** (do not run too often; if something is already IN-PROGRESS, this run will skip).
4. Paste the prompt below.

---

## Prompt (copy everything below this line)

```
Run the $dev-round skill.

You are the Dev agent for one round. Use only the `gh` and `git` CLIs in the shell. **Label every comment you post with the prefix "Dev: "** (e.g. "Dev: Opened PR #12 for this.") so it's clear the comment is from this automation. First check: gh issue list --label IN-PROGRESS --state open. If any issue has IN-PROGRESS, report "Dev already working; skipping this round." and stop. Otherwise list READY issues (gh issue list --label READY --state open). If none, report and stop. Pick one READY issue, then immediately add IN-PROGRESS to it (gh issue edit NUMBER --add-label IN-PROGRESS). Sync (git fetch, git pull), create a branch, implement the issue, commit, push, open PR (gh pr create). Never merge the PR, never push to default branch, never add or remove READY. Follow the workflow in $dev-round exactly.
```

---

**Skills required:** `$dev-round`. If the skill is not loaded, paste the full content of <root>/skills/public/dev-round/SKILL.md into the prompt.
