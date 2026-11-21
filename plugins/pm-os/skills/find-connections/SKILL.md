---
name: find-connections
description: Find the user's second-degree LinkedIn connections at a list of target companies, and who can introduce them, using Claude in Chrome in their own logged-in LinkedIn. Use for Module 3 "Build your network", or when the user wants warm paths into specific companies.
---

# Find second-degree connections at your target companies

Goal: for each target company, list people the user is two steps from, and name the first-degree contact who can introduce them. The user then chooses whom to approach.

This skill reads LinkedIn pages in the user's own browser session. It never sends messages, connection requests, or anything else. The user does all outreach.

## Before you start

1. Needs the Claude in Chrome extension, and Chrome open and signed in to LinkedIn. If the Chrome tools are not available, stop and tell the user. Point them to `docs/get-claude-in-chrome.md`. Do not try another route.
2. Ask for:
   - The companies (the list from the "pick your companies" step). Use 3 to 5 for a first run.
   - Optional: role keywords to prefer (for example "product", "design", "engineering manager"). Default is no filter.
3. Open a new tab for LinkedIn. Do not reuse the user's other tabs.

## Steps

For each company, one at a time:

1. Go to LinkedIn people search and search the company name. Use LinkedIn's own filters: Connections = 2nd, and Current company = the company. Choose the company from LinkedIn's suggestion list so you filter by the real company page and not by keyword. Add the role keywords if given.
2. Read the first page of results (about 10 people). For each person capture:
   - Name, headline, location, profile URL
   - The mutual-connection line LinkedIn shows (for example "Anna Schmidt and 4 other mutual connections")
3. The result card names only one or two mutual connections. For people you will list, open the "mutual connections" link to get the first-degree names, and take up to three. If LinkedIn does not show them, write "not shown". Do not guess.
4. Keep the pace human. Pause a few seconds between pages. Visit at most 15 profile or result pages per company. Do not paginate beyond page 2.
5. If LinkedIn shows a login wall, a verification check, or a warning about unusual activity: stop at once, tell the user, and do not continue or work around it.

## Output

A table, one row per person, grouped by company:

| Company | Person | Title | Degree | Who can introduce you | Profile link |
|---|---|---|---|---|---|

Then, per company:
- How many second-degree people you saw, and whether you hit the page cap (so the list may be partial).
- Outliers: someone with many mutual connections, someone senior with a single strong introducer, a company with no second-degree people at all.
- What is missing: people the search could not see, and anything marked "not shown".

Leave a blank column "Why you could add value" for the user to fill. Do not rank people or tell the user whom to pick. Do not write outreach messages here. The next lesson step covers that.

## Rules

- Read only. No messages, no connection requests, no endorsements, no follows.
- Use only what is on screen. Never invent names, titles or mutual connections.
- Do not scrape in bulk or leave the page cap. This is the user's own account and a small, user-led lookup.
- If the user asks for something LinkedIn's pages do not show, say so.
