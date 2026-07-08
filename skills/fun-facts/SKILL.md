---
name: fun-facts
description: >
  This skill should be used to surface surprising, non-obvious facts about a
  destination — triggers include a destination being set during trip
  planning, and direct asks like "fun facts about Lisbon", "did you know
  anything interesting about Japan", "tell me something cool about this
  place", "trivia about", or "something to tell my friends about". Also use
  it proactively, once, when a trip's destination is confirmed, and during
  on-trip downtime when the traveller wants a spontaneous nugget about where
  they are.
metadata:
  version: "0.1.0"
---

# Fun Facts

Give the traveller genuinely surprising, shareable facts about a
destination — the kind that make people say "wait, really?" and repeat it to
a friend. Never generic tourist-brochure trivia.

## What counts as a good fact

- **Non-obvious**: skip anything in the first paragraph of a guidebook
  (population, "it's the capital of…", "famous for its tower"). If it's the
  first thing a search result says, it's not a fun fact — dig further.
- **Verifiable**: search the web to confirm before using it; do not rely on
  memory alone, since specifics (numbers, records, "only place in the
  world…") are exactly where memory drifts and dates fastest.
- **Concrete and specific**: a precise, odd detail beats a vague claim. "The
  city has more canals than Venice" beats "the city has lots of water".
- **Light by default**: aim for delight and conversation value. Avoid
  anything grim, tragic, or a sensitive stereotype unless the trip itself is
  history/heritage-focused and the traveller would want that depth — and
  even then, handle it respectfully rather than as a shock fact.

## Tailor to the trip

Read `trip-brief.md` for the template and interests, and pick facts that
match:

| Trip flavour | Lean towards |
|---|---|
| Food & drink / gastronomy | Culinary origins, odd food laws, surprising ingredient history, where a dish "actually" comes from |
| Adventure & outdoors | Geological oddities, wildlife quirks, record-holding terrain |
| Culture & history | Overlooked history, surprising architectural stories, etymology of place names |
| Family holiday | Fun, safe-for-all-ages, nothing grim |
| Business trip | Quick, sharp, good for small talk with local colleagues or clients |
| No clear flavour / Surprise me | A broad, varied mix |

For multi-city trips, tailor per city, not just once for the whole trip.

## Delivering facts

- Format as a short "Did you know…?" line, one or two sentences, no more
  than 3–5 per delivery — a handful of great facts beats a wall of trivia.
- During trip planning: offer once, right after the destination is set,
  framed as a small bonus, not a mandatory step — easy to skip.
- On-trip (via `on-trip-concierge`): offer when the traveller has downtime
  or asks directly; can tie a fact to where they physically are if that
  context is available.
- Keep a running list of facts already shared in
  `travel/trips/<trip>/fun-facts.md` (one line per fact) so repeat requests
  during a trip surface new ones rather than repeating.

## Care points

- If a search turns up conflicting claims (a popular "fact" that's actually
  a myth), say so — "widely claimed, but…" — rather than repeating a myth as
  true.
- Keep the tone playful and genuine, never like padded content or an ad for
  the destination.
- Don't let this delay the actual planning — it's a garnish, not the main
  course.
