# Connectors

Travel Concierge is built around official, publicly available travel connectors.
They are declared in `.mcp.json` and matched by name to Claude's connector
directory — on first use each service will ask you to authorise it. You do
not need all of them: skills use whatever relevant connectors are available
and fall back to web search (clearly marked as estimates) otherwise.

## Connectors used by this plugin

| Category | Connectors | Used by skills | Notes |
|---|---|---|---|
| Flights | Kiwi.com, Ryanair, Expedia, Otto Travel, Turkish Airlines | `find-flights` | Kiwi.com and Expedia for worldwide search; Ryanair for budget European routes; Turkish Airlines for brand-direct search and routes via Istanbul; Otto Travel adds live inventory plus stored preferences and loyalty numbers (search only) |
| Stays | Booking.com, Expedia, Super.com, lastminute.com, DirectBooker, Tripadvisor, Wyndham Hotels and Resorts, Otto Travel | `find-stays` | Booking.com/Expedia primary; Super.com and lastminute.com for deals; DirectBooker compares direct rates; Tripadvisor for reviews; Wyndham brand-direct; Otto Travel adds live inventory and loyalty numbers (search only) |
| Activities | Viator, Veltra Activities, Super.com, AllTrails, lastminute.com, Tripadvisor | `find-activities`, `on-trip-concierge` | Viator/Veltra for tours and experiences; AllTrails for hiking and outdoors (incl. trail weather); lastminute.com for imminent deals |
| Dining | Resy, Uber Eats, Tripadvisor | `find-dining`, `on-trip-concierge` | Resy for reservations, Uber Eats for delivery, Tripadvisor for reviews |
| Getting around | Uber | `on-trip-concierge` | Ride estimates between two points, and rides on request |
| Calendar | Google Calendar | `sync-calendar` | Push flights, bookings and the day-by-day plan into your calendar |

## Search-only by design

Travel Concierge **never spends money in-chat**. Every connector is used for
searching, comparing, checking availability and estimating — the booking,
reservation, ride or order itself is always completed by you on the
provider's own site or app, which the plugin links you to. This is a
deliberate trust posture for a public plugin: no conversational click can
ever charge a payment method. Even connectors technically capable of acting
(Otto Travel, Resy, Uber, Uber Eats) are used in search-only mode.

## Alternatives

The skills describe workflows, not hard product dependencies. If you prefer
different providers, connect them in Claude and mention them in conversation
— the skills will use whatever relevant travel connectors are available.

## Privacy

Travel Concierge never stores payment details or passport numbers in its files.
