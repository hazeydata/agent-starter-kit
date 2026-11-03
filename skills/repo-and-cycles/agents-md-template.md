# AGENTS.md: <project>

<One line: what this project is and who it is for.>

## Repos
- `<project>`: the main output (<code, dashboard files, docs>).
- `<project>-meta` (this repo, private): plans, cycles, decisions, area docs.
- `<project>-<suffix>`: <what it holds and why it is separate>. Delete if none.

## State
Read the newest folder in `cycles/` first: `summary.md`, `plan.md`, `decisions.md`. Then do its next action.

## Skills agents MUST load before step 1 of any task
`repo-and-cycles`, `handoff-brief`, `ask-once-then-finish`, `autonomy-level`, `three-line-report`. Add `coding-standard` for code. Open every one of these every turn, without being asked or reminded — never skip one because it seems not to match this ask; that call belongs to the skill's own When-to-Use text, seen only after opening it.

## Autonomy
Default for every agent on this project: level 2 (`autonomy-level`'s default stop-list — money, irreversible, under your name). Override here, per agent, or per task; name the level and scope explicitly. Example: "level 3 for `<agent>` on `<repo>` doc changes only."

## Rules
- PRs only. No files over 1 MB.
- No secrets, tokens, `.env` files or personal data in any repo.
