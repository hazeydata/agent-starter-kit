---
name: three-line-report
description: Use when reporting a finished task or a stop.
---
# Three-line report

## When to Use
- Use whenever you report a finished task or a stop to a human or another agent.

Start every report with up to three short lines, so the reader can stop after them with confidence.

## Steps
1. **Result:** what you found, decided or finished, with a live link if there is one.
2. **Needs you:** anything to approve or decide.
3. **Unsure:** anything guessed or unverified.

## Rules
- Leave out Needs you or Unsure when there is nothing in it. Result is always there.
- If Result is the only line, drop the "Result:" label and write it as a plain sentence. Use labels only when there is more than one line.
- Put a blank line between the lines, for easy reading.
- Make every Needs you item clickable:
  - To approve: a markdown link straight to the exact thing (PR, file, card, page).
  - To decide: numbered options the human replies to with a number, or buttons if your harness has them. Always add an "Other" option for typed detail. Ask once, then finish (`ask-once-then-finish`).
- One line each. For several items, write a count ("3 decisions, see below") and list them below.
- Details go below these lines as optional reading. Never put anything critical only below the line.
- Use it whenever the reply hands back a finished result, even a quick one: a draft, a decision, a document, a fix. Skip it only for a plain factual answer with nothing to approve, nothing guessed, and nothing to follow up on (e.g. "it's Tuesday"). If the reply contains anything the human might need to approve, decide, or double-check, it is a report, not a quick answer, and needs this shape.
- Agent to agent: Result = outcome plus leftover count; Needs you = what the receiver must act on; Unsure = what to double-check.
- Never write SHIP or "done" for work that no separate quality-gate session reviewed. Put "not gated" under Unsure instead.
- Pairs with `ask-once-then-finish`: one round in, one glance out.

## Example
Ask: "Add a contact form to the `<project>` site."
```
Result: Contact form is live at <link>; leftovers: 0.

Needs you: 1 decision, see below.

Unsure: Spam filter tested with 2 fake submissions only.

Decision: where should form entries go? Reply with a number.
1. The shared inbox
2. A spreadsheet
3. Other (type it)
Details: 1 page changed, tests pass.
```
Nothing to approve and nothing unsure? Then the report is one plain sentence, no label:
```
Contact form is live at <link>; leftovers: 0.
```
