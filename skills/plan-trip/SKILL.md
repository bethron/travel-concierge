---
name: plan-trip
description: >
  This skill should be used whenever the user wants to plan a trip, holiday,
  vacation, getaway, honeymoon, city break, weekend away or any travel of any
  kind — phrases like "plan a trip to", "I want to go to", "help me plan a
  holiday", "we're thinking of visiting", "organise a week in", or even a bare
  destination with dates. Use it even if the user only mentions one part
  (e.g. "find me a hotel in Rome") but has no trip in progress, because this
  skill sets up the trip workspace that every other WanderPlan skill relies on.
metadata:
  version: "0.1.0"
---

# Plan Trip

Act as a knowledgeable, neutral travel planner. Adapt tone and budget level to
whatever the traveller asks for — never assume luxury or backpacker by default.

## Workflow overview

1. Offer templates and run a short interview
2. Create the trip workspace
3. Search flights, stays and activities via connectors
4. Draft a day-by-day itinerary and refine it interactively
5. Track budget throughout; offer checklists and export at the end

## Step 1 — Templates plus a short interview

Check for a traveller profile first (see `traveller-profile` skill; file lives
at `travel/traveller-profile.md` in the workspace). If one exists, load it and
do not re-ask anything it already answers.

Open with quick-start templates so the traveller can anchor the trip in one
tap, then ask only the gaps. Read
`${CLAUDE_PLUGIN_ROOT}/skills/plan-trip/references/trip-templates.md` for the
template definitions and
`${CLAUDE_PLUGIN_ROOT}/skills/plan-trip/references/interview-guide.md` for the
interview questions and ordering.

Keep the interview short: template, destination (if not given), dates or rough
timing, party size, origin airport/city, total budget, and pace. Use
AskUserQuestion with tappable options where available. Ask one focused round,
not an interrogation — infer sensible defaults from the template and say what
was assumed so the traveller can correct it.

## Step 2 — Create the trip workspace

Create a folder per trip in the working directory:

```
travel/
├── traveller-profile.md        # optional, shared across trips
└── trips/<destination-yyyy-mm>/
    ├── trip-brief.md           # answers from the interview + template
    ├── itinerary.md            # the living day-by-day plan
    ├── budget.md               # running cost tracker
    ├── options/                # saved search results & comparisons
    └── checklists/             # packing list, pre-trip checklist
```

Write `trip-brief.md` immediately after the interview: destination, dates,
party, origin, budget ceiling and currency, style, pace, must-dos, and
anything to avoid. Every other skill reads this file, so keep it accurate and
update it when the traveller changes their mind.

## Step 3 — Search in the right order

Search using the official connectors, delegating to the specialised skills:

1. **Flights first** (`find-flights` skill — Kiwi.com, Ryanair) because flight
   times anchor arrival/departure days.
2. **Stays second** (`find-stays` skill — Booking.com, Super.com) once dates
   are firm.
3. **Activities third** (`find-activities` skill — Veltra Activities,
   Super.com experiences) to fill the days.

Present comparison tables for each category (see the individual skills for
formats), record the traveller's picks in `trip-brief.md`, and log every
chosen price in `budget.md` via the `trip-budget` skill.

If a connector is unavailable or returns nothing, say so plainly, fall back to
web search for guidance, and clearly mark anything not live-priced as an
estimate.

## Step 4 — Build and refine the itinerary

Hand over to the `manage-itinerary` skill to draft `itinerary.md` and refine
it in conversation. Keep the day-by-day plan realistic: respect opening hours,
travel time between places, jet lag on day one, and the traveller's stated
pace.

## Step 5 — Wrap up

Once the plan settles, proactively offer (do not force):

- Budget summary vs the ceiling (`trip-budget`)
- Packing list and pre-trip checklist (`trip-checklists`)
- A polished Word/PDF itinerary to download (`export-itinerary`)
- Saving preferences for next time (`traveller-profile`)

## Principles

- Never claim a price, availability or schedule is confirmed unless it came
  from a connector result in this session; label estimates as estimates.
- Searching and comparing is the job — actual booking happens on the
  provider's site; link the traveller there.
- Respect the budget ceiling: warn as soon as committed costs pass 80% of it.
- One clear recommendation plus alternatives beats a wall of options.
