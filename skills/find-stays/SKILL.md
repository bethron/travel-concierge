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

Search live accommodation across the stay connectors and recommend where to
stay.

## Connector strategy

Primary search — run 2–3 of these in parallel and deduplicate by property:

- **Booking.com** — widest inventory, filters, and property Q&A (use its
  property-questions tool for "does it have parking/a pool?" follow-ups).
- **Expedia** — second broad search with strong filters.
- **Super.com** — price benchmark: city-wide rates and lowest price for
  shortlisted hotels; often surfaces discounted rates.
- **lastminute.com** — check when departure is close (within ~2 weeks) or the
  traveller wants a deal.

Price-check and enrich the shortlist:

- **DirectBooker** — resolve shortlisted hotels and compare the direct-booking
  rate; direct rates sometimes beat aggregators.
- **Tripadvisor** — reviews, rankings and hotel comparisons for the shortlist;
  use it when the traveller asks "which is actually nicer?"
- **Wyndham Hotels and Resorts** — brand-direct search and details when the
  traveller favours Wyndham brands or has their loyalty programme.
- **Otto Travel** — live bookable inventory; the one connector that can book
  a room in-chat with saved payment and loyalty numbers, after explicit
  confirmation.

When several sources list the same property, show each price with its source.
If no stay connector is available, ask the user to enable one, then fall back
to web search with an "indicative prices" caveat.

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
splurge alternative when the spread allows. For **business trips**, rank by
distance to the meeting venue first, then workspace, Wi-Fi and breakfast;
respect the policy cap from `trip-brief.md` and favour chains where the
traveller holds loyalty status (e.g. Wyndham brand-direct, or programmes
stored in Otto Travel). Flag non-refundable rates, city
taxes not included, and locations far from the planned activities.

## After the choice

- Record the chosen stay (property, dates, rate, cancellation terms, link) in
  `trip-brief.md`; log the cost in `budget.md`.
- Note check-in/check-out times for the itinerary's first and last days.
- Link out for the actual booking — or book in-chat via Otto Travel if the
  traveller asks, after confirming the exact room, rate, cancellation terms
  and total. Never claim anything else is booked.

## Care points

- State totals including nights count; make clear if taxes/fees are excluded.
- Use the connectors' ratings and facts; do not invent amenities — verify via
  Booking.com property Q&A when the traveller asks details.
