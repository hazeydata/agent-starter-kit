---
name: repo-and-cycles
description: Use when starting, resuming, or closing a work item.
---
# Repo and cycles

## When to Use
- Use when starting, resuming, handing off, or closing any work item, so state lives in files a fresh agent can read cold.

State lives in git, not in chat. A cycle is one work item with a start and an end. To resume, read only the newest cycle.

## Repos (structure inspired by Brian Casel)
- Every project has `<project>-meta` (private): everything around the output. It always has `AGENTS.md` (what this project is, which repos, how agents should work here) and `cycles/`. Add area folders (e.g. `strategy/`, `brand/`, `growth/`) only when that area has docs. Start here.
- The main output goes in `<project>` (no suffix), whatever it is: code, dashboard files, docs. Create it when there is output to keep.
- Default: new output goes in a folder in an existing repo. Propose a new `<project>-<suffix>` repo only for: different access or context (a person or agent working on one part should not see or load the other, e.g. keep `-accounts` out of `-site` work), a separate release, or a different audience or lifespan. The suffix names what it holds (e.g. `-site`, `-accounts`, `-settings`, `-data`).
- Never create a repo yourself: propose it with the reason, the human approves, log it in `decisions.md`.

## Cycle folder: `<project>-meta/cycles/YYYY-MM-DD-<slug>/`
- `summary.md`: one living page with date and author, Status, Next action, Blockers, Leftovers (each with an owner), Links.
- `plan.md`: strategy, design, phases, gates. LOCKED before any build. After that it changes only through a `decisions.md` entry that it links to.
- `decisions.md`: one entry per ruling, giving date, who, ruling, reason. If no reason was given, write `reason not recorded`. Never invent one. This is the only decisions log; file rulings that span cycles in the newest cycle.

## Steps
1. Start: no `<project>-meta` repo yet? Propose creating one. Human approves per the Repos rule above, then write its `AGENTS.md` from `agents-md-template.md` (ships alongside this skill) — fill in the project name, repo list, and any project-specific rules; don't write one from scratch. Then create the first cycle folder with a thin summary, a draft plan, and an empty decisions log.
2. Plan: strategy, then design, then roadmap. Ask per `ask-once-then-finish`.
3. Lock: record "plan locked" in `decisions.md`. Then build.
4. Each phase gets a brief, a builder, and review by quality-gate in a fresh chat.
5. Before stopping: update `summary.md` with what's done, next step, blockers.
6. Close: when exit criteria are measured, not claimed. Name every leftover and its owner.

## Git rules
- PRs only. Never force-push or rewrite shared history.
- Work in your own branch or worktree; don't reset or clean a shared clone.
- Never commit files over 1 MB (reference them by path and checksum), secrets, tokens, `.env` files, or personal data.
- Check the diff for big files, secrets and personal data before opening the PR. If one slipped in, stop and flag the human.
- Docs change in the same PR as the code they describe.
