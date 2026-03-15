# How Often Each Automation Should Run

Use **multiple automations** with different schedules so PM stays responsive and Dev does not over-poll. Recommended cadences:

| Automation | Prompt file | Recommended schedule | Why |
|------------|-------------|----------------------|-----|
| **PM-ADMIN** | [pm-admin.md](pm-admin.md) | **Every 15–30 min** | Human-created issues with label ADMIN get a quick PM response (review + clarify, then remove ADMIN). |
| **PM-Propose** | [pm.md](pm.md) | **Every 1–2 hours** | Post-merge cleanup (remove IN-PROGRESS when PR merged); review existing issues/comments; propose new (label PM). Less frequent than ADMIN so you’re not spamming proposals. |
| **Dev** | [dev.md](dev.md) | **Every 2 hours** | Pick one READY issue only if no issue is IN-PROGRESS; mark IN-PROGRESS, implement, open PR. **Dev must reference the issue in the PR** (e.g. Closes #42) so PM can remove IN-PROGRESS when the PR is merged. |
| **QA** | [qa.md](qa.md) | **Every 2 hours** | Review open PRs, add qa-done when good. Align with Dev so PRs get reviewed soon after they’re opened. |

---

## Order of operations (typical)

1. **PM-ADMIN** runs often (15–30 min) → ADMIN issues get triaged quickly.
2. **PM-Propose** runs every 1–2 h → post-merge cleanup (remove IN-PROGRESS), backlog review, and new PM-labeled issues.
3. You add **READY** to issues you want implemented.
4. **Dev** runs every 2 h → if no IN-PROGRESS, picks one READY, marks IN-PROGRESS, implements, opens PR.
5. **QA** runs every 2 h → reviews PRs, adds qa-done.
6. You merge PRs. **PM automation** removes IN-PROGRESS from the linked issue and **closes** it (marking it done). Dev must reference the issue in the PR body (e.g. Closes #42).

---

## Creating all four in the Codex App

1. **Automations** → New (four times).
2. For each: select **this project**, choose **Worktree** (QA can use Local if you prefer), set the **schedule** from the table above, paste the prompt from the linked file.
3. Ensure the four skills are loaded: `$pm-admin-round`, `$pm-round`, `$dev-round`, `$qa-round` (from [../skills/](../skills/)).

If you run automations **very frequently** (e.g. PM-ADMIN every 10 min), keep an eye on worktree cleanup and Triage so old runs don’t pile up.
