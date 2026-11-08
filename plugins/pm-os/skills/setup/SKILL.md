---
name: setup
description: Guide the user through setting up PM OS (Apify and Product Hunt). Use when the user asks to set up, install, configure or fix PM OS, or when setup-check reports something missing.
---

# PM OS setup

Walk the user through setup one step at a time. Short sentences. Wait for them to finish each step before you move on.

## Rules

- Never ask the user to paste a token into the chat.
- Never print a token back, even part of it.
- Ask what they already have before you start, so you skip finished steps.

## Step 1: Apify

1. Check if the Apify tools are available (search for tools whose names start with `mcp__plugin_pm-os_apify`). If they are, skip to Step 2.
2. If not, tell the user to run `/mcp`, pick the `apify` server from this plugin, and choose Authenticate. A browser window opens. They sign up or log in, then approve access.
3. Free accounts get $5 of credit. Point them to `docs/costs.md`.

## Step 2: Product Hunt token

1. Check if `PRODUCT_HUNT_TOKEN` is set. Run: `[ -n "$PRODUCT_HUNT_TOKEN" ] && echo set || echo missing`. Never echo the value.
2. If it is missing, give them the steps from `docs/get-product-hunt-token.md`.
3. Tell them to add this line to their shell profile (`~/.zshrc` on Mac), with their own token in place of the placeholder, then open a new terminal and start Claude Code again:

```
export PRODUCT_HUNT_TOKEN="paste-your-token-here"
```

The user types the real token into the file themselves. You do not see it.

## Step 3: Check

Run the `setup-check` skill. Tell the user what passed and what did not. Fix one problem at a time.
