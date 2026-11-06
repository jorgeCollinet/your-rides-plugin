---
name: plan-motorbike-route
description: Plan an enjoyable motorbike ride with the Your Rides tools — a curvy A→B route or a round-trip loop from home, sized to a time or distance budget, shown on an interactive map and saved to the rider's account on request. Use when the rider asks for a ride, a loop, a route to somewhere, or "where should I ride today". Motorbikes only — do not use for bicycle, walking or car routes.
---

# Plan a motorbike route with Your Rides

Work generate-and-test: pick candidate places, geocode them, run them through the
routing engine, keep what flows, and show the result on the map.

## 1. Understand the ask

- Clarify only what is genuinely ambiguous — usually the budget (hours or km) and the
  vibe (twisty mountain roads vs relaxed scenic cruise). Ask one short question, not a form.
- Call `get_rider_context` once at the start. Use the rider's **Home** as the default start
  unless they name another one, and respect the returned limits.
- Time budget → distance: on curvy back roads assume roughly 50–60 km/h moving average,
  so 3 hours ≈ 150–180 km. Check against the engine's duration, not your estimate.

## 2. Choose anchor points

- **Scenic anchors, not big cities.** Passes, ridge roads, lakes and reservoirs, castles,
  river valleys and small villages keep the route on enjoyable roads; cities pull it onto
  arterials.
- **Every point comes from `geocode_place`.** Never invent or guess coordinates.
- Plan a meaningful break every 1.5–2 hours of riding (café, viewpoint, fuel), not random pins.

## 3. Validate with the engine

- A→B: `plan_route` with origin, destination and ordered waypoints.
- Loop: `plan_round_trip` with a start and `length_km`; use `direction_deg` to head
  towards the scenery and `seed` for an alternative loop.
- Preferences: `curviness` 0–100 (100 = twistiest), `avoid_motorways` (on by default for
  riders), `avoid_tolls`.
- Never present a route you have not run through the engine. If it backtracks, flows
  awkwardly or misses the budget by more than ~15 %, drop, add or reorder anchors and re-plan.
- **Limits:** max 300 km per route — plan longer trips one leg per route (see the
  `multi-day-trip` skill). Best coverage is Germany, Austria and the Czech Republic;
  elsewhere a fallback engine serves and loops over ~100 km may fail. If a point is out of
  coverage, say so and suggest the nearest covered area.

## 4. Present it

- The map appears with the route; in the chat give a compact list of stops with one
  reason each, plus total distance and riding time. State trade-offs plainly
  ("+12 min for the lake road").
- Briefly explain how you chose the stops — it invites correction.
- Use place names, never raw coordinates or GeoJSON.
- Mention that the map has controls (curviness, motorways, tolls, stops, loop length)
  and a **Plan again** button, so the rider can tweak it directly.
- Refine iteratively: "twistier", "shorter", "add a lunch stop" modify the current plan
  rather than starting over.

## 5. Saving

- `save_route` is the only tool that changes anything. Call it **only when the rider
  explicitly asks to save** ("save it", "keep this one").
- Save exactly what the rider is looking at: if they changed the route on the map, the
  latest stops and settings are in the conversation context — use those.
- If the map's Save button already saved it, do not save it again.
- After saving, tell them where to find it: phone app → Routes → the route name, ready
  for turn-by-turn navigation.

## Safety

- Mention darkness if the ride would end after sunset, and suggest a shorter variant.
- Don't promise road conditions, closures or legality of specific roads — suggest
  checking locally for passes that close seasonally.
