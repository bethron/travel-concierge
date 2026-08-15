---
name: trip-checklists
description: >
  This skill should be used whenever the user wants packing or preparation
  help — phrases like "packing list", "what should I pack", "what do I need
  before the trip", "pre-trip checklist", "don't let me forget", "do I need a
  visa/adapter", or proactively once an itinerary settles and departure
  approaches.
metadata:
  version: "0.1.0"
---

# Trip Checklists

Produce a tailored packing list and a pre-trip checklist, saved to
`travel/trips/<trip>/checklists/`.

## Packing list — `packing.md`

Tailor to the actual trip, not a generic template:

- **Weather**: use the `trip-weather` skill — a live forecast for travel
  dates within its horizon, seasonal norms beyond it — before writing the
  list.
- **Activities**: mine `itinerary.md` — hiking booked means boots; snorkelling
  means swimwear and reef-safe sunscreen; a smart dinner means one smart
  outfit.
- **Party**: children, medical needs and dietary kit from the traveller
  profile.
- **Trip length & bags**: match volume to the booked baggage allowance from
  `trip-brief.md`; warn if the list clearly exceeds a cabin-bag-only fare.

Use the base checklists in
`${CLAUDE_PLUGIN_ROOT}/skills/trip-checklists/references/packing-library.md`
as the starting point and prune/extend per the trip. Format as tick-box
markdown (`- [ ]`) grouped by category.

## Pre-trip checklist — `pre-trip.md`

Time-ordered, with deadlines where they exist:

- **Now**: passport validity (6 months rule where applicable), visa/ETA
  requirements for the traveller's nationality (verify with a web search —
  never guess), travel insurance, advance-booking deadlines from the
  itinerary notes.
- **2 weeks before**: online check-in windows, currency, prescriptions,
  vaccinations if relevant.
- **A few days before**: weather re-check via `trip-weather`, download
  offline maps, print or save tickets, arrange pet/plant/home cover.
- **Day before**: check in online, charge devices, confirm transfer times.

## Care points

- Visa and entry rules change and depend on nationality: state the
  traveller's nationality assumption, verify via search, and link an
  official source.
- Offer to add key deadlines to the user's reminders or calendar where the
  interface supports it — ask before creating anything.
