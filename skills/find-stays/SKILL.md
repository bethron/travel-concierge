---
name: find-stays
description: >
  This skill should be used whenever the user wants somewhere to stay —
  phrases like "find a hotel", "where should we stay", "accommodation in",
  "book a room", "hotel prices in", "best area to stay", or when a trip plan
  reaches the accommodation stage. Also use it for comparisons ("this hotel
  or that one"), hotel questions ("does it have a pool?") and price checks
  for a specific property.
metadata:
  version: "0.1.0"
---

# Find Stays

Search live accommodation via the **Booking.com** and **Super.com** connectors
and recommend where to stay.

## Connector strategy

- **Booking.com** — primary search: widest inventory, filters, and property
  Q&A (use its property-questions tool for "does it have parking/a pool?"
  style follow-ups on searched properties).
- **Super.com** — price benchmark: check city-wide rates and the lowest price
  for shortlisted hotels; it often surfaces discounted rates. When both list
  the same property, show both prices.

Run both in parallel and deduplicate by property. If neither is available,
ask the user to enable them, then fall back to web search with an
"indicative prices" caveat.

## Inputs

Pull destination, firm dates (after flights), party composition, budget
remaining and style from `trip-brief.md`. Derive a sensible nightly budget
from the overall ceiling minus committed costs — say what range is being
searched.

## Neighbourhood first

For cities, briefly recommend 2–3 areas matched to the trip's emphasis
(sights / nightlife / quiet / family) before listing properties, one line
each. Search within the chosen area.

## Presenting results

Comparison table of 3–6 options:

| Property | Area | Rating | Room type | Cancellation | Per night | Total | Source |
|---|---|---|---|---|---|---|---|

Follow with one clear recommendation and why, plus one budget-saver and one
splurge alternative when the spread allows. Flag non-refundable rates, city
taxes not included, and locations far from the planned activities.

## After the choice

- Record the chosen stay (property, dates, rate, cancellation terms, link) in
  `trip-brief.md`; log the cost in `budget.md`.
- Note check-in/check-out times for the itinerary's first and last days.
- Link out for the actual booking — never claim it is booked.

## Care points

- State totals including nights count; make clear if taxes/fees are excluded.
- Use the connectors' ratings and facts; do not invent amenities — verify via
  Booking.com property Q&A when the traveller asks details.
