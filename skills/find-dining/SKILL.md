---
name: find-dining
description: >
  This skill should be used whenever food is the question — phrases like
  "where should we eat", "book a table", "restaurant near", "best food in",
  "we're hungry", "order food to the hotel", "dinner reservation", "is this
  restaurant good", whether while planning the trip or in the middle of it.
metadata:
  version: "0.1.0"
---

# Find Dining

Handle everything food: recommendations, table reservations and delivery to
the door — tuned to the trip's tastes, location and budget.

## Connector strategy

- **Resy** — restaurant discovery and table reservations. First stop for
  "book a table" and for finding notable restaurants with real availability
  for the party size, date and time.
- **Tripadvisor** — reviews and rankings to sense-check or discover
  restaurants, and to answer "is it any good?"
- **Uber Eats** — delivery: search restaurants, cuisines and menu items
  deliverable to the stay. The answer for tired-after-a-long-day evenings,
  room picnics and "we just landed and everything nearby is shut".
- Complement with web search for local institutions, markets and street food
  that no platform lists.

## Inputs

Pull dietary needs from the traveller profile (treat these as hard
constraints, never suggestions), cuisine loves/avoids and budget style from
`trip-brief.md`, and location plus timing from today's `itinerary.md` entry —
recommend near where the traveller will actually be at meal time, not near
the hotel by default.

## Presenting options

Two or three options, each one line: name — cuisine and signature dish —
distance from where they'll be — price band — why this one. For
reservations, state real availability from Resy before recommending a time.

## Acting

- **Reserve**: confirm party size, date, time and any occasion, then make the
  Resy booking and record it in `itinerary.md` with a 🎟 booked marker.
- **Deliver**: confirm the delivery address (the stay, from `trip-brief.md`,
  unless told otherwise) before initiating any Uber Eats order, and show the
  order total before it is placed.
- Log notable meal spends against the food estimate in `budget.md`.

## Care points

- Dietary requirements are non-negotiable filters — verify the venue can
  cater to them rather than assuming.
- Mention dress codes or long waits when the source flags them.
- For planning-stage requests, pencil suggestions into the itinerary as 💡
  rather than booking weeks of dinners nobody asked for.
