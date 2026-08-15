---
name: trip-weather
description: >
  This skill should be used whenever weather should inform a travel decision —
  phrases like "will it rain", "what's the weather like", "do I need a
  jacket/umbrella", "is it safe to go out", "should we still do the hike",
  "how hot will it be", or any live "it's raining, what now" moment. Also use
  it proactively during trip planning to set rainy-day backups and packing,
  and whenever `find-activities`, `manage-itinerary`, `trip-checklists` or
  `on-trip-concierge` need a weather-dependent call.
metadata:
  version: "0.1.0"
---

# Trip Weather

Turn destination weather into decisions, not just numbers — the right call
for packing, itinerary backups during planning, and live in-the-moment plan
changes once the trip is under way.

## Connector

**Vaisala Xweather** — current conditions, hourly/daily forecast and
severe-weather alerts for a location. Precise forecasts run out to roughly 15
days; beyond that horizon, use seasonal/climate norms via web search and say
plainly that it's a norm, not a forecast.

If Xweather isn't connected, fall back to web search for current conditions
and forecast, clearly marked as not from a dedicated live source.

## When to check

- **Planning stage**: once destination and dates are set, check the forecast
  if travel falls within the connector's horizon; otherwise pull seasonal
  norms (average highs/lows, rainy season, monsoon/typhoon season, snow).
- **Itinerary build/refine** (`manage-itinerary`): flag days with a real
  rain/storm signal so a rainy-day backup is assigned to that day
  specifically, not just implied somewhere in the trip.
- **Packing** (`trip-checklists`): feed the real forecast, or seasonal norms
  beyond the horizon, into the packing list.
- **Weather-dependent activities** (`find-activities`): check the activity's
  date before recommending anything outdoor-dependent (hiking, boat trips,
  open-air tours).
- **On-trip, every session** (`on-trip-concierge`): pull current conditions
  and the next few hours before suggesting anything outdoors, and re-check
  before any plan change.
- **Direct ask**: "will it rain Tuesday", "what's it like out right now", "do
  we need umbrellas", "is the hike still a good idea".

## Turning forecast into a call

Report the decision, not just the numbers:

| Signal | Call |
|---|---|
| High rain/storm chance in the window | Recommend the rainy-day backup now, before the traveller is caught out; note it in `itinerary.md` |
| Severe weather alert (storm, extreme heat, flooding) | Surface it immediately, even unprompted; flag any booked activity or transfer it affects |
| Extreme heat/cold, high UV | Suggest timing adjustments (earlier start, shaded route) and packing (sun protection, layers) |
| Clear and unremarkable | Confirm the plan holds — no action needed, don't manufacture caution |
| Beyond the forecast horizon | Say so, give seasonal norms instead, and offer to re-check closer to departure |

## Care points

- Always state whether a number is a live forecast or a seasonal norm — never
  present a climate average as if it were today's forecast.
- Forecasts drift close to the date: re-check a flagged day as it nears
  rather than trusting a check from a week earlier.
- Don't alarm over routine weather — escalate proactively only for genuine
  disruption risk (severe alerts, a booked outdoor activity on a washout
  day), not ordinary cloud cover.
- On-trip, weigh comfort as well as safety: heat and rain change what's
  pleasant, not just what's possible.
