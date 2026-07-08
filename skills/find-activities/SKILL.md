---
name: find-activities
description: >
  This skill should be used whenever the user wants things to do — phrases
  like "what should we do in", "activities in", "tours in", "day trips from",
  "tickets for", "experiences", "excursions", or when a trip plan reaches the
  activity-filling stage. Also use it for interest-led asks ("snorkelling
  near", "cooking class in", "something for kids in").
metadata:
  version: "0.1.0"
---

# Find Activities

Search bookable tours, tickets, experiences and trails across the activity
connectors, blend in free sights, and match everything to the traveller's
interests and pace.

## Connector strategy

- **Viator** — the broadest experiences catalogue: tours, tickets, day trips.
  A strong default alongside Veltra; fetch full details for anything
  shortlisted.
- **Veltra Activities** — keyword search for tours, classes, day trips and
  experiences. Search per interest ("food tour Kyoto", "snorkelling Bali"),
  not one generic query.
- **Super.com experiences** — city-level search for bookable attractions,
  tickets and day trips; good for headline sights and skip-the-line tickets.
- **AllTrails** — the specialist for anything outdoors: hiking, running and
  cycling trails near a location, trail details, and the trailhead weather
  forecast. Reach for it whenever the trip template is adventure/outdoors or
  the traveller mentions walking, hiking or nature.
- **lastminute.com** — check for experience deals when the trip is imminent
  or the traveller is already there.
- **Tripadvisor** — sense-check a shortlisted attraction's reputation when
  the traveller asks whether it is worth it.
- Run the relevant sources in parallel, deduplicate, and complement with web
  search for free or unbookable highlights (viewpoints, markets,
  neighbourhoods, beaches) so the plan is not purely commercial.

If neither connector is available, ask the user to enable them and continue
with web-search suggestions clearly marked as not live-bookable.

## Inputs

Pull interests, party (children's ages matter), pace and remaining budget
from `trip-brief.md`. Aim for a density that matches the pace: roughly one
booked activity per day for "balanced", two for "packed", every other day for
"downtime".

## Presenting results

Group by interest or by day slot, in a table:

| Activity | Type | Duration | Suits | Price (pp) | Source |
|---|---|---|---|---|---|

Mark free sights as **Free**. Recommend a shortlist that fits the days
available, and note anything needing advance booking or with limited
schedules.

## After the choice

- Slot each chosen activity into `itinerary.md` on a sensible day and time
  (respect opening hours, travel time, meal times, and rest after arrival).
- Record picks and prices in `trip-brief.md` and `budget.md`.
- Link to the provider for the actual booking.

## Care points

- Check seasonal availability — do not schedule an activity outside its
  operating season or hours as returned by the connector.
- Warn about weather-dependent activities and suggest a rainy-day backup.
- Keep at least one unscheduled block per day unless the pace is "packed".
