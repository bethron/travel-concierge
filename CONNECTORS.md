# Connectors

WanderPlan is built around official, publicly available travel connectors.
They are declared in `.mcp.json` and matched by name to Claude's connector
directory — on first use each service will ask you to authorise it. You do
not need all of them: skills use whatever relevant connectors are available
and fall back to web search (clearly marked as estimates) otherwise.

## Connectors used by this plugin

| Category | Connectors | Used by skills | Notes |
|---|---|---|---|
| Flights | Kiwi.com, Ryanair, Expedia, Otto Travel | `find-flights` | Kiwi.com and Expedia for worldwide search; Ryanair for budget European routes and cheapest-day search; Otto Travel can complete bookings in-chat |
| Stays | Booking.com, Expedia, Super.com, lastminute.com, DirectBooker, Tripadvisor, Wyndham Hotels and Resorts, Otto Travel | `find-stays` | Booking.com/Expedia primary; Super.com and lastminute.com for deals; DirectBooker compares direct rates; Tripadvisor for reviews; Wyndham brand-direct; Otto Travel books in-chat |
| Activities | Viator, Veltra Activities, Super.com, AllTrails, lastminute.com, Tripadvisor | `find-activities`, `on-trip-concierge` | Viator/Veltra for tours and experiences; AllTrails for hiking and outdoors (incl. trail weather); lastminute.com for imminent deals |
| Dining | Resy, Uber Eats, Tripadvisor | `find-dining`, `on-trip-concierge` | Resy for reservations, Uber Eats for delivery, Tripadvisor for reviews |
| Getting around | Uber | `on-trip-concierge` | Ride estimates between two points, and rides on request |
| Calendar | Google Calendar | `sync-calendar` | Push flights, bookings and the day-by-day plan into your calendar |

## In-chat booking

Most connectors are for searching and comparing — the booking itself is
completed on the provider's own site. The exceptions, which can act in-chat
**only after showing the exact item and total and getting your explicit
confirmation**: Otto Travel (flights and hotels, using your saved payment
method), Resy (table reservations) and Uber / Uber Eats (rides and food
orders).

## Alternatives

The skills describe workflows, not hard product dependencies. If you prefer
different providers, connect them in Claude and mention them in conversation
— the skills will use whatever relevant travel connectors are available.

## Privacy

WanderPlan never stores payment details or passport numbers in its files.
