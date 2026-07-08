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
- **Otto Travel** — live bookable inventory, and the only connector that can
  complete a booking in-chat using the traveller's saved payment method and
  loyalty programmes. Read its skill guide before first use; apply its stored
  preferences. Only book after showing the exact fare and getting explicit
  confirmation.
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

- Record the chosen flight (airline, times, price, booking link) in
  `trip-brief.md` and log the cost in `budget.md` (`trip-budget` skill).
- Anchor the itinerary: day 1 starts after landing, the last day ends before
  the departure airport cut-off.
- Link to the provider to complete the booking — or, if the traveller wants
  it booked now and Otto Travel is connected, book via Otto after explicit
  confirmation of the exact flight, fare and total, then record the PNR in
  `trip-brief.md`. Never claim anything else is booked.

## Care points

- Always state prices with currency and whether they are per person or total.
- Quote the fare rules the connector returns; never invent baggage allowances.
- Prices move: note that quotes were live at search time.
- **Business trips**: weight schedule reliability, direct routings and
  arrival buffers (evening before a morning meeting) over lowest price;
  respect any company policy in `trip-brief.md` and apply loyalty programmes
  via Otto Travel. Otto can also book for managed travellers (colleagues)
  where authorised — confirm the traveller identity before booking.
