---
name: manage-itinerary
description: >
  This skill should be used whenever the user wants to build, see, change or
  discuss a day-by-day plan — phrases like "build the itinerary", "what's the
  plan for day 3", "move the museum to Tuesday", "swap those days", "add a
  rest day", "we land at 2pm now", "show me the itinerary", or after flights,
  stays and activities have been chosen and the trip needs assembling into
  days.
metadata:
  version: "0.1.0"
---

# Manage Itinerary

Own the living day-by-day plan: draft it, keep it in `itinerary.md`, and
refine it interactively in conversation.

## Drafting

Read `trip-brief.md` for chosen flights, stay, activities, pace and must-dos.
Write `travel/trips/<trip>/itinerary.md` using the exact format in
`${CLAUDE_PLUGIN_ROOT}/skills/manage-itinerary/references/itinerary-format.md`.

Sequencing rules:

- Day 1 starts after landing plus transfer; keep it light after long-haul or
  a late arrival.
- Cluster activities by geography to cut back-and-forth travel; state rough
  travel time between stops.
- Respect opening days/hours and any timed tickets; meals at sensible local
  times, naming one or two well-regarded nearby options as suggestions.
- Final day: nothing after the required departure for the airport
  (check-out time, transfer, check-in cut-off).
- Leave breathing room per the stated pace; mark one flexible backup
  (rainy-day option) somewhere in the plan.

## Refining interactively

This is the default mode after the first draft. When the traveller asks for a
change:

1. Apply it to `itinerary.md` (edit the file, do not just describe the change).
2. Resolve knock-ons — timing clashes, geography, opening hours — and say
   what else moved and why.
3. Show only the changed day(s) in chat, not the whole plan, unless asked.

Common moves: swap days, shift an activity, add/remove a rest day, react to a
flight change (re-anchor day 1 or the last day), add a late find.

## Showing the plan

When asked to "show the itinerary", render it in chat as a compact day-by-day
view (day heading, then morning/afternoon/evening lines). Offer the polished
export (`export-itinerary` skill) once the traveller sounds settled.

## Care points

- The file is the source of truth; keep chat and file in sync.
- Anything unconfirmed (estimate, unbooked) stays marked as such in the file.
- If a change breaks the budget ceiling, flag it via the `trip-budget` skill
  before finalising.
