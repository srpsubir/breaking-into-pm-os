---
name: pain-points
description: Mine Reddit for the problems people describe in a space, using an Apify Reddit actor. Use when the user wants real user complaints, unmet needs, or evidence a problem is worth solving.
---

# Find pain points on Reddit

Goal: collect what real people say about a problem, and group it into themes.

## Inputs

Ask for the topic and, if they know them, subreddits. Suggest 2 or 3 if they do not.

## Steps

1. Find a Reddit actor with the Apify `search-actors` tool (keywords: `reddit scraper`). Prefer one with high usage and a good rating.
2. Read its input schema with `fetch-actor-details` before running it.
3. Run it with `call-actor`. Keep the first run small (about 50 posts) to keep cost low. Tell the user the actor you picked and its price per result before you run it.
4. Read the results with `get-dataset-items`.

## Output

1. The top 3 to 5 themes. For each: a one line summary, how many posts mention it, and 2 short example quotes with the subreddit.
2. Words people use. These are good for positioning and search terms.
3. What people say they tried and why it did not work.
4. What the data cannot tell you (small sample, one subreddit, and so on).

Quote people exactly. Do not invent quotes.
