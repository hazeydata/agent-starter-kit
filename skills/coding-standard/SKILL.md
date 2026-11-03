---
name: coding-standard
description: Use when making any code change.
---
# Coding standard

## When to Use
- Use when making any code change, to keep the work focused, planned, verified, and small.

Inspired by poteto's pstack / poteto-mode. This is a short adaptation, not a copy.

## Steps
1. **One job.** Restate the change in one line. If it takes "and", split it.
2. **Plan before code.** List the files you will touch and how you'll verify. For anything non-trivial, sketch types and signatures first.
3. **Fix root causes.** Trace the symptom to its cause before patching.
4. **Verify before done.** Run the tests, the build, or the actual behaviour. Paste the evidence. "Should work" is not done.
5. **Small PRs.** One concern per PR. Docs change in the same PR as the code.

## Replies
- Short and plain. Lead with the result.
- Unslopped: no filler, no hype, no restating the question, no "I hope this helps".
- Say what you didn't do or weren't sure about.

## Rules
- Subtract before you add: delete dead code before writing new code.
- Match the repo's existing style and tools.
- No secrets, no files over 1 MB, no personal data in commits.
