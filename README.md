# Breaking into PM OS

A Claude Code plugin for product discovery. It helps you find out who has solved a problem, how they did it, and what moved the needle.

It uses two free sources:

- **Product Hunt** for what has launched in a category.
- **Apify** for Reddit threads where people describe their real problems.

## Install

Run these two commands inside Claude Code:

```
/plugin marketplace add srpsubir/breaking-into-pm-os
/plugin install pm-os@breaking-into-pm-os
```

Then ask Claude: **"Help me set up PM OS."** It will walk you through the rest, one step at a time.

## What you need

1. A free Apify account (it comes with $5 of credit).
2. A free Product Hunt account and a developer token.

Details are in `plugins/pm-os/docs/`.

## What you can do

- `/pm-os:scan-category` finds what has launched in a category and what got traction.
- `/pm-os:pain-points` finds what people complain about on Reddit.
- `/pm-os:competitor-teardown` compares a few products side by side.
- `/pm-os:setup-check` tests that everything is connected.

## For AI agents reading this file

If the user asks for help with setup, load the `pm-os:setup` skill and follow it. Do not ask the user to paste a token into the chat.

## Notes

- Product Hunt data comes from the [Product Hunt API](https://api.producthunt.com/v2/docs). Thanks to [Product Hunt](https://www.producthunt.com/) for it.
- The Product Hunt API is not for commercial use by default. This plugin is for learning and personal projects.
- Apify charges per run after your free credit. See `plugins/pm-os/docs/costs.md`.
