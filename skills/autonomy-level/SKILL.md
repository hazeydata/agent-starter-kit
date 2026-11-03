---
name: autonomy-level
description: Use at task start to set how much a bot may do alone.
---
# Autonomy level

## When to Use
- Use at the start of any task, alongside `ask-once-then-finish`, to know how much of
  the work you may do without stopping to ask.

Every bot's default is level 2 below. A human can set a different level for one task,
one agent going forward, or a whole project. The level in force is always the most
specific one set: task line > agent's own `.agent.md` > project `AGENTS.md` > this
default.

## The levels
1. **Ask every step.** Propose each action before doing it, including reversible ones.
   Wait for a yes each time. Use for a new, high-stakes, or trust-building task.
2. **Ask only about: `<list>`.** Work straight through everything else. The kit default
   list, when no human has named their own, is: costs money, can't be undone, or goes
   out under the human's name (emails, posts, messages, commits as them). A human may
   replace this list with their own named items (e.g. "ask me about anything touching
   the billing table, nothing else").
3. **Never ask, just do it.** Work straight through, including money, irreversible
   steps, and anything sent under the human's name. No stop, ever, for this task or
   agent.

## Steps
1. Find the level in force (task line, then agent file, then project `AGENTS.md`, then
   level 2 default). Keep this to yourself when it's the default — don't tell the human
   which level you're working at unless it changed what you'd normally do (you skipped a
   question you'd usually ask, or stopped for something you'd normally not), or they ask.
2. At level 1, turn every action in your plan into a question before doing it.
3. At level 2, follow `ask-once-then-finish` as written, stopping only for the items on
   the level-in-force list.
4. At level 3, do not stop for anything on that list either. Still record what you did
   and why in the cycle's `decisions.md` — level 3 removes the question, not the paper
   trail.
5. A human raises or lowers the level mid-task: that's a new question, always answer it
   (changing your own autonomy is never something you decide for yourself).

## Rules
- Level 3 is granted per task or per agent by name, in plain chat or `decisions.md`,
  never assumed from silence or from "they seemed busy."
- Never grant yourself level 3. Only a human sets it, and only for named scope — "just
  do it" for one task is not "just do it" forever, unless they say so explicitly.
- A new agent's default is always level 2 (`agent-builder` sets this); never ship a new
  agent defaulting to level 3.
- When unsure which level applies, use the more cautious one and say why.
