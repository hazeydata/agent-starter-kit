---
name: ask-once-then-finish
description: Use at the start of any task to ask everything, one item at a time.
---
# Ask once, then finish

## When to Use
- Use at the start of any task from a human or another agent, to gather every gap before you start work, then work without stopping until done.

Gather everything up front, before any work starts — but one item per message, not a bundle.

## Steps
1. **Plan the whole job first.** List everything you need to finish without stopping. Answer what you can yourself from context, files, memory, or a sensible default. State each default in one line instead of asking.
2. **Ask only what's left, one item per message, before starting work.** Send one question, end your turn, and wait for the reply. Then send the next. Repeat until every gap from step 1 is answered — don't open work until all of them are in. Each question:
   - Known options: use clickable choices (real buttons/cards when the harness supports them; numbered text with "Other" only when it doesn't). Never fall back to numbered text if a native choice UI is available — check for it, don't default past it.
   - Open answer (a link, a name): ask a plain question.
3. **Once answered, work until done.** Stop per the level set in `autonomy-level` (default: an action that costs money, can't be undone, or goes out under the human's name). At level 3 ("never ask"), nothing in this step stops you.
4. **New question mid-work?** If it's not on the autonomy-level stop-list, pick the safe choice, note it, and keep going. Otherwise stop and ask that one question.
5. **Agent to agent.** The sender writes one self-contained brief (see `handoff-brief`). The receiver asks its questions the same way — one item per message, wait for each reply — then works until done and reports the live outcome plus a leftover count.

## Anti-patterns
- Bundling every question into one message.
- Asking what you could decide.
- Asking permission for reversible steps.
- Stopping at "acknowledged".
- Falling back to numbered text when the harness has real clickable choices.

## Example (test walk-through)
Ask: "Set up a weekly status report for `<project>`."
1. Plan: needs a source, a format, a day and time, an audience, and a place to save it. From context: source = the newest cycle's `summary.md`. Defaults: "Format: one page, matching summary.md headings." "Saved to: `cycles/<current>/reports/`."
2. Three separate turns, each waiting for a reply before the next:
   - Turn 1: "Which day? (a) Monday (b) Friday" → wait.
   - Turn 2 (after "Friday"): "Who reads it? (a) just you (b) the team (c) Other: ___" → wait.
   - Turn 3 (after "the team"): "What time should it run?" → wait.
3. Answers come back one at a time: Friday, the team, 9:00. Build the report and the schedule, then run it once as a test.
4. Mid-work: the reports folder doesn't exist. Creating it is reversible, so create it, note it, and continue.
5. Mailing the team goes out under the human's name, so stop and ask once: "Send the first report to the team now? (yes / no)"
6. Report: the live report link, the schedule, "Leftovers: 0".
