# WanderPlan ✈️

**A travel agency in a Claude plugin.** WanderPlan plans complete trips for
individual travellers — flights, stays and activities searched live through
official connectors, assembled into a day-by-day itinerary you refine in
chat, with budget tracking, packing lists and a polished document to take
with you.

## What it does

- **Plan a whole trip** from a quick-start template (city break, beach,
  adventure, honeymoon…) plus a short interview — or just say "plan me a week
  in Lisbon".
- **Search live prices** for flights (Kiwi.com, Ryanair), stays (Booking.com,
  Super.com) and activities (Veltra Activities, Super.com experiences), with
  clear side-by-side comparison tables.
- **Build an interactive itinerary** you refine conversationally — "move the
  museum to Tuesday", "we land at 2pm now" — kept in a living file.
- **Track the budget** against your ceiling, with warnings before you
  overshoot and cheaper swaps suggested.
- **Prepare properly**: tailored packing lists and time-ordered pre-trip
  checklists.
- **Export** a polished Word or PDF itinerary to print or share.
- **Optional traveller profile** remembers your home airport, style and
  dietary needs across trips — only if you ask.

## Skills

| Skill | Say things like |
|---|---|
| `plan-trip` | "Plan a week in Japan in October" |
| `find-flights` | "Cheapest flights Manchester to Faro in June" |
| `find-stays` | "Find a hotel near the old town under £120 a night" |
| `find-activities` | "What should we do in Kyoto? We love food" |
| `manage-itinerary` | "Swap day 2 and day 3", "show me the plan" |
| `export-itinerary` | "Make a PDF I can send to my partner" |
| `trip-budget` | "Are we still under £2,000?" |
| `trip-checklists` | "What should I pack?" |
| `traveller-profile` | "Remember my home airport is Bristol" |

## Connectors

WanderPlan uses **official, publicly available connectors** — no API keys to
manage; each prompts you to sign in on first use:

| Service | Used for |
|---|---|
| Booking.com | Hotel search, property Q&A |
| Super.com | Hotel price benchmarking, experiences |
| Veltra Activities | Tours, classes, day trips |
| Kiwi.com | Worldwide flight search |
| Ryanair | Budget European flights, route maps, cheapest-day search |

See [CONNECTORS.md](CONNECTORS.md) for details and alternatives. WanderPlan
searches and compares; actual bookings are completed on the provider's own
site.

## Installation

**Claude Code / Cowork (from this repo as a marketplace):**

```
/plugin marketplace add <your-github-user>/wanderplan
/plugin install wanderplan
```

**Or from a packaged file:** download `wanderplan.plugin` from Releases and
open it in Claude Cowork.

## How a trip is organised

WanderPlan keeps everything in files in your working folder, so a trip
survives across sessions:

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
- Visa and entry requirements are verified by search per your nationality —
  always double-check the official source linked.
- No payment details or passport numbers are ever stored.

## Licence

MIT — see [LICENSE](LICENSE).
