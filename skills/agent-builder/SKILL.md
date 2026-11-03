---
name: agent-builder
description: Use when writing or repairing a kit agent (.agent.md).
---
# Agent builder

## When to Use
- Use when `skill-or-bot` calls for a new agent, or an existing agent's job, voice, or
  boundary needs to change — never for a skill, `skill-builder` owns that shape.

## Shape
- Frontmatter: `name` and a one-line `description` of 60 characters or fewer. Only part
  loaded up front, so it says exactly what the agent owns.
- Body, in this order: **One job** (a single sentence). **Anti-jobs** (what it never
  does, and which other agent does it instead). **Voice**. **Wake** (what starts a run).
  **MUST load, every turn, before any other action:** the skills this agent needs,
  always including `autonomy-level` and `ask-once-then-finish`, each
  with when it applies. **Step 0**, written out in full, not a cross-reference: open
  every skill on that line every turn, no pre-filtering by the parenthetical hint or by
  guessing the skill doesn't apply — that call belongs to the skill's own When-to-Use
  text, seen only after opening it. Do this in reasoning, not the visible reply: never
  narrate which skills were opened or which category the ask fell into to the human —
  that's internal bookkeeping, and most agents' own Voice forbids this kind of filler.
  The
  agent MUST open and name every skill before step 1, every turn, no
  exception for an ask that looks simple or quick, and a skipped Step 0 makes the reply
  invalid even when the skip itself is invisible to the human. **## Steps**: numbered, imperative. **Follow-through rule**: what "done" means
  for this agent, as a leftover count.
- Never write "see the shared Hard rules" or point at README for the MUST/STOP framing —
  only the agent's own body ships into an installed persona (most harnesses expose no
  way to also ship README). Each agent must be able to enforce itself standalone, so
  write the MUST/Step 0 language directly into its body every time, in full.

## Steps
1. Check `skill-or-bot`'s 4 bot tests actually hold (memory, own wake, boundary, or a
   standard many requesters share). If none holds, this is a skill, not an agent — stop
   and hand it back as a skill job.
2. Write the one job and anti-jobs first; an agent whose anti-jobs are vague will drift
   into another agent's work.
3. List every skill this agent needs on its `MUST load` line, each with the "when" that
   triggers it. Write its Step 0 in full per the Shape section above.
4. Add it to the roster table in the kit's README (name, one job, never does).
5. Test it once on a real ask, unprompted — don't hint that it should open a skill.
   If it needs a reminder, Step 0's wording is the bug; fix the wording, not the agent's
   one-off behavior.
6. Note the test result in the PR description.

## Rules
- One job per agent; if you need "and", it's two agents or a skill plus an agent.
- Imperative voice, short sentences.
- Never add a new agent when a skill would do — skills are cheaper and portable.
- Improve the Step 0 wording after any real use that needed a reminder to open a skill.
- If a check (list, read, search) comes back the same twice in a row, stop checking and act on what you have. Repeating it hoping for a different answer is a stall, not caution.
