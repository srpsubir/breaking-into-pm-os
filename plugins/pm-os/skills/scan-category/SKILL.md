---
name: scan-category
description: Scan Product Hunt for products launched in a category and explain what got traction. Use when the user wants to see who has solved a problem, what launched in a space, or what the leading products do.
---

# Scan a category on Product Hunt

Goal: show who has launched in a category, how they pitched it, and what seems to have moved the needle.

## Inputs

Ask for the category or problem in the user's words. Ask for a time window if they did not give one (default: the last 12 months).

## Steps

1. Find the topic slug. Query topics with the user's words:

```
curl -s https://api.producthunt.com/v2/api/graphql \
  -H "Authorization: Bearer $PRODUCT_HUNT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ topics(first: 10, query: \"KEYWORD\") { edges { node { name slug } } } }"}'
```

2. Pull the top launches in that topic by votes:

```
curl -s https://api.producthunt.com/v2/api/graphql \
  -H "Authorization: Bearer $PRODUCT_HUNT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ posts(first: 20, order: VOTES, topic: \"SLUG\", postedAfter: \"2025-11-01T00:00:00Z\") { edges { node { name tagline description votesCount commentsCount website url createdAt } } } }"}'
```

Replace KEYWORD and SLUG. Set `postedAfter` from the time window.

3. If a call returns errors, show the error message and stop. Do not guess at data.

## Output

Keep it short and plain.

1. The 5 to 8 most relevant launches: name, one line on what it does, votes, comments.
2. Patterns across them: what problem each solves, who it is for, how they position it.
3. What seems to have moved the needle. Only claim what the data shows (votes, comments, tagline). Say when something cannot be determined from the data.
4. Gaps: what the list does not cover.

End with: "Data from Product Hunt (producthunt.com)."
