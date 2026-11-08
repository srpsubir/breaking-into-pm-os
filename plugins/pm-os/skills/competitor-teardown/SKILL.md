---
name: competitor-teardown
description: Compare 2 to 5 products side by side using Product Hunt data and their own websites. Use when the user names competitors or wants to know how similar products differ.
---

# Competitor teardown

Goal: show how a few products differ, using facts.

## Steps

1. Ask which products to compare. If they give a category instead, run `scan-category` first and let them pick.
2. For each product, get its Product Hunt record:

```
curl -s https://api.producthunt.com/v2/api/graphql \
  -H "Authorization: Bearer $PRODUCT_HUNT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ post(slug: \"SLUG\") { name tagline description votesCount commentsCount website createdAt topics { edges { node { name } } } } }"}'
```

3. Read each product's own website (home page and pricing page) with a web fetch tool.

## Output

Short and plain. No tables unless the user asks.

1. One paragraph per product: who it is for, the main promise, the price.
2. Where they overlap.
3. Where they differ.
4. A gap that none of them cover, if the data shows one.

Cite where each fact came from. If you could not find something, say so.
