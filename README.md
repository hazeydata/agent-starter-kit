# Agent Starter Kit

A small, platform-agnostic team of AI agents and skills, written in plain markdown. No vendor lock-in: every file is a prompt you can load into any agent harness that supports a system prompt, on-demand markdown skills, and function-calling tools.

## The minimum team

| Agent | One job | Never does |
|---|---|---|
| [chief](agents/chief.agent.md) | Front door: sorts each ask, routes it, keeps `decisions.md` current | Builds or reviews its own routing |
| [bot-maker](agents/bot-maker.agent.md) | Creates and repairs agents and skills, owns the roster | Ships its own work without the gate |
| [quality-gate](agents/quality-gate.agent.md) | Binary SHIP / HOLD with a one-line note | Reviews anything it built |

Skills (loaded on demand, each short):

| Skill | Use when |
|---|---|
| [skill-builder](skills/skill-builder/SKILL.md) | Writing or refining a skill |
| [agent-builder](skills/agent-builder/SKILL.md) | Writing or refining an agent (`.agent.md`) |
| [skill-or-bot](skills/skill-or-bot/SKILL.md) | Sorting an ask: quick ask, work for an existing bot, change to a bot or skill, or new capability (a skill unless one of the 4 bot tests holds; the human approves new ones) |
| [repo-and-cycles](skills/repo-and-cycles/SKILL.md) | Starting, resuming, or closing any work item |
| [handoff-brief](skills/handoff-brief/SKILL.md) | Handing work to another agent or person |
| [coding-standard](skills/coding-standard/SKILL.md) | Any code change |
| [ask-once-then-finish](skills/ask-once-then-finish/SKILL.md) | Start of any task: gather everything in one round, then work until done |
| [autonomy-level](skills/autonomy-level/SKILL.md) | Start of any task: how much it may do before asking — ask every step, ask only about named items, or never ask |
| [three-line-report](skills/three-line-report/SKILL.md) | Reporting a finished task or a stop: Result, Needs you, Unsure |

