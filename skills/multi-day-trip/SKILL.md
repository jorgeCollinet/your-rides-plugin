---
name: multi-day-trip
description: Plan a multi-day or longer-than-300-km motorbike trip with Your Rides by splitting it into daily legs, each planned and saved as its own route. Use when the rider asks for a weekend trip, a tour, a trip over several days, or any route longer than 300 km.
---

# Plan a multi-day motorbike trip

Your Rides plans routes of up to 300 km each, so a tour is a chain of daily legs.

1. **Agree the frame:** number of days, rough daily riding time (4–6 h is a comfortable
   touring day), start and end (same place for a round tour, or one-way), and the region.
2. **Call `get_rider_context`** for Home and the coverage limits.
3. **Sketch the overnight stops first.** Pick towns roughly one riding day apart that make
   good overnight bases, and geocode each with `geocode_place`. Share the sketch
   (Day 1: A → B, ~220 km …) before planning every leg in detail.
4. **Plan each leg with `plan_route`** — that day's start and overnight stop, plus scenic
   anchors in between (passes, lakes, castles; avoid big cities). Keep each leg under
   300 km and within the agreed riding time; re-plan legs that run long.
5. **Present the trip day by day:** distance, riding time, highlights and a break every
   1.5–2 hours. Keep it compact.
6. **Save only on explicit request.** When the rider asks, save each leg with
   `save_route` as its own route, named so they sort together, e.g.
   "Alps tour — Day 1: Munich → Innsbruck". Confirm the names before saving several.

Outside Germany, Austria and the Czech Republic a fallback engine serves; if a leg fails
there, say so plainly and propose a covered alternative.
