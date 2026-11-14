# claude-continue

A small repo that lets Claude Code pick a task back up on Anthropic's cloud after your 5-hour usage limit resets, while your laptop is off.

## How it works
- `CLAUDE.md`: standing rules Claude reads at the start of every run.
- `CHECKPOINT.md`: the handoff (goal, what is done, the next step).
- A scheduled routine starts a fresh cloud session, clones this repo's default branch, reads the checkpoint, and continues.

## Before you go offline
1. Put your project files in this repo, or copy `CLAUDE.md` and `CHECKPOINT.md` into your existing project repo.
2. Ask Claude to update `CHECKPOINT.md` (goal, done, next step).
3. Commit and push to `main`. The cloud run only sees what is on GitHub.
4. In Claude Code, before you hit the limit, run:

   ```
   /schedule in 5 hours: in <your-username>/<repo>, read CHECKPOINT.md and continue from "Next step". Update CHECKPOINT.md and commit when finished.
   ```

   Already locked out? Create the same routine at claude.ai/code/routines instead.

## After the run
Changes land on a `claude/`-prefixed branch. Review it and merge it into `main`.
