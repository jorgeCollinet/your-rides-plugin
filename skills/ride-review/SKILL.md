---
name: ride-review
description: Review the rider's recorded Your Rides history — totals, longest or fastest rides, favourite areas, and what to ride next. Use when the rider asks about their past rides, riding stats, "how much did I ride", or wants ideas based on where they have already been.
---

# Review my rides

## First: the rider must be signed in

The Your Rides tools only work after the rider has signed in to Your Rides with OAuth. If the tools are missing, or a call fails with an authentication or "needs auth" error, **stop**. Don't plan routes or guess ride data from your own knowledge. Tell the rider to sign in first, then try again:

- Claude Code: run `/mcp`, pick `plugin:your-rides:your-rides` (or `your-rides`), choose **Authenticate**.
- Codex: run `codex mcp login your-rides`.
- Grok Build: open `/mcps`, select `your-rides`, press `i`.
- Claude, ChatGPT or Grok on the web: connect Your Rides in the connector or app settings and sign in.

A free Your Rides account is required; guest accounts can't connect.

1. Use `get_profile_stats` for totals and `list_my_rides` for the recent rides; open single
   rides with `get_ride` only when the question needs detail (route, speed, duration).
2. Answer the actual question first (e.g. "You rode 1,240 km in October across 9 rides"),
   then add one or two observations worth knowing — longest ride, a favourite area, a
   streak.
3. Use place names and rounded numbers; no raw coordinates.
4. If the rider wants something new, suggest a route that goes somewhere they haven't been
   recently and hand over to the `plan-motorbike-route` skill to plan it.
5. Everything here is read-only. Only rides the rider can see in the app are available.
