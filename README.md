# Travel Concierge ✈️

**A one-stop travel companion in a Claude plugin.** Travel Concierge plans complete
trips for individual travellers — leisure and business — flights, stays, activities and dining
searched live through official connectors, assembled into a day-by-day
itinerary you refine in chat — and then stays with you **during** the trip as
a concierge for spontaneous plans, rides, tables, delivery and last-minute
changes.

## What it does

**Before the trip**

- **Plan a whole trip** from a quick-start template (city break, beach,
  adventure, honeymoon, business trip…) plus a short interview — or just say
  "plan me a week in Lisbon".
- **Business travel** gets its own mode: meetings anchor the schedule,
  flights are picked for reliability and buffers, hotels for distance to the
  venue, loyalty programmes applied, calendar synced early, costs kept
  itemised for expenses — with an optional "bleisure" extension for the free
  days.
- **Search live prices** for flights (Kiwi.com, Expedia, Ryanair, Otto
  Travel), stays (Booking.com, Expedia, Super.com, lastminute.com,
  DirectBooker, Wyndham, Otto Travel) and activities (Viator, Veltra,
  Super.com, AllTrails), with clear side-by-side comparison tables and
  Tripadvisor reviews on tap.
- **Book must-have tables** via Resy, and — where you choose to — complete
  flight and hotel bookings in-chat via Otto Travel.
- **Build an interactive itinerary** you refine conversationally — "move the
  museum to Tuesday", "we land at 2pm now" — kept in a living file.
- **Track the budget** against your ceiling, with warnings before you
  overshoot; get tailored **packing lists** and pre-trip checklists.
- **Sync to Google Calendar** and **export** a polished Word or PDF itinerary.

**During the trip** (leisure or business)

- "We have a free afternoon — what's near us?" → same-day options from
  lastminute.com, Viator and Veltra, trails from AllTrails, all checked
  against what's already planned and the budget that's left.
- "Get us there" → Uber ride estimates and rides.
- "We're hungry" → a Resy table nearby, Tripadvisor-checked picks, or Uber
  Eats to the hotel door.
- "It's raining / the tour got cancelled" → an instant replacement that fits
  the slot, and the itinerary file updated to match reality.

## Skills

| Skill | Say things like |
|---|---|
| `plan-trip` | "Plan a week in Japan in October", "business trip to Berlin, meetings Tue–Wed" |
| `find-flights` | "Cheapest flights Manchester to Faro in June" |
| `find-stays` | "Find a hotel near the old town under £120 a night" |
| `find-activities` | "What should we do in Kyoto? We love food and hiking" |
| `find-dining` | "Book a table for two on Friday", "order food to the hotel" |
| `manage-itinerary` | "Swap day 2 and day 3", "show me the plan" |
| `on-trip-concierge` | "We're here and have a free evening — ideas?" |
| `trip-budget` | "Are we still under £2,000?" |
| `trip-checklists` | "What should I pack?" |
| `sync-calendar` | "Put the trip in my Google Calendar" |
| `export-itinerary` | "Make a PDF I can send to my partner" |
| `traveller-profile` | "Remember my home airport is Bristol" |

## Commands

- `/new-trip` — start planning (e.g. `/new-trip Lisbon in September`)
- `/concierge` — on-trip mode: "we're here, what now?"

## Connectors

Travel Concierge uses **17 official, publicly available connectors** — no API keys
to manage; each prompts you to sign in on first use:

Booking.com · Expedia · Super.com · lastminute.com · DirectBooker ·
Tripadvisor · Wyndham Hotels and Resorts · Otto Travel · Kiwi.com · Ryanair ·
Viator · Veltra Activities · AllTrails · Resy · Uber · Uber Eats ·
Google Calendar

You don't need them all — and you shouldn't start with them all, or you'll
face a wall of sign-in prompts. **Start with five**: Booking.com, Kiwi.com,
Viator, Tripadvisor and Google Calendar cover most trips; connect the rest
when a skill asks for them (deals, dining, rides, in-chat booking). Skills
use whatever is connected and say so when a useful one is missing. See [CONNECTORS.md](CONNECTORS.md) for the category
map, alternatives, and exactly which connectors can act (book, order,
reserve) versus search-only.

## Installation

**Claude Code / Cowork (from this repo as a marketplace):**

```
/plugin marketplace add <your-github-user>/travel-concierge
/plugin install travel-concierge
```

**Or from a packaged file:** download `travel-concierge.plugin` from Releases and
open it in Claude Cowork.

## How a trip is organised

Travel Concierge keeps everything in files in your working folder, so the same
context serves you from first idea to final day of the trip:

```
travel/
├── traveller-profile.md          # optional, cross-trip preferences
└── trips/lisbon-2026-09/
    ├── trip-brief.md             # your answers & chosen bookings
    ├── itinerary.md              # the living day-by-day plan
    ├── budget.md                 # running costs vs your ceiling
    ├── options/                  # saved comparisons
    └── checklists/               # packing & pre-trip lists
```

## Notes

- Prices and availability come live from connectors at search time and can
  change; anything not live-priced is clearly marked as an estimate.
- Anything that spends money in-chat (Otto Travel bookings, Resy
  reservations, Uber rides, Uber Eats orders) happens only after the exact
  item and total are shown and you explicitly confirm.
- Visa and entry requirements are verified by search per your nationality —
  always double-check the official source linked.
- No payment details or passport numbers are ever stored in the trip files.

## Publishing tips

For GitHub search visibility, add these repository **topics** after pushing:
`claude-plugin`, `travel`, `travel-concierge`, `trip-planner`, `itinerary`,
`travel-assistant`, `claude`, `mcp`.

## Licence

MIT — see [LICENSE](LICENSE).
