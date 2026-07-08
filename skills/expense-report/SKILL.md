---
name: expense-report
description: >
  This skill should be used whenever the user wants trip costs as a
  spreadsheet or a wrap-up of what the trip cost and saved — phrases like
  "export my expenses", "expense report", "spreadsheet of the costs", "what
  did the trip cost in the end", "how much did I save", or at trip wrap-up
  when receipts were requested (business trips) or a final summary would
  help.
metadata:
  version: "0.1.0"
---

# Expense Report

Turn `budget.md` into a proper spreadsheet and close the trip with an honest
"what you saved" summary.

## The spreadsheet (.xlsx)

Build it with the platform's spreadsheet capability (follow its guidance)
from the trip's `budget.md`:

- **Expenses sheet** — one row per item: date, vendor, category, description,
  per-person, total, currency, status (committed/estimate), and — for
  business trips — a Business/Personal column so bleisure spend never mixes
  with reclaimable costs.
- **Summary sheet** — totals by category, committed vs estimates, versus the
  ceiling or policy cap, with a simple category chart.
- Formulas for the totals, not hard-coded numbers, so the traveller can edit.

Save to the outputs location and present it. Offer CSV if their expense
system prefers it.

## The savings summary — say thank you with numbers

Close with a short, warm wrap-up: **"This trip, Travel Concierge saved you
roughly £X and about Y hours of planning."** Compute both honestly:

- **Money saved**: for each booked item, compare the chosen price against
  the alternatives recorded at decision time in the trip's `options/` files
  (use the median comparable alternative, not the most expensive one — no
  flattering the number). Add any same-property price gaps found across
  sources (e.g. Super.com vs Booking.com). Show the per-item breakdown so
  the figure is auditable.
- **Time saved**: a stated heuristic — roughly 30 minutes of manual
  research per comparison run (flights, stays, activities, dining), plus 30
  minutes for itinerary assembly. Present it as "a rough estimate assuming
  you'd have done this research by hand".
- If `options/` has no recorded comparisons, skip the money figure rather
  than invent one, and say why.

Label both figures clearly as estimates. Offer to include the savings
summary as a third sheet in the spreadsheet and in the `export-itinerary`
document.

## Prerequisite kept elsewhere

The search skills save their comparison tables to
`travel/trips/<trip>/options/` when a pick is made — that ledger is what
makes the savings figure honest. If it is missing for this trip, note it for
next time rather than fabricating.