Optional add-on: [pstack](https://github.com/cursor/plugins) (MIT, Lauren Tan, cursor/plugins) is a fuller coding standard for Cursor users. It isn't part of the kit because it depends on Cursor-specific tooling.

[templates/project-meta/](templates/project-meta/) is a skeleton meta repo (README, `AGENTS.md`, and one example cycle with its decisions log).

Follow-through rule (all agents): finish all of the ask. Done = the live outcome plus a leftover count (0 is a valid count).

## For an agent installing this kit

What's here:
- `agents/`: one markdown file per agent (job, anti-jobs, voice, wake, loads).
- `skills/`: one folder per skill (9 today), each holding only a `SKILL.md`.
- `templates/project-meta/`: copy it to start a project's `-meta` repo. Its `AGENTS.md` is the shared instructions file.

Hard rules (read before step 1):
- MUST, STOP, and "only if" are not suggestions. If a step can't be done as written, STOP and report the blocker. Never swap in your own plan.
- Agent files are not skills. Never put a `.agent.md` file in the skill library.
- One role per session. Never ask one session, helper, or subagent to act as more than one kit agent.
- Ask the human in plain chat, then end your turn. A pop-up or question tool may not reach them. Silence is not a yes.
- Keep a list of every file, agent, and setting you create or change. The install report includes it, so the install can be undone.

Install:
1. **Coding question.** Name your own harness (don't ask the human). Ask only: "Will this kit be used for coding?" Then end your turn and install nothing until the human replies. If yes, chief does a one-time web search for the best available coding standard for that harness, for example pstack's poteto-mode on Cursor (if the team later has a research agent, this lookup goes to it), and, with the human's OK, installs it in place of `coding-standard`, crediting the source. If no, keep `coding-standard`.
2. **Map the harness.** Read your harness's own docs. Search them for: agent, custom agent, bot, persona, profile, assistant, mode, gem, project, system prompt, instructions. Fill in this table; it goes in the install report:

   | Kit piece | Harness feature used | Proof (doc link or command output) |
   |---|---|---|
   | Persona: an agent with its own instructions and skill set | | |
   | Skill library: markdown loaded on demand | | |
   | Separate session or helper (for quality-gate) | | |
   | Default-agent setting | | |

   Write "none" only with a doc link that shows the feature doesn't exist. "I didn't find it" is not proof.
3. **Install skills.** Copy each `skills/<name>/` folder into the skill library, names unchanged. No skill library? Put each skill where the agent can read it on demand (a knowledge file, a project file, or a repo folder), and list each skill's `name` and `description` in the agent's instructions.
4. **Install agents.**
   - Persona row is not "none": you MUST make one persona per `.agent.md`. Its body is the persona's instructions, word for word — never paraphrase or summarize the MUST/Step 0 language down to something shorter, that's the whole mechanism that forces skill use. Enable only the skills on its `MUST load...` line, if the harness can limit skills; if it can't, say so in the report.
   - Only if the persona row is "none" with proof: run one session per agent, starting each with that `.agent.md` body as its instructions.
5. **Default agent.** If the harness has a default-agent setting that can be undone, ask the human in plain chat whether chief should become the default. Change it only on a yes. Otherwise leave the current default alone.

Check (every item MUST pass; any fail = the install is HOLD):
1. Loads coverage. Find where your harness stores installed skills; they may be nested, so search recursively. From the kit folder, set `P` to that path:
   ```sh
   P=skills; for s in $(grep -ho '^\*\*MUST load.*' agents/*.agent.md | grep -o '`[a-z0-9-]*`' | tr -d '`' | sort -u); do find "$P" -path "*/$s/SKILL.md" | grep -q . || echo "missing: $s"; done
   ```
2. Personas exist. Show the harness's own list of agents or personas (command output or screenshot) with chief, bot-maker, and quality-gate in it. Skip only when the persona row is "none".
3. End-to-end ask. Send this ask, word for word, to chief's own persona or session. Not a helper you brief yourself, and give no hints, reminders, or nudges about skills before or after sending it — if you have to remind it to use a skill, that is a FAIL on this check, not a pass with a note: "Make me a skill for writing a weekly status update for a project."
   - chief named the skills it opened and restated the ask in one line, unprompted, before doing anything else.
   - chief ran `skill-or-bot`, searched the installed skills, and named what it found.
   - chief asked the human to approve a new skill before anything was created.
   - chief wrote a `handoff-brief` with yes/no success criteria and delivered it to bot-maker's persona or session.
   - bot-maker built and tested the skill and did not review it.
   - quality-gate ran in a separate persona or session from bot-maker and gave SHIP or HOLD against the brief.
   - The rulings are in a cycle's `decisions.md` (if there is no `-meta` repo yet, create a scratch cycle folder per `repo-and-cycles`).
   If the harness can't pass a message from one persona to another, the human carries each brief. Say so in the report; that is not a failure.
4. Report per `three-line-report`. Include the step 2 table, the result of each check, the undo list, and every step that was unclear.

A harness linter may warn that kit skills lack extra frontmatter fields (version, author, license, tags). That is expected; ignore it.

Don't:
- Add harness-specific steps to this README. Name capabilities, not products.

## Portability

Every piece maps to three generic harness parts:

| Kit piece | Generic harness part |
|---|---|
| `agents/*.agent.md` body | System prompt (one per agent) |
| `skills/*/SKILL.md` | Markdown loaded on demand: list each skill's `name` and `description` in the system prompt, load the body only when it applies |
| "read files, write files, run commands, open PRs" | Tools, exposed through standard JSON-schema function calling |
| `AGENTS.md` (or your harness's instructions file) | Shared preamble prepended to every system prompt |
| `decisions.md`, cycle folders | Memory. State lives in git, not in the model or a vendor memory feature |

Running on open-weight models:
- Smaller context windows. Keep each skill under about 60 lines and load it only when needed. Never load all skills up front.
- Tool calling goes through standard function calling (OpenAI-compatible `tools` schema, as served by vLLM, llama.cpp, Ollama and similar). The kit names capabilities ("open a PR", "read a file"), never a vendor's tool names.
- No proprietary memory. A fresh agent recovers state by reading the newest cycle's `summary.md`, `plan.md` and `decisions.md`.
- Smaller models follow short, imperative, numbered steps better than long prose. Keep the house style.
- Keep the quality gate on a separate model call (ideally a different model) from the builder.
