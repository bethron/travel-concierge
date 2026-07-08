---
name: find-flights
description: >
  This skill should be used whenever the user wants flights — phrases like
  "find flights", "cheapest way to fly", "how do I get to", "flight prices",
  "flights from X to Y", "when is it cheapest to fly", or when a trip plan
  reaches the flight-search stage. Also use it for route questions ("does
  Ryanair fly to…", "can I fly direct from…") and flexible-date searches.
metadata:
  version: "0.1.0"
---

# Find Flights

Search live flight options via the **Kiwi.com**, **Ryanair**, **Expedia** and
**Otto Travel** connectors and present a clear comparison the traveller can
decide from.

## Connector strategy

- **Kiwi.com** is the general search engine: use it for any route worldwide,
  multi-airline options, and virtual interlining. Default here.
- **Expedia** — second broad-coverage search; run alongside Kiwi.com and
  merge, keeping whichever source is cheaper per option.
- **Ryanair** is best for intra-European budget routes: use its
  cheapest-per-day and cheapest one-way/round-trip tools when the route is in
  Ryanair's network or the traveller is price-first. Its route tools also
  answer "where can I fly from X?" questions.
- **Otto Travel** — a further live-inventory search source, plus stored
  travel preferences and loyalty programme numbers to apply to the search.
  Read its skill guide before first use. Search only: never place a booking
  through it.
- **Turkish Airlines** — brand-direct search when the traveller favours
  Turkish Airlines or holds Miles&Smiles status, and useful for routes
  connecting through Istanbul.
- Run the relevant searches in parallel and merge results, noting the source
  of each option.

If neither connector is available, ask the user to enable them, then fall back
to web search with a clear "indicative prices only" caveat.

## Inputs

Pull origin, destination, dates, party size and cabin preferences from
`trip-brief.md` and the traveller profile before asking anything. For rough
dates ("early September"), search a date window and use cheapest-per-day
results to recommend the best-value days.

## Presenting results

Show a comparison table of the 3–6 strongest options:

| Option | Airline(s) | Depart → Arrive | Stops | Duration | Bags | Price (pp) | Total |
|---|---|---|---|---|---|---|---|

Then give one plain-sentence recommendation and why (e.g. best balance of
price, timing and total journey time). Flag red-eye departures, tight
connections (<75 min), distant secondary airports (name the actual city
distance) and fare types that exclude cabin bags.

## After the choice

- Save the comparison table to `options/flights-<date>.md` — it feeds the
  end-of-trip savings summary (`expense-report` skill).
- Record the chosen flight (airline, times, price, booking link) in
  `trip-brief.md` and log the cost in `budget.md` (`trip-budget` skill).
- Anchor the itinerary: day 1 starts after landing, the last day ends before
  the departure airport cut-off.
- Link to the provider to complete the booking. Travel Concierge is
  search-only by design: it never places bookings or takes payment in-chat,
  and never claims anything is booked until the traveller says so — then
  record the confirmed details in `trip-brief.md`.

## Care points

- Always state prices with currency and whether they are per person or total.
- Quote the fare rules the connector returns; never invent baggage allowances.
- Prices move: note that quotes were live at search time.
- **Business trips**: weight schedule reliability, direct routings and
  arrival buffers (evening before a morning meeting) over lowest price;
  respect any company policy in `trip-brief.md` and surface the loyalty
  programmes stored in the traveller profile or Otto Travel so the traveller
  applies them when booking on the provider's site.
