---
name: skill-or-bot
description: Use when an ask may need a new or changed agent or skill.
---
# Skill or bot

## When to Use
- Use when a chat ask might need a new agent, a new skill, or a change to an existing one, to decide which and who acts on it.

A skill is a method: how to do one thing well. Any agent can load it, and it's plain markdown, so it works in any AI tool. An agent is an owner: it has its own memory, schedule, voice, or boundary.

## 1. Sort the ask
Pick exactly one:
- Quick ask: answer or do it now. Stop here.
- Routine work for an existing agent: hand it to that agent.
- Change to an existing agent or skill: an agent should act differently, or a skill is wrong, stale, or missing a step.
Before calling anything a new capability, list the installed skills and grep their names and descriptions for the ask's keywords (e.g. "CTA", "button"). If a skill matches, it is routine work or a change, not new. If it already covers the ask as is, say so, point to it, and stop: a complete outcome with 0 leftovers.
- New capability: no agent or skill owns or describes it yet.
Repeat signal: if the same kind of ask has come up 2-3 times and is handled by hand each time, treat it as a new capability even if each instance looked quick.

## 2. New capability: skill or agent?
Make an agent only if at least one is true:
1. It must remember things across days (its own memory or open loops).
2. It must wake on its own (schedule or event trigger) (only if your harness supports it).
3. It must be kept apart (its own voice, inbox, permission or boundary, e.g. the only one that may send email or spend).
4. It owns a standard that must stay consistent across many requesters.
Otherwise make a skill, and say which existing agents should load it. Prefer a skill when in doubt: it's cheaper, portable, and can be promoted to an agent later. Never make an agent that's just one method with no memory, schedule, or boundary.

## 3. Change: which file?
- How an agent behaves (job, anti-jobs, voice, wake) goes in its `.agent.md` file.
- How a task is done goes in a skill. If several agents would need the same fix, it belongs in a skill, not in each `.agent.md` file.

## 4. Who acts
- The agent that got the ask runs steps 1-3 and states its call in one line with the reason.
- It does not create or edit agents or skills itself unless that's its job. It hands the call to bot-maker with a self-contained brief: the ask, the call, the evidence, and the proposed home.
- The human approves any new agent or new skill before it's created. Ask in plain chat and wait; no answer means no.
