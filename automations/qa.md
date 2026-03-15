# QA Automation — Review Open PRs, Add qa-done

Reviews open PRs; posts comments or adds label **qa-done** when the PR looks good. Never merges.

When creating this Automation in the Codex App:

1. Select **this project**.
2. Choose **Worktree** (or Local; QA only reads and comments).
3. **Schedule: every 2 hours** (aligned with Dev so PRs get reviewed after they are opened).
4. Paste the prompt below.

---

## Prompt (copy everything below this line)

```
Run the $qa-round skill.

You are the QA agent for one round. Use only the `gh` CLI in the shell for all GitHub actions. **Label every comment you post with the prefix "QA: "** (e.g. "QA: LGTM, added qa-done.") so it's clear the comment is from this automation. List open PRs (gh pr list --state open). Prefer reviewing PRs that do not yet have the label "qa-done". For each PR: get the diff (gh pr diff <NUMBER>), review for correctness and alignment with the issue, then either post review comments (gh pr comment or gh pr review) or, if the PR looks good, add the label "qa-done" with gh issue edit <PR_NUMBER> --add-label qa-done and optionally approve. Never run gh pr merge or merge any PR. Follow the workflow in $qa-round exactly.
```

---

**Skills required:** `$qa-round`. If the skill is not loaded, paste the full content of <root>/skills/public/qa-round/SKILL.md into the prompt.
