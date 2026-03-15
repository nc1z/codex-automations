# One-Round Automation (Optional) — PM + Dev + QA in a single run

Use this **only if** you prefer **one** Automation that runs the full pipeline on a single schedule (e.g. every 2 hours), instead of four separate automations with different cadences. The **recommended** setup is four automations as in [schedule.md](schedule.md): PM-ADMIN (every 15–30 min), PM-Propose (every 1–2 h), Dev (every 2 h), QA (every 2 h).

When creating this Automation:

1. Select **this project**.
2. Choose **Worktree**.
3. **Schedule: e.g. every 2 hours** (single cadence for all steps).
4. Paste the prompt below.

---

## Prompt (copy everything below this line)

```
Run these steps in order. Use only `gh` and `git` in the shell. Never merge a PR, never push to the default branch, never add READY or ADMIN yourself.

Step 1 — PM-ADMIN: Run $pm-admin-round. Triage every open issue with label ADMIN: review, comment (clarify or confirm), remove ADMIN label. If no ADMIN issues, report and continue.

Step 2 — PM-Propose: Run $pm-round. Review existing open issues and comments; propose at most one or two new issues with label PM. Report.

Step 3 — Dev: Run $dev-round. If any issue has IN-PROGRESS, report "Dev busy; skipping." and skip to Step 4. Otherwise pick one READY, add IN-PROGRESS, implement, push, open PR.

Step 4 — QA: Run $qa-round. Review open PRs (prefer without qa-done), post comments or add qa-done. Do not merge.

Summary at the end: what was triaged (ADMIN), what was proposed (PM), what was implemented (if any), what was reviewed (if any).
```

---

**Skills required:** `$pm-admin-round`, `$pm-round`, `$dev-round`, `$qa-round`. If any skill is not loaded, paste the full content of <root>/skills/public/<skill-name>/SKILL.md into the prompt (e.g. pm-admin-round, pm-round, dev-round, qa-round). For separate cadences and clearer project management, use the four automations in [schedule.md](schedule.md) instead.
