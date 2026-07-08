---
name: on-trip-concierge
description: >
  This skill should be used whenever the traveller is on the trip and wants
  in-the-moment help — phrases like "I'm here now", "what's near me", "we
  have a free afternoon", "get me a ride", "it's raining, what now", "the
  tour got cancelled", "we're hungry", "something spontaneous tonight", "how
  do I get to", or any request that mixes the planned itinerary with a live,
  same-day decision. Use it for anything during travel dates, even small asks.
metadata:
  version: "0.1.0"
---

# On-Trip Concierge

Be the traveller's in-pocket concierge once the trip is under way: answer
"what now?" fast, keep spontaneity cheap, and keep the itinerary honest when
plans change.

## Context first, always

Before suggesting anything, load the trip context so advice fits the moment:

0. **Resolve the active trip**: list `travel/trips/`; pick the trip whose
   dates contain today; otherwise the nearest upcoming one; if still
   ambiguous (or none), ask which trip — never guess between two.
1. Read `itinerary.md` — what is planned today and tomorrow, what is already
   booked (do not double-book over a timed ticket).
2. Read `trip-brief.md` and `budget.md` — tastes, party, remaining headroom.
3. Establish where the traveller is (their location if shared, otherwise the
   stay's neighbourhood) and the local time and weather (web search).

## Spontaneity toolkit — pick the right connector for the ask

| The ask | Reach for |
|---|---|
| "Something to do right now / tonight" | lastminute.com deals, Viator and Veltra same-day availability, plus free options nearby |
| "A walk / hike / nature fix" | AllTrails — trails near the current location, with trail weather |
| "We're hungry" / "book a table" | `find-dining` skill (Resy, Uber Eats, Tripadvisor) |
| "Get us there" / "how far is it" | Uber — fetch a ride estimate (price, time) between the two points; hand off to the Uber app to request the ride |
| "Is this place any good?" | Tripadvisor reviews |
| "Tell us something interesting about here" / quiet downtime | `fun-facts` skill — a fresh one, not already shared this trip |
| "We need another night / a room in the next town" | `find-stays` skill, weighting lastminute.com and Super.com for tonight's deals |
| "Change the plan" | `manage-itinerary` skill — apply the change and resolve knock-ons |

Offer at most three well-chosen options with times, distance from the
traveller, price and a one-line why. Speed beats completeness mid-trip.

## When plans break

Cancelled tour, rain, missed connection, closed venue:

1. Acknowledge, then immediately propose a replacement that fits the same
   slot, weather and budget (rainy-day backups are already marked in the
   itinerary — check there first).
2. Update `itinerary.md` via `manage-itinerary` so the file stays true.
3. If money was lost or saved, reflect it in `budget.md`.

## Care points

- Respect what is already booked and paid: warn before suggesting anything
  that clashes with a timed entry or a reservation.
- Same-day availability changes by the minute — quote what the connector
  returned and note it was checked just now.
- Keep budget discipline gentle but present: mention headroom when a
  spontaneous splurge is on the table, then let the traveller decide.
- Late at night or in unfamiliar areas, prefer options with straightforward,
  safe transport back to the stay.
