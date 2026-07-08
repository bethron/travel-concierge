# Connectors

WanderPlan is built around official, publicly available travel connectors.
They are declared in `.mcp.json` and matched by name to Claude's connector
directory — on first use each service will ask you to authorise it.

## Connectors used by this plugin

| Category | Included connectors | Used by skills | Notes |
|---|---|---|---|
| Flights | Kiwi.com, Ryanair | `find-flights` | Kiwi.com covers worldwide routes; Ryanair adds budget European routes and cheapest-per-day search |
| Stays | Booking.com, Super.com | `find-stays` | Booking.com is the primary search (incl. property Q&A); Super.com benchmarks prices |
| Activities | Veltra Activities, Super.com | `find-activities` | Veltra for tours and experiences; Super.com for city attractions and tickets |

## Alternatives

The skills describe workflows, not hard product dependencies. If you prefer
different providers (e.g. Turkish Airlines for flights), connect them in
Claude and mention them in conversation — the skills will use whatever
relevant travel connectors are available, falling back to web search (with an
"estimates only" caveat) when none are connected.

## Privacy

Bookings are always completed on the provider's own website. WanderPlan never
stores payment details or passport numbers in its files.
