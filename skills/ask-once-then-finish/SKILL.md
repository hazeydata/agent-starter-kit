---
name: ask-once-then-finish
description: Use at the start of any task to ask once, then finish.
---
# Ask once, then finish

## When to Use
- Use at the start of any task from a human or another agent, to gather what you need in one round and then work until done.

Gather everything in one round of questions, then work without stopping until the outcome is live.

## Steps
1. **Plan the whole job first.** List everything you need to finish without stopping. Answer what you can yourself from context, files, memory, or a sensible default. State each default in one line instead of asking.
2. **Ask only what's left, all at once, in one message.** Each question must be one only the requester can answer. Ask in plain chat, then end your turn. A pop-up or question tool may not reach the human, and silence is never a yes.
   - Known options: use multiple choice. Add "Other" for typed detail only when the list may be incomplete.
   - Open answer (a link, a name): ask a plain question.
3. **Once answered, work until done.** Stop per the level set in `autonomy-level` (default: an action that costs money, can't be undone, or goes out under the human's name). At level 3 ("never ask"), nothing in this step stops you.
4. **New question mid-work?** If it's not on the autonomy-level stop-list, pick the safe choice, note it, and keep going. Otherwise stop and ask that one question.
5. **Agent to agent.** The sender writes one self-contained brief (see `handoff-brief`). The receiver replies once with all its questions, or none, then works until done and reports the live outcome plus a leftover count.

## Anti-patterns
- Dribbling questions one at a time.
- Asking what you could decide.
- Asking permission for reversible steps.
- Stopping at "acknowledged".

## Example (test walk-through)
Ask: "Set up a weekly status report for `<project>`."
1. Plan: needs a source, a format, a day and time, an audience, and a place to save it. From context: source = the newest cycle's `summary.md`. Defaults: "Format: one page, matching summary.md headings." "Saved to: `cycles/<current>/reports/`."
2. One message:
   - "Which day? (a) Monday (b) Friday"
   - "Who reads it? (a) just you (b) the team (c) Other: ___"
   - "What time should it run?"
3. Answers come back: Friday, the team, 9:00. Build the report and the schedule, then run it once as a test.
4. Mid-work: the reports folder doesn't exist. Creating it is reversible, so create it, note it, and continue.
5. Mailing the team goes out under the human's name, so stop and ask once: "Send the first report to the team now? (yes / no)"
6. Report: the live report link, the schedule, "Leftovers: 0".
