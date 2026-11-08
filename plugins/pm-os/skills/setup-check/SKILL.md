---
name: setup-check
description: Test that Apify and Product Hunt are connected for PM OS and report what is missing. Use after setup or when a PM OS skill fails.
---

# PM OS setup check

Run both checks. Report each as pass or fail in one line. Do not print any token.

## Product Hunt

Run:

```
curl -s -o /dev/null -w "%{http_code}" https://api.producthunt.com/v2/api/graphql \
  -H "Authorization: Bearer $PRODUCT_HUNT_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query":"{ posts(first: 1) { edges { node { name } } } }"}'
```

- `200`: pass.
- `401` or `403`: the token is wrong or expired. Send them to the `setup` skill, Step 2.
- `000` or empty: no network, or the token variable is not set.

## Apify

Call the Apify `search-actors` tool with the keyword `reddit` and limit 1.

- A result comes back: pass.
- An authentication error: send them to the `setup` skill, Step 1.

## Finish

If both pass, say "PM OS is ready" and suggest one first thing to try, like scanning a category they care about.
