---
name: new-account-setup
description: Use when a task needs a brand-new account on an outside service.
---
# New account setup

## When to Use
- Use whenever a task requires creating a brand-new account on an external service (GitHub, Google, a SaaS tool, a messaging provider, etc.) — not when using or connecting an account that already exists.

## Rule
Any signup that can require a CAPTCHA, phone verification, or email verification from a fresh address almost always fails from a hosted sandbox: platforms' bot-detection flags datacenter IPs and blocks the signup, often before the form even loads. Don't attempt the signup first and fail; go straight to asking the human.

Before reaching for a brand-new account at all, check whether a native connector (OAuth to an existing account) covers the need instead — it's usually simpler and avoids this problem entirely. A new account is for when a separate identity is actually wanted (for example, a bot's actions attributed to the bot, not a person), not the default.

## Steps
1. Confirm a new account is actually needed, not just a connection to an existing one (`skill-or-bot` and the human's own call on identity).
2. If a new account is needed: ask the human to create it themselves, on their own device and network. Give them exactly what's needed: the username/account name to use, the email address, and what you'll need back (a password saved securely, a confirmation code, an API token, an invite accepted).
3. Once the human confirms the account exists, take over from there: use the invite, API key, OAuth token, etc. that the account yields.
4. Only attempt a signup directly yourself when the human explicitly says the service doesn't block sandboxed IPs, or after one attempt visibly fails for that reason — then don't retry here, go straight to step 2.

## Example
Needing a new GitHub account `hazeydata-rakazo` for a bot's own identity: ask the human to create it on their own device, confirm the username/email to use, and say what they'll hand back (an invite accepted, or a personal access token). Don't try the signup form here first.
