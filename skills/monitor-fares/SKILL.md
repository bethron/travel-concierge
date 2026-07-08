---
name: monitor-fares
description: >
  This skill should be used whenever the user wants to watch or re-check
  flight prices — phrases like "track this fare", "watch prices for", "tell
  me if it gets cheaper", "has the price dropped", "check my fares", "should
  I book now or wait", or when a traveller hesitates on a flight and wants
  to keep an eye on it.
metadata:
  version: "0.1.0"
---

# Monitor Fares

Keep a fare watchlist, re-check it on demand, and advise honestly on
book-now versus wait.

## Be honest about the mechanism

Claude cannot run in the background: fares are re-checked **when asked** (or
whenever a session touches the watchlist), not continuously. Say this when a
watch is created. Offer to create a recurring "Check my fares" reminder or
Google Calendar event (every 2–3 days, via `sync-calendar`'s connector) so
the traveller remembers to ask — with their consent.

## The watchlist — `travel/watchlist.md`

```markdown
# Fare Watchlist

## LHR → LIS, out 07 Sep, back 12 Sep, 2 adults
- **Target:** ≤ £120 pp return · **Watching since:** 2026-07-06
- **History:**
  | Checked | Best price (pp) | Source | Airline |
  |---|---|---|---|
  | 2026-07-06 | £142 | Kiwi.com | TAP |
```

One section per watched route; append a history row on every check. Keep the
search parameters exact (airports, dates or date window, party, cabin) so
checks compare like with like.

## Checking

On "check my fares" (or the `/check-fares` command): re-run each watch
through the flight connectors (Kiwi.com, Expedia; Ryanair for its routes —
its cheapest-per-day tool suits date windows), append results, then report
per watch: current best, change since last check and since watching began,
and whether the target is met.

## Advice, honestly

- Target met → say so plainly and offer to proceed to booking via
  `find-flights`.
- Trend advice must come from the recorded history, not folklore: rising
  across checks near departure usually keeps rising; do not invent "prices
  drop on Tuesdays" claims.
- Always state the risk both ways: waiting can save money and can lose the
  good fare. The decision stays with the traveller.
- When a watch's trip gets booked or its dates pass, offer to retire it.
