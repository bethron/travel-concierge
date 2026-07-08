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
- **Otto Travel** — a further live-inventory search source with the
  traveller's stored preferences and hotel loyalty numbers. Search only:
  never place a booking through it.

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

- Save the comparison table to `options/stays-<date>.md` for the savings
  summary (`expense-report` skill).
- Record the chosen stay (property, dates, rate, cancellation terms, link) in
  `trip-brief.md`; log the cost in `budget.md`.
- Note check-in/check-out times for the itinerary's first and last days.
- Link out for the actual booking — Travel Concierge is search-only by
  design and never books or takes payment in-chat. Record the details in
  `trip-brief.md` once the traveller confirms they have booked.

## Care points

- State totals including nights count; make clear if taxes/fees are excluded.
- Use the connectors' ratings and facts; do not invent amenities — verify via
  Booking.com property Q&A when the traveller asks details.
