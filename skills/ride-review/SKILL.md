---
name: ride-review
description: Review the rider's recorded Your Rides history — totals, longest or fastest rides, favourite areas, and what to ride next. Use when the rider asks about their past rides, riding stats, "how much did I ride", or wants ideas based on where they have already been.
---

# Review my rides

1. Use `get_profile_stats` for totals and `list_my_rides` for the recent rides; open single
   rides with `get_ride` only when the question needs detail (route, speed, duration).
2. Answer the actual question first (e.g. "You rode 1,240 km in October across 9 rides"),
   then add one or two observations worth knowing — longest ride, a favourite area, a
   streak.
3. Use place names and rounded numbers; no raw coordinates.
4. If the rider wants something new, suggest a route that goes somewhere they haven't been
   recently and hand over to the `plan-motorbike-route` skill to plan it.
5. Everything here is read-only. Only rides the rider can see in the app are available.
