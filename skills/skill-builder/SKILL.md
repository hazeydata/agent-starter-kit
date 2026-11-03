---
name: skill-builder
description: Use when writing or refining a skill.
---
# Skill builder

## When to Use
- Use when writing a new skill or refining an existing one, so it stays short, generic, and tested.

## Shape
- Frontmatter: `name` and a one-line `description` of 60 characters or fewer, in quotes if it contains a colon. It is the only part loaded up front, so it says exactly when the skill applies.
- Body: about 60 lines, with a `## When to Use` section, then numbered steps, then rules.
- If the harness's own skill lint is stricter, follow it.
- Frontmatter stays portable: `name` and `description` only. Treat a harness's warnings about extra fields as advisory; never add harness-specific fields to kit skills.

## Steps
1. List every skill this team has, once — one pass, not a repeated check. Scan that one list for a name or description that covers this ask. One does? Say which, edit it or skip, and stop: done, no new skill needed. Nothing covers it and it will be used more than once? Continue to step 2. Never re-list or re-read the same skills a second time to double-check — one pass is enough to decide either way.
2. Write the when-to-use line first. If you can't write it in one sentence, the skill does two jobs; split it.
3. Write generic steps: name capabilities ("open a PR", "read the file"), not a vendor's tool names.
4. Strip private details: no names, emails, tokens, internal URLs, client or employer data. Use placeholders like `<project>`.
5. Save it the way this harness actually saves a skill — a file in a repo, a "new skill" action, a "save as skill" prompt, whatever it exposes. Don't assume a raw file write is the only option; check what the harness offers before picking one.
6. Test it once on a real ask. Fix whatever step the agent got wrong.
7. Note the test result in the PR description (or the save, if there's no PR).

## Rules
- One skill, one use.
- Imperative voice, short sentences. Smaller models follow these better.
- Link to other skills instead of copying them.
- Improve the skill after each real use that exposes a gap.
- Cut before you add: when refining, remove or merge an old line before adding a new one.
- If a check (list, read, search) comes back the same twice in a row, stop checking and act on what you have. Repeating it hoping for a different answer is a stall, not caution.
