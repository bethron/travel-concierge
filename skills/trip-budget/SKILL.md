---
name: trip-budget
description: >
  This skill should be used whenever money and the trip meet — phrases like
  "how much so far", "are we over budget", "what's left to spend", "track the
  budget", "can we afford", "cheaper option", or automatically whenever a
  flight, stay or activity is chosen so its cost gets logged against the
  ceiling.
metadata:
  version: "0.1.0"
---

# Trip Budget

Keep a running cost tracker in `travel/trips/<trip>/budget.md` and hold the
plan to the traveller's ceiling.

## File format

```markdown
# Budget — <Trip title>
**Ceiling:** £2,000 (total, incl. flights) · **Currency:** GBP

| Item | Category | Status | Per person | Total |
|---|---|---|---|---|
| LHR→LIS return, KL1234 | Flights | Committed | £120 | £240 |
| Hotel Exemplo, 4 nights | Stay | Committed | — | £520 |
| Food tour | Activities | Committed | £55 | £110 |
| Meals (4 days, est.) | Food | Estimate | — | £320 |
| Local transport (est.) | Transport | Estimate | — | £40 |

**Committed:** £870 · **Estimates:** £360 · **Projected total:** £1,230
**Headroom vs ceiling:** £770 (39%)
```

## Rules

- Log every chosen flight, stay and activity the moment it is picked; keep
  the summary lines recalculated on each edit.
- Add sensible estimates for the unpriced realities — meals, local transport,
  airport transfers — scaled to destination and style, and mark them
  Estimate.
- Convert to the traveller's currency; note the rate used for conversions.
- **Warn at 80%** of the ceiling and on any single pick that would cross it,
  offering one or two concrete cheaper swaps.
- When asked "what's left", answer with headroom and the biggest remaining
  unpriced items.
- Present spend visually when helpful (category breakdown as a simple table
  or chart where the interface supports it).
